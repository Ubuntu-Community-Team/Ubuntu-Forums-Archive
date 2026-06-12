---
title: "Alternate CD, LVM, Ultra ATA133x2 PCI Card"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by modprobe on 2009-07-15
Ok, here it goes:

I downloaded the 9.04 alternate ISO, mainly because I wanted to install to an LVM setup.

I have 4 x 40GB hard drives connected to an Ultra ATA133 PCI Card, all IDE.

During the partitioning step, I keep pressing the 'spacebar' to select all the drives I wanted to include in the LVM setup, but nothing happens.

So I pressed 'Enter' on the top drive, started setting up LVM, but was not given the option to add the other 3 drives.

I've been "googling" for an Ubuntu alternate CD installation guide, but so far haven't found something that will help.

Any comments, suggestions, tips are welcome.  Thanks.

:popcorn:

---

### Post by modprobe on 2009-07-16
Found an excellent guide:

[http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/](http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/)

Went through the motions and had my LVM setup the way I wanted it, and WHAM!!!: the CD I burned is corrupted.

Can't believe it!  Now I have to use a guide I stumbled upon that uses the Live CD to install to LVM2.

Bye bye!  Thanks.

):P

---

### Post by modprobe on 2009-07-16
Had to come back and share some more!

Awesome stuff!  Here is the guide I used to install 9.04 on an LVM setup:

[http://polishlinux.org/linux/ubuntu/install-ubuntu-804-on-lvm2/](http://polishlinux.org/linux/ubuntu/install-ubuntu-804-on-lvm2/)

The LVM setup I had worked through with the alternate CD was still there.  So the guide was perfect for my situation.

Note: when I ran 'modprobe dm-mod' I received a FATAL error, but it can be safely ignored.  Probably something needed for 8.04.

:guitar:

---

