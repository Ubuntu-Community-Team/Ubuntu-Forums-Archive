---
title: "HDDs &quot;vanished&quot;?"
date: 2005-03-19
forum: Hardware &amp; Laptops
---

### Post by kb00heda on 2005-03-19
Hi,

I recently installed Ubuntu this morning. My machine has 3 HDDs, one being a Seagate SATA drive, where I placed Ubuntu. The other two discs, two Western Digital IDEs, showed up in the Partitioner during the install, but now, when the system is up and running, I can't seem to find them. Only the SATA disc is available.

I tried to execute "df", and then I had a look at the /etc/fstab file, but still no sign of them. Does anyone know how for me to locate the "missing" HDDS and mount them?

Regards,
David

---

### Post by alastair on 2005-03-19
System logs are a good place to start - look for boot messages regarding IDE/ATA etc. :

/var/log/syslog

---

### Post by kb00heda on 2005-03-19
OK... they do seem to exist (as "hda" and "hdb"):

```
Mar 19 21:45:58 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Mar 19 21:45:58 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Mar 19 21:45:58 localhost kernel: Probing IDE interface ide0...
Mar 19 21:45:58 localhost kernel: hda: WDC WD1200JB-00DUA3, ATA DISK drive
Mar 19 21:45:58 localhost kernel: hdb: WDC WD1200JB-00DUA3, ATA DISK drive
Mar 19 21:45:58 localhost kernel: Probing IDE interface ide1...
Mar 19 21:45:58 localhost kernel: hdc: _NEC DVD_RW ND-2500A, ATAPI CD/DVD-ROM drive
Mar 19 21:45:58 localhost kernel: Probing IDE interface ide2...
Mar 19 21:45:58 localhost kernel: Probing IDE interface ide3...
Mar 19 21:45:58 localhost kernel: Probing IDE interface ide4...
Mar 19 21:45:58 localhost kernel: Probing IDE interface ide5...
Mar 19 21:45:58 localhost kernel: ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Mar 19 21:45:58 localhost kernel: ide1 at 0x170-0x177,0x376 on irq 15
Mar 19 21:45:58 localhost kernel: hda: max request size: 1024KiB
Mar 19 21:45:58 localhost kernel: hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63
Mar 19 21:45:58 localhost kernel: hda: cache flushes supported
Mar 19 21:45:58 localhost kernel:  /dev/ide/host0/bus0/target0/lun0: p1
Mar 19 21:45:58 localhost kernel: hdb: max request size: 1024KiB
Mar 19 21:45:58 localhost kernel: hdb: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63
Mar 19 21:45:58 localhost kernel: hdb: cache flushes supported
Mar 19 21:45:58 localhost kernel:  /dev/ide/host0/bus0/target1/lun0: p1
``` 

If I try to mount either of them I only get:

```
kb00heda@ubuntu:~$ sudo mount /dev/hda /mydisk1
Password:
mount: mount point /mydisk1 does not exist
```

Is it possible for me to mount them?

During the install I didn't pay attention to whether or not I created mount points for those discs. I only marked the SATA drive to be erased and for new partitions to be created on it. My fear is the other discs got formatted by default, and then, on top of everything, they didn't get mounted?  [-o< 

Hopefully someone are able to calm me down...!

/David

---

### Post by kb00heda on 2005-03-19
Also, if I run "sudo fdisk -l" I get

```
kb00heda@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9399    75497436   83  Linux
/dev/sda2            9400        9729     2650725    5  Extended
/dev/sda5            9400        9729     2650693+  82  Linux swap / Solaris

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       14592   117210208+  83  Linux

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14592   117210208+  83  Linux
``` 

as the partition table. Then "df -T -h" renders

```
kb00heda@ubuntu:~$ df -T -h
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3     71G  7.3G   61G  11% /
tmpfs        tmpfs    506M     0  506M   0% /dev/shm
/dev       unknown     71G  7.3G   61G  11% /.dev
none         tmpfs    5.0M  2.8M  2.3M  55% /dev
``` 

and finally "mount" gives

```
kb00heda@ubuntu:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
``` 

Hopefully that can help someone to help me! :)

Regards,
David

---

### Post by Buffalo Soldier on 2005-03-19
[QUOTE=kb00heda]If I try to mount either of them I only get:

```
kb00heda@ubuntu:~$ sudo mount /dev/hda /mydisk1
Password:
mount: mount point /mydisk1 does not exist
```

Is it possible for me to mount them?[/QUOTE]Did you create a */mydisk1* directory first?```
kb00heda@ubuntu:~$ sudo mkdir /mydisk1
Password:
kb00heda@ubuntu:~$ sudo mount /dev/hda1 /mydisk1

```

EDIT: Thanks alastair for pointing out /dev/hda**1**.

---

### Post by munki on 2005-03-20
> 
kb00heda@ubuntu:~$ sudo mount /dev/hda /mydisk1
Password:
mount: mount point /mydisk1 does not exist


It seems like you are trying to mount the drive(s) on a directory that doesn't exist,
dit you create the /mydisk1 first? else you can't :)

sudo mkdir /mydisk1
sudo mount /dev/hda /mydisk1

---

### Post by alastair on 2005-03-20
Mount the partitions - not the device.

The WHOLE disk is /dev/hda.
The PARTITION is /dev/hda1.

So :

mount /dev/hda1 /mydisk1

for instance.

---

### Post by kb00heda on 2005-03-20
You are absolutely correct. I managed to mount them using "hda1" and "hdb1", after creating the necessary folders, e.g., /mydisk1 and /mydisk2. And all files were still intact. 

Guess I sat way to long staring at my machine, banging my head against the screen, and simply was not thinking.

Anyway, thanks for your help, and your replies!

Regards,
David

---

### Post by Buffalo Soldier on 2005-03-20
[QUOTE=kb00heda]Guess I sat way to long staring at my machine, banging my head against the screen, and simply was not thinking.[/QUOTE]I believe we all have been there and gone through the same experience. :)

---

