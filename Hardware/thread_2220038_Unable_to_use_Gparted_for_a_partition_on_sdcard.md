---
title: "Unable to use Gparted for a partition on sdcard"
date: 2014-04-26
forum: Hardware
---

### Post by vkay on 2014-04-26
Hey guys,

some days ago I installed Android system on my micro sdcard. Now, I want to delete the created partition of 2GB from it (32GB). In Windows the partition was not visible, so I installed Ubuntu and it was visible.

I tried Gparted to delete it. The problem is that the programm tries to check the storage (/dev/sdb) endlessly when I unmount it.
I already tried unmount it firstly with terminal:

sudo umount /dev/sdb3

but then Gparted checks the storage at startup endlessly. Other partitions on the sdcard can be edited without problems.

Can anyone help? Are there other alternatives out there?

Thanks ^^

---

### Post by coffeecat on 2014-04-26
I have one slightly drastic solution - but it involves effectively removing all the partitions. When I have been confronted with a similar situation I have simply zeroed out the first few kilobytes of the device using the terminal in order to remove the partition table. If you then unplug it and plug it back in again, none of the partitions can be mounted and gparted will see it as unallocated. You can then create a new partition table in Gparted from the Device menu, and then whatever partitions you need.

Assuming your SD card is sdb, this should do the trick:

```
sudo shred -vzn 0 /dev/sdb
```

Wait a few seconds until the terminal output tells you it has done enough - a MBR partition table is only 512 bytes long - and then ctrl-c to stop the process. Be very, very careful that you use the correct device identifier - you say sdb, but check this. One time that I did this, in a fit of absent-minded carelessness I typed sda instead of whatever it should have been and wiped out the partition table on my main multi-booting drive. The good news was that it was an opportunity for me to learn how to use testdisk in the real world. :rolleyes:

One caveat - I have no experience of installing Android to a SD card and I wonder if the partition table may not be a simple mbr one. There might be GPT data at the end of the drive. In which case you might need to zero the whole drive.

---

