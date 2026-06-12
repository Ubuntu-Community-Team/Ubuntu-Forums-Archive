---
title: "Problem with Ext HDD - no folders visible"
date: 2012-06-26
forum: Hardware
---

### Post by juitz on 2012-06-26
Hi all,
I've managed to somehow lose the folders on an WD external HDD which I use to keep photos, music, etc...
I'm using Ubuntu 11.04 and I formatted this drive to Ext3. I had no problems with it for a long while but decided to transfer some files from a Windows 7 machine using ext2fs program. When I plugged the drive back into my Ubuntu machine, none of the folders are visible except for the lost+found folder. 
Any ideas as to what I have done and if I can reverse it?


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d39fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38149   306425856   83  Linux
/dev/sda2           38149       38914     6142977    5  Extended
/dev/sda5           38149       38914     6142976   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029fe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953511424    7  HPFS/NTFS

edit: when I plug the drive back into the Windows 7 machine using ext2fs I can see all the folders and files without a problem. Guessing it's a ownership issue or such?


Cheers!!

---

### Post by juitz on 2012-06-28
bump

---

### Post by ahallubuntu on 2012-06-28
Something doesn't make sense.  You said you formatted the drive as ext3, yet the output of your fdisk command shows the internal drive /dev/sda having ext partitions but /dev/sdb having one big NTFS partition?  Is /dev/sdb your 2TB WD drive, or is that some other drive?

What am I missing?

I've personally had issues with the ext for Windows drivers, particularly with external drives.  I'd stick to NTFS if you ever plan to use such a drive with Windows - and it sounds like you do.

FYI, it's very dangerous to have only one copy of your files on a single drive.  Hard drives fail all the time, sometimes without warning, and you could easily lose everything.  If you have anything of vital importance on this drive - irreplaceable pictures, etc. - it would be wise to have a backup on a second drive, just in case.

---

### Post by juitz on 2012-06-28
> **ahallubuntu said:**
> Something doesn't make sense.  You said you formatted the drive as ext3, yet the output of your fdisk command shows the internal drive /dev/sda having ext partitions but /dev/sdb having one big NTFS partition?  Is /dev/sdb your 2TB WD drive, or is that some other drive?

What am I missing?


Yes, you are correct. I formatted the WD 2TB drive to ext3 when I first installed Ubuntu and have been using it as my "media" drive. At the time, I wasn't planning on using windows which is why I formatted to ext3. But now I see I might need to format to NTFS in the future. 
(p.s. I have important files backed up :) )

I don't know why it's showing up as NTFS when I formatted to ext3, or why the files/directories do not show up in Ubuntu but they show up in Windows when using ext2fs?

---

### Post by ahallubuntu on 2012-06-28
> **juitz said:**
> Yes, you are correct. I formatted the WD 2TB drive to ext3 when I first installed Ubuntu and have been using it as my "media" drive. At the time, I wasn't planning on using windows which is why I formatted to ext3. But now I see I might need to format to NTFS in the future. 
(p.s. I have important files backed up :) )

I don't know why it's showing up as NTFS when I formatted to ext3, or why the files/directories do not show up in Ubuntu but they show up in Windows when using ext2fs?

I think you are mistaken about formatting this drive as ext3.  I think it is still NTFS.  Just because you think you are using ext2fs in Windows doesn't mean it's DOING anything.  All that does is let it show up as a drive letter.  If you're accessing it as say E: in Windows, it's E: whether it is ext2 or NTFS.  If it is ext2, you'd need the driver for it to show as a filesystem in Windows.

Are you actually mounting it in Ubuntu?

sudo mount /dev/sdb1 /mnt

?

(And then what shows up in /mnt ?)

It doesn't automatically mount unless you tell it to in /etc/fstab .  I don't recommend that for an external drive anyway.

---

### Post by juitz on 2012-06-30
> **ahallubuntu said:**
> I think you are mistaken about formatting this drive as ext3.  I think it is still NTFS.  Just because you think you are using ext2fs in Windows doesn't mean it's DOING anything.  All that does is let it show up as a drive letter.  If you're accessing it as say E: in Windows, it's E: whether it is ext2 or NTFS.  If it is ext2, you'd need the driver for it to show as a filesystem in Windows.

Are you actually mounting it in Ubuntu?

sudo mount /dev/sdb1 /mnt

?

(And then what shows up in /mnt ?)

It doesn't automatically mount unless you tell it to in /etc/fstab .  I don't recommend that for an external drive anyway.
I formatted the drive using the format option using ubuntu and chose ext3. Not sure why it now shows as NTFS? 

Like I said, I had no problems seeing the directories on the drive. Usually, when I plugged it in, the drive showed on the desktop as I was able to navigate without problem. Now the drive shows but no directories are visible. 

I'll try to use the command you suggested and let you know the of the output. 

Cheers!

---

### Post by juitz on 2012-07-02
Hi, 
I entered the command you suggested and got no errors.
FYI - i think my drive is ext4? Im a very inexperienced user o not sure if this helps? fstab file:


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=e6030f03-3636-4d06-bd1a-747a7af3f799  /               ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=345ad7bf-8e79-493c-a134-b7d34a974647  none            swap  users,sw,user,owner  0  0  
/dev/sdb1                                  /media/DAVEHDD  ext4  defaults             0  0

---

