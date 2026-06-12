---
title: "Triple Boot Ubuntu, Fedora, and winXP"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by j_cook on 2009-09-03
Hey guys,

Sorry, if this has been covered already, but I've searched to no avail. If this has been covered, please point me in the right direction.

 So here's the background:

I have successfully dual-booted my netbook with winXP and Ubuntu thanks to some previous help here. Now I want to triple-boot my netbook, adding Fedora as well (for no other reason than because I want to). Here's were my problem begins:

The ubuntu partition is an extended partition (instead of a primary partition) so on gparted it looks something like this:

>Extended partition[INDENT]-ext3
-linux swap
[/INDENT]My goal then is to shrink the whole extended partition to make room for a Fedora partition, however, I am unable to do so, because it will not let me resize the extended partition.

I have tried:
-Resizing the ext3 linux partition in hope that creating free space within the extended partition would give me liberty to shrink it.
-directly trying to shrink by right clicking the extended partition and trying to resize
-opening up Fedora's installer and using the partition editor (same problems encountered there as well).

Yes, I am using a live CD with gparted to do it, and not using the Ubuntu installed on my netbook. Yes, I swapped off my swap partition. No, I have no clue what I'm doing. Please help! 

Thanks!

---

### Post by zvacet on 2009-09-04
First delete swap partition and then shrink Ubuntu partition inside extended and on that unallocated space install Fedora.Of course you will add swap at the end ( or Fedora will do it I don´t know).You can try using [Gparted live CD.]("http://gparted.sourceforge.net/")

---

### Post by ronparent on 2009-09-04
Keep in mind that the swap partition is assigned auuid on install and automatically added to /etc/fstab to mount. If you create a new swap and would lke to use it for ubuntu, you will have to replace the old uuid in the ubuntu fstab with the new swap uuid.

---

### Post by j_cook on 2009-09-04
Thanks guys, I'm not sure why I didn't think of that. For whatever reason I was under the impression that I needed to resize the whole extended file to make room for the fedora partition. 

I'm not quite sure, though, why I need to delete my swap partition if I'm just going to make a new one at the end of the installation process. Shouldn't Fedora share the swap for Ubuntu?

Will I still be able to use the Ubuntu GRUB or after installing Fedora does it automatically use it's version of GRUB?

---

### Post by zvacet on 2009-09-05
Yes Fedora will share swap with Ubuntu.Fedora will install it´s own grub (or whatever bootloader it use) and you wil have to reinstall Ubuntu grun if you want to use it.

---

### Post by j_cook on 2009-09-05
All right, that's what I thought. I thought they should share the same swap, but I wasn't sure.

Fedora uses grub as well, but with different loading options. I like the loading options on Ubuntu's grub though. I know I can probably just edit the options on the Fedora grub, but I'm just a tad too lazy and it'll give me some experience with grub to learn how to install it anyway. :P

Thanks for the help!

---

