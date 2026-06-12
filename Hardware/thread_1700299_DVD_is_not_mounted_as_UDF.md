---
title: "DVD is not mounted as UDF"
date: 2011-03-04
forum: Hardware
---

### Post by Hellion DarkLord on 2011-03-04
Trying to mount an X-plane DVD install disc. The installer errors saying the DVD is not mounted as UDF and it can try to continue but fails every time.

I have tried command line mounting.


```
sudo umount /dev/dvd
mkdir -p /dev/dvd
mount -t udf /dev/dvd /mnt/dvd

and also 

sudo umount /dev/scd0
sudo mkdir -p /media/dvd
sudo mount -t udf /dev/scd0 /media/dvd

as well as

sudo umount /dev/scd0
sudo mkdir -p /mnt/dvd
sudo mount -t udf /dev/scd0 /mnt/dvd


```

this is the error that is shown every time.

```
LinuxBox:~$ sudo mount -t udf /dev/dvd /mnt/dvd
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

syslog =

```
@LinuxBox:~$ dmesg |tail
[ 3054.735174] 2:2:1: endpoint lacks sample rate attribute bit, cannot set.
[ 3070.654784] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 3070.684756] ISO 9660 Extensions: RRIP_1991A
[ 3208.390402] 2:2:1: endpoint lacks sample rate attribute bit, cannot set.
[ 3208.400386] 2:2:1: endpoint lacks sample rate attribute bit, cannot set.
[ 3213.646711] 2:2:1: endpoint lacks sample rate attribute bit, cannot set.
[ 3213.662062] 2:2:1: endpoint lacks sample rate attribute bit, cannot set.
[ 3311.571863] lo: Disabled Privacy Extensions
[ 3583.809028] UDF-fs: No VRS found
[ 3583.809036] UDF-fs: No partition found (1)

```

Fstab =

```
LinuxBox:~$ cat /etc/fstab
UUID=b0b09aa2-508c-40f3-a60b-2b989ceefca6 / ext4 defaults 0 1
UUID=cb683b77-260b-4a2e-915b-912484cff4da swap swap sw 0 0

```

Mtab=
```
LinuxBox:~$ cat /etc/mtab
/dev/sda2 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdb1 /media/7940-F47C vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush 0 0
/dev/sdc1 /media/3B63-5D21 vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush 0 0
gvfs-fuse-daemon /home/***********/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=gabriel 0 0
{*=hidden character edited after pastee}

```


Lshw =

 ```
*-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-H653N
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 0609
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom

```

Thanks for any help!

---

