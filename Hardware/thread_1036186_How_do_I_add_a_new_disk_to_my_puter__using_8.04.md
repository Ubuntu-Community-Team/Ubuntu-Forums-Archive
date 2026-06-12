---
title: "How do I add a new disk to my puter?  using 8.04"
date: 2009-01-10
forum: Hardware
---

### Post by Linuxwho? on 2009-01-10
Hi All,

I am using desktop but would like to do it from command line too as I want to learn command line.  Thanks.[LIST=1]
[/LIST]

---

### Post by taurus on 2009-01-10
Is it a new harddrive?  Is there any partition (something like /dev/sdb1) and filesystem on that drive?

```
sudo fdisk -l
```
If not, you need to create a partition and format it before you can use it.

---

### Post by Linuxwho? on 2009-01-11
I dont see it in any form of disk manager or know its identity.  How do I know what command with or what to fdisk?  It is an attached array via scsi cable.  Is there a command to identify it before using the fdisk command?

This is what I get:
owner@owner-desktop:~$ sudo fdisk -l
owner@owner-desktop:~$ sudo fdisk 

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
owner@owner-desktop:~$ fdisk /dev/sda

Unable to open /dev/sda
owner@owner-desktop:~$ fdisk /dev/sdb

Unable to open /dev/sdb

---

I already craeted it using smart start cd for compaq but it duznt see it.

I tried another command but I dunno what he output means lol...

"owner@owner-desktop:~$ dmesg |grep scsi
[    4.407330] scsi0 : pata_serverworks
[    4.407628] scsi1 : pata_serverworks
[    4.752299] scsi 0:0:0:0: CD-ROM            COMPAQ   CD-224E          A.8D PQ: 0 ANSI: 5
[    4.777970] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    4.815103] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[    4.815328] sr 0:0:0:0: Attached scsi CD-ROM sr0
"

---

### Post by Linuxwho? on 2009-01-11
Anyone?

---

### Post by cariboo on 2009-01-11
THe command is:

```
sudo fdisk -l
```

that is a lower case L. If you have the drive hooked up, the above command will list your new hard drive and tell you that it is unpartitioned. to create partitions at then prompt type:

```
sudo fdisk /dev/<new_drive>
```

where <new_drive> = what ever the output of fdisk -l told you what label your new drive was.

From there press m for help to see what the commands are.

Once you have partitioned your new drive at the prompt type: 

```
sudo mkfs.ext3 -b 4096 /dev/hdb1
```

/dev/hdb1 is only example your device lable may differ. The above command will format the partition as ext3.

Jim

---

### Post by Linuxwho? on 2009-01-11
> **cariboo907 said:**
> THe command is:

```
sudo fdisk -l
```

that is a lower case L. If you have the drive hooked up, the above command will list your new hard drive and tell you that it is unpartitioned. to create partitions at then prompt type:

```
sudo fdisk /dev/<new_drive>
```

where <new_drive> = what ever the output of fdisk -l told you what label your new drive was.

From there press m for help to see what the commands are.

Once you have partitioned your new drive at the prompt type: 

```
sudo mkfs.ext3 -b 4096 /dev/hdb1
```

/dev/hdb1 is only example your device lable may differ. The above command will format the partition as ext3.

Jim

Thanks Jim!  The trouble is that I type that command and it doesn't come up with any output. #-o



"root@owner-desktop:/dev# fdisk -l
root@owner-desktop:/dev# "

---

### Post by Linuxwho? on 2009-01-11
Could it be bc I already used the compaq smart start cd (array utility) to make a logical drive?

---

