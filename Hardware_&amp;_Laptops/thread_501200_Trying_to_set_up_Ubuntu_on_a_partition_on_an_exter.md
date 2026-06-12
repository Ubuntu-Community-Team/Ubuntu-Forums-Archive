---
title: "Trying to set up Ubuntu on a partition on an external hard drive"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by runemaster on 2007-07-14
I am want to set up linux on an external hard drive so I can use it on my laptop without touching my main drive, but before I try anything I was wondering if it was possible to keep 3 partitions on the hard disk (160 GB drive) one 90 GB part for the Vista on my laptop to use, and one 65 GB Ubuntu. Is there also a way to sort of create a "live" partition on the disk so I can run it on my other computers?

---

### Post by scrooge_74 on 2007-07-14
Hi,

you can have multiple partitions on the same disk.

You can have Vista and Ubuntu on the same drive (There are a couple of Howtos in the forums)

By a live partition I am not sure what you want.  Do you want to be able to use the external drive on diferent PCs?  If so, you can always either install Ubuntu on its machine, but tell Grub to read from the external drive

Or make a bootable floppy or USB and tell the system that your system is on the external drive (also depends if the BIOS accept booting from USB)

---

### Post by runemaster on 2007-07-14
I don't want to put Ubuntu on my main hard drive because I like gaming and want all my games on my main hard drive. So is there a guide to put Ubuntu on the external, or is it the exact same procedure as the dual booting?

---

### Post by scrooge_74 on 2007-07-15
It will be as doal booting, the only thing that is going to get install in your main drive is GRUB, which will let you pick which OS to run.  At install time you tell the system that Ubuntu is on the external drive and to let the windows partition as it is.

---

### Post by gabeyg on 2007-07-19
:guitar:
Hi guys.. I don't know why.. but since no one is answering my questions... And since this is my case, too, I might ask you to show me what the problem is.
This is my question link:[http://ubuntuforums.org/showthread.php?t=504308&highlight=Grub+bootable+CD]("http://ubuntuforums.org/showthread.php?t=504308&highlight=Grub+bootable+CD")
[http://www.linuxforums.org/forum/ubuntu-help/98730-problems-loading-using-grub-bootable-cd.html#post488374]("http://www.linuxforums.org/forum/ubuntu-help/98730-problems-loading-using-grub-bootable-cd.html#post488374")
[http://www.linuxquestions.org/questions/showthread.php?p=2828873#post2828873]("http://www.linuxquestions.org/questions/showthread.php?p=2828873#post2828873")
:popcorn:

---

