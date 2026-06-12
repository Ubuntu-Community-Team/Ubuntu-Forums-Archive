---
title: "Cannot mount a hard drive"
date: 2009-03-02
forum: Hardware
---

### Post by bwallum on 2009-03-02
Hi I have two sata hard drives. Recently I have not been able to mount one. The attachments show the error messages. Can you help please?

Rgds
Bob

---

### Post by anubhavrocks on 2009-03-02
Can you post the output of:
```
cat /etc/fstab
```

---

### Post by ajgreeny on 2009-03-02
Or if you are trying to mount it manually using terminal, let's see your command that throws up this error.

---

### Post by bwallum on 2009-03-02
> **anubhavrocks said:**
> Can you post the output of:
```
cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c3ea772e-63b8-4b12-bc7b-4f7d5668f241 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b30ead77-4284-4dbe-9c70-6799a3ea1270 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by bwallum on 2009-03-02
> **ajgreeny said:**
> Or if you are trying to mount it manually using terminal, let's see your command that throws up this error.

What is the command to attempt a manual mount please?

---

### Post by khelben1979 on 2009-03-02
```
man mount
```
is a good start.

---

### Post by ajgreeny on 2009-03-02
> What is the command to attempt a manual mount please? 		                   		  		  		 		 			 				Yes, ```
man mount
``` will help you here, but the problem appears to be that your fstab is only showing one drive with two partitions, sda1 and sda5.  Can you also show the output from the command ```
sudo fdsik -l
``` to see what drives your machine actually recognises.  Hopefully there will be another drive (sdb?) in the output to give us a chance of mounting it manually or with a line in fstab.

---

### Post by bwallum on 2009-03-02
> **ajgreeny said:**
> Yes, ```
man mount
``` will help you here, but the problem appears to be that your fstab is only showing one drive with two partitions, sda1 and sda5.  Can you also show the output from the command ```
sudo fdsik -l
``` to see what drives your machine actually recognises.  Hopefully there will be another drive (sdb?) in the output to give us a chance of mounting it manually or with a line in fstab.

I've done lshw and got:

> -disk:0
                description: ATA Disk
                product: ST3808110AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 3.AD
                serial: 9LR4MC8J
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000099a1
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: c3ea772e-63b8-4b12-bc7b-4f7d5668f241
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-05-08 14:20:39 filesystem=ext3 modified=2009-03-02 20:25:34 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-03-02 20:22:44 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   size: 2941MiB
                   capacity: 2941MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2941MiB
                      capabilities: nofs
           *-disk:1
                description: ATA Disk
                product: ST3808110AS
                vendor: Seagate
                physical id: 1
                bus info: scsi@3:0.0.0
                logical name: /dev/sdb
                version: 3.AD
                serial: 9LR4MC9S
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0008237a
              *-volume
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@3:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /media
                   version: 1.0
                   serial: b6d9a9b3-855b-4e2b-97c3-1ee7cbecf657
                   size: 74GiB
                   capacity: 74GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-05-09 17:10:21 filesystem=ext3 modified=2009-03-02 23:03:08 mount.fstype=ext3 mount.options=rw,errors=remount-ro,data=ordered mounted=2009-03-02 23:03:08 state=mounted

as the relevant info. Please forget earlier reports as I have had the lid off and checked cabling. I have also tried to add the drive to /etc/fstab file as below:-

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c3ea772e-63b8-4b12-bc7b-4f7d5668f241 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b30ead77-4284-4dbe-9c70-6799a3ea1270 none            swap    sw              0       0
# /dev/sdb1
UUID=b6d9a9b3-855b-4e2b-97c3-1ee7cbecf657 /media	ext3 	errors=remount-ro 	0 	1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

It looks as though the sdb1 drive is mounted according to lshw but I can't see it????

Here's the output from fdisk -l

> Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000099a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9351    75111876   83  Linux
/dev/sda2            9352        9726     3012187+   5  Extended
/dev/sda5            9352        9726     3012156   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008237a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9726    78124063+  83  Linux


---

### Post by ajgreeny on 2009-03-02
I think you need to make a folder other than just /media for the mount point for the sdb1 disk partition.  Do a ```
sudo mkdir /media/sdb1
``` and change the fstab line to ```
# /dev/sdb1
UUID=b6d9a9b3-855b-4e2b-97c3-1ee7cbecf657 /media/sdb1 ext3 defaults 0 1
```

---

### Post by bwallum on 2009-03-02
> **ajgreeny said:**
> I think you need to make a folder other than just /media for the mount point for the sdb1 disk partition.  Do a ```
sudo mkdir /media/sdb1
``` and change the fstab line to ```
# /dev/sdb1
UUID=b6d9a9b3-855b-4e2b-97c3-1ee7cbecf657 /media/sdb1 ext3 defaults 0 1
```

Done that and now get error as screenshot...can now see the drive in places though.

---

### Post by anubhavrocks on 2009-03-02
Use this command:
```
sudo mount -a
```

---

### Post by bwallum on 2009-03-03
> **anubhavrocks said:**
> Use this command:
```
sudo mount -a
```


I have re partitioned the hard drive and given it a label Drive2.

I tried sudo mount -a and get the error attached.

UPDATE

Ok, I've got to a satisfactory point now. My second harddrive is labelled Drive2. I formatted a single partition to ext3 using gparted (available in repository - System>Administration>Synaptic Package Manager)

I set up a directory in root/media called Drive2 (/media/Drive2). I used nautilus as root with the command sudo nautilus to enable me to make the directory.

My /etc/fstab file is as follows:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c3ea772e-63b8-4b12-bc7b-4f7d5668f241 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b30ead77-4284-4dbe-9c70-6799a3ea1270 none            swap    sw              0       0
# /dev/sdb1
UUID=6790a0bf-4fa4-46d7-b439-bab35cc24d7e /media/Drive2	ext3	defaults	0 	0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I think the final 0 at the end of 'UUID=6790a0bf-4fa4-46d7-b439-bab35cc24d7e /media/Drive2	ext3	defaults	0 	0' line allowed access.

UPDATE 2

I remain stuck because I can't write to the mounted Drive2

---

### Post by anubhavrocks on 2009-03-03
After you have mounted the partition;post the output of:
```

