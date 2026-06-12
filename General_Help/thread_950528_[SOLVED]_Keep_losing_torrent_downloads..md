---
title: "[SOLVED] Keep losing torrent downloads."
date: 2008-10-17
forum: General Help
---

### Post by rmjohnson144 on 2008-10-17
Whenever I turn on my computer and start Deluge to continue my ttorrent downloads I get an error and when it resumes it starts my downloads all over and I loose countless hours of download time.  I have my files on a secondary downloads drive.  I think it is not finding the drive when I first turn on my computer as I noticed that if I go to the downloads hard drive before starting Deluge then I don't get errors and it resumes my previous downloads just fine.

Is there something I need to do to make it recognize my hard drive at bootup?  My Places menu shows the drive there at startup, it just isn't being read properly by Deluge.  I even tried Azureus and got the same problems.

Any suggestions would be great
-=Mark=-

---

### Post by kpkeerthi on 2008-10-17
Post the outputs of:
```
sudo fdisk -l
```
.. and highlight which drive you want to mount automatically at boot.

```
sudo blkid
```

```
cat /etc/fstab
```

```
mount
```

This will help us provide you the right instructions.

---

### Post by rmjohnson144 on 2008-10-17
> **kpkeerthi said:**
> Post the outputs of:
```
sudo fdisk -l
```
.. and highlight which drive you want to mount automatically at boot.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b7a886a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59323   476511966   83  Linux
/dev/sda2           59324       60801    11872035    5  Extended
/dev/sda5           59324       60801    11872003+  82  Linux swap / Solaris

[B]Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a2c5b45[/B]

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdc: 1048 MB, 1048575488 bytes
255 heads, 63 sectors/track, 127 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         128     1023968    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(126, 254, 63) logical=(127, 122, 58)


```
sudo blkid
```

/dev/sda1: UUID="a0bd8bed-aca0-4b8d-b307-6482f193d5cd" TYPE="ext3" 
/dev/sdb1: UUID="4060FCC960FCC726" TYPE="ntfs" 
/dev/sdc1: SEC_TYPE="msdos" UUID="7720-5518" TYPE="vfat" 
/dev/sda5: TYPE="swap" UUID="72bfa139-d751-4336-a9fe-6f3dfe10fe21" 


