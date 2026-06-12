---
title: "Issues With Mass Storage device"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by killaray on 2007-08-22
well i just got me a Moto Z6 and im having issues connecting to my PC in mass storage mode

the device shows up on dmesg but i dont see it connected as a drive... anyone know what could be the problem... heres the dmesg

```
[    7.696309] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    7.886735] usb 3-2: configuration #1 chosen from 1 choice
[    8.604152] usb 2-2.1: new full speed USB device using uhci_hcd and address 4
[    8.740936] usb 2-2.1: configuration #1 chosen from 1 choice
[    8.753821] usbcore: registered new interface driver libusual
[    9.419258] Initializing USB Mass Storage driver...
[    9.419363] scsi2 : SCSI emulation for USB Mass Storage devices
```

---

### Post by killaray on 2007-08-22
anyone?

---

### Post by merlinus on 2007-08-22
You might post results of:

```

sudo fdisk -l
mount

```

-merlin

---

### Post by killaray on 2007-08-23
FDisk
```
Disk /dev/hda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6996    56195338+  83  Linux
/dev/hda2            6997        7299     2433847+   5  Extended
/dev/hda5            6997        7299     2433816   82  Linux swap / Solaris

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24792   199141708+   7  HPFS/NTFS

```

Mount
```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/hdb1 on /media/hdb1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
fusesmb on /home/killaray/Network type fuse (rw,nosuid,nodev,allow_other,max_read=32768)

```

---

### Post by merlinus on 2007-08-23
Looks like it is mounted on /home/killaray/Network, but not listed as a partition.

Can you see it there in Nautilus?

Perhaps ubuntu cannot understand the filsystem it is using?

-merlin

---

### Post by killaray on 2007-08-23
i dont think thats it cause even when i remove the phone that network entry remains... i also cant see it threw nautilus and the filesystem its using is fat i reformated it yesterday

---

### Post by killaray on 2007-09-25
can anyone help me with this issue? i think im getting closer.. ive tried to manually mount the device and i get
```
sudo mount /dev/sda Z6
mount: No medium found

```
if a do a **lsscsi** i get 
```
lsscsi
[2:0:0:0]    disk    Generic  USB SD Reader    1.00  /dev/sda
[4:0:0:0]    disk    Motorola MSnc.                  -       
[4:0:0:1]    disk    Motorola MSnc.  
```
so i know its being recognized also if i do **scsiinfo -l** it comes up as 
```
scsiinfo -l
/dev/sda

```
which im guessin is where the device is mounted but still doesnt work.. any help?

---

### Post by killaray on 2007-09-25
ok just removed my SD card reader, it seems like that was the device that was mounted.. so the phone isnt recognized

---

### Post by killaray on 2007-09-25
tried a **scsiadd -a** and i got
```
sudo scsiadd -a disk
Attached devices:
Host: scsi4 Channel: 00 Id: 00 Lun: 00
  Vendor: Motorola Model: MSnc.            Rev:     
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi4 Channel: 00 Id: 00 Lun: 01
  Vendor: Motorola Model: MSnc.            Rev:     
  Type:   Direct-Access                    ANSI SCSI revision: 02

```

---

### Post by killaray on 2007-09-26
according to another member from another forum.. this post has wut i need to get this to work but this is to technical for me

[http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg19221.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg19221.html)

that drivers/scsi directory is that within the source of the kernel?

---

