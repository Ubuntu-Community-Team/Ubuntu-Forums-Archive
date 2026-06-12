---
title: "Ext4 is it ready yet?"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by Wanas on 2009-02-24
Is the ext4 ready to use at the desktop use or not?
and If its great to use it at home what is the best way to format my partition to ext4 extension, is it by parted magic live CD or what? 
I want to install ubuntu 8.10 i386.

---

### Post by wfp on 2009-02-24
I would wait for Ubuntu Jaunty to start using Ext4. Jaunty will be using Kernal 2.6.28. So heres some information i found here> [http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)
Ext4 was released as a functionally complete and stable filesystem in Linux 2.6.28, hence it's safe to use it in production environments, but as any piece of software, it has bugs (which are more likely to be hit in the first stable versions). Any known critical bug will be quickly fixed.

---

### Post by lensman3 on 2009-02-25
It is ready.  I installed it on a terabyte drive.  I have it running on top of Truecrypt.  So I first formatted the drive with truecrypt and then did a mkfs.ext4 on top of that.  It as been running for about 2 months and not a hiccup.   I am running Fedora core 10 with kernel 2.6.27 (2.6.27.12-170.2.5.fc10.x86_64). The ko files have been available for several releases.  

I am about to try converting a ext3 to an ext4  without a format.  That will be the test if everything is working.  But I'll make sure to backup first.

---

### Post by absolutezero1287 on 2009-02-25
Ext4 is great. I think they're going to (or already do) support online defragmentation.

---

