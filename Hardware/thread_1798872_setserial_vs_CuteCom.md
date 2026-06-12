---
title: "setserial vs CuteCom"
date: 2011-07-06
forum: Hardware
---

### Post by chrisstankevitz on 2011-07-06
Hi,

Q1: Why would I use setserial to set a serial port's baud rate when every program that uses a serial port allows me to set the baud rate?

Q2: When when I use CuteCom to set /dev/ttyS0 to 9600 bps and click "open device", the command "setserial -G -a /dev/ttyS0" reports that the baud rate is 115200.  I would have expected that CuteCom set the rate to 9600 and "setserial -G -a" would report the same number: 9600  Why doesn't setserial report 9600, the rate CuteCom just set?

Q3: Is it true that if I use setserial to configure /dev/ttyS0, I can write to the serial port by writing to /dev/ttyS0 and read from the port by reading /dev/ttyS0?  If so, what if anything will cause the configuration to change such that I need to re-issue the setserial command?  (e.g. reboot, CuteCom, etc)

Thank you,

Chris

---

