---
title: "How to I make a bootable CD that contains grub2?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2009-11-02
I'm looking for something like Super Grub Disk, but with Grub2. Or even just something simple with the Grub2 tools.

I can't use the tips I have found so far because my running system is using legacy grub.
See this link:
[http://www.justlinux.com/forum/showthread.php?t=152790](http://www.justlinux.com/forum/showthread.php?t=152790)

That's good info, but if I'm running legacy grub now, how do I make a boot CD with grub2?

---

### Post by MountainX on 2009-11-15
Super Grub_2_ Disk will do it.
[sgd_cdrom_1.21.iso.gz]("http://prdownload.berlios.de/supergrub/sgd_cdrom_1.21.iso.gz")

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by oldfred on 2009-11-15
+1 on supergrub
Whenever I am making changes to my system I always download and have an up to date supergrub.

Another way is from Herman:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkrescue](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkrescue)

---

### Post by exsencon on 2011-04-14
> **oldfred said:**
> 

Another way is from Herman:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkrescue](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkrescue)

I followed Herman's way and what a joy! I now have a Grub2 boot CD besides my Grub1 boot CD. I can boot whatever OS I want with it and just a few lines:
set root=(hd0,x)
chainloader +1
boot
Now I don't really need it because everything is booting fine, but you never know...
And Grub2 will someday replace Grub1(3-4 years)completely although they are running quite a lot behind schedule.

---