ls -l /media
```

Your fstab looks okay.You might want to check the permissions of the mount point specifically.

---

### Post by bwallum on 2009-03-06
Thanks for all the help. I've found a help page [http://help.ubuntu.com/community/InstallingANewHardDrive]("http://help.ubuntu.com/community/InstallingANewHardDrive") that gets me most of the way there. I then changed the defaults option to 'user,noauto' in etc/fstab to allow me to mount and unmount the drive when I want.

So the /etc/fstab file is now> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a4ac6e85-3c16-4f54-ba52-ca27ee1310f4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ff33b832-1d90-4e22-bf5e-3b735e3dda7c none            swap    sw              0       0
# /dev/sdb1
/dev/sdb1	/media/drive2	ext3	user,noauto	0	0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 

All appears to be well

ls -l /media now gives
> total 12
lrwxrwxrwx 1 root root         6 2004-01-01 00:08 cdrom -> cdrom0
drwxr-xr-x 2 root root      4096 2004-01-01 00:08 cdrom0
drwxrwxr-x 4 root berrybush 4096 2009-03-06 20:43 drive2
lrwxrwxrwx 1 root root         7 2004-01-01 00:08 floppy -> floppy0
drwxr-xr-x 2 root root      4096 2004-01-01 00:08 floppy0



berrybush is the group I allow to access the drive. drive2 is the name of the directory in /media that /dev/sdb1 is mounted on. I almost understand it!

Thank you very much for sticking with me and thank you for the insight into a number of commands.

---

