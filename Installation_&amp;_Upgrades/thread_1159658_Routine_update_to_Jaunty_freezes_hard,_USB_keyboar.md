---
title: "Routine update to Jaunty freezes hard, USB keyboard locked on reboot, SSH broken"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by Mythbuster1848 on 2009-05-14
Hello everyone,

This is somewhere between a bug and a config problem. I installed Mythbuntu 9.04 without any issue. I've been using this install for a few weeks now. Last night I ran some routine updates and the box froze solid. On reboot, my keyboard locks up, even in recover mode (works fine in the BIOS and Grub though), even with the previous version of the kernel. 

That's fine, you say, just connect remotely. Unfortunately when I try to SSH in, I get an error message about not being able to allocate PTY0 on this channel. 

So here's what I know:

    Hardware is fine. I can run the Mythbuntu Live CD without any problems. 

    It's something in the init scripts that's causing the problem, because I get the same problem with two different kernels.

    File system seems to be ok. I did fsck on the boot and root partitions from the Live CD, no errors found, nothing in the lost+found directory. 

    
If I can just fix the keyboard problem or the SSH problem from the Live CD, I can get in to the system while it's running and figure out what happened. It think it's either the packages I was updating or some unrecovered error from the freeze and reboot that's causing this. 

Does anyone have any thoughts? I know I can just re-install, but I really want to find out what caused this and recover if possible, if only for the learning experience.

---

