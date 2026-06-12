---
title: "Hard disk problem, interfering with installation"
date: 2012-02-21
forum: Hardware
---

### Post by javierc on 2012-02-21
I have this problem, am trying to install xubuntu: but i get errors that the hard drive might have be bad and the installation just stops.

knowing windows, windows lets you scan sectors and mark bad sectors

I have not yet install xubuntu and hard drive is blank, so i can only boot from the flash drive trying to to install xubuntu

---

### Post by ahallubuntu on 2012-02-21
You need to test the hard drive to see if it's bad or not.

Try the Parted Magic CD to query the drive's S.M.A.R.T. status - download it and burn the ISO to blank CD, then boot it.

[http://sourceforge.net/projects/partedmagic/](http://sourceforge.net/projects/partedmagic/)

and run SmartControl.  Look for Attributes that are highlighted in pink.  You can also run S.M.A.R.T. tests like the Extended Test.

If you see serious S.M.A.R.T. errors, the drive is bad and you can't use it for Xubuntu.

---

### Post by javierc on 2012-02-22
Done and GSmartControl says overall health Self-Assessment Test Passed

and that it does have bad sectors, they are labeled as uncorrectable error in data i hope it just means bad sectors

---

### Post by ahallubuntu on 2012-02-22
Sounds like you need to get a new hard drive if this one has bad sectors.

---

### Post by javierc on 2012-02-22
Windows can scan for bad sectors and makes so the file system never uses them and this utility in linux is like difficult to find


I been using file system ext4 because its there by default when you install xubuntu

---

### Post by javierc on 2012-03-15
thanks ahallubuntu for the software to diagnose the hard drive and it turns out it was healthy, what i needed to do was to use Gpartition and partition it to linux ext4 or ext3 then right click it > select check > 

selecting check, checks for bad sectors and after that it worked fine and completed installation

---

