---
title: "what is needed to use an ext4 partition on Intrepid?"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by graysky on 2009-04-08
I am running Intrepid-amd64 with my own kernel (2.6.29) in which I have enabled support for ext4.  I checked, and the version of e2fsprogs that is in the Intrepid repo is 1.41.3 which isn't the latest, but should be fine for ext4 partitions, right?  What else do I need to update/make sure I have installed to safely convert my /home partition to ext4?

I don't think I'll be converting / to ext4 until I'm using Jaunty/stable so for now, it's just /home (I think an update to grub is required to boot an ext4 formatted / no?)

---

### Post by whoop on 2009-04-08
If I understand you correctly you are currently running intrepid with ext3 and you don't really want to use ext4 until you upgrade to jaunty and you don't want to do a fresh install of jaunty.

I upgraded to jaunty a while back and I converted my file system from ext3 to ext4 via the following method:
[http://ubuntuforums.org/showpost.php?p=7026195&postcount=8](http://ubuntuforums.org/showpost.php?p=7026195&postcount=8)

---

### Post by graysky on 2009-04-08
> **whoop said:**
> If I understand you correctly you are currently running intrepid with ext3 and you don't really want to use ext4 until you upgrade to jaunty and you don't want to do a fresh install of jaunty.

Not quite... I am using Intrepid now and plan to do a fresh install of Jaunty when it is 'final' but I am interested in messing around w/ ext4 now.

> I upgraded to jaunty a while back and I converted my file system from ext3 to ext4 via the following method:
[http://ubuntuforums.org/showpost.php?p=7026195&postcount=8](http://ubuntuforums.org/showpost.php?p=7026195&postcount=8)

I'll have a look.

---

