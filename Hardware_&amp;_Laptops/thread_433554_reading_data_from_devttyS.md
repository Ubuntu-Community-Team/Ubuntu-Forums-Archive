---
title: "reading data from /dev/ttyS*"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by atasmrk on 2007-05-05
I am trying to read some data from serial line, however, I am getting nothing, no matter what program I use (slsnif, gtkterm...).

Device sending the data is homemade, but it works with Windows and it worked in Debian right before I switched to Ubuntu (I am using Dapper Drake 6.06).

Some information about the system is provided below,

```

anze@atasmrk:/dev$ dmesg | grep tty
[17179570.860000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.860000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179570.864000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179570.864000] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

anze@atasmrk:/dev$ ls -lA ttyS1
crw-rw---- 1 root dialout 4, 65 2007-05-05 12:29 ttyS1

anze@atasmrk:/dev$ groups
anze adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin


```

Is there something I missed?

---

### Post by pbeeson on 2007-05-08
If you figure this out on your own.  Please post the solution.  I am in the exact same position as you, can read from a homemade serial device just fine in FC3, but not Dapper.

---

### Post by pbeeson on 2007-05-10
I don't know if your solution will be a easy as mine.  Turns out the software I was using in Fedora Core that worked just fine, had hardware flow support enabled.  But, this caused problems in Dapper.  Turned this off, and it works normally in Dapper.  Hope this help you.

---

