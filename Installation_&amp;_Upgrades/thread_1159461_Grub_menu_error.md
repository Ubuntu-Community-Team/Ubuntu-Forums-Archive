---
title: "Grub menu error"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by lsearcey on 2009-05-14
I am having a problem after I chose the "Install inside Windows" option.  I did the install and rebooted I chose Ubuntu from the OS menu and it went to a black screen with only grub> to choose from what do I do next?

partial screenshot below:

[IMG]http://img207.imageshack.us/img207/5999/0514091825.jpg[/IMG]
By [lsearcey](http://profile.imageshack.us/user/lsearcey), shot with [1.3 Megapixel](http://profile.imageshack.us/camerabuy.php?model=1.3+Megapixel&make=Motorola) at 2009-05-14

---

### Post by Luke oX on 2011-02-23
bump

---

### Post by johnson094 on 2011-02-26
Hi got the same problem.  Identical screen shot, but just before that screen, this message flashes...
 
"Try (hd0,0) : NTSF5: error: no such device: /ubuntu/disks/root.disk. error: no such device: /ubuntu/install/boot/grub/grub.cfg"
 
I am runing Windows XP SP3 on a pentium 4 with 2 G RAM.  Trying to set this up for my nephew and wanted to install Ubuntu 10.04 inside Windows on a 160 GB HD
 
Thanks 
 
David

---

### Post by Luke oX on 2011-02-26
@johnson094

Here is my current thread on the problem. 

[http://ubuntuforums.org/showthread.php?t=1693673](http://ubuntuforums.org/showthread.php?t=1693673)

---

### Post by Rubi1200 on 2011-02-26
@Luke oX: this is not the same problem and you are confusing users by directing them to your thread.

You have a problem with a regular Ubuntu install and the GRUB bootloader.

This thread was started by a user with a Wubi install. Wubi does not use GRUB in the MBR, so advising people to look at solutions which will break their install is clearly not very helpful.

@johnson094:

please refer to the [Wubi Megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for problems and solutions. I suggest you begin by posting the results of the boot info script.

---

### Post by Luke oX on 2011-02-26
Thanks for correcting me Rubi so there wasn't further problems, I'll have to check for that in the future.

---

