---
title: "Asus OLED device access problem"
date: 2009-08-20
forum: Hardware
---

### Post by threetwoone on 2009-08-20
I've been having a lot of trouble with my Asus G1Sn-B1's oled.  I've installed the driver and it sort of works but not how it should.

I am not able to access anything to do with the device.  I cannot open any of the files associated with it gedit gives me the following error message" Unexpected error: No such device".  The command "cat tux.txt > /sys/class/asus_oled/oled*/picture" gives me the error "cat: write error: Bad address".

The OLED Daemon will not run (obviously, given the problem is with accessing the device).
leds.log
```
ASUS G1 forced in the configuration file
Found an ASUS OLED device under '/sys/class/asus_oled/oled_1/picture'
Sorry, cannot find the asus_oled entry in /sys/class/asus_oled/. Please make sure you did all the following:
- grabbed the latest version of asus_oled from SVN
- executed make and make install for asus_oled
- rmmod usbhid; modprobe asus_oled; modprobe usbhid.
```Now for the catch.
```
echo "<s:32x32>000000000000011111110000000000000000000000001       100000000000000000000001         10000000000000000000001         10000000000000000000001         10000000000000000000001 1  111  10000000000000000000001    1 1   1000000000000000000001  111     1000000000000000000001 111111   1000000000000000000001 111111   1000000000000000000001    1 1    10000000000000000001      11    10000000000000000001 11111111    100000000000000001  11111111     1000000000000001   111111111    1000000000000001  1111111111     10000000000001   11111111111    10000000000001  111111111111     100000000001   111111111111     100000000001   111111111111     100000000001   111111111111     100000000001   111111111111     10000000000011 11111111111      10000000011 11  11111111111    1000000001  1111  111111111111111 1000001 1111111  11111111111111 1000001 1111111  1111111  111111 100001 11111111 111111   1111111 10001 11111111          11111  100001  1111111          111  11100000111   111   11111  11  100000000000111   111111111    1000000" > /sys/class/asus_oled/oled_1/picture
```Will change the picture on the device!!!  Displaying a very nice picture of Tux.  Using  this method I am able to turn the device on and off and manipulate the picture however I want.

I don't have a clue about how to fix this problem.  There are no other signs of an error.  Any and all help is appreciated.

---

### Post by threetwoone on 2009-08-21
Bump

---

### Post by AndyC_772 on 2009-11-01
The problem with "cat tux.txt > /sys/class/asus_oled/oled*/picture" is the asterisk, you need to change oled* to oled_1. 

I've just upgraded to 9.10 and, although I too can change the picture manually, I'd really like it to display a clock, or CPU temperature, or something even vaguely useful - but although I clearly have a driver installed, I can't find any applications that actually use the oled display.

Under 8.10 I had a clock on the oled display, but I can't remember how!!

Any ideas please?

---

### Post by threetwoone on 2009-11-21
The problem with the oled had to do with the kernel.  It is fixed in 9.10.

---