```
cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a0bd8bed-aca0-4b8d-b307-6482f193d5cd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=72bfa139-d751-4336-a9fe-6f3dfe10fe21 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```
mount
```

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/mark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mark)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb1 on /media/disk-1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


> This will help us provide you the right instructions.

Thank you for such a fast response.
-=Mark=-
ps. I'm using the 1000.2GB hard drive.  It is a 1TB Seagate hard drive I just bought recently.

---

### Post by kpkeerthi on 2008-10-17
1. Create the folder where you want to mount your NTFS drive:
```
sudo mkdir /media/Windows
```

2. Edit /etc/fstab:
```
gksudo gedit /etc/fstab
```

3. Add this line to the end of the file:
```
/dev/sdb1 /media/Windows ntfs-3g defaults 0 0
```
Save and exit.

4. To test, run this command:
```
sudo mount -a
```

This should mount the partition and you should see a desktop shortcut. Post back if you get any errors.

The partition will automount next time you reboot.

---

### Post by kpkeerthi on 2008-10-17
You may also want to check out:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.ubuntu.com/ntfs-3g](https://wiki.ubuntu.com/ntfs-3g)
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by rmjohnson144 on 2008-10-17
> **kpkeerthi said:**
> 1. Create the folder where you want to mount your NTFS drive:
```
sudo mkdir /media/Windows
```

2. Edit /etc/fstab:
```
gksudo gedit /etc/fstab
```

3. Add this line to the end of the file:
```
/dev/sdb1 /media/Windows ntfs-3g defaults 0 0
```
Save and exit.

4. To test, run this command:
```
sudo mount -a
```

This should mount the partition and you should see a desktop shortcut. Post back if you get any errors.

The partition will automount next time you reboot.

hmm, I did as you said and it seemed to work, but Deluge still gave me that error (boost::filesystem::create_directory) but this time it just paused the download and now it won't resume.

The folder names seems to be the same.  I did change the windows folder name to Backup.  I'll try using Windows and see if that fixes it.

Thanks again
-=Mark=-

---

### Post by kpkeerthi on 2008-10-17
You may want to go Deluge's Preferences and reselect the folder when it will save the torrents and downloaded files. Looks like Deluge is not able to find the folder locations. Make sure you point it to /media/Backup. You don't have to change it to Windows (thats for illustration anyway; the folder name could be anything you would like).

---

### Post by rmjohnson144 on 2008-10-17
ok, Iswitched it back to Windows folder and it all comes up the same still.

For some reason it can't find the ddrive anymore at all for all the current downloads.  Is there a way to retrieve/restart the torrent files and have it force a recheck again?

Thanks for any help
-=Mark=-

---

### Post by rmjohnson144 on 2008-10-17
ok, looking at the torrent in Deluge it is pointing to /media/disk-1/Users/Mark/Downloads.  I assume it should now read /media/Windows/Users/Mark/Downloads?  Is there a simple way to change this?

-=Mark=-

---

### Post by kpkeerthi on 2008-10-17
Earlier if you have saved all the downloaded torrent files to /dev/sda1, they should still be there. 

We have just changed the partition's mount point and nothing else. So the path to the folder has changed from /media/disk-1 to /media/Windows. Open the desktop shortcut to the windows drive and you should be able to see all the folders in the windows drive.

---

### Post by kpkeerthi on 2008-10-17
> **rmjohnson144 said:**
> ok, looking at the torrent in Deluge it is pointing to /media/disk-1/Users/Mark/Downloads.  I assume it should now read /media/Windows/Users/Mark/Downloads?  Is there a simple way to change this?

-=Mark=-

You should be able to change that in Deluge's Preferences.

---

### Post by rmjohnson144 on 2008-10-17
> **kpkeerthi said:**
> You may want to go Deluge's Preferences and reselect the folder when it will save the torrents and downloaded files. Looks like Deluge is not able to find the folder locations. Make sure you point it to /media/Backup. You don't have to change it to Windows (thats for illustration anyway; the folder name could be anything you would like).

Looks like you overlapped my replies and I missed it.

Anyway, now my dilima is new ones work great (I have selected ask me for folder on every download), but old ones are stuck looking at the old folder that doesn't exist anymore.  do you know where and how to change the small torrent info file it uses to do the download?

-=Mark=-

---

### Post by kpkeerthi on 2008-10-17
This may help:
[http://forum.deluge-torrent.org/viewtopic.php?f=7&t=517](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=517)

Basically, load the .torrent file again in Deluge and when it asks you where to save the files, instead of choosing a brand new location, choose the one you already have at /media/Windows/<folder-containing-partially-downloaded-files> for the torrent.

---

### Post by rmjohnson144 on 2008-10-17
> **kpkeerthi said:**
> This may help:
[http://forum.deluge-torrent.org/viewtopic.php?f=7&t=517](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=517)

Basically, load the .torrent file again in Deluge and when it asks you where to save the files, instead of choosing a brand new location, choose the one you already have at /media/Windows/<folder-containing-partially-downloaded-files> for the torrent.

I was going to try that, but I was afraid it would wipe out the old files.

I did get it working though.  I just changed the Windows directory to disk-1 and it worked!!!!

I will have to change it back to Backup after I get these torrents finished.

Thanks a lot for the help.  Much appreciated.
-=Mark=-

---

### Post by kpkeerthi on 2008-10-17
> **rmjohnson144 said:**
> I was going to try that, but I was afraid it would wipe out the old files.

I did get it working though.  I just changed the Windows directory to disk-1 and it worked!!!!

I will have to change it back to Backup after I get these torrents finished.

Thanks a lot for the help.  Much appreciated.
-=Mark=-

Yeah.. That'd be safe. Glad you sorted it out.

---

### Post by kpkeerthi on 2008-10-17
> **rmjohnson144 said:**
> I was going to try that, but I was afraid it would wipe out the old files.



I just tested it out for you. I let a torrent complete 91%. Deleted it from the queue. Restarted Deluge. Download the .torrent file from the website I downloaded from earlier. Loaded it in deluge and it resumed from 91% (after bit of hash check).

---

### Post by rmjohnson144 on 2008-10-17
> **kpkeerthi said:**
> I just tested it out for you. I let a torrent complete 91%. Deleted it from the queue. Restarted Deluge. Download the .torrent file from the website I downloaded from earlier. Loaded it in deluge and it resumed from 91% (after bit of hash check).

Thank you, I was going to try it out after I finished this session, although I got it to recover from it this session with a forced recheck.  Not sure why, but beffore when I was losing the files and when resuming that it would restart downloading it from scratch and not continue or recheck on it's own.

a weird thing has been happening since I mounted my drive as disk-1 and that is my drives keep renumbering themselves on reboot sometimes.  It has been schaning from /dev/sdb1 to /dev/sdc1 and then switches back.  It seems to be switching with my flash drive.  my guess that its the flash drive getting assigned a drive number or something and its maybe trying to use the disk-1 naming somehow and throwing it off.  Hopefully when I swap the drive name back to backup it will go away.

anyway all is fine and thanks again for all your help.
-=Mark=-

---

