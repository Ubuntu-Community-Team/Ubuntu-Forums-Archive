---
title: "dvd will not mount"
date: 2011-01-02
forum: Hardware
---

### Post by ryadav on 2011-01-02
Can some help me get my dvd-drive to mount and work? It seems to be ok  when I bootup into windows? 

i have the following entry in my fstab 

/dev/sr0 /mnt/cdrom udf,iso9660 noauto,owner,kudzu,ro 0 0 

likewise wodim give me: 

$ sudo wodim --devices 

wodim: Overview of accessible drives (1 found)
------------------------------------------------------------------------- 
 0  dev='/dev/scd0'     rwrw-- : 'HL-DT-ST' 'DVD-RAM GSA-H55N' 
------------------------------------------------------------------------- 

NOTE: scd0 links to sro 

if I try to mount, I get a no media found? i've tried a few cds, dvds 

$ sudo mount -t iso9660 */dev/scd0 /cdrom/* 

I keep getting: "mount: no medium found on /dev/sr0"

---

### Post by ryadav on 2011-01-05
bump

---

### Post by nomko on 2011-01-05
> **ryadav said:**
> Can some help me get my dvd-drive to mount and work? It seems to be ok when I bootup into windows? 
 
i have the following entry in my fstab 
 
/dev/sr0 /mnt/cdrom udf,iso9660 noauto,owner,kudzu,ro 0 0 
 
likewise wodim give me: 
 
$ sudo wodim --devices 
 
wodim: Overview of accessible drives (1 found)
------------------------------------------------------------------------- 
0 dev='/dev/scd0' rwrw-- : 'HL-DT-ST' 'DVD-RAM GSA-H55N' 
------------------------------------------------------------------------- 
 
NOTE: scd0 links to sro 
 
if I try to mount, I get a no media found? i've tried a few cds, dvds 
 
$ sudo mount -t iso9660 */dev/scd0 /cdrom/* 
 
I keep getting: "mount: no medium found on /dev/sr0"
 
In as much as I can see your drive has a medium point at /dev/scd0 but when you mount it, it doesn't exist in some way: /dev/sr0.
 
Also in your fstab there are some weird things:
 
**/dev/sr0 /mnt/cdrom udf,iso9660 noauto,owner,kudzu,ro 0 0 **
 
Assuming that your device mounting point is /dev/scd0 then your fstab entry needs to be and changing some options:
 
**/dev/scd0 /mnt/cdrom   udf,iso9660   defaults   0   2** 
 
Even better, mount the device using it's UUID.
-open a terminal
-type in: **sudo blkid**
-place the output here (to assist you)
 
The line in the fstab will change into this:
**UUID=********** /mnt/cdrom   udf,iso9660   defaults   0   2** 
 
Make sure there's a mounting point for the cd-rom in the folder /mnt:
-open a terminal
-type in: **sudo mkdir /mnt/cdrom**
 
If this doens't work, check your /media folder. In most cases all devices are mounted here.
- in terminal type in: **ls /media/**
- place the output here (to assist you)
 
If your cdrom is mounted under /media/ (i.e. /media/cdrom/) then the line in fstab changes into:
**UUID=********** /media/cdrom   udf,iso9660   defaults   0   2** 
 
Why using the UUID?
As you discovred, mounting devices using /dev/(..) is prone to creating errors which results in not mounting the device. Using the UUID you're much more sure that whatever changes after a update or reboot, the device is still mounted. UUID cannot be changed since this is a fixed combination of numbers and letters.
 
Try this and let us know if this helpt you.

---

### Post by ryadav on 2011-01-05
it's looking like it might be bad hardware or a bad ide cable

---

### Post by nomko on 2011-01-05
> **ryadav said:**
> it's looking like it might be bad hardware or a bad ide cable
 
That doesn't explain the difference of device names:
/dev/scd0
/dev/sr0
 
There's something crooked about fstab and the mounting points.

---

### Post by shrdlu on 2011-01-12
I've got a similar problem. This machine has two Panasonic DVD writers. They worked fine until I did a distribution upgrade to 10.10 and now neither of them recognise any inserted media.

---

### Post by bertram_wooster on 2011-02-13
I am also having this issue.

I am not sure whether I need to open my machine and check the cables or whether I can troubleshoot at the command line.

I have:
```

$ sudo wodim --devices 
wodim: Overview of accessible drives (2 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : 'OPTORITE' 'CD-RW CW5205'
 1  dev='/dev/scd1'	rwrw-- : 'HL-DT-ST' 'DVDRAM GH22NS50'
-------------------------------------------------------------------------

```

But there doesn't appear to be a UUID given to the optical device if nothing is mounted.
```

$ sudo blkid
/dev/sda: TYPE="isw_raid_member" 
/dev/sdb1: UUID="EAF5-8112" TYPE="vfat" 
/dev/sdc: TYPE="isw_raid_member" 
/dev/sdd1: UUID="0de44771-ece9-48ec-a631-f69495429419" TYPE="ext4" 
/dev/sde1: UUID="0447dc2e-70f6-420f-ad7a-d750ec6f61f4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sde2: UUID="933ff0fd-9338-4664-8b2a-c027ab31f8ab" TYPE="ext4" 
/dev/sde3: UUID="41db0bc6-b0c3-42d7-a25a-431d5cfeefea" TYPE="ext4" 
/dev/sde5: UUID="ea4dc821-e653-4dd0-830e-fb408bdadee7" TYPE="swap" 
/dev/sde6: UUID="a15b8a7d-fa72-4b19-8924-7d8d40a2b6aa" TYPE="ext3" 
/dev/sde7: UUID="a0a066e1-a73b-4fe7-a23c-063c129dbe02" TYPE="ext4" 
/dev/mapper/isw_ccddgdghai_the_ant_colony4: UUID="17671a6b-5e7c-41ac-bc7d-94b5b3bf0608" SEC_TYPE="ext2" TYPE="ext3"

```

None of these are the optical device.

I have tried to edit the fstab file anyway, to use the device path instead, i.e.
```

/dev/scd1       /media/dvd       udf,iso9660 defaults        0     2   

```

I even tried it with the path I expected to see here:

```

/dev/sr1       /media/dvd       udf,iso9660 defaults        0     2   

```

Nothing.

Please give me some advice as to how I get my machine reading DVDs again. It was reading them fine before the software disaster that precipated the new install.

---

