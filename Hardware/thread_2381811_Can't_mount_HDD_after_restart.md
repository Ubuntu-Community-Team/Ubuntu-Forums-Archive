---
title: "Can't mount HDD after restart"
date: 2018-01-05
forum: Hardware
---

### Post by rouvenster on 2018-01-05
Hi,
I have a bunch of HDD connected to my pc, and one of them is named "Lacie NTFS" as "sdc" with 2 partition (sdc1 which i can access, and sdc2)
Well, I may have deleted some windows folder from the sdc2 (something like windowsapp or something) but i was able to access it before. Sadly, after the restart, When I try to open the partition it says :

"Error mounting /dev/sdc2 at /media/ruben/Lacie NTFS DOCS:
 Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdc2" "/media/ruben/Lacie NTFS DOCS"' 
exited with non-zero exit status 13: ntfs_mst_post_read_fixup_warn: magic: 0xffffffff  size: 1024   usa_ofs: 65535  usa_count: 65534: Invalid argument
Record 6 has no FILE magic (0xffffffff)
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sdc2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details."

Problem is, I don't have WIndows anymore on my PC, but I am sure there is a linux magic software out there than can solve my problem in 2 seconds. I already found a thread from 2011 from a guy with the same problem and he said a package called NTFSprogs resolved it but sadly it seems it became obsolete.
Any ideas ?
Thanks

---

### Post by sccman on 2018-01-05
ntfsprogs was merged with ntfs-3g in 2011: [https://en.wikipedia.org/wiki/Ntfsprogs](https://en.wikipedia.org/wiki/Ntfsprogs)

Try installing ntfs-3g:

```
sudo apt install ntfs-3g
```

If ntfs-3g wasn't installed then the drive may have been slightly corrupt without the software.

You could try the instructions using ntfs-3g and see if that works. If that doesn't work I know you can run Linux's version of chkdsk /f:

```
sudo umount /dev/sdc
sudo fsck /dev/sdc
sudo mount /dev/sdc /media/ruben/Lacie
```

---

