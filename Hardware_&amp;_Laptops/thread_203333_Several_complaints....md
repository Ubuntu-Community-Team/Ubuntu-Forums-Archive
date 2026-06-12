---
title: "Several complaints..."
date: 2006-06-25
forum: Hardware &amp; Laptops
---

### Post by nolongerlivecd on 2006-06-25
[LIST=1]
[*]**CPU scaling problem! (Pentium M 2GHz 760)**
[*]Ubuntu still won't detect my external hard disk as writable...
[*]After using Windows, when I mute my sound, and I hibernate, then sound cannot work in Ubuntu
[*]SD card not detected (waiting for new kernel)
[/LIST]

---

### Post by hippy4life on 2006-06-25
dont complain! **Contribute!**

yeah, some things wont work and maybe never will, but most of the time these things get sorted, 

plus if you want help from other users trying being more detailed and open a thread for each problem.  Include all relivant info ie, sound card, kernels, any output from consoles/logs etc etc that way your fellow ubunters can help you to help yourself

---

### Post by ola on 2006-06-25
[QUOTE=nolongerlivecd]
Ubuntu still won't detect my external hard disk as writable...
[/QUOTE]
If your external hard disk is formated using NTFS you probably will have problems getting it to work. There have been some different approaches to deal with this, but as far as I know there are no out-of-the-box -experience for NTFS in Linux. You can see: [http://www.linux-ntfs.org/](http://www.linux-ntfs.org/) for more information.

[QUOTE=nolongerlivecd]
After using Windows, when I mute my sound, and I hibernate, then sound cannot work in Ubuntu
[/QUOTE]
My best guess here comes from a similar experience with wireless cards, from what I understand the computer needs some software to enable the hardware again and that software is probably only available under Windows.

[QUOTE=nolongerlivecd]
SD card not detected (waiting for new kernel)
[/QUOTE]
Using standard SD (Secure Digital) cards should work in Linux since they are found as standard usb drives.

If you want to file bugs on these matters you can always check out the Launchpad web site ([https://launchpad.net/)](https://launchpad.net/)).

Well, hope some of your questions were answered and good luck!

---

### Post by nolongerlivecd on 2006-06-25
2.6.15 doesn't support SD cards right?

---

### Post by nolongerlivecd on 2006-06-25
And perhaps you're right, I should change the title, to a few gripes. I'm still trying to code a simple linux program, "HELLO WORLD".

---

### Post by nolongerlivecd on 2006-06-26
UPDATE: Even after properly shutting down XP, and un-muting before that, I still get no sound. Also, cat /proc/cpuinfo keeps displaying 1995MHz even when the top panel shows it as 800MHz.

---

