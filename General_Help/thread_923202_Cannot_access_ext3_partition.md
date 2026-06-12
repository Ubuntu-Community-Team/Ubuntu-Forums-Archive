---
title: "Cannot access ext3 partition"
date: 2008-09-18
forum: General Help
---

### Post by Jeztastic on 2008-09-18
Hi, I have formatted my hard drive as per the following illustration (taken from psychocats guide).

[IMG]http://www.psychocats.net/ubuntu/images/partitioning5.png[/IMG]

FS Drive was allowing XP to access the shared ext3 drive. However, XP can no longer see the drives, and I cannot get mp3s etc to play in Ubuntu either. 

Please help, I am this close to ditching Ubuntu altogether.

---

### Post by Pro-reason on 2008-09-18
Fiddle with your FS Drive program to see if you can make it work.  You probably need to change the drive letter.  Don't dump Ubuntu because Windows is broken.

Look up how to enable the Medibuntu repository, and then use Synaptic to install *ubuntu-restricted-extras*, *non-free-codecs*, *lame* and *libdvdcss2*.  You'll then have total multimedia support.

---

### Post by Jeztastic on 2008-09-18
Maybe I didn't explain myself properly. I've had medibuntu for ages, that's not the problem. This setup was working for me for ages. Then it started to only selectively play mp3s in Windows - I had to keep re-adding them to my itunes library. Now windows will access nothing from the ext3 partition, and neither will ubuntu. I will fiddle with the drive letters, but as far as I am aware I have done nothing to change the setup.

---

### Post by mb_webguy on 2008-09-18
That doesn't sound like a problem with Ubuntu or Windows, to me.  If *both* OSes are having problems with the partition, the partition itself is probably corrupted.  Have you tried scanning the partition with fsck?

While this has nothing to do specifically with your problem, I prefer to use an NTFS partition to share data between Windows and Linux, and have a separate small (<1GB) ext3 partition for /home with symlinks to folders on the NTFS partition.  Linux's support for NTFS seems more stable than Window's support for ext3.  

Actually, it could be that Windows has been gradually eating away at your ext3 partition...

---

### Post by RobOrr on 2008-09-18
Windows gets temperamental with ext3 - think of microsoft as your jealous ex watching you move to a happy relationship that doesn't take all your effort to keep going. It creates less problems if you have the shared drive as NTFS - Ubuntu is perfectly happy reading from that, and I only had one problem which is now fixed - getting the NTFS drive to automount. consider running fsck or chkdsk or your partition though, it may be hardware problems or corruption.

---

### Post by Jeztastic on 2008-09-18
Oh god I don't like the sound of windows eating my ext3 partition! I have all my photos and mp3s on there! :( Ultimately, I really need to know how to retrieve my files so I can back them up and then reformat to NTFS.

Ubuntu completed a scan at startup recently incidently, and did not flag up any errors. What is Ubuntu's default scan? Could this be related?

---

### Post by Pro-reason on 2008-09-18
Open a terminal, enter these commands, and post the output here:

```

cat /etc/fstab
sudo fdisk -l
sudo blkid
mount

```

---

### Post by Jeztastic on 2008-09-18
OK, can access files in ubuntu now, not sure what that was about. May have been a glitch in Rhythmbox.

```
jez@jez-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=67e0949e-41f8-442a-b5ff-96cda257e34c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f5265bae-ade6-4822-9361-10a3d8372d42 /home           ext3    relatime        0       2
# /dev/sda4
UUID=4d9bd4de-3edc-4143-bfe7-82da7c7d74fb none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 

```

```
jez@jez-laptop:~$ sudo fdisk -l
[sudo] password for jez: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a51a9f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/sda2            2433       12891    84011917+   5  Extended
/dev/sda3           12892       14107     9767520   83  Linux
/dev/sda4           14108       14593     3903795   82  Linux swap / Solaris
/dev/sda5            2433       12891    84011886   83  Linux

```

```
jez@jez-laptop:~$ sudo blkid
/dev/sda1: UUID="C6A4EF3DA4EF2E9D" TYPE="ntfs" 
/dev/sda3: UUID="67e0949e-41f8-442a-b5ff-96cda257e34c" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="4d9bd4de-3edc-4143-bfe7-82da7c7d74fb" 
/dev/sda5: UUID="f5265bae-ade6-4822-9361-10a3d8372d42" TYPE="ext3"
```

```
jez@jez-laptop:~$ mount
/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda5 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/jez/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jez)
```

Still no go in XP. Will attempt to fiddle with FS Drive.

---

### Post by Jeztastic on 2008-09-18
Heheh... You guys were right, it was a problem with FS Drive, for some reason it had un-assigned drive letters to the ext3 partitions. I can only think that it did this when Ubuntu did a drive check at boot. This is obviously a real pain. Please forgive my panic! It would be nice to have suggestions on how to prevent this happening again.

---

### Post by mb_webguy on 2008-09-18
> **Jeztastic said:**
> Heheh... You guys were right, it was a problem with FS Drive, for some reason it had un-assigned drive letters to the ext3 partitions. I can only think that it did this when Ubuntu did a drive check at boot. This is obviously a real pain. Please forgive my panic! It would be nice to have suggestions on how to prevent this happening again.

Ubuntu shouldn't affect your Windows installation at all.  You don't have the Windows partition mounted, so Ubuntu has no access to it.  If there was a problem with FS Drive, it had nothing to do with Ubuntu...

---

### Post by TeXtonyx on 2008-09-18
"Oh god I don't like the sound of windows eating my ext3 partition! I have all my photos and mp3s on there!  Ultimately, I really need to know how to retrieve my files so I can back them up and then reformat to NTFS."
[http://www.sharewareconnection.com/diskinternals-linux-reader.htm](http://www.sharewareconnection.com/diskinternals-linux-reader.htm)
This is free and maybe less invasive. It doesn't do writes to Linux, but it can extract or save some particular file back to XP.  I think extracting files will meet most situations.
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) This describes how to install ntfs-3g which has presented no problems. This will read and write from Ubuntu to XP.
I've got a desktop, so I was able to install a second hard drive. I used Acronis True Image to back my Linux partition on first drive to second drive.  Since I installed to first sector of Ubuntu boot partition, I put the same bootsect.bin in boot.ini that I used to boot Ubuntu installed on the first drive, just changed the label You can use Bootpart 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
C:\ubuntu.bin="Ubuntu"
C:\bootsect.lnx="Linux"
The names have been changed to protect the innocent, but their games are all the same,
that is from the boot.ini. I would get rid of fs-drive. If the problems don't disappear, then there is a chance you have a hardware problem, drive most likely. I don't know the best backup software for Linux, but if things get grim you can find one and obtain a USB portable drive backup gadget, they can work for both size drives, laptop/desktop.
The good news is that this is something that you should do anyway.

---

