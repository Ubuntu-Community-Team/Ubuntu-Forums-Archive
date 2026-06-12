---
title: "how to combine two hard without loss of contents?"
date: 2013-03-24
forum: Hardware
---

### Post by mohammad alsharqi on 2013-03-24
hi

I have a 500 GB Hard has installed Squid and i want to install a new hard with an old one without loss of contents 

an old one is 500 gb 
a new one is 2000 gb
and i would get 2500 gb 

thanks

---

### Post by Bashing-om on 2013-03-24
mohammad alsharqi 	


The tutorial that I use (command line):
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

The tutorial works for me, hope you find it as useful.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by mohammad alsharqi on 2013-03-25
is this combine between an old and new hard??

---

### Post by Bashing-om on 2013-03-25
mohammad alsharqi;

The instructions are to add the capacity to your system, how you use that added capacity is at your discretion.

Specific questions get specific answers.[INDENT=6]hope this helps

[/INDENT]

---

### Post by mohammad alsharqi on 2013-03-28
this is not useful for me 
i think there is lvm method uses to merge two hard disk ??

---

### Post by mohammad alsharqi on 2013-04-04
any helllllp please????

---

### Post by Cheesemill on 2013-04-04
If you partitioned the first disk using LVM when you installed the system then its easy to combine the drives.

If you aren't using LVM then there is no easy way to simply pool the drives together, your best bet would be to migrate the contents of the squid cache directory to your new drive before mounting it under the original directory location. This method would give you 2TB for just your cache, the rest of your OS and its data would still be on the original 500GB drive.

If you must have both drives pooled together to give you 2500GB of continuous storage space then it would be easiest to reinstall using LVM, and then restore your current data from your last backup.

---

### Post by mohammad alsharqi on 2013-04-04
yeah i partitioned it with lvm
what is the steps to combine it

---

### Post by Cheesemill on 2013-04-04
Without knowing your exact setup I can't give you the commands you need.

If you can post back with the output of the following commands I'll get back to you (can you post your output in between [NOPARSE] ```
 
```[/NOPARSE] tags to make it easier to read please).

```
sudo parted -l
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay
```

---

### Post by mohammad alsharqi on 2013-04-04
sudo parted -l
```
Model: ATA ST2000DM001-1CH1 (scsi)Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  ext4




Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot, raid
 2      257MB   500GB  500GB  extended
 5      257MB   500GB  500GB  logical                lvm




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ALSHARQI-swap_1: 9181MB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  9181MB  9181MB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ALSHARQI-root: 477GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  477GB  477GB  ext4




Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label    
```

sudo pvdisplay
```
 --- Physical volume ---  PV Name               /dev/sdb5
  VG Name               ALSHARQI
  PV Size               465.52 GiB / not usable 2.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              119173
  Free PE               3350
  Allocated PE          115823
  PV UUID               w6sHZN-zD3V-7HAz-wJIO-vnkW-Nk0F-e6309E



```

 sudo vgdisplay
```
 --- Volume group ---  VG Name               ALSHARQI
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               465.52 GiB
  PE Size               4.00 MiB
  Total PE              119173
  Alloc PE / Size       115823 / 452.43 GiB
  Free  PE / Size       3350 / 13.09 GiB
  VG UUID               1AtRfd-GY9j-VLcd-Ny2W-375X-6t0u-YkYSZZ



```

sudo lvdisplay
```
 --- Logical volume ---  LV Name                /dev/ALSHARQI/root
  VG Name                ALSHARQI
  LV UUID                lZI6r3-8D7x-KFo5-JYpj-2f4I-rtrb-AaEmca
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                443.88 GiB
  Current LE             113634
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:0
   
  --- Logical volume ---
  LV Name                /dev/ALSHARQI/swap_1
  VG Name                ALSHARQI
  LV UUID                hHYa1E-wGHH-NzKu-e165-3Bh1-ngSV-sqSrun
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                8.55 GiB
  Current LE             2189
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:1



