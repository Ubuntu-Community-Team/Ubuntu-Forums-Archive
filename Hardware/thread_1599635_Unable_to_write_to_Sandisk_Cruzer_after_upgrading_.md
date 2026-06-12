---
title: "Unable to write to Sandisk Cruzer after upgrading to 10.10"
date: 2010-10-18
forum: Hardware
---

### Post by shayzu on 2010-10-18
Hi

Yesterday, my Ubuntu 10.04 desktop was successfully upgraded to 10.10. 
Everything seems to be OK, except that the OS is unable to write to 4GB Sandisk Cruzer USB drive, as it could before the upgrade.

On the other hand, the OS is able to write to a generic 4GB "noname" without any problem.

Could anyone advice if there's a way to overcome the issue?

Thanks!

Shay

---

### Post by Fafler on 2010-10-18
Open a terminal and type
```
tail -F /var/log/messages
```
Now connect the flashdrive and try writing something to it. Cut'n'paste the output.
Also do a
```
cat /etc/mtab
```
with the drive connected and post results.

---

### Post by shayzu on 2010-10-18
Hi

This was quick!

As I am now located remotely from my desktop, I only have a terminal access and the USB drive is in my bag ...

Enough of excuses ...

Now, right before answering me, I made a look at the output of dmesg and found the following:


20367.734206] scsi4 : usb-storage 1-7:1.0
[20367.734286] usbcore: registered new interface driver usb-storage
[20367.734288] USB Mass Storage support registered.
[20368.733055] scsi 4:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.20 PQ: 0 ANSI: 2
[20368.733504] sd 4:0:0:0: Attached scsi generic sg2 type 0
[20368.735915] sd 4:0:0:0: [sdb] 8027793 512-byte logical blocks: (4.11 GB/3.82 GiB)
[20368.736409] sd 4:0:0:0: [sdb] Write Protect is off
[20368.736413] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[20368.736415] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[20368.738534] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[20368.738540]  sdb: sdb1
[20368.745406] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[20368.745412] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[20370.595913] FAT: Filesystem error (dev sdb1)
[20370.595917]     fat_get_cluster: invalid cluster chain (i_pos 0)
[20370.595921] FAT: Filesystem has been set read-only
[20370.596125] FAT: Filesystem error (dev sdb1)
[20370.596127]     fat_get_cluster: invalid cluster chain (i_pos 0)
[20370.596246] FAT: Filesystem error (dev sdb1)
[20370.596248]     fat_get_cluster: invalid cluster chain (i_pos 0)
[20370.596363] FAT: Filesystem error (dev sdb1)
[20370.596365]     fat_get_cluster: invalid cluster chain (i_pos 0)
[20370.596483] FAT: Filesystem error (dev sdb1)
[20370.596485]     fat_get_cluster: invalid cluster chain (i_pos 0)
[20370.596600] FAT: Filesystem error (dev sdb1)
[20370.596602]     fat_get_cluster: invalid cluster chain (i_pos 0)
[20370.596716] FAT: Filesystem error (dev sdb1)
[20370.596718]     fat_get_cluster: invalid cluster chain (i_pos 0)
[20370.596833] FAT: Filesystem error (dev sdb1)
[20370.596835]     fat_get_cluster: invalid cluster chain (i_pos 0)
[20370.596949] FAT: Filesystem error (dev sdb1)
[20370.596951]     fat_get_cluster: invalid cluster chain (i_pos 0)
[20370.597060] FAT: Filesystem error (dev sdb1)
[20370.597062]     fat_get_cluster: invalid cluster chain (i_pos 0)
[27161.932043] usb 1-7: USB disconnect, address 2

I wonder if this is related to the problem.
I did try to write the USB drive from a Mac, and it did!!

Do you have any idea from the above?

I will later check your suggestion.

Thanks!

Shay

---

### Post by Fafler on 2010-10-18
That was exactly was i was looking for.
Do a
```
sudo fsck.msdos -aw /dev/sdb1
```

---

### Post by shayzu on 2010-10-18
Hi

GREAT!!!

This has solved the problem.
 I guess I didn't wait enough during the last umount after a file write to the disk.

Thanks a lot!!!!

Shay

---

