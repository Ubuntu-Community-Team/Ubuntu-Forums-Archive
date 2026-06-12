---
title: "Newbie Questions - Replacing Windows XP"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by Jason32 on 2009-03-26
OK, so I'm new to Linux but I'm planning on replacing my current Windows XP installation with ubuntu.

I'm not quite ready to cut the Redmond cord just yet, so for the time being I'm planning a dual-boot system. I'm comfortable with reducing the size of my windows partition and installing ubuntu in the free space, and using the default boot-loader (Grub?) to handle the dual-boot duties.

What I hope to do is install ubuntu and use VirtualBox to run Windows XP as a guest operating system for the (hopefully few) occasions when I need it. Once I'm happy with this setup I plan on deleting the original Windows partition and filling my harddrive with ubuntu goodness, and it's this part of the plan I'm not sure about.

I know that if I had windows installed on disk 0 partition 1 and I subsequently decided to move it to disk 0 partition 0 and use the entire disk I'd be setting myself up for untold misery. Will ubuntu and it's bootloader be able to handle that change better, or am I likely to cause myself problems by doing that?

Also, I know Windows uses just the one partition whereas ubuntu is going to have both a primary and a swap partition. When I resize it to fill the whole disk, should I be growing just the primary partition, or should I be resizing the swap partition as well?

Thanks in advance for your help! I'm sure I'll have a hundred more questions as I work through the process :P

---

### Post by zvacet on 2009-03-27
For now just dual boot and when you become more comfortable with Ubuntu  then you can think of changing things( I suppose that you need your Windows).I will recommend to create root home and swap partition.That way you can always reinstall,fresh install... without been afraid about your files and settings.There is no need to make swap bigger.

---

### Post by tommcd on 2009-03-27
If you want to dual boot and later delete Windows:
Windows will be the 1st partition on the disk.  It will be a primary partition when you partition the disk for Ubuntu. Then create a 1GB swap partition, also as a primary. Then create 2 logical partitions. The 1st logical will be a 10-15GB partition for root (it could be less if you have a small drive or are short on space). Root is where you will install Ubuntu. The 2nd logical will be for a home partition for your data. Home will be the rest of your disk.

When you decide to get rid of Windows, wait untill a new version of Ubuntu comes out (new versions are released every 6 months). Then do a clean install of the new Ubuntu over top of Windows. You should then use a Gparted or Parted magic live CD to merge the 2 logical partitions into 1 big home partition. Be sure to have your data backed up before you do this just to be safe. 
If you can, shrink Windows XP down to 15GB when you install Ubuntu. This is plenty as long as you don't have a lot of data and games on your XP system. Delete everything you can to make enough room to shrink it down. Just backup your data and you can copy it onto Ubuntu's home after the install.
Here is guide to VM ware on Ubuntu:
[http://howtoforge.com/how-to-install-vmware-server-1.0.x-on-an-ubuntu-8.10-desktop](http://howtoforge.com/how-to-install-vmware-server-1.0.x-on-an-ubuntu-8.10-desktop)
Here is a good guide to getting started with Ubuntu:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
Here is another good resource:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

And welcome to the Ubuntu forums! Welcome to the cool side of computing!

---

