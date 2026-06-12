---
title: "CD/DVD writer not recognized in Gutsy"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by alvisetrevi on 2007-10-28
Hi all,

I have a Leonovo 3000 N200 laptop. I just installed Gutsy. Unfortunately, the CD/DVD writer does not seem to be detected (e.g. K3B says on startup "No CD/DVD writer found".
The releveant lines from lspci -v are:

```

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Lenovo Unknown device 3c2b
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]

```

dmesg gives, among the other messages, the following:
```

[   22.145573] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

```

It did not help...
Any ideas?

Thank you,
Alvise

---

### Post by alvisetrevi on 2007-11-06
Anyone?

---

### Post by dabl on 2007-11-06
This drive shows up in BIOS?  Did you use it to install Gutsy?  Is there a mount line for it in /etc/fstab?

K3b is not exactly the "acid test" for a CD/DVD drive -- I think mine is actually on the fritz at this moment -- wodim drivers or something screwed up (again). If it looks normal in /etc/fstab, you might want to give brasero a shot.  :)

---

### Post by alvisetrevi on 2007-11-07
Thanks for the reply!

Yes, the drive shows up in BIOS and I used it to install Gutsy from the CD. 
There is no line for the drive in /etc/fstab though, and I just realized it does not work as reader too...

I really have no idea how to fix this... maybe a newer kernel? I am not too fond of the idea of messing around with it however...

Alvise

---

