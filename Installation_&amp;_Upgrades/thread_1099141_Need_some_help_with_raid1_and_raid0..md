---
title: "Need some help with raid1 and raid0."
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by morsmortis on 2009-03-17
Alright here we go.  I just recently installed Ubuntu, and I am enjoying it.  However, I decided to mess around with the softraid functions within linux.   I installed with the alternative cd, and did this  

two 150 gig drives partitioned as follows

/boot raid1 partition  sda1/sdb1=md0 (both individual drives are marked as bootable)

/   raid0   partition sda2/sdb2=md1 (90gig) 
/home raid0 partition sda3/sdb3=md2 (200gig) 
and two 4 gig swap files. 

Okay... now when grub loads it tries to load ubuntu and gives me a loading screen but it dumps be to a shell and tells me Alert! /dev/md1 does not exist... 

When I run the recovery portion of the alternative cd, I can access md0, md1, md2, ect...   

So, I guess my question would be, What is causing this to happen?  I have read various guides and nothing mentions anything about this except that grub cannot see raid0.  Do I need to add some code to the grub loader to load mdadm?   

thanks in advance.

---

### Post by Pumalite on 2009-03-17
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=15605](http://ubuntuforums.org/showthread.php?t=15605)

---

### Post by morsmortis on 2009-03-17
I'm using softRAID and dmraid seems to be assigning sba1 and sba2 nvidia stripes under dmraid(dmraid -s is Claiming I have a 590mb stripe)I have two 150gb drives.   Mdadm is impotent and can't do a thing after boot. Mdadm has functionality in recovery where the appropriate softRAID mds are available but dmraid also displays the 590 stripe in the recovery shell.  I think this maybe a bug with fakeRAID interfering with softRAID during boot? 
I don't even have my fakeRAID enabled in bios and the system still detects it.    

  I read in another forum about a similar problem but I cannot find the post.


Does anyone have any idea how I can get dmraid not to install or how to uninstall it? Does softRAID require dmraid?  I did sudo apt-get remove dmraid in the recovery shell and it looked like it worked but it was still there on boot. :(  
But then again, I am still not sure if this will fix the problem.

---

### Post by davecgs on 2009-03-18
Here is the ultimate guide to RAID.  Trust me...this one rocks.


Here is one specific to Ubuntu

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

[http://www.ping.co.il/node/1](http://www.ping.co.il/node/1)

This one is for Fedora but I've never seen a better guide on using RAID on linux.

---

### Post by mrsteveman1 on 2009-03-18
Am i reading that wrong or do you have 2 partitions on the same disk RAID0'd together?

EDIT: nm, bad eyes :)

---

### Post by morsmortis on 2009-03-18
FIXED!   My previous raid array through windows was NOT deleted.  However, RAID support through the motherboard was disabled in BIOS. The install detected the old array, and still wanted to use it, even though I told it "No". Reenabling the old array and deleting it fixed the problem.

---

