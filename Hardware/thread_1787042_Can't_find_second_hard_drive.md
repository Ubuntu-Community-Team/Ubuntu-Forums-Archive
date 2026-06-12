---
title: "Can't find second hard drive"
date: 2011-06-20
forum: Hardware
---

### Post by Davander on 2011-06-20
Hello.  I have a laptop that came with Windows Vista and I recently installed Ubuntu 11.04.  I have been having trouble finding my second hard drive.  I'm not exactly sure if it is recognized by the BIOS... I'm new to this kind of thing.  When I go into the terminal and put in the sudo lshw -C Disk I get this: 

PCI (sysfs)  
  *-disk                  
       description: ATA Disk
       product: ST9320320AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 0303
       serial: 5SX4LYYR
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0002ad67
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RW DVRTD08RS
       vendor: PIONEER
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.06
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb

When I try to do anything with /dev/sdb it says that it is unable to open. 
I would really appreciate any help!

---

### Post by jerrrys on 2011-06-20
will your 'disk utility' (system>admin) show it?  pull it up?

---

### Post by Davander on 2011-06-20
No, it only brings up the one that I have the OS installed on and the host adapter.  The hard drive hasn't been tinkered with and as far as I know should still be connected.  It suddenly disapeared with my formatting to ubuntu.

---

### Post by Yellow Pasque on 2011-06-20
Was the disk already partitioned?

---

### Post by Davander on 2011-06-20
The disk drive in question contains files still and was previously partitioned yes.

---

### Post by Yellow Pasque on 2011-06-20
Can you post output of:
```
sudo fdisk /dev/sdb -l
```

---

### Post by Davander on 2011-06-21
It asks me for a password and then I get a new command line.  So there is no output.

---

