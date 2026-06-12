---
title: "Unable to access hard drive after first formatting"
date: 2010-08-27
forum: Hardware
---

### Post by jheronimus on 2010-08-27
Hi,

I just bought an external hard drive Samsung HM500JI and (without thinking much, I admit) formatted it to ext4 right after first plugging-in (i right-clicked on desktop drive icon and selected format to ext4). I did not even try first to copy my files on the drive (naive isn't it?). Formatting seemed to process fine.

Since then I still can see the drive, but can not do any operation on it. Gparted do not recognize the file system type, and do not manage to format or partition the disk in any sort of file system type (error is mke2fs 1.41.11 (14-Mar-2006)/dev/sdb1 is mounted; will not make a filesystem here!). Right-clicking properties from desktop icon indicates that file system is ext3/ext4, with 23G used which are not seen by Gparted). Finally, disk utility indicates that file system type is ext4, with partition type HPFS/NTFS.

I hope there is a way out of that quagmire! Any help would be greatly appreciated!

J

---

### Post by arrange on 2010-08-27
Open up GParted, umount the partition in it (so that you don't see the keys icon next to the */dev/sdb1* partition), and then try formatting it again (in GParted). Look out for any error messages while formatting.

---

### Post by jheronimus on 2010-08-28
Thanks for the feed back, arrange. The Unmount field is not active for any partition in the drive. It also not access the drive from nautilus, the drive seems not mounted (mount point is not mounted in disk utility).

---

### Post by arrange on 2010-08-28
Could you please unplug the drive, then plug it back in, wait for a few seconds so that the system is given a chance to recognize the device, and then provide the output of these command from the [Terminal](https://help.ubuntu.com/community/GnomeTerminal)?```
mount
sudo fdisk -l
sudo parted -l
dmesg | tail -20
```

---

### Post by jheronimus on 2010-08-28
edeline@edeline-laptop:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda7 on /home type ext3 (rw,relatime)
/dev/sda6 on /usr type ext3 (rw,relatime)
/dev/sda5 on /var type ext3 (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/edeline/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=edeline)
/dev/sdb1 on /media/10288f03-8944-496c-a4c1-95b44950616c type ext2 (rw,nosuid,nodev,uhelper=udisks)
edeline@edeline-laptop:~$ sudo fdisk -l
[sudo] password for edeline: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         491     3943926   82  Linux swap / Solaris
/dev/sda2   *         492        1707     9767520   83  Linux
/dev/sda3            1708       19457   142576875    5  Extended
/dev/sda5            1708        3531    14651248+  83  Linux
/dev/sda6            3532        9610    48829536   83  Linux
/dev/sda7            9611       19457    79095996   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ceec3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux
edeline@edeline-laptop:~$ sudo parted -l
Model: ATA ST9160411ASG (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  4039MB  4039MB  primary   linux-swap(v1)
 2      4039MB  14.0GB  10.0GB  primary   ext3            boot
 3      14.0GB  160GB   146GB   extended
 5      14.0GB  29.0GB  15.0GB  logical   ext3
 6      29.0GB  79.0GB  50.0GB  logical   ext3
 7      79.0GB  160GB   81.0GB  logical   ext3


Model: SAMSUNG HM500JI (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ext2


edeline@edeline-laptop:~$ dmesg | tail -20
[   80.407093] EXT4-fs (sdb1): bad geometry: block count 122096000 exceeds size of device (10239421 blocks)
[ 2636.019548] dell-wmi: Unknown key ffd0 pressed
[ 2672.548471] dell-wmi: Unknown key ffd1 pressed
[ 2698.379098] usb 2-3: USB disconnect, address 3
[ 2723.616309] usb 2-3: new high speed USB device using ehci_hcd and address 4
[ 2723.750304] usb 2-3: configuration #1 chosen from 1 choice
[ 2723.751384] scsi7 : SCSI emulation for USB Mass Storage devices
[ 2723.751597] usb-storage: device found at 4
[ 2723.751603] usb-storage: waiting for device to settle before scanning
[ 2728.748569] usb-storage: device scan complete
[ 2728.749307] scsi 7:0:0:0: Direct-Access     SAMSUNG  HM500JI               PQ: 0 ANSI: 0
[ 2728.750645] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 2728.760853] sd 7:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 2728.761561] sd 7:0:0:0: [sdb] Write Protect is off
[ 2728.761569] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 2728.761575] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 2728.767794] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 2728.767806]  sdb: sdb1
[ 2728.793056] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 2728.793067] sd 7:0:0:0: [sdb] Attached SCSI disk
edeline@edeline-laptop:~$

---

### Post by arrange on 2010-08-28
Do you see the icon of *sdb1* partition on your desktop? Can you right-click on it and select *Unmount*?

---

### Post by jheronimus on 2010-08-28
I can see the drive icon on the desktop, identified as 500 GB Filesystem (not as /dev/sdb1). Right-clicking do not propose *Unmount* despite that after unplugging-replugging the drive has now mount point: /media/10288f03-8944-496c-a4c1-95b44950616c

In Nautilus the drive contains one single folder called "lost+found" (500 GB, ie the entire drive), on which I can not perform any action (i have no permissions on it).

---

### Post by arrange on 2010-08-28
OK, then try unmounting manually```
sudo umount /dev/sdb1
```If successfull, format the drive again using GParted. If you see any error messages, paste them here.

---

### Post by jheronimus on 2010-08-28
All went OK, I managed to format the disc (although 7.5 GB remain "Used" on it), the disc now appears as a folder in root (/lost+found) which content can still not be displayed (not enough permissions). The disc is also still seen as /dev/sdb1 by Gnome disk utility.

---

### Post by jheronimus on 2010-08-28
After opening nautilus in gksudo I can access the drive and do some operations on it (copying, deleting...etc), but I can copy only up to 7.5GB. This correspond to the space seen as *Used* in Gparted.

---

### Post by arrange on 2010-08-29
?Could you connect the drive, and post again the output of```
mount
df -Th

```

---

### Post by jheronimus on 2010-09-13
Hi Arrange,

sorry for responding so lately, I've had health trouble. Actually the problem seems solved since now I can access and use the whole hard drive. In the interval (before you answered 2 weeks ago) I have formatted the drive with Gparted as sudo, which might have solved the problem (by the way, the strange 500GB lost+found folder is still there). Thanks for your help!

J

---

