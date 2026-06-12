---
title: "drives"
date: 2006-08-07
forum: Hardware &amp; Laptops
---

### Post by somi38 on 2006-08-07
how can i open my fat32 drives in ubuntu
please help me

---

### Post by mority on 2006-08-07
> **somi38 said:**
> how can i open my fat32 drives in ubuntu
please help me

You must mount the partition, i.e. add the drive to your directory tree.

You will have to know by which device file the drive/partition is accessed. If it is an IDE drive, this short overview may help you:

/dev/hda - primary master
/dev/hdb - primary slave
/dev/hdc - secondary master
/dev/hdd - secondary slave

To access partitions, just append the number of the partition counting from 1. So /dev/hdb3 is the third partition on the primary slave.

To mount it you would type something like this:
```

mount -t vfat /dev/hdb3 /mnt/mydrive

```

You can find more information here: [http://www.tldp.org/LDP/intro-linux/html/sect_03_01.html](http://www.tldp.org/LDP/intro-linux/html/sect_03_01.html)

---

### Post by somi38 on 2006-08-07
what is mounted tree.
how can i mount my drives.
where these commands are written
please help me 
i use linux first time

---

### Post by mority on 2006-08-07
> **somi38 said:**
> what is mounted tree.
how can i mount my drives.
where these commands are written
please help me 
i use linux first time

If you plan to use Linux seriously I would strongly recommend you to read this document: [Introduction to Linux](http://www.tldp.org/LDP/intro-linux/html/index.html). It is very well written and addresses people completely new to Linux. Maybe you think it is too much to read for a beginner, but the time you will spend reading that document will pay off tenfold.

To answer some of you questions: the easisest way to enter commands in Ubuntu is to start a gnome terminal (Applications -> Accessoires -> Terminal).

Do this to find out where your FAT32 partition is: Start the gnome terminal as described above and type
```

mo@ash:~$ **sudo fdisk /dev/hda**
Password:

The number of cylinders for this disk is set to 77520.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): **p**

Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30480    15361888+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           30489       77520    23703907+   5  Extended
Partition 2 does not end on cylinder boundary.
/dev/hda5           30489       38617     4096543+  83  Linux
/dev/hda6           38617       40641     1020096   82  Linux swap / Solaris
/dev/hda7           40641       77520    18587173+  83  Linux

Command (m for help): **q**

```
I marked the commands you have to enter with bold font. The output on your system will look similar but not identical.
Post the output here and I will tell you the right command to mount your FAT32 partition.
Maybe repeat these commands for /dev/hdb, /dev/hdc and /dev/hdd.

---

### Post by somi38 on 2006-08-08
salman@ubuntusalman:~$ sudo fdisk /dev/hda
Password:

The number of cylinders for this disk is set to 7297.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         637     5116671    b  W95 FAT32
/dev/hda2             638        1746     8908042+  83  Linux
/dev/hda3            1747        7296    44580375    f  W95 Ext'd (LBA)
/dev/hda5            1799        1912      915673+   b  W95 FAT32
/dev/hda6            1913        4462    20482843+   b  W95 FAT32
/dev/hda7            4463        7296    22764073+   b  W95 FAT32
/dev/hda8            1747        1798      417627   82  Linux swap / Solaris

Partition table entries are not in disk order

Command (m for help): q

---

### Post by somi38 on 2006-08-08
salman@ubuntusalman:~$ sudo fdisk /dev/hda
Password:

The number of cylinders for this disk is set to 7297.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         637     5116671    b  W95 FAT32
/dev/hda2             638        1746     8908042+  83  Linux
/dev/hda3            1747        7296    44580375    f  W95 Ext'd (LBA)
/dev/hda5            1799        1912      915673+   b  W95 FAT32
/dev/hda6            1913        4462    20482843+   b  W95 FAT32
/dev/hda7            4463        7296    22764073+   b  W95 FAT32
/dev/hda8            1747        1798      417627   82  Linux swap / Solaris

Partition table entries are not in disk order

Command (m for help): q
please tell e more

---

### Post by somi38 on 2006-08-08
salman@ubuntusalman:~$ sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists
salman@ubuntusalman:~$ sudo mount /dev/hda /media/windows -t vfat -0 iocharset=utf8,umask=000
mount: invalid option -- 0
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by somi38 on 2006-08-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by somi38 on 2006-08-08
my keyboard's space bar butten is not working ,when i am in linux .in win xp it i absolutly correct
what i do

---

### Post by somi38 on 2006-08-08
salman@ubuntusalman:~$ sudo fdisk /dev/hda
Password:

The number of cylinders for this disk is set to 7297.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         637     5116671    b  W95 FAT32
/dev/hda2             638        1746     8908042+  83  Linux
/dev/hda3            1747        7296    44580375    f  W95 Ext'd (LBA)
/dev/hda5            1799        1912      915673+   b  W95 FAT32
/dev/hda6            1913        4462    20482843+   b  W95 FAT32
/dev/hda7            4463        7296    22764073+   b  W95 FAT32
/dev/hda8            1747        1798      417627   82  Linux swap / Solaris

Partition table entries are not in disk order

Command (m for help): q

---

### Post by mority on 2006-08-08
I see four FAT32 on your primary master harddisk. If you want to mount them all at once, create four directories in /mnt like this:
```

sudo mkdir /mnt/win1
sudo mkdir /mnt/win2
sudo mkdir /mnt/win3
sudo mkdir /mnt/win4

```
Then you can mount every partition like this:
```

sudo mount -t vfat /dev/hda1 /mnt/win1
sudo mount -t vfat /dev/hda5 /mnt/win2
sudo mount -t vfat /dev/hda6 /mnt/win3
sudo mount -t vfat /dev/hda7 /mnt/win4

```

And please, put your system output in code tags to increase readability.

---

### Post by somi38 on 2006-08-08
salman@ubuntusalman:~$ sudo mkdir /mnt/win1
mkdir: cannot create directory `/mnt/win1': File exists
salman@ubuntusalman:~$ sudo mount -t vfat /dev/hda1 /mnt/win1
mount: /dev/hda1 already mounted or /mnt/win1 busy
mount: according to mtab, /dev/hda1 is already mounted on /mnt/win1
salman@ubuntusalman:~$ sudo mkdir /mnt/win2
mkdir: cannot create directory `/mnt/win2': File exists
salman@ubuntusalman:~$ sudo mount -t vfat /dev/hda5 /mnt/win2
mount: /dev/hda5 already mounted or /mnt/win2 busy
mount: according to mtab, /dev/hda5 is already mounted on /mnt/win2
salman@ubuntusalman:~$ sudo mkdir /mnt/win3
mkdir: cannot create directory `/mnt/win3': File exists
salman@ubuntusalman:~$ sudo mount -t vfat /dev/hda6 /mnt/win3
mount: /dev/hda6 already mounted or /mnt/win3 busy
mount: according to mtab, /dev/hda6 is already mounted on /mnt/win3
salman@ubuntusalman:~$ sudo mkdir /mnt/win4
mkdir: cannot create directory `/mnt/win4': File exists
salman@ubuntusalman:~$ sudo mount -t vfat /dev/hda7 /mnt/win4
mount: /dev/hda7 already mounted or /mnt/win4 busy
mount: according to mtab, /dev/hda7 is already mounted on /mnt/win4
salman@ubuntusalman:~$

---

### Post by somi38 on 2006-08-08
please tell me what i do next

---

### Post by darrenm on 2006-08-08
Type ```
sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1
```

For the space bar, check your language and keyboard layouts are correct in the System menu, Preferences then keyboard.

---

### Post by mority on 2006-08-08
> **somi38 said:**
> salman@ubuntusalman:~$ sudo mkdir /mnt/win1
mkdir: cannot create directory `/mnt/win1': File exists
salman@ubuntusalman:~$ sudo mount -t vfat /dev/hda1 /mnt/win1
mount: /dev/hda1 already mounted or /mnt/win1 busy
mount: according to mtab, /dev/hda1 is already mounted on /mnt/win1
salman@ubuntusalman:~$ sudo mkdir /mnt/win2
mkdir: cannot create directory `/mnt/win2': File exists
salman@ubuntusalman:~$ sudo mount -t vfat /dev/hda5 /mnt/win2
mount: /dev/hda5 already mounted or /mnt/win2 busy
mount: according to mtab, /dev/hda5 is already mounted on /mnt/win2
salman@ubuntusalman:~$ sudo mkdir /mnt/win3
mkdir: cannot create directory `/mnt/win3': File exists
salman@ubuntusalman:~$ sudo mount -t vfat /dev/hda6 /mnt/win3
mount: /dev/hda6 already mounted or /mnt/win3 busy
mount: according to mtab, /dev/hda6 is already mounted on /mnt/win3
salman@ubuntusalman:~$ sudo mkdir /mnt/win4
mkdir: cannot create directory `/mnt/win4': File exists
salman@ubuntusalman:~$ sudo mount -t vfat /dev/hda7 /mnt/win4
mount: /dev/hda7 already mounted or /mnt/win4 busy
mount: according to mtab, /dev/hda7 is already mounted on /mnt/win4
salman@ubuntusalman:~$

What exactly did you do and why are you posting only **this** output and why don't you put it in code tags?

This output is telling that you **already** mounted the fat32 partitions. So you did not post everything you did, but just a bunch of random output lines. That's not making it easier to help you.

Anyways, according to the output you posted, the paritions are mounted and you should see them in nautilus. So the task is done. Go to Places -> Computer -> Filesystem -> mnt -> winX to browse the files of your fat32 partitions.

And then **please** read some Linux documentation like "Introduction to Linux" before you proceed. It will save you and the people at this forums a lot of time.

---

### Post by somi38 on 2006-08-08
ThankYou for this
i opened my drives
please tell me how can i play songs

---

### Post by mority on 2006-08-08
> **somi38 said:**
> ThankYou for this
i opened my drives
please tell me how can i play songs

You are welcome.

How to play songs is a completely different topic so you should start another thread for this question or even better you should try and search the forum for an answer before you do so.

As a hint: The standard application for music listening in Gnome and Ubuntu is rhythmbox. You find it at Applications -> Sound & Video -> Rhythmbox Music Player. But because of patent issues you will have to install some packages from the multiverse repository in order do activate mp3 support. Just follow the instructions at this page: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by somi38 on 2006-08-09
when we restart our pc then drives also disappears.whwt would be the conclusion of this problem. we again mount the drives then we can see the drives.help me

---

### Post by mority on 2006-08-09
> **somi38 said:**
> when we restart our pc then drives also disappears.whwt would be the conclusion of this problem. we again mount the drives then we can see the drives.help me

You will have to add the drives to the file /etc/fstab. Please read the [Introduction to Linux](http://www.tldp.org/LDP/intro-linux/html/index.html) and/or ```
man fstab
``` to see how to do this.

---

### Post by somi38 on 2006-08-09
i want my drives at desktop what i do.
you send me some codes these are not permanent
please send me permanent codes

---

### Post by somi38 on 2006-08-09
you send me some links that cannot hel me send proper commands
please

---

### Post by mority on 2006-08-09
> **somi38 said:**
> you send me some links that cannot hel me send proper commands
please

Yeah, of course, I will send you my bank information for the support fees. :-s

By the way: Please stop spamming my PM Inbox with "plz answer my post".

I'm out.

---

### Post by somi38 on 2006-08-10
i have w32codecs.
how can i install w32codecs.
i have system of intel(R)
733MH processer
60 GB HD
can i install ubuntu dapper drack6.06

---

### Post by somi38 on 2006-08-10
please answer my question

---

