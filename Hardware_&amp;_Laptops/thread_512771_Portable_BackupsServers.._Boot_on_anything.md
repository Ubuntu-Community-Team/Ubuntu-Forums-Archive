---
title: "Portable Backups\Servers.. Boot on anything?"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by justinshafer on 2007-07-29
Wow this is pretty cool. WIth all the combined knowledge from the forums and google I have managed to get Fesity booted from a usb flash drive that saves info with the unionfs. So I have made a portable open dental server with mysal, samba, mono, etc. Very cool. 

Here is what I want. The ability to save and union with /dev/md0 instead of /dev/sda2. I want /dev/sda2 and /dev/sdb2 to be raid arrays, with /dev/sda1 and /dev/sdb1 having a bootabe fat16\fat32 partition as well.

Is this possible? Will it all conflict? If it wont (I will find out soon) 

It will allow me to create a server that has 2 internal hard drives and 5 external drives. I want them to all be raid 1, and the external drives will be labeled monday tuesday wednes, etc.

So we can deactivate them from the raid and take them offsite (we also rsync offsite with x-rays and mysqldump etc) each day. And when tuesday is hooked up I want the drive to be synced with the internal drives.

every drive will have the bootable fat16 partition so they will all be "live hd's". and if the server goes down the external 160gb freeagent go drive can be booted off a workstation, and then be the server, because of hardware detection. 

Am I Crazy? I dont see why it wouldnt work... If /dev/md0 is labeled casper-rw, and the 2nd partition on the actual drives are not labeled casper-rw. The fat directories will just be individual partitions that help boot the raid array, or repair, memcheck etc. =)

---

