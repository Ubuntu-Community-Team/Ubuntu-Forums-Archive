---
title: "Issues with HPA - how to solve correctly"
date: 2013-05-04
forum: Hardware
---

### Post by malaTG on 2013-05-04
Hi everyone,

I recently got around to upgrade my server from 10.04 to 12.04 and it worked like a charm except for one thing which is kind of serious. After a couple of reboots it couldn't mount one of my disks anymore (3 TB :(). It was something about the partition being bigger than the disk and after some digging I found this

[http://hardforum.com/archive/index.php/t-1726071.html](http://hardforum.com/archive/index.php/t-1726071.html)

Where another person had solved it by disabling HPA at boot up. I tested it and now I can mount my disk however after reading this bug I got afraid that this is not something I should do

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/380138](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/380138)

My system is a "Gigabyte GA-P35-DS3" and I also has an extra SATA card "HighPoint RocketRAID 2300 4P SATA II" but no RAID set up just a bunch of disks.

Does anyone know how to solve this in the correct and "safe" way? Any input is appreciated

Best regards

Marcus

---

### Post by malaTG on 2013-05-13
bump

---

### Post by malaTG on 2013-07-07
bump

---

