---
title: "Serial Mouse on Dell C400"
date: 2011-06-03
forum: Hardware
---

### Post by JohnBN on 2011-06-03
I want to get a serial mouse (PS/2 with adapter) to work on a Dell C400 notebook (so I can use the one USB for wireless).
I enabled the serial port in the BIOS, but the mouse didn't work.
 
Help!

---

### Post by Perkins on 2011-07-07
The program you need is called input attach.  You can get it via:
```
sudo apt-get install inputattach
```

Then you test it with:

```
inputattach -<mouse type> /path/to/serial/device
```

A full list of mouse types may be found with:
```
man inputattach
```

It may take a little guesswork.  For example: my Kraft trackball uses the mouse systems protocol.

Serial devices are, with few exceptions, located under /dev/ttyS*.

Your port is probably ```
/dev/ttyS0
``` as it's the only one.

Once you get it working, you can make it run on startup by adding it to /etc/rc.local with an & at the end of the line.

---

