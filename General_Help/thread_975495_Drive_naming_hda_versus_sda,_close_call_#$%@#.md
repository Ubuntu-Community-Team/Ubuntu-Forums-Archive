---
title: "Drive naming hda versus sda, close call #$%@#"
date: 2008-11-08
forum: General Help
---

### Post by dhughes on 2008-11-08
Not so much Ubuntu family specific as it is all Linux i.e. the way drives are currently named are "sda" instead of "hda", the old days an IDE hard drive was hda and as far as I can recall a USB thumbdrive was sda. From what I have heard sda is now used due to most disks being SATA instead of IDE, I don't know if that's true or not.

 After a very close call of nearly wiping a 300GB disk (sdb...not my main drive) instead of a 3.5GB USB key (sdc) I uttered a few curse words about the very close call. Even saying sdb and sdc is confusing. Yes I know hda, hdb and hdc would be as confusing but I'm more concerned with smaller USB thumb drives which are formatted and moved around more often than an internal system drive.

 I wish there was a more distinct way to specify, critical, system drives compared to smaller possibly less important drives.

---

### Post by geirha on 2008-11-08
> **dhughes said:**
> Not so much Ubuntu family specific as it is all Linux i.e. the way drives are currently named are "sda" instead of "hda", the old days an IDE hard drive was hda and as far as I can recall a USB thumbdrive was sda. From what I have heard sda is now used due to most disks being SATA instead of IDE, I don't know if that's true or not.

That is correct. Read about it here [http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce](http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce)

Ubuntu has been using the new drivers gradually as they've become stable.

> **dhughes said:**
> 
 After a very close call of nearly wiping a 300GB disk (sdb...not my main drive) instead of a 3.5GB USB key (sdc) I uttered a few curse words about the very close call. Even saying sdb and sdc is confusing. Yes I know hda, hdb and hdc would be as confusing but I'm more concerned with smaller USB thumb drives which are formatted and moved around more often than an internal system drive.

 I wish there was a more distinct way to specify, critical, system drives compared to smaller possibly less important drives.

I always run ```
sudo fdisk -l
``` and carefully identify which is the correct drive before I start wiping things. ```
sudo lshw -class disk
``` gives you a nice overview as well.

---

