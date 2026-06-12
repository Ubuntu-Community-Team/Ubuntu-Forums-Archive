---
title: "formatting usb-stick"
date: 2008-10-03
forum: General Help
---

### Post by Achilles124 on 2008-10-03
I formatted an[COLOR="Red"] USB-stick[/COLOR] with G-parted live CD. There was some program installed on it and I wanted to get rid of it. Sandisk or something it was called. Anyway, it left a map on the stick called "lost+found". I right-clicked to get the menu and I clicked on properties. There it says that I cannot do anything with it because I do not own the stick. I am not the owner so I cannot change the permissions. 

Meanwhile the stick is useless because I cannot paste anyting on the stick.

What to do?

---

### Post by Sycron on 2008-10-03
Make sure you have the proper rights to copy the files. Open up a terminal and type ```
gksudo nautilus
``` Then try to copy a file.

lost+found is the place where corrupted files are placed when they are found during a filesystem check.

---

### Post by Achilles124 on 2008-10-03
Didn't work. But I did get an errormessage:
> Details
Mount: wrong fs type, bad option, bad superblock on /dev/sdf, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try. dmesg|tail or so

---

### Post by Sycron on 2008-10-03
Scan the removable device ```
sudo fsck /dev/sdf1
```.

---

### Post by Achilles124 on 2008-10-03
This is the message I get:
> fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: No such file or directory while trying to open /dev/sdf1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by Sycron on 2008-10-03
How about ```
sudo fdisk -l
``` .

---

### Post by Achilles124 on 2008-10-03
This is what I get:
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009fa48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/sdf: 2048 MB, 2048728064 bytes
64 heads, 62 sectors/track, 1008 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Disk identifier: 0x000be0ab


---

### Post by Sycron on 2008-10-03
You don't have any partititons on your usb stick. That's why don't work. Are you sure that you copied the exactly output of **sudo fdisk -l**

---

### Post by Achilles124 on 2008-10-03
someone else has the same problem:
[http://ubuntuforums.org/showthread.php?t=925505&highlight=superblock]("http://ubuntuforums.org/showthread.php?t=925505&highlight=superblock")

Unfortunately with no solution.

---

### Post by Sycron on 2008-10-03
The link you posted is not exactly your problem.

---

### Post by Achilles124 on 2008-10-03
yes, that is the exact output after sudo fdisk -l

---

### Post by Sycron on 2008-10-03
Use gparted again and create a new partition. Then format it and try again.

---

### Post by Achilles124 on 2008-10-03
Used G-parted and I made a partition. One of 15.69 Mb and the other the rest of the 2Gig. I formatted the second partition. Couldn't format the 16 MB though. It is called "unallocated". Tried to use the stick again but couldn't mount the stick. Same problem.

---

### Post by Sycron on 2008-10-03
Unallocated is the free space on your usb stick. Is NOT a partitition. Post the output of the ```
sudo fdisk -l
``` again.

---

### Post by Achilles124 on 2008-10-03
This is what I get:
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009fa48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18700   150207718+  83  Linux
/dev/sda2           18701       19457     6080602+   5  Extended
/dev/sda5           18701       19457     6080571   82  Linux swap / Solaris

Disk /dev/sdf: 2048 MB, 2048728064 bytes
255 heads, 63 sectors/track, 249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000be0ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               3         249     1984027+  83  Linux


---

### Post by Achilles124 on 2008-10-03
I have searched for disk properties and it says:
1 item, with size 16,0 KB
(some contents unreadable)

---

### Post by Achilles124 on 2008-10-03
I give up. I tried to format the stick again but now it is definitely broke. Thank you Sycron for answering my question.

---

### Post by mike555 on 2008-10-03
I think your problem might be the "U3" software on the Sandisk thumbdrive , it needs to be removed using the U# uninstaller from their site  (in Windows )because it's a separate locked partition ......

---

