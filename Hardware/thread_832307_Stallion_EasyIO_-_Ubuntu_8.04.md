---
title: "Stallion EasyIO - Ubuntu 8.04"
date: 2008-06-17
forum: Hardware
---

### Post by kdepa on 2008-06-17
I am trying to use a Stallion EasyIO 4-port serial card with my install of hardy heron.  Unfortunately, the drivers on Stallion's (now lantronix) website are for a 2.2.x kernel, and it says to use the drivers that come with newer versions of the linux kernel if using 2.3.x or greater.  

If I do an lspci, the card is seen:  

[INDENT]00:0f.0 Communication controller: Stallion Technologies, Inc. EasyIO (rev 01)
[/INDENT]

However, when I do a dmesg | grep tty, it only shows the two built in serial ports:

[INDENT][   31.973887] console [tty0] enabled
[   34.420238] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.420763] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   34.422544] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.423544] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   80.329733] audit(1213734661.595:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4694 profile="/usr/sbin/cupsd" namespace="default"
[/INDENT]

How would I go about getting this card to work?

---

### Post by daniele75 on 2008-11-04
Hello.
Have you found a solution?
I've also a Stallion multiserial port and it seems ubuntu doesn't load the drivers (but from lspci I can see it properly).

Thanks
Daniele

---

### Post by kdepa on 2008-11-04
Unfortunately I haven't.  I had to resort to using windows in order to get the card to work.  I really wish I could use it in Ubuntu though.

---

