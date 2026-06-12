---
title: "Install grub to karmic partition, not MBR?"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by dsmithhfx on 2009-10-30
Hi,

I have a multiboot pc with 6 or 8 linux installations, including intrepid and jaunty, scattered over 3 hdd's.

I am planning to nuke the intrepid, and install karmic to that partition.

My MBR points to Grub 1 on an opensuse partition, from whence all others are chainloaded. I want to keep it that way.

I tried a karmic install in virtualbox, using the alternate-install cd (64-bit), and guided partitioning/whole disk. This breezed through all the steps (well, actually it took an hour), including auto-installing Grub to the MBR.

I played around with the installer a bit more, this time in "expert mode", which appears to involve a rather tedious manual stepping through all the installation tasks. I did not take it to the point of seeing the Grub install options; presumably you get to choose where to write Grub?

Is there a way to invoke this particular step (or menu) during a standard (non-expert) installation at the appropriate stage? Or can anyone point me to a guide for installing karmic with Grub on the partition, rather than MBR?

Thanks!

---

### Post by markbuntu on 2009-10-30
Using the standard install, after partitioning there is a "advanced" option on the bottom left. if you click this you will be asked where you want to install grub. At least that is what it did with rc. I am downloading the release now so I have not tried that yet but it should be the same, this has not changed since hardy or before.

It is very easy to miss.

I used it to put karmic grub in the karmic partition and could chainload to it from my MBR grub with no problems. 

Please use the torrents. They are a lot faster than the mirrors or repos. (I just downloaded karmic in less than 4 minutes using bittorrent at ~3MB/s. There are currently about 4 times as many seeders as leachers.)

---

### Post by dsmithhfx on 2009-10-30
When you say "standard install" do you mean the installer on the live cd?

---

### Post by markbuntu on 2009-10-30
Yes.

---

### Post by louieb on 2009-10-30
> using the alternate-install cd (64-bit), I did not take it to the point of seeing the Grub install options; presumably you get to choose where to write Grub?

The alternate CD uses the Debian installer. I used the 32 bit alternate when I installed Karmic.   Used manual partitioning, did not use expert mode. IIRC The Grub install option was toward the end of the install. Unlike the live CD - the Grub install location on the alternate is kind of hard to miss. (I to put Grub in the boot sector of the install partition)  Makes me wonder if the 64 bit Debian installer is different.

---

### Post by dsmithhfx on 2009-10-31
Well I didn't see it except in expert mode on the alternate. With the standard live cd installer you do get it, under an "advanced button" right after adding username and password (and before commiting partition layout to disk, which is good), where it is bundled with network proxy. A tad illogical, but might prevent noobs from messing around with something that would effectively make their new installation unbootable...

---

### Post by pantzir on 2010-01-24
just for sake of others landing here via search:
I used ubuntu 9.10 alternate i386. full disk option does not prompt for grub location, while manual does (at the very end).

---

