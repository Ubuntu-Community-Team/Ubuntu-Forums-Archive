---
title: "Computer wont boot from cd after installation"
date: 2008-02-27
forum: Hardware &amp; Laptops
---

### Post by Jre35 on 2008-02-27
Hello, 
I installed ubuntu in a dual boot with windows xp two weeks ago, and this weekend, my computer stalled on the boot screen for 10+ minutes. It eventually sped up, but now im having some issues. My computer wont boot from a cd, it recognized them after it is booted, and while it is booting, i get the "press any key to boot from cd..." message, but it just stays on a black screen and doesnt boot and the CD drive isnt moving. Is there a way i can reinstall windows and Ubuntu from the other OS? If i boot into linux and insert the Windows XP boot cd, can i install windows into the partition windows is already in from ubuntu? Would i need a program in order to be able to write to the disk in windows format if it is possible?

THanks in advance.

---

### Post by dabl on 2008-02-27
> **Jre35 said:**
> Hello, 
I installed ubuntu in a dual boot with windows xp two weeks ago, and this weekend, my computer stalled on the boot screen for 10+ minutes. It eventually sped up, but now im having some issues. My computer wont boot from a cd, it recognized them after it is booted, and while it is booting, i get the "press any key to boot from cd..." message, but it just stays on a black screen and doesnt boot and the CD drive isnt moving. Is there a way i can reinstall windows and Ubuntu from the other OS? If i boot into linux and insert the Windows XP boot cd, can i install windows into the partition windows is already in from ubuntu? Would i need a program in order to be able to write to the disk in windows format if it is possible?

THanks in advance.


Unless you have some idea of the cause for the "stalled on the boot screen" problem, this sounds like some kind of hardware issue -- a failing hard drive or other component.  I would either start testing things myself, or have it looked at by someone who knows how.

If the hardware is all good to go, then "YES" you should be able to install (1) first Windows, and then (2) Ubuntu.  That's the right sequence to keep from having to edit the menu file yourself.  You need multiple disk partitions -- one for Windows and a minimum of two ("/" and "swap") for Linux.  Use GParted for disk partitioning -- if it's not still on the Ubuntu Live CD, download the ver. -10 ISO and burn a Gparted Live CD from here:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

:)

---

