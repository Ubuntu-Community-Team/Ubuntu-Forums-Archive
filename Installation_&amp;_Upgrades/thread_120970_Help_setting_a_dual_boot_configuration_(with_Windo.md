---
title: "Help setting a dual boot configuration (with Windows XP)."
date: 2006-01-24
forum: Installation &amp; Upgrades
---

### Post by DAXP on 2006-01-24
I've tried many times before, getting Grub errors 15, 17, or 22 after trying. I have two 400GB HDDs in a RAID 0 setup, and one IDE 160GB HDD. Before getting the IDE HDD and wanting to install Linux, I had Windows on the RAID HDDs. Now, however, I get a problem trying to instal Windows onto the disks. The drivers supplied by my motherboard are not certified by Windows, and require you to authorize installation of them. After a while it comes to one that I cannot do, whether by clicking no or yes. The pointer freezes and the keyboard no longer works here. 

When I tried to have the dual boot config, I had the Windows on the IDE drive and Linux on the RAID (though it showed as two different 400GB HDDs instead of one 800GB HDD). This caused the errors. I now want to know if I would have a different outcome by installing Linux and Windows onto small partitions of the 160GB HDD, and installing/storing all programs for both OSes onto the two 400GB HDDs, setting them to JBOD instead of RAID 0. If so, I also need to know if there is a driver of some sort I could download online to gain access to my 400GB HDDs, as I have had no success at all trying to install the drivers with Windows. And, to confirm, both OSes can read and write to ext3, correct? 

I also know the HDDs are still fully functional, as I'm now running on Ubuntu. Everything works fine, it's just getting dual boot and Windows to work right.

Thanks in advance, and sorry if this post seems hard to read. I seem to have a problem writing or typing things that are kinda long. >_>


EDIT: Actually, it could have been Grub error 21 instead of 22. Something in the low twenties, at least.

EDIT 2: After toying around with the Windows and Ubuntu installers, I have managed to make this work. I now have them both set to dual boot. Woohoo!

---

### Post by Oren on 2006-01-25
Yes but how?

Please detail..... :confused:

---

### Post by dundas on 2006-01-25
ya, I also wanna know how did u manage that? grub in mbr? and then it auto dual boot windows without a prob?doesn't affect NT loaders?

---

