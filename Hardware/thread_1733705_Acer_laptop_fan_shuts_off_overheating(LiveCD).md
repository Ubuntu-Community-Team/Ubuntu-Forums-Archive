---
title: "Acer laptop fan shuts off overheating(LiveCD)"
date: 2011-04-19
forum: Hardware
---

### Post by bumr055 on 2011-04-19
Recently I've been trying to get a laptop going with ubuntu 10.04.  The problem I've been having is; the fan shuts off usually when I get to grub or load from liveCD.

I'm trying to reinstall ubuntu because my first attempt, the laptop of course overheated and crashed before completing the install.  The OS boots but, I would like to get the fan going and install fresh with no crashes/errors.

The fan is working and I've cleared the dust out.  It stays on sometimes when I restart multiple times, but never when loading from the LiveCD.

Still searching online but haven't found much to help during liveCD boot.  Bios has nothing useful, no fan readings/settings at all. very basic.


ACER ASPIRE 5315-2681  
Intel Celeron Processor 530  1.73GHz  
256MB Mobile Intel Graphic Media Accelerator X310

---

### Post by sanguinoso on 2011-04-19
Supposedly updating the bios can fix it, do you have a recent one?

---

### Post by bumr055 on 2011-04-19
Thanks.  I have V1.21.  Newest version on Acer website is 1.45.

Looking into updating it, never had to before.  Really don't want to brick the laptop.

EDIT:  Bios update is a windows exe file.. figures.

I don't think I'm really willing to trust wine for a bios upgrade.

I think I might just open the back and point a house fan while I try and install it again, unless maybe someone knows a good spot to solder the fan directly to power.  As long as it doesn't stay on when the laptops off.

---

### Post by ajgreeny on 2011-04-19
> **bumr055 said:**
> Thanks.  I have V1.21.  Newest version on Acer website is 1.45.

Looking into updating it, never had to before.  Really don't want to brick the laptop.

EDIT:  Bios update is a windows exe file.. figures.

I don't think I'm really willing to trust wine for a bios upgrade.

I think I might just open the back and point a house fan while I try and install it again, unless maybe someone knows a good spot to solder the fan directly to power.  As long as it doesn't stay on when the laptops off.
I think it is possible to update your BIOS using freedos, so have a read around this and see if it might help.
[http://www.freedos.org/](http://www.freedos.org/)
[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

I must add that I have never used it myself, nor updated any machine BIOS, so I may be barking up a badly wrong tree, but I'm fairly sure freedos can be used that way, when you have no windows to use.

---

### Post by bumr055 on 2011-04-19
[IMG]http://i54.tinypic.com/3581j87.jpg[/IMG]

[SIZE="4"]GREAT SUCCESS![/SIZE]:P
[IMG]http://i53.tinypic.com/2me38fs.jpg[/IMG]
Cool as a cucumber!

Now, lets see if I can't get the actual fan to turn on consistently if I turn off acpi.
Hopefuly I don't have to update my bios after all.:)

---

### Post by csunderland on 2011-04-21
Hi,

what did you do to resolve the problem, please?

---

### Post by sanguinoso on 2011-04-22
> **csunderland said:**
> Hi,

what did you do to resolve the problem, please?

He pointed a desktop fan at it to keep it cool during the install.

---

