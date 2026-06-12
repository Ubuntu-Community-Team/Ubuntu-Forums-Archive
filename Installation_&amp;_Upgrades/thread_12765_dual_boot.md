---
title: "dual boot"
date: 2005-01-26
forum: Installation &amp; Upgrades
---

### Post by the stranger on 2005-01-26
does anyone know of a **step by step **guide to having a dual boot!

i have a 200gig HD with ubuntu currently on it, i want to half it and have xp on the other!

thanks in advance

---

### Post by rudi on 2005-01-26
How is your partition scheme? Have you allready devided your disk (made room for Window$)? Also, it's more common (easier) to install windows first, then linux, just because when you install windows it automatically overwrites your MBR. So if you install windows after Linux, you'll have to fix your grub/ lilo again. I've written an installation manual to dual boot windows with Debian, but i think it can be used with ubuntu also [img]http://www.ubuntuforums.org/images/smilies/eusa_shhh.gif[/img] You can find it on my website:
    
    [http://www.bio-informatics.nl/debinstall1.php]("http://www.bio-informatics.nl/debinstall1.php")

---

### Post by the stranger on 2005-01-26
i dont have any thing, i just brought the HD and installed ubuntu right on to it, so i only have want ubuntu sets during the installation.

---

### Post by rudi on 2005-01-26
If you just bought the HD, i assume you don't have a lot of files on it you want to keep, just back them up (burn on CD/DVD). Then install windows, when the partition step comes up, use some space for windows system partition,  and perhaps a  fat partition for shared files (linux can read/write fat, not ntfs) and install windows.
 
 Then insert your ubuntu CD and  install it, when the partition step comes use the rest of the unpartitioned space to set up your defaut scheme. (if you plan to do a lot of distro shuffling make sure you create a seperate /home partition).
 
 I think that this is the easiest way on setting a dual boot PC up. This is described in a step-by-step fashion on my site. Hope it helps you.

---

