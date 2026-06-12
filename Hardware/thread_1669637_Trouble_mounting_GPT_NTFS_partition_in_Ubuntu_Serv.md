---
title: "Trouble mounting GPT NTFS partition in Ubuntu Server 10.10"
date: 2011-01-18
forum: Hardware
---

### Post by tyreck on 2011-01-18
I'm in the process of setting up a media server (Ubuntu Server 10.10) to house my movie and music collection and I've run into a small problem.

In anticipation of of building the server I purchased a 2TB WD drive and installed it in my main computer which is running Windows 7 Ultimate. I formated the drive using Windows 7 and chose GPT as the partition table and NTFS as the partition type (single partition on the drive).

It's come time to move the contents of this drive to another 2TB drive in the Ubuntu Server but it is not being recognized as an NTFS partition and subsequently won't let me mount it.

fdisk shows the following information
(i've included the other 2TB drive information for reference)
--------------------------------------------
Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   8e  Linux LVM

Disk /dev/dm-2: 2000.4 GB, 2000393601024 bytes
255 heads, 63 sectors/track, 243200 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-2 doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sde'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      266306  2147483647+  ee  GPT


gdisk shows the following information
------------------------------------------
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sde: 3907029168 sectors, 1.8 TiB
Disk identifier (GUID): C3326410-3290-4921-9F66-ED4535745092
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907029134
Total free space is 2157 sectors (1.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved par
   2          264192      3907028991   1.8 TiB     0700  Basic data partition


Any help is greatly appreciated.

(Unrelated question, the /dev/dm-2 entry in there is one of 10 entries like it. there is one for every lvm lv i created, though their sizes are not quite the same as the actual lv's. Why are these there and should they be?

Edit: They are not all aligned with the lv's two of them look like the drives [aka size matches the whole physical drive], the rest look like the lv's [approx. the same size as the lv's I created]. there is not how ever one for each physical drive, only the 2TB and the 500GB [which is actually two 500GB in an mdadm mirror].)

---

### Post by srs5694 on 2011-01-18
What does typing "sudo blkid /dev/sde2" produce for output?

Can you mount the partition manually by typing "sudo mount -t ntfs-3g /dev/sde2 /mnt"? Does typing this command produce any error messages?

---

### Post by tyreck on 2011-01-18
Wow, that was ridiculously easy.... I feel pretty dumb right about now!

I would have to assume that the second partition was not showing up because fdisk doesn't know how to read GPT, and I don't know how to read gdisk so i missed that it was showing two partitions.

mounting sde2 worked like a charm. (blkid showed that it was an NTFS partition btw)

Thank you

---

### Post by srs5694 on 2011-01-19
The tools most people use (knowingly or not) to mount partitions have nothing to do with fdisk, so fdisk's inability to handle GPT has nothing to do with the problem. Rather, it's the automounter in GNOME that's deficient, if indeed it can't recognize NTFS partitions on GPT disks. I seldom use GNOME directly, though, so I don't know all the details of its capabilities.

You might consider simplifying things in the future by creating an /etc/fstab entry for the partition, like this:

```

UUID=57D1E3C715464FC8  /some/convenient/directory  ntfs-3g  uid=1000,gid=100,dmask=022,fmask=133  0  0

```

Change the UUID value to whatever blkid reports for this and change /some/convenient/directory to the directory where you want to access the drive. (This directory must exist, but you can create a new one.) This entry will automatically mount the partition whenever you boot, give ownership of all files to whoever has UID 1000 (you can change this), and sets group ownership to GID 100 (normally "users"). The fmask and dmask options set the permissions so that files have 644 (rw-r--r--) and directories have 755 (rwxr-xr-x) permissions. You can change those options as well, of course.

Of course, if you just need to transfer the files on a one-time basis, this is probably overkill; just mount the drive and transfer the files.

---

