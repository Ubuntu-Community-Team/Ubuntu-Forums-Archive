---
title: "Newbie Building an Ubuntu File Server for Macs"
date: 2008-08-05
forum: Hardware
---

### Post by sit-ubu-sit on 2008-08-05
To anyone willing to help:

I've never built my own computer and I've barely ever used Linux.  I've never used Ubuntu.  I've always owned Macs (for 20+ years), and have reluctantly used Windows at work.

I have a CoolerMaster RX 810 chassis and a CoolerMaster 450W power supply.  I also have a Trendnet Gigabit Ethernet card.

I have 8 IDE hard drives currently full of data in an HFS+ file system (journaling may or may not be on).  The data was put on there by Macs and is used by Macs.

The chassis can fit 8 more drives, and I would like to make sure that my configuration will support those additional drives when/if I buy them.

My goal is simply to use the box as wired network attached storage.

Does anyone have suggestions as to what motherboard, CPU, and memory to purchase to make this possible using Ubuntu?

How do I configure Ubuntu to either be able to read/write the HFS+ data and/or allow networked Macs to read/write the HFS+ data?  

Right now I do not plan to implement any RAID array or the like.  I simply want access to each drive individually.

Any suggestions would be greatly appreciated.  The more detail the better!

Thanks in advance.

---

### Post by tuxxy on 2008-08-05
Have you read the server guide, maybe useful

[http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

---

### Post by sit-ubu-sit on 2008-08-05
Thank you for posting.  I will read through those materials.  It seems I may need to set up Windows networking (SMB).

---

### Post by cariboo on 2008-08-05
You can use Appletalk for your network, it is available in the reposiitories. Search for netatalk using Synaptic or add/remove programs.

Jim

---

### Post by samick88 on 2009-01-12
I'm also a newbie. I switched from opensuse to ubuntu because of the great support you can find.
I and installed netatalk.
When I share a folder on the HD everythings works ok. 
I have also a wd mybook (formatted in ext3).

I have added the folowing in /etc/netatalk/AppleVolumes.default
/media/mybook/backup TimeMachine allow:myuser cnidscheme:cdb options:usedots,upriv

In fstab I added:
/dev/sdb4 /media/mybook/backup ext3 auto,rw,user 0 0
When I mount the disk and restart netatalk, my connection is refused on my mac leopard.

Security settings on /media/mybook/backup:
drwxrwxrwx 5 root  root  4096 2009-01-12 19:35 backup

Any idea what is wrong?

Thanks for your help
Fred

---

