---
title: "Reading data from /dev/ttyS0 [rs232]"
date: 2014-03-20
forum: Hardware
---

### Post by e-San on 2014-03-20
Hi!

Today i'm trying to read data from serial port.
Those data i would like to process (not the case in this topic) and write down to a file.

Communication looks like this:

- send to port one character (eg 0 up to 7);
- read 0 - 32kB (depending on sent number);

I tried minicom, cutecom, ct, screen and others but i can not find exact solution to write this down.
Datum consist from one number 0-255 so its represented in hex with two signs.

The problem is that minicom and others work as communication, so i do not know how to dump data.
I used [S-Jinn]("http://sjinn.sourceforge.net/commands.html") which seems to be exact what i need, but i cannot make it to read more than 1024.

So, how can i easily send one sign TO rs and then read all incoming data (eg. to text file - one datum per line)?

Some technical informations of transmission:
- Speed: 19200
- Parity check: No
- Stop bits: 1
- No. of data bits: 8
- Used lines: RxD, TxD, GND

Best regards!

[B]edit.
[/B]oh! and i prefer bash or python, since i know somehow those.

---

### Post by e-San on 2014-03-20
Found it!

```

import serial
import time
import sys


port = serial.Serial('/dev/ttyS0', 19200)


port.bytesize = serial.EIGHTBITS
port.parity = serial.PARITY_NONE
port.stopbits = serial.STOPBITS_ONE


print("Open")
port.close()
port.open()


print("Write")
port.write('0')

while True:
    print("Read")
    line = port.read()
    print line

```

---

