# esp32_lcd_tft
Interface 2.4" TFT display with esp32


Here is the steps to make 3.5"/2.4" MCUFriend TFT LCD works on ESP32:

1. Wiring
Follow wiring guidance by David Prentice in this post 269 :

#if defined(ESP32)       //regular UNO shield on TTGO D1 R32 (ESP32)
#define LCD_RD  2  //LED
#define LCD_WR  4
#define LCD_RS 15  //or LCD_CD - hard-wired to A2 (GPIO35) 
#define LCD_CS 33  //hard-wired to A3 (GPIO34)
#define LCD_RST 32 //hard-wired to A4 (GPIO36)

#define LCD_D0 12
#define LCD_D1 13
#define LCD_D2 26
#define LCD_D3 25
#define LCD_D4 17
#define LCD_D5 16
#define LCD_D6 27
#define LCD_D7 14
2. Library
Download "MCUFRIEND_kbv" and "adafruit gfx"from library manager

3. Edit
Edit the pinout definition in graphictest_kbv.ino file for matching with ESP32 pinout

#define LCD_CS 33 // Chip Select goes to Analog 3
#define LCD_RS 15 // LCD_RS = Register Select or LCD_CD = Command/Data goes to Analog 2
#define LCD_WR 4 // LCD Write goes to Analog 1
#define LCD_RD 2 // LCD Read goes to Analog 0
#define LCD_RESET 32 // Can alternately just connect to Arduino's reset pin
4. Upload
Finally upload graphictest_kbv.ino to test the LCD.

If it doesn't work, double/triple check the wiring. It use many wires, wrong wiring could happen.

NOTE: This 3.5" MCUFriend TFT LCD use 3.3V, it become very very hot when use 5V.
