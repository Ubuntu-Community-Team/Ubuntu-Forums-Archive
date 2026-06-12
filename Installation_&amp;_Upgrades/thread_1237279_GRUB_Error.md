---
title: "GRUB Error"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by fast-Eddie on 2009-08-11
Hi Folks,

I'm using 64bit Jaunty and have a possible GRUB problem as my PC is no longer booting. When issuing the command after booting from a LIVE CD:

grub-install --root-directory=/media/root /dev/sda1

I get the following:

grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
Installing GRUB to /dev/sda1 as (hd0,0)...
Installation finished. No error reported.
This is the contents of the device map /media/root/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

Note the error in the first 2 lines of output. Is this normal when booting from a LIVE CD?? I have both my root and /boot filesystems mounted.

Any ideas??

---

### Post by fast-Eddie on 2009-08-11
Okay, I really need help with fixing GRUB. I followed all the instructions here:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

to help me with reinstalling GRUB however when I reboot without my LIVE CD, my PC hangs at the point where GRUB usually loads.

I am by no means a Linux expert and am still relatively new so...
Help Please!!

---

### Post by madhavhmk on 2009-08-11
Please post output of fdisk -l

---

### Post by madhavhmk on 2009-08-11
I dont know...you can access net from live cd right..?

run sudo fdisk -l from livecd

---

### Post by fast-Eddie on 2009-08-11
Output of fdisk -l:

root@ubuntu:~# fdisk -l

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1221     9807651   83  Linux
/dev/sda2            1222       18241   136713150   83  Linux

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1221     9807651   82  Linux swap / Solaris
/dev/sdb2            1222       18241   136713150   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x956b956b

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   83  Linux
root@ubuntu:~#

---

### Post by fast-Eddie on 2009-08-11
Yes, I can access the internet from the LiveCD.

---

### Post by merlinus on 2009-08-11
Did you try this:

