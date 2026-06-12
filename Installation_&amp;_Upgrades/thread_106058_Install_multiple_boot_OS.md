---
title: "Install multiple boot OS"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by wingknight on 2005-12-19
Hi! Does anyone has a guide how to install multiple OS. Currently, I have a windows xp installed in my pc and red hat linux. Hearing great feedbacks about ubuntu, I decided to use ubuntu as my partner in learning linux environment.

Basically, below are the os i want to install in my pc appearing only in one boot loader (grub). Formatting my PC for a new installation is no problem.
  1.  Windows XP
  2.  Red hat
  3.  Ubuntu

Is it also possible to install another os like DOS?

---

### Post by btdown on 2005-12-19
Not to jack your thread, but i understand your issues...I am also looking for info on this as well. I'd like to run a dual boot Ubuntu Breezy/Suse 10 system, but havent done so yet because Im not quite sure how to go about it. Too many questions...like:
 
Should I install one before the other? How well would they coexist?
Should I partition the drive in half in preparation (one for each OS)? 
What kind of prep is recommended, and how do I set it up to specify which one to boot?
 
BT

---

### Post by Ocxic on 2005-12-19
I belevie Grub will detect the other OS's in the system during the install, at least it did for me, windows included, just install your new OS and install grub to where it is now during your new install,it should just add the OS's for you.

---

### Post by aysiu on 2005-12-19
It's actually a lot simpler than you think it is.

Let's say you have Windows on /dev/hda1, Red Hat on /dev/hda5, and then make a new partition and install Ubuntu on /dev/hda6. If you install Ubuntu's Grub to the MBR, it'll automatically add Windows to the Grub boot menu. 

Then, if it doesn't add Red Hat (which it may not), just mount the Red Hat partition in Ubuntu, find the relevant /dev/hda5/boot/grub/menu.lst Grub entry for Red Hat and add it to /dev/hda6/boot/grub/menu.lst in Ubuntu.

---

### Post by wingknight on 2005-12-19
[QUOTE=aysiu]It's actually a lot simpler than you think it is.

Let's say you have Windows on /dev/hda1, Red Hat on /dev/hda5, and then make a new partition and install Ubuntu on /dev/hda6. If you install Ubuntu's Grub to the MBR, it'll automatically add Windows to the Grub boot menu. 

Then, if it doesn't add Red Hat (which it may not), just mount the Red Hat partition in Ubuntu, find the relevant /dev/hda5/boot/grub/menu.lst Grub entry for Red Hat and add it to /dev/hda6/boot/grub/menu.lst in Ubuntu.[/QUOTE]
Thank's for the advice. But I'm a little confused with what you said. Actually, I'm a beginner to linux and only know basic settings.

Is there a step by step guide in installing multi boot OS including partitioning and configuring mbr for the correct grub?

---

### Post by aysiu on 2005-12-19
[QUOTE=wingknight]
Is there a step by step guide in installing multi boot OS including partitioning and configuring mbr for the correct grub?[/QUOTE] The closest I know is this guide:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

It address specifically changing a Windows-only computer into a dual boot with Ubuntu, but you could probably learn a lot about partitioning and Grub from reading it.

---

### Post by Herman on 2005-12-19
I am triple-booting Windows, Breezy and Kubuntu Breezy now, (gosh the 'hermanzone' website looks ugly in the konqueror browser).
Triple-booting is not too difficult, if you know how to dual boot. I have Windows as a 'primary' partition, then Ubuntu as a 'primary'. After that I have one swap in the middle between Ubuntu and kubuntu, they both share it. I don't think it matters where it is, closer to the outside of the disk is better for swap, performance-wise, I have read. Then on the other side of the swap I have kubuntu, as a primary partition. 
According to what I have been reading in the Gnu Parted Manual:
[http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC73]("http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC73")
it's a little better to make your bootable partitions 'primary'. But it isn't compulsory.
Probably the main thing you would need to keep in mind for multi-booting is that you can have up to four 'primary' partitions. If you want, you can have one of these primary partitions automatically become an 'extended' partition, and it can have as many as 63 logical partitions inside it. These logical partitions need to be 'contiguous' (all in one chain or string). You can create a primary partition in between and then add another logical partition, but it will be unuseable.
So you will need to plan ahead a little and decide which partitions you want as primary, and which ones as logical inside your extended partition. 
Actually. it would be the easiest to just make them all logical, then you won't have to worry about it.
Some-one should make a multi-boot website, there are lots of people around here who know a lot more than me, but the I felt that someone should point out the problem of mixing primary and logical partitions. You can easily 'snooker yourself' if don't know the rules about that. ('Snooker yourself' is an Australian term with a meaning similar to 'Paint yourself into a corner'). :D (Herman)

---

### Post by wingknight on 2005-12-20
Thanks for the advice. I agree that it's really helpful if someone would make a site for multiboot installation.

---

### Post by Herman on 2005-12-20
Ahh, okay,  I'll explain things a little simpler:

_Don't do_ what I did and make a primary partition (Windows), then another primary (Ununtu), and a swap area. My swap area is logical,using up my 'extended' partition for just one little item. Kubuntu is on another primary. I have used up all my options. I'm 'snookered'. It's okay for me, because that's all I wanted for this computer.

_Do something like this_:
If I wanted to make a multi-boot computer, and go for the maximum possible number of OS's, I 'd put Windows in first, on a primary partition.
If I want another Windows, I would use another primary partition.
I could use three of those in a row, if I wanted.
Linux doesn't care if it's on a logical partition or primary, so I'd make all the rest of my partitions 'logical', and I could have up to 63 of them. 
As long as I don't break the chain by trying to put a primary partition in the middle, everything will be okay. 
I can have more primary partitions at the end if I didn't use them all up at the beginning, as long as I don't try to put them in the middle anywhere.

P.S. I haven't really tried more than three OS's at once yet myself, but the above should work from what I've been reading. I will try it out soon too, just for fun.:D (Herman)

---

