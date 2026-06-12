---
title: "External HDD Mounted Read-Only?"
date: 2008-12-17
forum: Hardware
---

### Post by shear on 2008-12-17
Hi everyone

I have a 250GB acomdata external hard drive. It worked fine for a couple weeks, but recently began mouting as read-only on my 8.04 system. It still mounts just find on the Xandros install on my eeePC.

UPDATE: I have the same issue on a fresh install of 8.10 on a brand new machine. That rules out the hardware or install on the old machine. As well, it works fine (normal read / write access) on both the eeePC version of Xandros Linux and a plain-vanilla XP install on another desktop.

Same message from /var/log/messages, same info from fdisk -l, and same behaviour when I try the two solutions listed below.
END UPDATE

Here is some info I've gleaned.

-------Output of dmesg-------

```
[25941.026744] usb 3-2: new high speed USB device using ehci_hcd and address 7
[25941.159882] usb 3-2: configuration #1 chosen from 1 choice
[25941.506044] scsi6 : SCSI emulation for USB Mass Storage devices
[25941.508483] usb-storage: device found at 7
[25941.508490] usb-storage: waiting for device to settle before scanning
[10376.128089] usb-storage: device scan complete
[10376.133651] scsi 6:0:0:0: Direct-Access     DMI      Ultra HDD        1.21 PQ: 0 ANSI: 0
[10376.144118] sd 6:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[10376.147168] sd 6:0:0:0: [sdc] Write Protect is off
[10376.147172] sd 6:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[10376.147174] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[10376.148167] sd 6:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[10376.149169] sd 6:0:0:0: [sdc] Write Protect is off
[10376.149173] sd 6:0:0:0: [sdc] Mode Sense: 0b 00 00 08
[10376.149174] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[10376.149178]  sdc: sdc1
[10376.831097] sd 6:0:0:0: [sdc] Attached SCSI disk
[10376.831136] sd 6:0:0:0: Attached scsi generic sg2 type 0
[10380.638298] FAT: Filesystem panic (dev sdc1)
[10380.638305]     fat_get_cluster: invalid cluster chain (i_pos 0)
[10380.638308]     File system has been set read-only
[10380.639234] FAT: Directory bread(block 119258) failed
[10380.639242] FAT: Directory bread(block 119259) failed
[10380.639249] FAT: Directory bread(block 119260) failed
[10380.639255] FAT: Directory bread(block 119261) failed
                      .
                      .
                      .
                      .
[10380.640267] FAT: Directory bread(block 119321) failed
[10380.710610] FAT: Filesystem panic (dev sdc1)
[10380.710617]     fat_get_cluster: invalid cluster chain (i_pos 0)
[10382.845326] FAT: Filesystem panic (dev sdc1)
[10382.845334]     fat_get_cluster: invalid cluster chain (i_pos 0)
```

-------Output of lsusb-------
```
Bus 003 Device 007: ID 0c0b:b311 Dura Micro, Inc. (Acomdata)
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 001: ID 0000:0000
```

-------Output of fsck-------
```
contenti@mjolnir >% sudo fsck -n /dev/sdc1
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Invalid disk format in boot sector.
```

I really don't know what could cause this, and I'm at a loss as to how to fix it.

---

### Post by shear on 2008-12-18
Any bites?

---

### Post by xjcannonx on 2008-12-18
What does /var/log/messages say?

---

### Post by taurus on 2008-12-18
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
df -h
```
And please do not use fsck on /dev/sdc1 unless you want to trash it.

---

### Post by shear on 2008-12-19
tail /var/log/messages

```
Dec 19 21:05:45 mjolnir kernel: [102175.881512] usb 3-2: new high speed USB device using ehci_hcd and address 8
Dec 19 21:05:45 mjolnir kernel: [102176.014455] usb 3-2: configuration #1 chosen from 1 choice
Dec 19 21:05:45 mjolnir kernel: [102176.123713] scsi7 : SCSI emulation for USB Mass Storage devices
Dec 19 21:05:50 mjolnir kernel: [255546.562100] scsi 7:0:0:0: Direct-Access     DMI      Ultra HDD        1.21 PQ: 0 ANSI: 0
Dec 19 21:05:50 mjolnir kernel: [255546.576626] sd 7:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
Dec 19 21:05:50 mjolnir kernel: [255546.577558] sd 7:0:0:0: [sdc] Write Protect is off
Dec 19 21:05:50 mjolnir kernel: [255546.579053] sd 7:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
Dec 19 21:05:50 mjolnir kernel: [255546.579930] sd 7:0:0:0: [sdc] Write Protect is off
Dec 19 21:05:51 mjolnir kernel: [255546.579952]  sdc: sdc1
Dec 19 21:05:51 mjolnir kernel: [255547.214341] sd 7:0:0:0: [sdc] Attached SCSI disk
Dec 19 21:05:51 mjolnir kernel: [255547.214418] sd 7:0:0:0: Attached scsi generic sg2 type 0

```


and

```
contenti@mjolnir >% sudo fdisk -l
[sudo] password for contenti:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbeb9beb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        6203        7296     8787555   83  Linux
/dev/sda2            6081        6202      979965   82  Linux swap / Solaris
/dev/sda3               1        6080    48837568+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
256 heads, 63 sectors/track, 30282 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Disk identifier: 0xa8c8bead

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30283   244198111    c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.

```

and also

```
 
contenti@mjolnir >% df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             8.3G  4.8G  3.2G  61% /
varrun                252M  128K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   64K  252M   1% /dev
devshm                252M   84K  252M   1% /dev/shm
lrm                   252M   39M  213M  16% /lib/modules/2.6.24-22-generic/volatile
/dev/sda3              46G   44G  187M 100% /home
/dev/sdc1             233G   44G  189G  19% /media/External

