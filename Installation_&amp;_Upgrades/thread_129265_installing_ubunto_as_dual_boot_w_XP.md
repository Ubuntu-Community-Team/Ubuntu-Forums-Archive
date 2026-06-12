---
title: "installing ubunto as dual boot w/ XP"
date: 2006-02-13
forum: Installation &amp; Upgrades
---

### Post by adambeazley on 2006-02-13
Hello,
I am trying to find a good tutorial on how to install ubuntu as a second OS on my XP machine. I tried to do this yesterday and the MBR and/or partition table got screwed up and I had to reload windows. So I have a 200Gig SATA hard drive on a AMD 64 3200+ processor. I am using ubuntu 64 5.10 and right now I have the whole 200 Gig partitioned and formated NTFS.
I also should mention that I have Partition Magic 8.0 and can use that if need be, considering the partition creator in ubuntu corupted something, I might use Partition Magic this time around. 

correct me where  am wrong:

Create 10 Gigs free space from existing partition
Create Swap partition - 300MB
Create / Root partition --about 10 Gigs - 300MB   -format ext3
install ubuntu
install Grb bootloader to existing boot partition???????(this is the one that I have questions about)??????


thanks
Adam

---

### Post by klett on 2006-02-13
I used this one, adapting it to my laptop and configuration:
[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)

cheers!

---

### Post by Coelocanth on 2006-02-13
You may want to check out [This Guide](http://users.bigpond.net.au/hermanzone/). It's what I'll be using as a reference when I try a dual boot, as it seems quite comprehensive and easy to understand. FWIW, my system is remarkably similar to yours:

AMD Athlon 64 3200+
Seagate SATA 250 GB HDD
Win XP Home (NTFS - hard drive is one large partition)

Good luck!

---

### Post by aysiu on 2006-02-13
[The hermanzone guide](http://users.bigpond.net.au/hermanzone/) (the fifth link of my signature) is much better than this:

[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)

...for two reasons:

1. It walks you through the entire process with screenshots of every step.
2. It encourages you to install Grub to the MBR, the far easier method, as Grub automatically add Windows to the boot menu. Window's boot.ini will not automatically add Ubuntu to its menu--I can **guarantee** it.

---

### Post by bluevoodoo1 on 2006-02-13
[QUOTE=aysiu][The hermanzone guide](http://users.bigpond.net.au/hermanzone/) (the fifth link of my signature) is much better than this:[/QUOTE]

Agreed. I printed out the Ubuntu+NTFS guide there when I did a dual install (since I wouldn't have internet access) and it worked like a charm. 

The "nuke anything" extension for firefox is handy in getting rid of some of the graphics you might not need. (To save your printer ink)

---

### Post by DarkED on 2006-02-13
[QUOTE=aysiu][The hermanzone guide](http://users.bigpond.net.au/hermanzone/) (the fifth link of my signature) is much better than this:

[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)

...for two reasons:

1. It walks you through the entire process with screenshots of every step.
2. It encourages you to install Grub to the MBR, the far easier method, as Grub automatically add Windows to the boot menu. Window's boot.ini will not automatically add Ubuntu to its menu--I can **guarantee** it.[/QUOTE]

I agree, took me three installs each of WinXP and Ubuntu to get it right. RedHat only took one :D

My computer is similar to yours, except it's a laptop. I installed WinXP first, and this is how I did it. Not saying it's the 'correct' way but it worked for me:

60gig hdd, partitioned IN THIS ORDER!

hda0: 50meg /boot partition (set as the 'boot' partition when I installed Ubuntu)
hda1: 49gig/WinXP, NTFS (installed first, used it's partitioner to make the table)
hda2: 10gig/Ubuntu, EXT3 (installed second, used it's partitioner to do the filesystems on the non-windows partitions)
hda3: gig swap partition (installed with Ubuntu)

Like I said, it's not the 'correct' way to do it. Having Grub install to your MBR would be better. However, it works for me :D If you have any questions about doing it this way. just drop me a line on AIM...

---

