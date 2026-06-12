---
title: "SATA drive via USB &quot;seen&quot; but can not access"
date: 2008-06-04
forum: Hardware
---

### Post by lsutiger on 2008-06-04
I have a SATA drive attached to the usb with an adapter. I just want to run a simple file system check on it. 

By looking at dmesg I see this:```
[ 1770.907723] usb 2-9: new high speed USB device using ehci_hcd and address 5
[ 1771.046709] usb 2-9: configuration #1 chosen from 1 choice
[ 1771.051653] scsi8 : SCSI emulation for USB Mass Storage devices
[ 1771.047405] usb-storage: device found at 5
[ 1771.047409] usb-storage: waiting for device to settle before scanning
[ 1776.040308] usb-storage: device scan complete
[ 1776.036691] scsi 8:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
[ 1776.045062] sd 8:0:0:0: [sdd] Attached SCSI disk
[ 1776.045102] sd 8:0:0:0: Attached scsi generic sg4 type 0

```
but when I do fdisk -l it is not listed.

With lsusb I get :```
Bus 002 Device 005: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 045e:00f9 Microsoft Corp. 
Bus 001 Device 002: ID 059b:0032 Iomega Corp. Zip 250 (Ver 2)
Bus 001 Device 001: ID 0000:0000  

```
It is the first one on the list there.

What am I missing?

---

### Post by Rocket2DMn on 2008-06-04
Can you please post
```
sudo fdisk -l
mount
```
We should be able to see the drive like that, then it can be mounted manually using the mount command.

---

### Post by lsutiger on 2008-06-04
fdisk -l ```
Disk /dev/sdb: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc0fac0fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1219     9791586   83  Linux
/dev/sdb2            1220        9606    67368577+  83  Linux
/dev/sdb3            9607        9730      996030   82  Linux swap / Solaris

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc5cbc5cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdc2            2551        9038    52114860    f  W95 Ext'd (LBA)
/dev/sdc5            2551        9038    52114828+   7  HPFS/NTFS

```

mount ```
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-17-generic/volatile type tmpfs (rw)
/dev/sdb2 on /home type ext3 (rw)
**none on /proc/bus/usb type usbfs (rw,devgid=120,devmode=664)** ??? This is it??
securityfs on /sys/kernel/security type securityfs (rw)
//SERVER/brian on /mnt/brian type cifs (rw,mand)
//SERVER/LogFiles on /mnt/logs type cifs (rw,mand)
//SERVER/tfalgout on /mnt/pnl type cifs (rw,mand)
//SERVER/ftp on /mnt/ftp type cifs (rw,mand)
//SERVER/Inetpub on /mnt/mail type cifs (rw,mand)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc5 on /media/disk-2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdc1 on /media/disk-1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/scd0 on /media/OFFICE2003 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)

```

I can see it if I go to System-->Places-->Computer, just can not mount it
Thanx!

---

### Post by Rocket2DMn on 2008-06-04
Which one are you trying to mount?  The 2 NTFS drives or the FAT32 drive?  mount says the NTFS drives are already mounted, so I assume you want the FAT32 drive to mount (/dev/sdc2)?
If so, try this
```
sudo mkdir /media/sdc2
sudo mount -t vfat /dev/sdc2 /media/sdc2 -o user,o=1000,umask=000
```
That will mount the drive at /media/sdc2

---

### Post by lsutiger on 2008-06-04
Thanx for the reply! 

Correct me if I am wrong.
From fdisk -l what I see is 2 hard drives, 3 partitions each.
The first is my main drive for Linux - my 80gb Western digital
The second is by old Windows disk - my 74gb raptor
The usb disk couldn't be either of those.

From the mount command I saw this:
none on /proc/bus/usb type usbfs (rw,devgid=120,devmode=664)
Could this be it?

The hard drive that is hooked up to this has been formatted NTFS.  

I'll ssh into the machine and try it and let you know what I get.

Thanx again!

---

### Post by lsutiger on 2008-06-04
Ok here it is:```
 sudo mount -t vfat /dev/sdc2 /mnt/usb -o brian,o=1000,umask=000
[sudo] password for brian: 
mount: wrong fs type, bad option, bad superblock on /dev/sdc2,
       missing codepage or helper program, or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

UPDATE:
I tried```
 sudo mount -t usbfs /proc/bus/usb /mnt/usb -o brian,o=1000,umask=000D

```

and got no error, but it is not listed with fdisk -l

---

### Post by Rocket2DMn on 2008-06-04
OK, well if it's not listed with fdisk, then something is wrong with the drive or the SATA/USB converter.  Is it possible to plug the drive directly into the board to test that the drive works OK?
If not, I think you should plug the drive with the converter into a Windows machine since NTFS is a native Windows filesystem, and linux doesn't troubleshoot it very well.  Have you tested this converter and/or disk on this machine or other machines before?

---

### Post by lsutiger on 2008-06-07
sorry it took so long to respond.

We hooked it up to an xp machine. It saw it, but we could not access it.

Popped it back into the notebook and the first thing that chowed up after POST was 'S.M.A.R.T. detects an imminent failure' yada,yada,yada

thanx!

---

### Post by Rocket2DMn on 2008-06-07
Sounds like the drive is on it's way out - time to replace it.  Good luck!

---

