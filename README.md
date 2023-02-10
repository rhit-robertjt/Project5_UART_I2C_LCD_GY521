# Project5_UART_I2C_LCD_GY521
/*! \file */
/******************************************************************************
 *
 * Description: This project uses a terminal in UART mode to communicate with a
 * microcontroller. The microcontroller will interface with a MPU6050 in I2C
 * configuration and an LCD. Based on the chosen parameter in the terminal, the
 * MPU will be in 2g, 4g, 8g, or 16g mode, and the LCD will display the X-axis,
 * Y-axis, or Z-axis of the accelerometer in terms of gravity to the nearest mg.
 * The terminal is in 38400 8E1 and the DCO, MCLK, and SMCLK are at 12MHz.
 *
 * Author: Justin Roberts
 * Last-modified: 1/30/23
 *
 * An external LF crystal between LFXIN & LFXOUT is required for ACLK
 *                                  ___  ___
 *                                   |    |
 *               MSP432P411x        10k  10k     MPU6050
 *             ------------------    |    |    -----------
 *         /|\|     P1.6/UCB0SDA |<--|----|-->| SDA
 *          | |                  |   |        |
 *          --|RST               |   |        |
 *            |     P1.7/UCB0SCL |<--|------->| SCL
 *            |              Vcc |<---------->| ADD
 *            |                  |             -----------
 *            |                  |
 *            |                  |                LCD
 *            |                  |             --------
 *            |             P5.7 |----------->| RS
 *            |                  |            |
 *            |             P5.6 |----------->| En
 *            |                  |            |
 *            |                  |     8      |
 *            |              P4  |-----\----->| DB
 *            |                  |            |
 *            |                  |             --------
 *            |                  |
 *            |             PJ.0 |------
 *            |                  |     |
 *            |                  |    LFXT @ 32kHz
 *            |                  |     |
 *            |             PJ.1 |------
 *            |                  |
 *            |     P1.3/UCA0TXD |---------->  PC (echo)
 *            |     P1.2/UCA0RXD |<----------  PC
 *
*******************************************************************************/
