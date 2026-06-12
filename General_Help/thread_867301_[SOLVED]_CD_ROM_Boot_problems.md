---
title: "[SOLVED] CD ROM Boot problems"
date: 2008-07-22
forum: General Help
---

### Post by m005k on 2008-07-22
I installed Ubuntu 8.04 on my Toshiba laptop. It install without a hitch, I have sound and wireless. One thing I can no longer do is boot an other distro from my cd drive. It seem Grub just skips it altogether, even though I have my computer set to boot from the cd. I looked and Grub, but could not see how to make it boot from the cd. Could som eone help me with this?

Mike

---

### Post by logos34 on 2008-07-22
It's not grub but the Bios or the disc that's the problem.  Check to make sure the cdrom is set first in device boot order, ahead of hard disk.  Check the cd you're trying to boot--it must be burned as an image.  Verify the checksum of the iso

---

### Post by m005k on 2008-07-23
I'm using a Cd rom that boots just fine in my other computer. The cd drive in the laptop read the info on the cd correctly.???

---

### Post by m005k on 2008-07-23
I rechecked, my bios is ok and he CD ROM is ok as well.

---

### Post by logos34 on 2008-07-23
I've heard of a case of grub causing a problem in a windows-linux dual boot setup, where it wasn't recognized at boot in linux and consequently couldn't be accessed (but worked fine in windows). 

You might try [GAG bootloader]("http://gag.sourceforge.net/") just to see if indeed the bootloader could be at issue.  But I'm disinclined to believe grub is the culprit here because grub is located on the mbr and has nothing to do with booting the cdrom--that's handled in the Bios device boot order.  In all cases, to boot from a cd you set the cdrom first and the Bios looks for it, before it ever goes to the hard disk.  So maybe the cd drive is partly malfunctioning.

---

### Post by m005k on 2008-07-27
The final answer for me at least is booting the laptop without he hard drive plugged in. As soon as he CD starts to boot, I plug the HD back in. 
I tried formating the drive, but I used windows so grub was still here. I will later low level format my drive in linux, then start again. My laptop is about 2 or so years old and sees heavy use, so It could be that the hardware isn't up to snuff anymore.

Mike

---

