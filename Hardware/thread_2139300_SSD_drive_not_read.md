---
title: "SSD drive not read"
date: 2013-04-26
forum: Hardware
---

### Post by alican timur on 2013-04-26
I have an Asus Zenbook UX32VD which contains a 500 gb spinner and a 30 gb ssd drive. I had a windoze installation when I got the machine, and I've backed up quite a lot of things in the SSD (windows filesystem).

Now after installing ubuntu, I can't mount the drive. 

fstab: (doesnt even see it)

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=913b72be-07fe-4eab-8168-87b9b5e4c63c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c496d22f-52c6-4c30-af5d-a0947b529eb2 none            swap    sw              0       0
```

"Disks" says that the drive is on
/dev/sdb 
and the primary logical partition im looking for is on 
/dev/sdb1. (filesystem HPS(?))

please help?

---

### Post by oldfred on 2013-04-26
Is this an UltraBook and SSD really was Intel SRT or just caching the Windows on the hard drive? SSD will then have RAID meta-data that needs to be removed to see it.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

    
 > Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

