---
title: "Using PL2303 converter on Ubuntu"
date: 2009-07-24
forum: Hardware
---

### Post by coderx on 2009-07-24
I have connected PL2303 to of USB ports and I need to get data from this converter. 
Here are quastions : 
1. This device creates new SERIAL PORT device ?
2. How to read data from PL2303 converter stream ?

All I see is this :
[LEFT]```

dummy@ubuntu:~$ dmesg | grep tty
[    0.004000] console [tty0] enabled
[ 2328.348995] usb 5-1: pl2303 converter now attached to ttyUSB0
[ 2389.626998] usb 5-1: pl2303 converter now attached to ttyUSB1
[ 2398.160597] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[ 3529.709688] pl2303 ttyUSB1: pl2303 converter now disconnected from ttyUSB1
[ 3533.602313] usb 5-1: pl2303 converter now attached to ttyUSB0

```

Any solutions ? :confused:
[/LEFT]

---

### Post by davidmohammed on 2009-07-24
at a guess - does this [website]("http://www.cyberciti.biz/tips/connect-soekris-single-board-computer-using-minicom.html") help?

---

