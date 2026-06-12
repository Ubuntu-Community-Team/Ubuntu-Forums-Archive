---
title: "Dell Mini-9, Unable to install GRUB"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by ConfederateColonel on 2009-09-19
Each time I try to install  Ubuntu 9.04 onto a Dell Mini-9, I get the following error:

"Unable to install GRUB in /dev/mmcblk0"
"Executing grub-install /dev/mmcblk0 failed"

I have tried downloading from two different sites, created the USB drive image two different ways (1 on Windows, 1 on another Ubuntu machine) - each time I get the exact same result.

Any help would be greatly appreciated - thank you!

Stephen

---

### Post by quixote on 2009-09-20
A drive which the system registers as a usb drive is handled different from an ordinary hard disk.  I'm not sure if that's your problem, but in case it is, you might want to take a look here, [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) and see if any of that helps.  A regular CD iso on a USB stick, or smart card, won't work.

Once you're on Jaunty, there's a nice simple menu item to create bootable "usb" media, but I realize that doesn't help you on Hardy. :(

---

### Post by ConfederateColonel on 2009-09-21
Thanks, Quixote! I'll see where that takes me and then post the results. Again, thank you.

---

### Post by ConfederateColonel on 2009-09-21
I just checked, and that article seems to be aimed at problems getting the USB stick drive to work in the first place. I can get it to work just fine - it just fails at that one point in the installation.

---

