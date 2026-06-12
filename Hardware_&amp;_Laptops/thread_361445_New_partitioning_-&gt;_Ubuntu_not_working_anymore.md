---
title: "New partitioning -&gt; Ubuntu not working anymore"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by Znupi on 2007-02-14
I have Ubuntu 6.06LTS installed, and Windows XP, too. It all worked fine until I tried making a FAT32 partition to share information between the two Operating Systems. The partition is made, Windows works just fine, but I think Ubuntu is trying to boot from the new FAT32 partition? It says "File system is FAT32" (The Linux partition is Ext3) "blah blah blah... file not found". Is there any way to fix this other than reinstalling Ubuntu? It wouldn't be too much of a problem since I'm not a big Linux user and I don't have any super-important files on it...

---

### Post by link141 on 2007-02-14
Sounds like grub is trying boot from the new partition (like you said), I think this can happen if the ubuntu partition is moved due to the making of a new partion.  Luckily, there is an easy way to fix this.  Grab a copy of the ubuntu alternate install cd from the  [Download page](http://releases.ubuntu.com/6.10/), or get a copy of the super grub boot disk from [this page](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml), and use one of them to reinstall grub.  They both should automatically detect your os's and put them into the grub menu.  Unfortunately, I don't know how to do this from either disk (being that I never used either one), although it should be pretty easy to find out.  

Hope this helps you out
link141

---

### Post by Znupi on 2007-02-15
Thanks but that wasn't the solution :)
The solution was to edit the boot commands from grub (by pressing `e') like this:
[B]root (hd0,5) -> root (hd0,6)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda6 ro quiet splash ->
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda7 ro quiet splash[/B]
And then do the same thing in the /boot/grub/menu.lst file.
Thanks anyway :)

---

