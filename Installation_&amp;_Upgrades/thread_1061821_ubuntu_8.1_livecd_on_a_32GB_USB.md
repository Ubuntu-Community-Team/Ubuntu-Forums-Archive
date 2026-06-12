---
title: "ubuntu 8.1 livecd on a 32GB USB"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by bavi on 2009-02-06
I created a usb startup disk but when I start the computer using the USB, it says only 3.6 GB free on the drive(I assigned all the memory to ubuntu). 

I like to have ubuntu live cd and windows xp using virtualbox on the usb.  what is the proper way for it?

---

### Post by C.S.Cameron on 2009-02-06
Persistence on a typical "Live" install is stored in a file named casper-rw.
As the partition it is on is formatted Fat there is a limit to file size.

You can create two new partitions formatted ext3 and label them casper-rw and home-rw.

These partitions will make the install persistent without the limits of Fat file size.

Alternately you can do a full install to your flash drive just like to an internal HDD. This sort of install is fully upgradeable but takes about a gig of extra disk space.
Suggest disabling your internal HDD before proceeding.

---

### Post by bavi on 2009-02-09
I created two partition as mentioned above. casper-rw with 11 GB & home-rw with 10 GB.  even ext3 shows 3.6GB free after startup usb created.  Any other option to accomplish my need?

---

