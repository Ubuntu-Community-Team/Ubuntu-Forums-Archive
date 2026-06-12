---
title: "Can't access data partition from dead Seagate Central 2TB NAS"
date: 2014-12-29
forum: Hardware
---

### Post by joel30 on 2014-12-29
Hey folks, I'm trying to recover my data from my recently deceased Seagate Central 2TB NAS, but I can't access the data partition though windows and Xubuntu 13.10 hasn't yielded any results. 
I followed these threads but eventually ran into issues in each one of them;
[http://ubuntuforums.org/showthread.php?t=2058632](http://ubuntuforums.org/showthread.php?t=2058632)
[http://www.serkey.com/ubuntu-how-to-recover-data-from-seagate-blackarmor-drives-beau85.html](http://www.serkey.com/ubuntu-how-to-recover-data-from-seagate-blackarmor-drives-beau85.html)
[http://superuser.com/questions/436341/cant-mount-filesystem-on-hd-that-came-from-wd-nas](http://superuser.com/questions/436341/cant-mount-filesystem-on-hd-that-came-from-wd-nas)
[http://www.linuxquestions.org/questions/linux-newbie-8/reading-data-from-seagate-hard-drive-extracted-from-seagate-central-4175516790/](http://www.linuxquestions.org/questions/linux-newbie-8/reading-data-from-seagate-hard-drive-extracted-from-seagate-central-4175516790/)
[http://myanwyn.blogspot.com/2014/08/how-to-recover-seagate-central-data.html](http://myanwyn.blogspot.com/2014/08/how-to-recover-seagate-central-data.html)

Running Sudo parted -l yields this;

Model: ST2000VM 003-1CT164 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name                Flags
 1      1049kB  22.0MB  21.0MB  ext2         Kernel_1            msftdata
 2      22.0MB  43.0MB  21.0MB  ext2         Kernel_2            msftdata
 3      43.0MB  1117MB  1074MB  ext4         Root_File_System_1  msftdata
 4      1117MB  2190MB  1074MB  ext4         Root_File_System_2  msftdata
 5      2190MB  3264MB  1074MB  ext4         Config              msftdata
 6      3264MB  4338MB  1074MB               Swap
 7      4338MB  5412MB  1074MB  ext4         Update              msftdata
 8      5412MB  2000GB  1995GB               Data                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg1-lv1: 1995GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system  Flags
 1      0.00B  1995GB  1995GB  ext4


Any help would be hugely appreciated, and would hopefully serve others in my situation.

Cheers!

---

### Post by weatherman2 on 2014-12-29
It looks like the data is in the LVM, which is being detected in a logical volume at /dev/mapper/vg1-lv1 .  Have you tried doing this in a terminal:

```

sudo mount /dev/mapper/vg1-lv1 /mnt 

```

I'm not sure if Xubuntu has all of the needed LVM tools installed - earlier versions of Ubuntu did not, though I think as of 14.04 they do.    Try typing the command

```
sudo lvdisplay
```

Do you get any results?  The output should be the name of the logical volume and size, etc. (which is vg1-lv1 - that is what the NAS is calling "Volume Group 1, Logical Volume 1").  But if the lvdisplay command is not found on your system, then you need to install lvm2 tools:

```
sudo apt-get install lvm2
```

---

### Post by ajgreeny on 2014-12-29
None of the lvm applications are installed by default and Xubuntu will not be able to see LVM filesystems without them, so follow weatherman2's suggestions and you should be more lucky.

---

### Post by joel30 on 2014-12-29
Thanks for taking a stab at this. 

The first command gives back;
user@chrubuntu:~$ sudo mount /mnt /dev/mapper/vg1-lv1
mount: /mnt is not a block device

Second command gives;
user@chrubuntu:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg1/lv1
  LV Name                lv1
  VG Name                vg1
  LV UUID                iedQHH-dsuQ-Y3k0-e7re-qRpe-gUew-LUvMBV
  LV Write Access        read/write
  LV Creation host, time , 
  LV Status              available
  # open                 0
  LV Size                1.81 TiB
  Current LE             475641
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0



I did have lvm2 already installed by following one of those articles, but I double checked to be safe.

---

### Post by weatherman2 on 2014-12-29
Oops - I got the mount command backwards.  Sorry!  Should be:

```
sudo mount /dev/mapper/vg1-lv1 /mnt
```

(edited above to correct the order.)

---

### Post by joel30 on 2014-12-29
This is the return;
mount: wrong fs type, bad option, bad superblock on /dev/mapper/vg1-lv1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I'm concerned that the actual "data" partition doesn't show a file structure.. and that might be the problem?

---

### Post by weatherman2 on 2014-12-29
Your data wasn't encrypted on that partition, was it?

We're assuming the partition is plain-old ext4 (which is what parted reports back).  But given that this was a Seagate NAS, could it be something custom?  Not sure.  I don't know how their NAS works.

---

### Post by joel30 on 2014-12-29
no.. I never set up any sort of special encryption. 
Is there a command to specifically load a ext4 partition?

---

### Post by weatherman2 on 2014-12-29
The mount command in Ubuntu/Xubuntu will automatically detect an ext2/3/4 partition and mount it without needing to specify a type.  ext4 is now the default/standard partition type.

I would try to find out more about how Seagate (it's their NAS right?  not just their hard drive?) sets up their data partitions.  Could be it encrypts your data by default even if you never selected such an option.  Can you try contacting Seagate support or finding a Seagate forum?

There is always a chance that the partition is indeed corrupted.  In fact - what got you to this point?  A hardware failure?

Have you checked the drive's S.M.A.R.T. status to see if it has experienced any sort of problem?  smartmontools (the smartctl command) can help you with that .  GSmartControl is the graphical version that's easier to use (smartctl is a terminal command).  If you find you have a bunch of bad sectors or something, the drive could have started to fail and your partition may be truly corrupted.  That's when I'd start looking into a data recovery approach e.g. something called "testdisk" that can recover data from corrupted/deleted partitions.

---

### Post by steeldriver on 2014-12-29
It's not that Sparc ext4 block size thing again is it? take a look here (apologies if you have seen it already) --> [http://ubuntuforums.org/showthread.php?t=2198460&page=2&p=12903047#post12903047](http://ubuntuforums.org/showthread.php?t=2198460&page=2&p=12903047#post12903047)

---

### Post by Reha_Andrew on 2014-12-30
Seeing all this i would suggest donot experimant much now as you already have. Consult and search for actual experts in this field. People already guide you much on this. Have patience and take professional guidance.

---

