---
title: "USB Flash partitions"
date: 2009-10-27
forum: Hardware
---

### Post by nemiux on 2009-10-27
Hey, everyone. I have a 16gb flash, and I tried to install ubuntu on it, however, after one try ([http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/)) my flash divided in two and instead of 16gb, i was left with only 8. It happened before on the old flash, I mean the partitions. I used fdisk command to get it to normal, than windows asked me to format it, everything was sloved. However, with the new flash, i enter fdisk /dev/sdb (b is my flash letter there), and there is only one partition. I try to delete it create a new one, give it win95 fat 32 (hex code 'c'), but it didn't work, still 8gb on windows. Could someone help me with that? Thanks

---

### Post by IcarusR on 2009-10-27
If you look at the script you downloaded in step 4 on the linked web page you will see that it creates 2 partitions, each 50% of the flash drive. One is ext2 (linux) & the other is fat32 (windows) they are then formatted with their respective file systems. 

The lesson here is to read through downloaded scripts before running them.

Did you try booting from the flash drive after following the instructions ??

---

