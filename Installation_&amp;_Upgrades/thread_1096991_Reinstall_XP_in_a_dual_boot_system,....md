---
title: "Reinstall XP in a dual boot system,..."
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by Mugzilla on 2009-03-15
Can I blow XP Pro away on a correctly-working dual boot machine, REINSTALL XP back into that same partition, and then STILL use the same GRUB to load the freshly-installed version of windows? (Same disk will be used to reinstall windows...) 

If I have to redo both partitions, it is no big deal.

---

### Post by munishvit on 2009-03-15
Once you install Windows, you lose GRUB. To make it dual boot you need to reinstall it. 
I too have problem with dual-boot. My aim is to install Windows XP on non-first primary partition.
[http://ubuntuforums.org/showthread.php?t=1095893](http://ubuntuforums.org/showthread.php?t=1095893)
May be you could figure out something for you after reading this thread!!!

---

### Post by Mugzilla on 2009-03-15
> **munishvit said:**
> Once you install Windows, you lose GRUB. To make it dual boot you need to reinstall it. 
I too have problem with dual-boot. My aim is to install Windows XP on non-first primary partition.
[http://ubuntuforums.org/showthread.php?t=1095893](http://ubuntuforums.org/showthread.php?t=1095893)
May be you could figure out something for you after reading this thread!!!

This is NOT the answer I was expecting.  I thought GRUB was on one of the linux partitions, and a straight-up reinstall of XP would only affect the XP partition.

ANALOGY TIME:  I ALSO thought the GRUB line to start XP was akin to a shortcut.  If you uninstall a program, but leave the shortcut, then REINSTALL THE SAME PROGRAM IN THE EXACT SAME PLACE, that old shortcut will still start the program (Since it only is a shortcut that points to a location and a startup file name...)

I apologize if it soulnds like I am argueing with you because I did not get the answer I wanted.  I am providing this clarification because I do not think I either asked my question correctly, or I lack understanding of GRUB...

---

### Post by munishvit on 2009-03-16
As per my knowledge, installation of Windows erases stage1 of GRUB which is installed on MBR.

---

### Post by hichamroudi on 2009-03-16
[http://ubuntuforums.org/showthread.php?t=1096354](http://ubuntuforums.org/showthread.php?t=1096354)

---

### Post by eli_d on 2009-03-16
i really don't know how you would do what your asking without reinstalling grub AFTER you re-install XP (since XP overwrites the master boot record & grub).

it wouldn't be that difficult to reinstall grub off of the ubuntu install cd or from the grub live install cd.

---

### Post by Mugzilla on 2009-03-16
> **hichamroudi said:**
> [http://ubuntuforums.org/showthread.php?t=1096354](http://ubuntuforums.org/showthread.php?t=1096354)


THANK YOU.  I lacked understanding of GRUB.

[/thread]

---

