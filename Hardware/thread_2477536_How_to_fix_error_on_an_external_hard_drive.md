---
title: "How to fix error on an external hard drive"
date: 2022-07-28
forum: Hardware
---

### Post by ubontik22 on 2022-07-28
Dear Experts,

The hard drive does not see one folder. I guess what happened... Once the power went down, hard drive was mounted, and after that the folder is not showing up.
Now, if I leave the hard drive mounted, and try to power off computer stays on until I unplug HD.

Thank you.

---

### Post by TheFu on 2022-07-29
Run an fsck on each file system on the drive.  There are lots of fsck how-to guides - just search the internet.  Ensure the file system is NOT mounted before you run the fsck.  The tool shouldn't allow that error, but we can force all sorts of things and make the situation much worse.

Typically, there is 1 file system per partition, but if you are using LVM, ZFS or BTRFS, the answer is a bit more complex, and you probably wouldn't be asking us any questions.


Of course, power hits can break things in any electronics, so the fsck may not fix it.  Sometimes life sucks, but I'm hopeful that the fsck will handle the current inconsistencies and all will be well.

After running fsck and it correcting any found errors, just run 
```
sudo mount -a
```
and that will mount all the non-mounted file systems listed in the /etc/fstab.

We had a hard power hit here last week and 1 of my USB backup drives needed an fsck.  Most of my stuff is on UPS batteries that last 45 minutes, but it seems 1 USB drive isn't. I really need to trace all the power connections to ensure they go into one of the UPS plugs. I need to re-balance the power across both UPSes in my office.

---

### Post by ubontik22 on 2022-07-29
I ran fsck as a root and got the following output:
> # fsck /dev/sdf
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdf

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Found a dos partition table in /dev/sdf

---

### Post by Autodave on 2022-07-29
Generally, when you see a superblock problem, the drive is toast.  Your chances of getting anything off of it are slim.  Reformatting it will usually allow you to reuse it, but I wouldn't trust it for anything precious.  To prevent this in the future, get yourself a UPS (uninterruptible power supply).

---

### Post by TheFu on 2022-07-29
This doesn't look correct. 
```
$ fsck /dev/sdf
```
The whole disk isn't likely to have a file system nor a superblock. 

That is pointing at the entire disk, not a partition. Typically, a file system would be placed onto a partition, not the whole disk.  To check, run
```
sudo fdisk -l  /dev/sdf
```
and post the results.  There should be a list with numbers on the left.  Those numbers are the number of the partition, if there are any.  It would be very odd.  BTW, if using LVM or BTRFS or ZFS, we need to see different information, but start with the fdisk "list" command above.

---

### Post by ubontik22 on 2022-07-30
Thank you for the reply.
Below is an output:
> $ sudo fdisk -l  /dev/sdf
 
Disk /dev/sdf: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: External USB 3.0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xb428d408

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sdf1  *    206848 976771071 976564224 465.7G  7 HPFS/NTFS/exFAT

---

### Post by TheFu on 2022-07-30
> **ubontik22 said:**
> Thank you for the reply.
Below is an output:

Ok, it is an NTFS file system on partition 1.  fsck cannot fix that. You need Windows to fix NTFS issues.

---

### Post by ubontik22 on 2022-07-30
[**[COLOR=#000000]TheFu[/COLOR]**]("https://ubuntuforums.org/member.php?u=1037685"), thank you. I'll look for a Windows machine.

---

### Post by hk42 on 2022-07-31
That is one of the many reasons why deleting a paid for Windows partition
to get a Linux only system is a bad idea.
Grub allows lots of options let's make good use of them.

---

### Post by mattbach on 2022-08-01
I thought you could fix NTFS systems with just a windows 10 boot usb or DVD.

---

### Post by rsteinmetz70112 on 2022-08-03
I think you can. You can also create a boot disk that contains the basic tools including chkdsk from the Windows Control Panel.
Or since this is an external HArd Drive you could simply connect it to a Windows computer and run chkdsk.

---

### Post by ubontik22 on 2022-08-12
Thank you All.

I've fixed with Windows check

---

