---
title: "Problem booting with kernel 2.6.12-10"
date: 2006-01-04
forum: Installation &amp; Upgrades
---

### Post by Zebulon on 2006-01-04
I upgraded my Ubuntu 5.10 to kernel 2.6.12-10 for i386. Now it does not reboot. GRUB halts it with the error message 
"Error 18: Selected cylinder exceeds maximum supported by BIOS"

The previous kernel version works well. I have a intel Pentium III with a 200GB harddisk with one partition. Does anyone have any suggestions for solutions?
/zeb

---

### Post by ed_d on 2006-01-04
Try getting the 686 version (linux-image-686)

---

### Post by visit0r on 2006-01-04
This is quite a serious bug, it seems. My work computer is now broken after this upgrade. First time the boot stopped because of "uncorrectable failures" in root partition. I also have a 200G disk (SATA) in a single partition.

When I tried to correct the failures manually (entered root pass and then mounted / as rw, executed fsck as it instructed), and after entering 'y' to couple of confirmations, fscks started repeately reporting errors on the disk and "correcting" them. As it seemed quite dangerous to me, I rebooted the system and now grub does not boot, stops with "error 17" (can't mount root?).

What can I do to maybe salvage my working computer?

---

### Post by az on 2006-01-04
Zebulon:  This is a grub problem and not a kernel problem - Grub uses bios to access the drive whereas once the kernel is in place, the hard drive is accessed through it, the kernel.  It seems that the kernel is able to see the vmlinuz file whereas the bios is not.  Unless you cannot update your bios, you may have to create a seperate /boot partition at the beginning of the drive to avoid this problem.

Visitor:  Your problem,  similarly is not a kernel problem.  You seem to ave a hardware problem.  Your filesystem seems corrupted.  It is unlikely that upgrading a kernel can do that.

---

### Post by Zebulon on 2006-01-05
Ok, so it's a grub-bios problem. I could set up a smaller disk as the boot disk and thereby avoid having to change the rest of my current setup. I still wonder why this comes up now? When I have previously upgraded of kernels in Ubuntu and Redhat, they have worked without any problems whatsoever.
/z

---

### Post by az on 2006-01-05
[QUOTE=Zebulon]Ok, so it's a grub-bios problem. I could set up a smaller disk as the boot disk and thereby avoid having to change the rest of my current setup. I still wonder why this comes up now? When I have previously upgraded of kernels in Ubuntu and Redhat, they have worked without any problems whatsoever.
/z[/QUOTE]
It's probably because that particular file (linux image) is on part of the disk that is just beyond where the bios can access.  Have you used Ubuntu longer than your other Oses?  Also, by default, ubuntu only creates one partition.  Perhaps former installs of other linux distros installed a seperate /boot partition at the beginning of the drive because of the prominece of this problem on legacy hardware.

---

### Post by Zebulon on 2006-01-05
[QUOTE=azz]It's probably because that particular file (linux image) is on part of the disk that is just beyond where the bios can access.  Have you used Ubuntu longer than your other Oses?  Also, by default, ubuntu only creates one partition.  Perhaps former installs of other linux distros installed a seperate /boot partition at the beginning of the drive because of the prominece of this problem on legacy hardware.[/QUOTE]

The harddisk is brand new, and Ubuntu is the first and only thing a I have on it.

I'm all new to ubuntu. I migrated recently from debian and redhat which I have used for many years. There I always did the partitioning myself - usually into a /boot a /usr and a /. This time I let Ubuntu do the partitioning, which possibly was a mistake given the combination of the large harddisk (200GB) with an elderly BIOS. If this is the case maybe it's something Ubuntu developers should think about.

---

### Post by hivemaster on 2006-01-14
I am having a similar problem. 

I have a HP Vectra with 750Mhz. Originally installed with 2.6.12-9 kernel which did (and still does) work correctly.

Updating to 2.6.12-10 causes the Error 18.

Im not the most knowledgeable about all this, so for me I dont have a clue about creating a boot partition.

I have just installed the i686 version and this is now working (maybe should have done it before) but I am wondering why the i386 version would fail when it used to be ok?

Thanks

---

