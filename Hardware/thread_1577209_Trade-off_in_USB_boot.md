---
title: "Trade-off in USB boot"
date: 2010-09-18
forum: Hardware
---

### Post by Tibuda on 2010-09-18
I have just "burned" the Ubuntu 10.10 beta to a USB drive using Unetbootin. I have never used boot from USB, but I'm trying now. My problem is: my BIOS can't see the USB drive unless I enable "Legacy USB support" in the BIOS settings, but if I enabled this option, I can't boot any Linux distro ([as I have found before the hard way](http://ubuntuforums.org/showthread.php?t=1384371)).

Is there another way I could boot from the USB drive? Perhaps using the installed GRUB?

---

### Post by Lateralis on 2010-09-18
Probably!  

I installed Arch linux to an external USB hard drive, which of course installed Grub to that drive.  My laptop is supposed to boot from USB but for some reason it didn't boot Arch when that hard drive was plugged in.  (Yes, I changed the boot order in the BIOS!)  I would instead get taken to the Grub installed on my laptop.  (Haven't tried on my desktop but I suspect the same thing will happen.)  So, I edited my grub menu and added an entry which pointed to the USB hard drive.  Selecting that entry takes me to the Arch grub menu, from which I can boot to Arch.  Slightly convoluted, but it works. :)  

Whether something similar will work for you or not I don't know but maybe there's a way you can get it to work?

---

### Post by Tibuda on 2010-09-19
Thanks for the answer!

I have contacted the manufacturer support, and they said it would not be possible to boot a Linux distro from USB, so I just burned a CD and installed it.

This is solved.

---

