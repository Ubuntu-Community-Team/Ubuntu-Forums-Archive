---
title: "Grub not recognizing XP install"
date: 2009-09-27
forum: Installation &amp; Upgrades
---

### Post by reversed on 2009-09-27
I first installed Ubuntu 9.04 and have been running that. I realized I needed XP on the machine too so I used a gparted live cd and shrunk the main install, formated the new partition and installed xp. Following [these]("http://ubuntuforums.org/showthread.php?t=1014708") instructions for restoring grub bootloader I have been able to boot back into ubuntu. Now that I am into my main ubuntu installation I cannot seem to get grub to recognize the xp installation and can only boot to ubuntu.

Using fdisk -l I get something similar too (some numbers replaced with x, not using that system atm):
```
Disk /dev/hda: 1000 GB, x bytes
255 heads, 63 sectors/track, x cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           x       x+      83  Linux
/dev/sda2   *           x           x       x+       7  HPFS/NTFS
/dev/sda3               x           x       x        5   Extended
/dev/sda4               x           x       x+       82  Linux swap / Solaris


```I also see that the XP partition has the boot flag, if that matters.

Thanks

---

### Post by TiredBird on 2009-09-27
This probably a silly question but...

What do you have in the grub menu?

I looked at the link you referred to and I don't see anything explaining what you need to do to your grub menu.

---

### Post by reversed on 2009-09-27
> **TiredBird said:**
> This probably a silly question but...

What do you have in the grub menu?

I looked at the link you referred to and I don't see anything explaining what you need to do to your grub menu.

It is likely the issue, I just don't know how to fix it. 

I just have Ubuntu 9.04, kernal 2.6.28-15, 28-11, and memtest86+. I can paste the whole file if you need me to though.

---

### Post by TiredBird on 2009-09-27
Well I had it all typed and lost it. Sorry for the delay. I'll try again. Please be patient.

---

### Post by TiredBird on 2009-09-27
Go to the grub menu with your text editor:

sudo gedit /boot/grub/menu.lst

from a terminal screen.

That should give you a look at the grub menu. In that menu you will find an example of what you need to boot your XP partition. It will have 'chainloader' in it. copy that into the main part of the menu, remove the comment marks, (#), and change the partition reference. Based on you first post it should probably be (hd0,1). (In grubese, thats the 2nd partition of the first hard drive. Grub doesn't understand 'sd' and it uses numbers starting at 0 instead of 1.)

Let me know what you find. I'll keep checking the thread. (I'm waiting for answers to a couple of posts I've made so I'll be here for a while.)

---

### Post by reversed on 2009-09-27
Worked like a charm, Thanks!

---

### Post by TiredBird on 2009-09-27
Anytime.

Go to thread tools and mark the thread 'solved'.

---

