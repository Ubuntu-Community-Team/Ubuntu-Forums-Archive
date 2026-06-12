---
title: "Norton GoBack + 9.04 = trashed system"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by Brad H on 2009-10-20
I just tried installing 9.04 on an old computer running 98SE.  I used all the defaults including a dual boot.  When it was nearly finished it reported an error reading the disc but seemed to continue and then opened with the Ubuntu desktop.  I noted however that the "Install" icon was still there.  I ejected the CD and shut down hoping all would be well.  But all is far from well as when the HD boots Norton GoBack is reporting an error and says it will try to remove itself and then it crashes - reboots and repeats.

I cannot get into either Windows or Ubuntu (except if I boot via CD).

BTW the HD is a SCSI device

Now what do I do?

---

### Post by xxterry1xx on 2009-10-20
> **Brad H said:**
> I just tried installing 9.04 on an old computer running 98SE.  I used all the defaults including a dual boot.  When it was nearly finished it reported an error reading the disc but seemed to continue and then opened with the Ubuntu desktop.  I noted however that the "Install" icon was still there.  I ejected the CD and shut down hoping all would be well.  But all is far from well as when the HD boots Norton GoBack is reporting an error and says it will try to remove itself and then it crashes - reboots and repeats.

I cannot get into either Windows or Ubuntu (except if I boot via CD).

BTW the HD is a SCSI device

Now what do I do?its a norton goback error i think try uninstalling it and that btw i been a long time windows user 7 years tweaking,coding mostly everything you can do in windows but if i where you i would trash that windows 98 cd and use ubuntu lol

but whats the error anyways? can you boot into windows 98 on and get to the desktop and remove a program?

---

### Post by Brad H on 2009-10-20
No I cannot log in - I get a dialog on boot that says that GoBack cannot recover becasue another program has changed the partition and/or boot record.  I click OK (only choice) and get a second dialog saying it will try to remove itself the I get a DOS screen with an error gb_eng2(7655) .. press any key.  When I do the process repeats (endless loop).  I downloaded a CD  image from Norton that is supposed to fix it but it does exactly the same thing.

I can still boot 9.04 from the CD and I can see the partitions including the new ext3.  I can also see that my files are intact.  It just will not boot from the HD!

---

### Post by tommcd on 2009-10-21
Try to restore the Windows 98SE MBR (master boot record). If you have a Windows 98SE boot disc or the Windows 98SE install CD you should be able to boot with that and run:
```
fdisk /mbr
```
Then you should (hopefully) be able to boot into Windows. Then uninstall the Norton Go Back. 
You will then need to boot from the Ubuntu live CD and reinstall grub to the MBR so you can boot both Ubuntu and Windows. See this to restore grub to the MBR:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)

---

### Post by Brad H on 2009-10-21
I used the Win 98 install CD and booted to DOS then used FDISK /MBR with minimal success - it no longer hangs on GoBack - but it cannot find drive C so it will not boot windows or even DOS.

---

### Post by presence1960 on 2009-10-21
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Brad H on 2009-10-21
The system is not on the net but I will do what you asked by moving the files back and forth with a flash drive.  It is currently using U9.04 running from CD to copy all of my data files onto a USB HD.  This will probably take another hour and then I will do my assignment.  Thanks for the help!!  This may yet become a Ubuntu only machine as I am downloading 9.1 as we speak.  Still I would like to have the option at least for now.

---

### Post by Brad H on 2009-10-21
OK - keep in mind that I am a newbie with Ubuntu....

At the terminal prompt **ubuntu@ubuntu:~$** I entered the sudo command exactly as you gave it.  I got a "file not found" error.  I tried it again using the actual file name (...032 instead of ...*).  same error.

I double clicked the file on the desktop and from the pop-up I chose "run from terminal".  It appeared to run (a terminal window popped up for an instant) but no results file - I tried it again - same result.

So what do you think I did wrong on the typed terminal entry?

What next?

---

### Post by xxterry1xx on 2009-10-21
> **Brad H said:**
> No I cannot log in - I get a dialog on boot that says that GoBack cannot recover becasue another program has changed the partition and/or boot record.  I click OK (only choice) and get a second dialog saying it will try to remove itself the I get a DOS screen with an error gb_eng2(7655) .. press any key.  When I do the process repeats (endless loop).  I downloaded a CD  image from Norton that is supposed to fix it but it does exactly the same thing.

I can still boot 9.04 from the CD and I can see the partitions including the new ext3.  I can also see that my files are intact.  It just will not boot from the HD!ahhh when your going to install norton goback install it when you have windows 98 and ubuntu installed because norton goback is being retarded and wont idk add ubuntu to its list and wont let you log on

---

### Post by Brad H on 2009-10-21
OK - so maybe NOT exactly <blush>  I discovered that Ubuntu is case dependent!  when I capitalized Desktop it worked fine!  I have ordered a book .. Ubuntu Bible.

So here's the file...
```

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.9 GB, 40981118976 bytes
255 heads, 63 sectors/track, 4982 cylinders, total 80041248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    74,798,639    74,798,577  44 Unknown
/dev/sdb2          74,798,640    80,035,829     5,237,190   5 Extended
/dev/sdb5          74,798,703    79,682,399     4,883,697  83 Linux
/dev/sdb6          79,682,463    80,035,829       353,367  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 131 MB, 131072000 bytes
16 heads, 32 sectors/track, 500 cylinders, total 256000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             47       255,999       255,953   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sdb1: LABEL="BIG40" UUID="07D0-0411" TYPE="vfat" 
/dev/sdb5: UUID="dad94e70-8ef5-49cb-adca-887b0538d0fc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="3fdf1291-173c-4c65-a87a-9899aa8cea61" TYPE="swap" 
/dev/sdc1: SEC_TYPE="msdos" UUID="0000-0000" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/BIG40 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=dad94e70-8ef5-49cb-adca-887b0538d0fc /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=3fdf1291-173c-4c65-a87a-9899aa8cea61 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=======Devices which don't seem to have a corresponding hard drive==============

sda 
```

---

