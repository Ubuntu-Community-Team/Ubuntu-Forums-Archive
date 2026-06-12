---
title: "nVidia proprietary driver and LUKS"
date: 2016-11-14
forum: Hardware
---

### Post by staticx420 on 2016-11-14
I have a EVGA GeForce GT 740. With the Nouveau driver I routinely have my display freeze (can still ssh in). Under OS X (“Hackintosh”) I have zero stability issues. I’m in Linux 95% of the time.

If I try to use the proprietary driver I get to the password prompt (luks) but it won’t let me type in my password. I can’t figure it out. I can ctrl-alt-del and reboot the machine, but I can’t decrypt the hard drive. Any suggestions?

[FONT=Courier New]$ lspci -k | grep -EA2 'VGA|3D'
01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GT 740] (rev a1)
[INDENT]Subsystem: eVga.com. Corp. GK107 [GeForce GT 740]
Kernel driver in use: nouveau
[/INDENT]
[/FONT]

Thanks.

---

### Post by Bucky Ball on 2016-11-15
> **staticx420 said:**
> I&#8217;m in Linux 95% of the time.

Welcome. Which release of Ubuntu and which flavour? For instance, Ubuntu 16.04 or something else?

---

### Post by staticx420 on 2016-11-15
16.04. I installed it as regular Ubuntu, though I use Gnome 3.

---

### Post by staticx420 on 2016-11-16
Any suggestion?

---

### Post by Bucky Ball on 2016-11-17
Not really, but where are you trying to install the NVidia driver from? Try installing from 'Additional Drivers'. There should be the proprietary driver available there if there is one for your card.

You could also try running with 'nomodeset' as an option and see if that cleans things up with the Nouveau driver. When you boot to the list of kernels, highlight the one you want to boot and hit 'e' to edit (you may need to go through the 'Advanced' entry on the grub menu to get to the kernels). Find the line that ends:

```
quiet splash
```

Or any one or combination of those two words. At the end, add 'nomodeset', so the end of that line looks like:

```
quiet splash nomodeset
```

You can also remove the 'quiet splash' if you want, no diff. Follow the instructions at the bottom of the screen to save and reboot. Any luck?

---