```

As for the fsk, fsck -n shouldn't actually make any changes at all, only list anything it finds wrong, no?

Thanks guys, for any help.

---

### Post by taurus on 2008-12-19
Try

```
sudo umount /dev/sdc1
sudo mount -t vfat /dev/sdc1 /media/External -o umask=000
ls -la /media
```

---

### Post by cdtech on 2008-12-19
If the device is already mounted just do a:
```
sudo mount /dev/sdc1 /media/External -o remount,rw
```

---

### Post by shear on 2008-12-21
Okay, thanks for the help so far guys, but neither of those worked.

> **cdtech said:**
> 
If the device is already mounted just do a:

```

sudo mount /dev/sdc1 /media/External -o remount,rw

```

This didn't change anything, but the command didn't fail either.


> **taurus said:**
> Try

```
sudo umount /dev/sdc1
sudo mount -t vfat /dev/sdc1 /media/External -o umask=000
ls -la /media
```

This was a little different. After the umount, I needed to create the folder /media/External manually with sudo in order for mount to work, so I did. After running the command, the locks on the icons disappeared, but no changes can be made.

```
contenti@mjolnir >% ls -la /media
total 52
drwxr-xr-x  5 root root  4096 2008-12-21 17:23 ./
drwxr-xr-x 21 root root  4096 2008-11-28 15:03 ../
lrwxrwxrwx  1 root root     6 2007-10-30 14:05 cdrom -> cdrom0/
drwxr-xr-x  2 root root  4096 2007-10-30 14:05 cdrom0/
drwxrwxrwx  9 root root 32768 1969-12-31 17:00 External/
-rw-r--r--  1 root root   442 2008-12-21 17:22 .hal-mtab
-rw-------  1 root root     0 2008-12-21 17:19 .hal-mtab-lock
drwxr-xr-x  2 root root  4096 2008-11-17 11:44 iso/

```

So which looks fine, right? So then I try,

```
contenti@mjolnir >% cd /media/External
contenti@mjolnir >% ls
CSEM2D_ComplexModel.mov*  Pictures/        SeismicLab/
Movies/                   Recycled/        setpath.m*
Music/                    screenshot.png*  System Volume Information/
contenti@mjolnir >% ls -la
ls: cannot access .Trash-1000: Input/output error
total 4388
drwxrwxrwx  9 root root   32768 1969-12-31 17:00 ./
drwxr-xr-x  5 root root    4096 2008-12-21 17:23 ../
-rwxrwxrwx  1 root root 4004944 2008-11-29 23:45 CSEM2D_ComplexModel.mov*
drwxrwxrwx 11 root root   32768 2008-11-30 08:53 Movies/
drwxrwxrwx 71 root root   32768 2008-10-15 23:54 Music/
drwxrwxrwx 11 root root   32768 2008-05-29 22:50 Pictures/
drwxrwxrwx  3 root root   32768 2008-12-01 13:56 Recycled/
-rwxrwxrwx  1 root root  193221 2008-11-29 23:41 screenshot.png*
drwxrwxrwx  5 root root   32768 2008-11-30 10:28 SeismicLab/
-rwxrwxrwx  1 root root     941 2008-11-30 10:28 setpath.m*
drwxrwxrwx  3 root root   32768 2008-11-30 10:28 System Volume Information/
d?????????  ? ?    ?          ?                ? .Trash-1000/
contenti@mjolnir >% rm CSEM2D_ComplexModel.mov
rm: cannot remove `CSEM2D_ComplexModel.mov': Read-only file system

```

Any ideas?

---

### Post by shear on 2009-01-01
Anyone?

Update: This is now not just my external HDD that is showing this behaviour, my Cowon iAudio 20 GB MP3 player is now doing the same thing. I've been using this MP3 player for years now, and just today it started behaving in the same way as the external drive.

---

### Post by shear on 2009-01-03
Another bump. :confused:

---

### Post by stefanst on 2009-01-05
I got a very similar problem.

I mounted an external USB NTFS drive. It worked fine for a day or so. Then I added some data from my XP computer. After that it mounted fine on my Ubuntu system and I could read/write for maybe half an hour. I moved some files from that drive to an internal drive, and after maybe 20 files or so, I got an error message, that the file could not be deleted and the FS is read-only. 
What the blazes?
It just changed from rw to ro.

This is truly weird...

ST

---

### Post by shear on 2009-01-09
Have you tried what was recommended to me by others in the thread? If so, and it still doesn't work, I suspect we have the same problem.

Although that's not very encouraging.

---

### Post by shear on 2009-01-22
Another update.

I have the same problem on a fresh install of 8.10 on a brand new machine.

However, I still really want to figure out how to write to the drive with Ubuntu. As I said before, works fine in the eeePC version of Xandros and a regular XP install, but not Ubuntu (even though it used to work fine).

No idea where to go from here though.

---

### Post by cdtech on 2009-01-23
Linux does come with a vfat version of fsck called dosfsck which does what chkdsk does. I would run dosfsck on the device and see what it comes up with. I think the Windows version of chkdsk is better for vfat but dosfsck works well.

It may, at some point, have been unmounted in an unclean fashion. By the output of dmesg:
```
FAT: Filesystem panic (dev sdc1)
[10380.638305]     fat_get_cluster: invalid cluster chain (i_pos 0)
[10380.638308]     File system has been set read-only

```
It looks as though it needs a chkdsk ran on the device or from Linux a dosfsck. 

Just a thought............

---

### Post by eanske on 2009-01-24
Just a quick question, have you tried to chown youruid:yourgid the /media/External directory? I had this issue and it solved it for me.

---

