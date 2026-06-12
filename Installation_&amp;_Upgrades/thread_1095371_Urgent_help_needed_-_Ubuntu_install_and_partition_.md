---
title: "Urgent help needed - Ubuntu install and partition choice"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by shiv379 on 2009-03-13
Hi all,
Firstly let me just say a quick hello to everyone, it's my first time here :)
I'm taking the plunge with linux and I've chosen Ubuntu as my distro to get started with. I'm sat in front of my laptop (I'm typing this on a second laptop) at the "Prepare Disk space" screen of the Ubuntu install. I prepared 15gb of free space according to the tutorial I found at [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3) and I can see the free space in the "Before" bar. My "before" bar looks like this:
2% /dev/sda1 (I believe this is the RECOVERY partition bundled with the laptop)
44% /dev/sda2 (my current VISTA install, I want to keep this and dual-boot)
5% free space (this is where I want to install Ubuntu, 15gb partition)
47% /dev/sda5 (this is my "stuff" partition, again one I want to preserve).

Now what's worrying me is if I click "Guided - use the largest continuous free space" the "After" bar shows completely blue and the text underneath shows "Ubuntu 8.10 100%"

Now this doesn't really sound like it's about to do what I'm hoping! Can anyone suggest anything pls? Really don't want my foray into linux to come to a halt before I even get installed.

~Shiv

EDIT: Tried the "resize and use freed space" but got an error about not being able to inform the kernel of the changes. Tried to cancel at this point then things have gone...a bit kaka (as they used to say on Quantum Leap). Watch this space :S

So shouldn't have tried this on Friday 13th after a bottle of wine.

---

### Post by zvacet on 2009-03-13
[Here]("http://psychocats.s465.sureserver.com/ubuntu/dualboot#partitioning") is one more guide for dual boot.That is best I can do,because I allways use alternate CD and manual installing.And it is not Friday 13th why you have troubles.But bottle of wine?! :-k

---

### Post by Elfy on 2009-03-13
You could delete the 15Gb partition using the partition editor in System > Admin and then use the guided - use largest continuous free space.

OR you could create the necessary partitions and then use manual.

You would need an extended, 2 logicals - 1 for / and 1 for swap

---

### Post by ntatealan on 2009-03-22
Not a reply but a related query. I'm using Vista as main OS but have just installed Ubuntu on second hard disk. How can I edit the grub loader so that the default is Vista and not Ubuntu?  The rest of the family are fed up with having to sit around and select from the grub loader to find a familiar OS!

---

### Post by LiamWilson on 2009-03-22
This should help:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by ntatealan on 2009-03-22
Many thanks. Defaults now to Vista by using the *default   saved*option below the line *##default num*.
Thanks a lot.

---

