---
title: "Simple question regarding hard drives"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by JonnyFunFun on 2005-09-11
Hi!  I currently have Ubuntu running flawlessly on my desktop with a SATA 120gb hard drive (I finally made the switch to all-Linux after seeing Cedega and CrossOver).  Now I have a SATA 250gb coming in the mail that I want to switch the OS to.  Can I just use something like Norton Ghost to copy the partitions from the 120 over to the 250 and boot accordingly, or will I have to set up Ubuntu all over again from scratch and copy my documents over after setting it up?  I currently have it running exactly how I want it running all the Windoze software I need so I would like to try to not have to set it up again.  Thanks for the responses in advance.

---

### Post by mlomker on 2005-09-11
Ghost should work.  Most linux geeks [use this bootable CD.](http://www.sysresccd.org/download.en.php) It isn't as user-friendly as Ghost, though.

---

### Post by JonnyFunFun on 2005-09-11
So I shouldn't need to make any changes to any configuration files or the grub config at all, just a simple copy and go?

---

### Post by mlomker on 2005-09-11
[QUOTE=JonnyFunFun]So I shouldn't need to make any changes to any configuration files or the grub config at all, just a simple copy and go?[/QUOTE]

Not if you are replacing the current drive.  Grub needs to know the drive number and partition number, but that won't change if you are swapping out.  You'll need to change grub if you are adding this drive rather than replacing...

---

