---
title: "Recovering data from unreadable RAID mirrored disks"
date: 2012-04-27
forum: Hardware
---

### Post by pnero on 2012-04-27
Hello all,

my previous pc (ubuntu+AMD) brought me a lot of pain, so I decided to change it; the Asrock motherboard supported RAID, so I  used two 500GB drives in mirrored configuration (ext4). To my knowledge, this should produce two exact copies of data, but each one of the disk should be readable as once if needed.
I was evidently wrong: when I tried to plug any of the two drives to my new pc (either via sata and usb) to move the data, I was unable to detect and mount the disk. Only gparted detected the drive, but the partition showed up as unknown/unallocated; I tried to scan the disk to detect the filesystem using gpart, but it hanged up for hours unsuccessfully.

I put back the RAID array in the old pc (where the partition was fully readable) and I started transferring data using samba - But it was a slow process, as the old pc kept freezing randomly as usual because of other reasons.
Some days ago, when rebooting the old pc, I found out the raid partition configuration had been lost for some reason, and hence the /data partition was no longer available.

The data should still be on the disks, but if I try to recreate a raid configuration at startup time the computer tells me that all the data on the disks will be lost... So it looks like I have no way to access my data to move it on my new pc, even if I own two copies of it!

Do you think I still could try something else, or should I consider my data lost?
Thanks

---

