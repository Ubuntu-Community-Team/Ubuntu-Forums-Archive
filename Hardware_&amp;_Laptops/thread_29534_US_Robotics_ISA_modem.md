---
title: "US Robotics ISA modem"
date: 2005-04-24
forum: Hardware &amp; Laptops
---

### Post by josh2112 on 2005-04-24
Can someone give me some suggestions for getting my modem set up?  I'm using Hoary on an old Compaq Pentium II with an ISA US Robotics modem.  The modem is set (via jumpers) to COM4 and IRQ7, and I've done the appropriate setserial stuff (setserial /dev/ttyS3 irq 7).  Here is (hopefully) some useful information:

/var/log/mgetty> sudo setserial -g /dev/ttyS3
/dev/ttyS3, UART: 16550A, Port: 0x02e8, IRQ: 7

/var/log/mgetty> cat vg_ttyS3.log
....<snip>....
04/24 18:41:35 yS3  locking the line
04/24 18:41:36 yS3  tio_get_rs232_lines: TIOCMGET failed: Input/output error
04/24 18:41:36 yS3  WARNING: DSR is off - modem turned off or bad cable?
04/24 18:41:36 yS3  lowering DTR to reset Modem
04/24 18:41:36 yS3  TIOCMBIC failed: Input/output error
04/24 18:41:36 yS3  cannot turn off soft carrier: Input/output error
04/24 18:41:36 yS3  tcgetattr failed: Input/output error
04/24 18:41:36 yS3  cannot get TIO: Input/output error
04/24 18:41:36 yS3  mg_init_device failed, trying again
....<snip>....

As you can see vgetty is totally stumped.  I have the speed in voice.conf set as 115200, although this doesn't matter - minicom won't connect to it at any speed.

I had this thing working under Redhat 7.2 for over a year... I can't remember, but it seemed like setserial was the only thing I had to do and vgetty automatically detected it.  I haven't changed any BIOS settings, added or removed any hardware from the computer, or changed any jumper settings on the modem.

Any suggestions?

---

### Post by alastair on 2005-04-24
When you boot, does the kernel notice it?

Check : /var/log/syslog

---

### Post by josh2112 on 2005-04-24
> When you boot, does the kernel notice it? 

Looks like it:

/var/log> grep ttyS3 syslog
Apr 24 17:53:48 localhost kernel: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A

I guess IRQ = 3 is a default value and the IRQ gets set correctly once /etc/init.d/setserial is invoked, right?  Because I can do a setserial -g /dev/ttyS3 and it shows the correct IRQ (7)

---

### Post by az on 2005-04-24
[QUOTE=josh2112]Looks like it:

/var/log> grep ttyS3 syslog
Apr 24 17:53:48 localhost kernel: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A

I guess IRQ = 3 is a default value and the IRQ gets set correctly once /etc/init.d/setserial is invoked, right?  Because I can do a setserial -g /dev/ttyS3 and it shows the correct IRQ (7)[/QUOTE]

try changing the jumpers to make the irq right, or use another com (ttyS)

---

### Post by josh2112 on 2005-04-25
Set the jumpers to IRQ 3, and it works like a charm!  I wonder why IRQ 7 worked in Redhat and not Ubuntu, though.

Thanks for the help alastair, azz!

---

### Post by az on 2005-04-25
[QUOTE=josh2112]Set the jumpers to IRQ 3, and it works like a charm!  I wonder why IRQ 7 worked in Redhat and not Ubuntu, though.

Thanks for the help alastair, azz![/QUOTE]
Must be a kernel thing.

---

