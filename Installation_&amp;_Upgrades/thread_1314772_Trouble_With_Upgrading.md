---
title: "Trouble With Upgrading"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by telecom369 on 2009-11-04
Hey,

So I recently tried to upgrade from 9.04 to 9.10. Everything went fine, until my computer restarted and I got an error saying "one or more of the mounts listed in /etc/fstab cannot yet be mounted"

I would use: mount -o remount,rw /

But I want to preserve my files, and I'm not sure that it will.

Any help?

---

### Post by cooper.z on 2009-11-04
you are luckier than me. you can see something after you upgrade to 9.10. 
I only got a black screen with a small ubuntu logo in the middle of the screen. and I cannot get any help after I read through the forum. :-(

---

### Post by antiram on 2009-11-04
but /etc/fstab is on / and must be mounted for reading this file. Try "cat /proc/mounts" or "mount" to see what is not mounted 

cooper.z, boot with the recovery boot entry, then you can see the error message. if the boot manager is not shown at boot then try pressing ESC (or cursor up/down keys) after bios

---

### Post by telecom369 on 2009-11-04
So what would I do if it's not mounted?

---

### Post by antiram on 2009-11-04
then you are in the buildin kernel shell. 
try mount your "/", eg. "mount /dev/sda1 /mnt". 
if you found your "/" then unmount, reboot to grub, press "e" to change the root=UUID=123xyz in the kernel commandline to root=/dev/sda1. Press return and "b" to boot

but your error message says that "/" is mounted. you could comment out the line in fstab, which is not mounted.

---

### Post by telecom369 on 2009-11-04
Except I am stuck in a Recovery Shell, which is Read-only. I can't edit fstab

---

