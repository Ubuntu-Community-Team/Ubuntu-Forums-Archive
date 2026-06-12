---
title: "I'm a straight up noob and I am about to make my laptop a duel boot."
date: 2009-12-17
forum: Hardware
---

### Post by OrangeNinja on 2009-12-17
I just want to have full disclosure with my new friends from Ubuntu Linux, I have had 4 beers and I am planning on having at least a couple more. 
 
I have a HP DV6775us and I am about to save some files and run disk defrag and attempt to install x64 unbuntu. I have been jumping around some threads for a while and was wondering does anyone have a similar setup? Are there anythings I should be prepared for other than a bottle opener?
 
I once installed Gentoo from scratch about 4 years ago and it worked fine for a few days till I broke xorg.

---

### Post by gradysghost on 2009-12-17
Well, getting Ubuntu to work typically involves far less effort than making Gentoo work, so I doubt you'll have problems.  The installer, Ubiquity, is so easy to work with, that you should be able to handle it completely drunk.

---

### Post by OrangeNinja on 2009-12-17
:P Nice I was hoping so!  I am just working a buzz anyway. But yes Gentoo was my first experience with Linux and I have no Idea why I did that but it was hard. One computer with the how to doc up the other compiling.....lol.

---

### Post by viper250 on 2009-12-17
gentoo is a very powerful distro with the maximum user control so set up would be very difficult but ubuntu will setup easily for dual boot  just choose the correct  partition option when you are at the partitioning stage. If you are unsure then use windows storage manager to resize and create a partition for your linux.
then boot up the iso and install linux to the chosen partition, and install the bootloader to the mbr.
hope this help!

---

### Post by OrangeNinja on 2009-12-17
Thanks I am deleting some old junk to make more room then defrag then install attempt...

---

### Post by OrangeNinja on 2009-12-18
will it make a /home dir automatically during install?

---

### Post by JBAlaska on 2009-12-18
Yes it will, but your best bet since your somewhat experienced is to make a "/" (root) a "/home" and a "/swap" partition.. Use the manual partition option and those 3 and don't be afraid to use ext4 it's super stable now.

Enjoy Ubuntu!

---

### Post by OrangeNinja on 2009-12-18
it's been a while JB is that during install or after...... could I do that?

---

### Post by OrangeNinja on 2009-12-18
still defraggin' wow didnt realize I had so much on this drive.

---

### Post by JBAlaska on 2009-12-18
NP, since you mentioned defraging, I assume (Always dangerous lol) that you need to re-size a NTFS partition to make room for some Linux ones., So boot from your LiveCD, go to System, Administration, "Gparted" and you should see a screen something like this:
[[IMG]http://img32.imageshack.us/img32/8704/resizes.th.png[/IMG]](http://img32.imageshack.us/i/resizes.png/) You get there by right clicking on the partition you want to resize/shrink.

Oh, first Please backup all your mission critical data!, then resize with gparted as shown in the screenshot.

When this is finished, you will have free space to work with. Note: a Physical HD can only have 4 **Primary** partitions, no worries as Linux can install on a **Logical partition** (except the swap partition). 

So Reboot with your LiveCD in and choose, "install Ubuntu", follow the prompts until you get to the partitioning page, choose "Manual Partition" right click on the free space on your drive, create a "/" (root) partition, a "/home" partition (Both about the same size) and a "/swap" partition (About 1 to 1.5 times your RAM)

Let the installer finish, and you should be booting into Ubuntu.

If this sounds to complicated, post back and I will be happy to try and answer your questions.

---

### Post by GodLikeCreature on 2009-12-18
Actually, for a first taste, I would recommend using Wubi and installing from within Windows.  Wubi is a great way to start.  It doesn´t make you change your setup dramatically, it involves far less risk (especially if you are to start tweaking partitions with Vista), and you get the overall idea.

If you like Ubuntu, you will have a quick and easy way to work with it and see if a full native installation is what you want (usually it takes a while to understand if you have all your needs covered in Linux, finding the right applications, getting your way through with Wine and all that jazz)

Anyways, good luck with whatever method you choose!

---

### Post by JBAlaska on 2009-12-18
> **GodLikeCreature said:**
> Actually, for a first taste, I would recommend using Wubi and installing from within Windows.  Wubi is a great way to start.  It doesn´t make you change your setup dramatically, it involves far less risk (especially if you are to start tweaking partitions with Vista), and you get the overall idea.

If you like Ubuntu, you will have a quick and easy way to work with it and see if a full native installation is what you want (usually it takes a while to understand if you have all your needs covered in Linux, finding the right applications, getting your way through with Wine and all that jazz)

Anyways, good luck with whatever method you choose!

Although this is generally good advice, Please note: A wubi install is meant for **temporary testing only**..Trying to use hibernate/suspend..will break it, a kernel update will break it etc.

If you really want to USE Linux and your laptop works booting the LiveCD, you might as well bite the bullet and do a proper install.

---

### Post by OrangeNinja on 2009-12-18
Boom! I did it. now I am going to bed.


[IMG]http://farm3.static.flickr.com/2779/4195038696_d9710b1ca2.jpg[/IMG]

---

