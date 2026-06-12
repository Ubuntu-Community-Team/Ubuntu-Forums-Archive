---
title: "Recently did an HP-update and dual-boot broke"
date: 2011-08-16
forum: Hardware
---

### Post by mayotte on 2011-08-16
I have an HP Pavilion dv6. I set it up for dual boot between the stock Windows 7 and Ubuntu 11.04 (which was very easy thanks to Ubuntu's smart installer.) It worked great for months. 

  A couple of days ago HP's updater installed one or more software updates to the windows side. After that, Windows fails to boot (Ubuntu is fine). 

  I restore the laptop to it's factory condition using the HP restore disks. (I back up, so data loss isn't an issue.) I update windows (over and over and over), Norton 360, AND run all of the HP updates, and windows still boots fine. But when I install Ubuntu dual-boot again, Windows stops booting. 

  My best (wild) guess is some sort of incompatibility between Grub2 and whatever HP's updater did (possibly something related to power management.) 

  I dread trying to talk to HP about Linux, so I thought I would check here first.  Is anyone else running dual-boot on a Pavilion dv6 or similar? Have you seen this? Is there a known fix?

---

### Post by Johnb0y on 2011-08-16
could try rebuilding boot loader...

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

did the trick for me once i did dual boot with ubuntu (ubuntu as last install after windows as windows was my main OS at the time)

---

