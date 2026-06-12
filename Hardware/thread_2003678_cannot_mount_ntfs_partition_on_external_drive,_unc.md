---
title: "cannot mount ntfs partition on external drive, unclean shutdown"
date: 2012-06-14
forum: Hardware
---

### Post by jskinner1724 on 2012-06-14
I have an external hard drive that I put into a usb dock. The Windows machine it came out of crashed. I am simply trying to get the data from it, but when I try to mount the disk utility just keeps trying to mount and all other routes give me a "...device is busy" error. Ubuntu will not mount the disk. I tried to attach it to a Windows machine but it sees the drive as raw and will not run chkdsk. Please help!!!

---

### Post by irv on 2012-06-14
> **jskinner1724 said:**
> I have an external hard drive that I put into a usb dock. The Windows machine it came out of crashed. I am simply trying to get the data from it, but when I try to mount the disk utility just keeps trying to mount and all other routes give me a "...device is busy" error. Ubuntu will not mount the disk. I tried to attach it to a Windows machine but it sees the drive as raw and will not run chkdsk. Please help!!!

Do you have gparted installed? If not, just run this command:
```
sudo apt-get install gparted
```
enter you password.
Plug in the drive then just type 
```
sudo gparted
```
Switch to the USB drive and see if you can mount and unmount it.
Then Unmount and run check on the drive.
[ATTACH]219697[/ATTACH]

---

### Post by jskinner1724 on 2012-06-14
gparted just hangs continually. it keeps scanning for the drive. If I turn the usb dock off, gparted will finally load (sans drive in question of course)

Here are the results of some of the commands I have tried:

```
jskinner1724@jskinner1724-laptop:~$ sudo mount
[sudo] password for jskinner1724: 
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
vmware-vmblock on /run/vmblock-fuse type fuse.vmware-vmblock (rw,nosuid,nodev,default_permissions,allow_other)
gvfs-fuse-daemon on /home/jskinner1724/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jskinner1724)
```

and I tried to list usb 
```
jskinner1724@jskinner1724-laptop:~$ sudo lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 13fd:1840 Initio Corporation Shintaro SH23SDOCK Hard Drive Docker [INIC-1608L]
Bus 002 Device 002: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
```

... and when I tried mount /dev/sdb3 /mnt it took forever and finally told me the device was temporarily unavailable. So I tried to force it to mount with mount -o force /dev/sdb3 /media/duffy (which was the temp mount point I made and chown'd to 777 for this) and it still failed. Didn't even think that was possible, but this drive seems pretty resilient.

---

### Post by irv on 2012-06-14
> **jskinner1724 said:**
> gparted just hangs continually. it keeps scanning for the drive. If I turn the usb dock off, gparted will finally load (sans drive in question of course)

It sounds like the drive when south. And if you can't read it in other machines it sound like it is bad.

---

### Post by ajgreeny on 2012-06-14
If you know someone with a windows machine just plug it in to that, then make sure you remove safely from windows.  That will do it and is the safest way.  You can even run chkdsk on it if needed, though I have forgotten how.

If no windows machine is available you may have to resort to force manual mounting in terminal.
```
sudo mount -t ntfs-3g /dev/sdb1 /home/*user*/sdb1 -o force
```assuming the drive's partition is sdb1 and you have already made the mountpoint folder in your home

---

### Post by jskinner1724 on 2012-06-14
The weird thing is, I tried to open it with testdisk, got to open (miraculously), and could see some of the files. The drive cannot be toasted THAT bad. Besides, the SMART data is still reporting on the drive itself. There are two other partitions (ntfs and fat16) that are viewable and mountable as well. So it isn't the DRIVE, just THIS partition.

I tried to run hdparm to look at the drive information but it just hangs as well as gpart, mount, fdisk -l and everything else I have tried so far.

---

### Post by jskinner1724 on 2012-06-14
> **ajgreeny said:**
> If you know someone with a windows machine just plug it in to that, then make sure you remove safely from windows.  That will do it and is the safest way.  You can even run chkdsk on it if needed...

first post of mine:
Windows sees it as raw and will not run chkdsk

---

### Post by ajgreeny on 2012-06-14
> **jskinner1724 said:**
> first post of mine:
Windows sees it as raw and will not run chkdsk
Whoops, sorry about that; I must read more carefully in future.

Have you attempted the force mount yet?

---

### Post by jskinner1724 on 2012-06-14
> **ajgreeny said:**
> Have you attempted the force mount yet?

Yep, here is results:
```
jskinner1724@jskinner1724-laptop:~$ sudo mount -t ntfs-3g /dev/sdb3 /media/duffy/sdb3 -o force
Failed to write lock '/dev/sdb3': Resource temporarily unavailable
Error opening '/dev/sdb3': Resource temporarily unavailable
Failed to mount '/dev/sdb3': Resource temporarily unavailable
```

---

