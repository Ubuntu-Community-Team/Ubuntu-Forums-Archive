---
title: "Can't create raid due to no /dev/md0"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by seertenedos on 2006-09-22
guy and girls,
I am trying to create a raid 5 array after i have installed to HD using the latest server edition.  I currently have the lastest version of webmin on there as well just to make things a little easier for me as i am not sure of all the commands to do everything in the console.

Whne i tried to create the raid 5 array i get the following error.
Failed to create RAID : mdadm in --create mode failed : 
mdadm: error opening /dev/md0: No such file or directory

So i checked /dev to see if md0 existed and it does not. How do i create this device?  I am sure i am missing some step but everything i have tried has failed to create the md0 device.

Chris

---

