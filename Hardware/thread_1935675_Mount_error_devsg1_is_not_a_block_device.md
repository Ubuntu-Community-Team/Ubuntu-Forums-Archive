---
title: "Mount error /dev/sg1 is not a block device"
date: 2012-03-04
forum: Hardware
---

### Post by ShiftyDrunk on 2012-03-04
Hi,

I am trying to mount my dvd / blu-ray drive and i am using 
sudo mount -t iso9660 /dev/sg1 /cdrom or 
sudo mount -t auto /dev/sg1 /cdrom

and i get the error - mount: /dev/sg1 is not a block device


when i use wodim --devices i get 

wodim: Overview of accessible drives (1 found) :
-----------------------------------------------------------------
 0  dev='/dev/sg1'	rwrwrw : 'HL-DT-ST' 'DVDRWBD CA10N'
-----------------------------------------------------------------

when i try mount I get -



/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/zach/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zach)


I am trying to get this to work so i can get office 2007 installed through playonlinux witch is unable to find the drive as well. i tried using wineconfig to auto-detect it and it found nothing. Please help me out.
Thank you,
Zach :))

---

