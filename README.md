# DYNAMIC OTP-DRIVEN SECURE ACCESS SYSTEM

## 🛡️ Project Overview

This project demonstrates a secure, time-limited access control system using One-Time Passwords (OTP) and GSM technology. It is designed using the LPC2148 microcontroller and communicates with a GSM module to deliver OTPs to the user's mobile. The system validates the password and OTP before granting access through a motor/LED mechanism.

## 🎯 Objective

To design and implement a microcontroller-based OTP verification system that:
- Authenticates users via a password.
- Generates and sends OTP to a registered mobile number via GSM.
- Validates OTP within a specific time using RTC.
- Provides or denies access based on OTP validity.
  
## 🔧 Hardware Requirements

- LPC2148 ARM7 Microcontroller
- GSM Module (M660A)
- 16x2 LCD Display
- 4x4 Matrix Keypad
- Switch
- LED / Bulb / DC Motor (with L293D driver)
- EEPROM (AT24C256)

---

## 💻 Software Requirements

- Embedded C Programming
- Keil µVision (C Compiler)
- Flash Magic (For flashing the microcontroller)

---

## 🧩 Modules and Files

Each peripheral is developed and tested individually before integrating into the main application.

- `lcd.c / lcd.h`: LCD control and display functions
- `keypad.c / keypad.h`: Matrix keypad scanning
- `uart.c / uart.h`: UART serial communication with GSM module
- `delay.c / delay.h`: Delay utilities
- `i2c.c / i2c.h`: EEPROM communication
- `projectmain.c`: Main application logic integrating all peripherals

## 🧪 Testing Steps

1. **LCD Module** - Display characters, strings, and integers.
2. **Keypad Module** - Display pressed key on LCD.
3. **EEPROM Module** - Byte/page write & read testing.
4. **UART Module** - Send/receive data; use UART interrupts.
5. **RTC** - Display current time using inbuilt RTC.
6. **GSM Module Testing**:
   - Manual testing using HyperTerminal:
     ```
     AT
     ATE0
     AT+CMGF=1
     AT+CMGS="MobileNumber"
     ```
   - Automatic testing using `gsm_init()` and `send_sms()` functions with UART interrupts.



## ⚙️ Final Execution Logic

1. Wait for the password via keypad.
2. Validate the password from EEPROM.
3. If valid, generate OTP and send via GSM.
4. Start timer using RTC.
5. Wait for OTP input within the defined time.
6. Grant or deny access based on OTP validity.
7. Support password update via external interrupt.



## 📦 How to Run

1. Flash all `.c` and `.h` files into LPC2148 using Flash Magic.
2. Connect GSM module, LCD, Keypad, and EEPROM.
3. Power on the system.
4. Follow the on-screen instructions on LCD.


## 📎 Notes

- UART interrupt-driven logic is mandatory for GSM functions.
- Validate GSM command responses before proceeding.
- All OTP and password values are stored/read from EEPROM.
