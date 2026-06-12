---
title: "Howto manualy fix sda device"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by shareMenaPeace on 2007-01-11
Hello,
sorry for double post but actualy nobody visited this topic over at the beginner forum

I just followed a user tip on howto clean a partition.
See here [http://ubuntuforums.org/showthread.php?t=336228](http://ubuntuforums.org/showthread.php?t=336228)

All went ok but now ubuntu is unable to mount the device.

> Log of fsck -C -R -A -a 
Thu Jan 11 18:53:20 2007

fsck 1.39 (29-May-2006)
/dev/sda2: clean, 11/272544 files, 25763/544201 blocks
fsck.ext3: Unable to resolve 'UUID=529b09ba-0750-4dde-baed-19c0fedd5eae'
/dev/sda7: clean, 18/1661376 files, 2270026/3321430 blocks
fsck died with exit status 8

Thu Jan 11 18:53:20 2007

Any idea how to fix this?
The console says it needs to be done manualy.

I know of the mount points, but they dont changed as i just formated the device.
I have no idea where to start ...Can someone help me please? 

Thanks

---

### Post by shareMenaPeace on 2007-01-11
Fix is here 
[http://ubuntuforums.org/showthread.php?t=336279](http://ubuntuforums.org/showthread.php?t=336279)

---

