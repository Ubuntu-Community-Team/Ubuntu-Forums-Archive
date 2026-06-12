---
title: "Connecting with minicom to serial port of an EdgeRouter ERLite-3"
date: 2014-08-08
forum: Hardware
---

### Post by sedawk on 2014-08-08
I wasted a good amount of time by deciding to make use of the serial (console) port provided by
my new EdgeRouter ERLite-3, for which you need one of those funny blue cables with DB9 and RJ-45
connectors.
I tried minicom on two Ubuntu boxes, one old box with DB9 serial port and one with a
USB-to-serial 4-way adapter (Delock 61877).
It is finally working now, so I want to share my findings:
* Parameters for the serial console in the manual for the ERLite-3 are wrong, kind of
  mixed up or something, actually it is a "default" 115200 8N1 setup for minicom:
    pu baudrate 115200
    pu bits        8
    pu parity     N
    pu stopbits  1
* Nothing worked for me until I turned of (Hardware) Flow Control - which is turned on by default:
    pu rtscts     no
  (Can anyone tell me why this is turned on by default? Which devices need it turned on?)
* My Delock 61887 has four DB9 connector, labeled (with stickers) A,B,C,D and Ubuntu reports
   four serial ports when connected:: /dev/ttyUSB[0123]
   In my case A is actually mapped to /dev/ttyUSB3. Surprise, surprise!
* You might want to turn off any of the strings for modem communication by setting them to empty strings:
   pu minit
   pu mreset
   pu mhangup

Have fun!

---

