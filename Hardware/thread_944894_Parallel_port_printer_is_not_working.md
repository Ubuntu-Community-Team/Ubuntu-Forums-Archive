---
title: "Parallel port printer is not working"
date: 2008-10-11
forum: Hardware
---

### Post by WattoDaToydarian on 2008-10-11
I am having trouble getting my printer to work on my server using CUPS.

I have a Canon LBP-460WL which works using this third party driver [http://www.boichat.ch/nicolas/lbp660/](http://www.boichat.ch/nicolas/lbp660/) which I have used before on the Clarkconnect distro.

My server is a HP Netserver 6000r running Ubuntu 8.04 and Linux 2.6.24-21-server. One thing that I noticed is in the CMOS config it says it only supports bi-directional and ECP both of which are not listed in the parport module which supports PCSPP,TRISTATE,EPP (copied and pasted from my kernel log) but it does show my printer in the kernel log and in the CUPS web admin page. I have tried both LPT modes.

This is the output section of my kernel log where parport gets loaded:
```
[  173.970279] parport0: PC-style at 0x378 (0x778) [PCSPP,TRISTATE,EPP]
[  174.108627] parport0: irq 5 detected
[  174.110431] parport0: Printer, Canon LBP-460WL
[  174.111408] lp0: using parport0 (polling).
[  174.152526] ppdev: user-space parallel port driver
[  174.955498] audit(1223771905.961:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5415 profile="/usr/sbin/cupsd" namespace="default"

```
This is the output I receive when I tried to print 4 test pages:
```
[ 1069.017783] audit(1223772800.422:4): type=1503 operation="capable" name="sys_rawio" pid=8768 profile="/usr/sbin/cupsd" namespace="default"
[ 1196.769836] audit(1223772928.231:5): type=1503 operation="capable" name="sys_rawio" pid=8791 profile="/usr/sbin/cupsd" namespace="default"
[ 1200.878962] audit(1223772932.340:6): type=1503 operation="capable" name="sys_rawio" pid=8804 profile="/usr/sbin/cupsd" namespace="default"
[ 1238.880930] audit(1223772970.362:7): type=1503 operation="capable" name="sys_rawio" pid=8819 profile="/usr/sbin/cupsd" namespace="default"

```
I am suspecting that these audit messages are a part of some kind of security software that blocks access to the parallel port which doesn't make much since but that's all I can figure out.

What gives:confused:

---

### Post by WattoDaToydarian on 2008-10-11
I forgot to add that in the CUPS admin page on the Printers tab it says ```
LBP-460 "/usr/lib/cups/filter/foomatic-rip failed"
``` on the line containing the name I gave my printer.
Also on the Jobs tab it says "Unknown" under "Pages" and "stopped" under "State".:(

---

