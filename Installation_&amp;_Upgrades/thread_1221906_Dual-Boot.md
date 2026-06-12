---
title: "Dual-Boot"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by Setarkos on 2009-07-24
Hi there

I recently installed Ubuntu 9.04 replacing my broken down Vista. I didn't leave a partition for Windows but now I think it might be a good idea to have Windows XP for some applications that don't work on Linux. Is it possible to create a Dual-Boot without losing my preferences and applications and data?

Thanks in advance

---

### Post by Partyboi2 on 2009-07-24
Hi, you can boot a Ubuntu live cd and use gparted (System>Admin>Partition Editor) and shrink down you Ubuntu partitions and make space for windows. Then install windows and after you have finished installing, boot the Ubuntu live cd again and follow [[COLOR=Blue]this [/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351")to restore grub.
Remember to backup your important stuff before working on partitions.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by pmlxuser on 2009-07-24
Its possible,

you can either use a virtual machine (install windows inside ubuntu) or

creat a partition while in ubuntu for windows.
and follow instructions from the web on how to install windows after ubuntu.
 
(i tell you its easier to install ubuntu after windows than windows after ubuntu )

If you follow the instructions well its possible not to loose anything at all..

---

### Post by raymondh on 2009-07-24
> **pmlxuser said:**
> 
(i tell you its easier to install ubuntu after windows than windows after ubuntu )


"Convenient" or "Simpler"  are better words, don't you think?  Recovering GRUB (the bootloader) is equally as easy, even for a beginner ;)

@ Setarkos

[Virtualization]("http://www.virtualbox.org/") has its' plus.  No need to reboot to use windows.  However, if Ubuntu misfires for some reason, so does your Windows .... until you get Ubuntu up and running.

A dual boot link for you.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by Setarkos on 2009-07-24
Thanks to everyone. It worked just fine.

---

