---
title: "Laptop does not switch off"
date: 2007-04-16
forum: Hardware &amp; Laptops
---

### Post by freshman on 2007-04-16
Hello,
trying Ubuntu 7.04 on Thinkpad 600E. **acpi** (or apm?) works correctly - Gnome shows the battery status, etc.

When I shut down laptop, it does not smitched power completely. What could be a problem?
Thanks in advance.

---

### Post by mac.ryan on 2007-04-16
Can you be more specific? Where does the shutdown script exactly stop? Is there any similarity with [this]("http://ubuntuforums.org/showthread.php?t=404062") issue?

---

### Post by freshman on 2007-04-16
> **mac.ryan said:**
> Can you be more specific? Where does the shutdown script exactly stop? Is there any similarity with [this]("http://ubuntuforums.org/showthread.php?t=404062") issue?
Yes, it is exactly the same thing. 

**# shutdown -f  ** puts laptop to some strange state - totally jammed with continuous beep from the system speaker. 

By the way, just have found: there is a line during booting, something like "...ACPI failed. To enable ACPI use acpi=force option"

---

### Post by rustybronco on 2007-04-16
acpi=force is added to your /boot/grub/menu.lst   kernel boot line
I use gksudo nautilus and navigate to the menu.lst and after the quiet splash ro "stuff" add the "acpi=force and save it then reboot and shutdown to see if it worked.

---

### Post by freshman on 2007-04-16
Stupid questions...

What actually "acpi=force" does? Does it mean that apci does not work correctly now? (just thinking about gnome battery applet - shows status correctly)

---

### Post by rustybronco on 2007-04-16
My understanding of acpi=force is it forces the kerel to use acpi no matter what.

[http://www.acpi.info/](http://www.acpi.info/)

---

### Post by freshman on 2007-04-16
Hi, 
An investigation result:

the whole line from laptop's boot: **[ 0.00000] APCI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI** 

Adding acpi=force option in the menu.lst helps - laptop switches power off. But there is a nasty thing - if **acpi=force** is present, kernel does not detect PCMCIA Ethernet card (no HW in lspci list). 

If there is no such an acpi option, Ethernet card is present, network is Ok. ](*,)

---

### Post by freshman on 2007-04-18
Ok, acpi and PCMCIA  problems solved. Few options for menu.lst:
```

acpi=force pci=noacpi

```

found it here: [http://www.mueller.ch.vu/misc/tp600e_en.html](http://www.mueller.ch.vu/misc/tp600e_en.html)

---

### Post by Princeg1 on 2007-06-09
> **mac.ryan said:**
> Can you be more specific? Where does the shutdown script exactly stop? Is there any similarity with [this]("http://ubuntuforums.org/showthread.php?t=404062") issue?


Hi I am a first time ubuntu user, when I am trying to install Ubuntu on my IBM Thinkpad 600 E I am getting this msg
0.000000  ACPI : Bios age (1999) fails cut offf (2000), acpi =force is required to enable ACPI

[58.362838] invalid compression format (err=1)
[58.367134] kernel panic - not syncing : VFS : Unable to mount root fs on unkno wn-block(104,1)
[58.367213] 

and after a short period the system swithes off.

Can some one please help me with this.

Thanks

---