```

---

### Post by Cheesemill on 2013-04-04
OK then. First we need to delete the ext4 partition you've created and create an LVM partition instead. This will delete all of the data that's currently on your new drive.

```
sudo fdisk /dev/sda
d
n
p
1
[ENTER]
[ENTER]
t
8e
w

```
If you now do 'sudo fdisk -l /dev/sda' you should see that your new drive has 1 LVM partition taking up the entire drive.

Next we create a new PV (physical volume) from the partition and add it to your existing VG (volume group).
```
sudo pvcreate /dev/sda1
sudo vgextend ALSHARQI /dev/sda1
```

We can now extend your root LV (logical volume) to take up all of the newly available space in your VG.
```
 sudo lvextend -l +100%FREE /dev/ALSHARQI/root
```
Finally we grow the root filesystem to use all of the available space on the underlying root VG.
```
sudo resize2fs /dev/ALSHARQI/root
```

All done. You can check the size of your new root partition using..
```
df -h
```

---

### Post by mohammad alsharqi on 2013-04-04
sorry, but will this delete all my data of old drive??

---

### Post by Cheesemill on 2013-04-04
No.
It will create a new partition on your new drive, add it to your LVM setup, and resize your existing installation to use all of the available space.

Although if anything does go wrong you do have a backup to restore from don't you?

---

### Post by mohammad alsharqi on 2013-04-04
[FONT=arial][SIZE=2]i would thank you for your helping and your patience 
but how to backup it???[/SIZE][/FONT]

---

### Post by mohammad alsharqi on 2013-04-04
i get this error on sudo pvcreate /dev/sda1

```
Device /dev/sda1 not found (or ignored by filtering).


```

---

### Post by Cheesemill on 2013-04-04
What does your new sda drive look like now, it should have one large LVM partition, sda1.
Can you post the output of...
```
sudo fdisk -l /dev/sda
```

---

### Post by mohammad alsharqi on 2013-04-04
```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x17441f77


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243201  1953512001   8e  Linux LVM
Partition 1 does not start on physical sector boundary.
```

---

### Post by Cheesemill on 2013-04-04
For some reason your LVM configuration isn't letting you add the new drive. I've not come across this before but I have a couple of ideas.
Can you post the output of...
```
grep filter /etc/lvm/lvm.conf | grep -v "#"
```

---

### Post by mohammad alsharqi on 2013-04-04
```
 filter = [ "a/.*/" ]
```

---

### Post by mohammad alsharqi on 2013-04-05
[COLOR=#000000]Cheesemill
is there solution for this error[/COLOR]

---

### Post by Cheesemill on 2013-04-05
I've been looking around and I might have just now found an answer.
Try running the following command and then see if you can continue with my earlier instructions.

```
sudo partprobe -s
```

---

### Post by mohammad alsharqi on 2013-04-05
after applied the [COLOR=#000000][FONT=Ubuntu Mono]partprobe -s and continue to earlier command i got this in [/FONT][/COLOR]sudo pvcreate /dev/sda1
```

 Can't open /dev/sda1 exclusively.  Mounted filesystem?



```

---

### Post by Cheesemill on 2013-04-05
Try unmounting it first...
```
sudo umount /dev/sda1
```

---

### Post by mohammad alsharqi on 2013-04-05
```
umount: /dev/sda1: not mounted


```

---

### Post by mohammad alsharqi on 2013-04-05
output of partprobe -s ```
/dev/sda: msdos partitions 1
/dev/sdb: msdos partitions 1 2 <5>
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.



```

---

### Post by mohammad alsharqi on 2013-04-07
thanks alot the problem is solved 
but  seem the first hard (500) gb is not mounted and may only a second hard is used 
and this the output of df- h

```
Filesystem            Size  Used Avail Use% Mounted on/dev/mapper/ALSHARQI-root
                      2.3T  418G  1.8T  20% /
none                  4.0G  236K  4.0G   1% /dev
none                  4.0G     0  4.0G   0% /dev/shm
none                  4.0G   64K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
none                  4.0G     0  4.0G   0% /lib/init/rw
/dev/sdb1             228M   17M  200M   8% /boot



```

---

