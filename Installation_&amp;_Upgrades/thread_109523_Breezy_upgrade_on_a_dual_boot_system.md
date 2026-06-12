---
title: "Breezy upgrade on a dual boot system"
date: 2005-12-28
forum: Installation &amp; Upgrades
---

### Post by djh3 on 2005-12-28
I have Win98 and Ubuntu 5.04 (Hoary) installed on a Toshiba Tecra 8000 laptop.  Win98 is on hda1, Ubuntu on hda2 and Swap on hda3.  GRUB is installed to select operating systems after booting.  I now want to upgrade Hoary to Breezy.  The installs on the laptop were recent so I don't mind losing everything on hda2 but I don't want to lose anything on hda1 or the ability to boot into Windows (for my wife and for those times when work makes it necessary for me!).  I have a 5.10 install disk.  What is the safest and cleanest way to do the install?  For example, should I reformat hda2 to wipe it clean and then install 5.10?  If so, what will happen to the Grub menu on startup?  Thanks.

---

### Post by towsonu2003 on 2005-12-29
before anything, **back up everything you're gonna need later** just in case... 

Once you wipe off hda2 (old hoary partition) and install breezy instead, it will install grub for you again, so there should be no problems with dual boot. 

while you are there, you might want to add a new partition for /home as you're gonna need to do another distro upgrade sooner or later...

---

### Post by djh3 on 2005-12-31
[QUOTE=towsonu2003]before anything, **back up everything you're gonna need later** just in case... 

Once you wipe off hda2 (old hoary partition) and install breezy instead, it will install grub for you again, so there should be no problems with dual boot. 

while you are there, you might want to add a new partition for /home as you're gonna need to do another distro upgrade sooner or later...[/QUOTE]

Thanks for the information.  I hope to give it a go tomorrow.  If I create a new partition (say, hda4) for /home how do I tell the new install (on hda2) that /home should be on hda4?

---

### Post by towsonu2003 on 2005-12-31
[QUOTE=djh3]If I create a new partition (say, hda4) for /home how do I tell the new install (on hda2) that /home should be on hda4?[/QUOTE]
during the *expert* partitioning in the ubuntu installation procedure, you will be formatting (which is optional -do not format your windows partition :) -) and mounting each partition one by one. let's say you want the installation to go to hda2 and /home to hda4. tell the *expert* partitioner (you'll see how to do that once you're there) to mount / (root) to hda2 and /home to hda4. 

Maybe I should note that / will need at least 4GB, swap will need (usually) twice  of your RAM (if you got 256MB, swap should be 512MB), and the rest (more than 1GB?) can go to /home...

---

