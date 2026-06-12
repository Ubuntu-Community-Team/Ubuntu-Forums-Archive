---
title: "No drive being detected at install"
date: 2010-06-24
forum: Hardware
---

### Post by glimmung on 2010-06-24
You know you are in trouble when the first link in Google for the issue you are trying to solve says "[You are a dumbass]("http://www.google.co.in/search?sourceid=chrome&ie=UTF-8&q=LSI+megasr+1068e+ubuntu")".

Anyway, I got a new machine at work which is a Fujitsu Celsius R670 server and it has this LSI fakeraid thing (LSI MegaRaid 1068e). When I try to install Linux it does not see any drive on the machine. Any idea on how could I solve this? I want to install Ubuntu on this but at this point I will be happy with any Linux flavor. The company we bought this from will only install Redhat Enterprise on this but I'd rather have a free distribution.

---

### Post by dabl on 2010-06-24
If there is a SATA RAID mode in the BIOS, you need to disable it.

Then, use an Alternate Install CD -- it has fewer issues seeing the SATA drive(s) than the Live CD with Ubiquity.

---

### Post by dino99 on 2010-06-24
better to prepare formatting before installing: boot on partedmagic

then remove raid installation if any: sudo dmraid -rE (open a console from partedmagic)

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by glimmung on 2010-08-18
Was not able to get it to work with either of the above two methods. What finally worked was removing the drive from the SAS port and connecting to the SATA port. Everything installed smoothly after that.

---