Boot from live cd, open a terminal and enter these commands one at a time:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use hd and numbers from the previous command
setup (hd0)  #use hd and its number from the previous command
quit 
```

Remove the cd and restart.

---

### Post by fast-Eddie on 2009-08-11
Hi Merlin,

Yes, I did try that and it didn't resolve the issue. 

Any other suggestions??

---

### Post by fast-Eddie on 2009-08-12
anyone?? any ideas??

---

### Post by fast-Eddie on 2009-08-13
i have also tried the following with no luck:

mkdir /media/root
mount /dev/sdd1 /media/root
mount /dev/sda1 /media/root/boot
grub-install --root-directory=/media/root /dev/sda1

This completes without error but does not work. When I reboot, at the point when Grub usually loads, the pc just stops.

Any ideas anyone??

---

### Post by presence1960 on 2009-08-13
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by fast-Eddie on 2009-08-14
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Testdisk is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Testdisk is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90909090

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    19,615,364    19,615,302  83 Linux
/dev/sda2          19,615,365   293,041,664   273,426,300  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90909090

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    19,615,364    19,615,302  82 Linux swap / Solaris
/dev/sdb2          19,615,365   293,041,664   273,426,300  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x956b956b

Partition  Boot         Start           End          Size  Id System



Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90909090

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,768,064   976,768,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="102d2853-11a4-4a6c-9dc2-cdcbb83a4b1a" TYPE="ext4" 
/dev/sda2: UUID="dcff81a0-72d1-4425-91c8-fe1f26965342" TYPE="ext4" 
/dev/sdb1: TYPE="swap" UUID="95862401-2170-433c-87ea-7abc5b6cffc4" 
/dev/sdb2: UUID="f77a137e-d657-4c91-bf3e-0f7df795e8f5" TYPE="ext4" 
/dev/sdd1: UUID="47e3ff60-6be3-4434-9515-6dea10964361" TYPE="ext4" 

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


=============================== sdd1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd1 during installation
UUID=47e3ff60-6be3-4434-9515-6dea10964361 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=c887f92e-ad05-4f36-8fce-fb140793086e /boot           ext4    relatime        0       2
# /home was on /dev/sda2 during installation
UUID=dcff81a0-72d1-4425-91c8-fe1f26965342 /home           ext4    relatime        0       2
# /tmp was on /dev/sdb2 during installation
UUID=f77a137e-d657-4c91-bf3e-0f7df795e8f5 /tmp            ext4    relatime        0       2
# swap was on /dev/sdb1 during installation
UUID=95862401-2170-433c-87ea-7abc5b6cffc4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by presence1960 on 2009-08-14
Your install is all fouled up. sda1  & sda2 are ext 4 but no boot files/directories. That is a problem because GRUB looks to sda1 when you boot.
sdd1 has /etc/fstab and is marked as your Ubuntu installation but it has no menu.lst
where are your sdc partitions? They are missing from the top section Boot Info Summary.
You have no menu.lst so your GRUB is never going to work. Also your GRUB is pointing to the wrong partition to boot Ubuntu.

I would reinstall Ubuntu. When you get to the Ready to install window click the advanced tab and choose the drive that boots first in BIOS to install GRUB onto the MBR of that drive. If sda boots first choose sda, if sdd boots first choose sdd. Do not choose sda1 or sdd1 as this will put GRUB on the partition and not MBR. You want GRUB on MBR so it will take over when you boot.

---

### Post by presence1960 on 2009-08-14
here is a shot of the Ready to install window

---

### Post by fast-Eddie on 2009-08-14
Thanks for the help and suggestions. Right before you posted, I actually (finally!!) managed to fix my system myself. 

Previously, at the point where Grub loads nothing used to happen - no text, no error, nothing. While surfing the net I found out that pressing Esc should show the Grub menu if it doesn't appear so I tried this after rebooting and it did display some text; just the usual 'Grub loading, please wait' however it then displayed an Error 15. I then rebooted the system using the LiveCD and looked up that error and realised that the files Grub was looking for didn't exist. To prove this, I mounted the root drive (sdd1) and searched for the menu.lst file and as you mentioned, it did not exist. I rebooted again, went into BIOS first and check the HDD boot priority and it was set to boot drive sdd1 first so I corrected it then re-installed Jaunty. During the setup, I configured the partitioning and when I got to the 'Ready to Install' window, I just left the default setting and proceeded with the install. Low and behold, after it was complete and I rebooted, the system came up on its own after a week in dire straights!!

---

### Post by fast-Eddie on 2009-08-14
presence1960, thanks for your help!! I really appreciate it.

---

### Post by fast-Eddie on 2009-08-14
Oh, and the reason I don't have any partitions on sdc is because I am planning to remove the drive and put it into another system.

---

### Post by presence1960 on 2009-08-14
Great fast-Eddie! Enjoy Ubuntu. Glad you got it working.

---

### Post by Eskobar on 2009-09-29
> **presence1960 said:**
> Your install is all fouled up. sda1  & sda2 are ext 4 but no boot files/directories. That is a problem because GRUB looks to sda1 when you boot.
sdd1 has /etc/fstab and is marked as your Ubuntu installation but it has no menu.lst
where are your sdc partitions? They are missing from the top section Boot Info Summary.
You have no menu.lst so your GRUB is never going to work. Also your GRUB is pointing to the wrong partition to boot Ubuntu.

I would reinstall Ubuntu. When you get to the Ready to install window click the advanced tab and choose the drive that boots first in BIOS to install GRUB onto the MBR of that drive. If sda boots first choose sda, if sdd boots first choose sdd. Do not choose sda1 or sdd1 as this will put GRUB on the partition and not MBR. You want GRUB on MBR so it will take over when you boot.



Brilliant!!! Thanks Bro!!! I was setting my MBR on the partition as you mentioned above and was searching for maybe an hour and I found your post!!! Thanks a million man......... AHHHHHH THE POWER OF SEARCH!!!!   This thread should be marked SOLVED

---

