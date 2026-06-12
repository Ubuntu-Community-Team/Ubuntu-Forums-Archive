---
title: "Unable to mount raid 1 data drive in Windows/Ubuntu 8.04 dual boot system"
date: 2008-08-22
forum: General Help
---

### Post by Mahler122 on 2008-08-22
I hope this is the right place to post this,

I am relatively new to linux.

Heres the situation, I have a Windows XP / Ubuntu 8.04 dual boot system. This is accomplished on a single 400GB disk. grub, the OS partitions for both windows and linux, the swap, and a games partition are on this disk. This set up works wonderfully. All data I deem worthy of keeping I put on a separate 200GB disk. This disk is can be accessed from both windows and linux. This disk is getting old and I felt a replacement and added security was in order since this data is worth keeping.

I now have two 500GB disks which I wish to put in a raid 1 configuration. Since I like linux for a lot of things, I would like both windows and linux to be able to read and write to the raid 1 'disk'.

My motherboard is an XFX nForce 680i LT SLI. This comes with an built in nVidia Raid Controller. This seems to be called 'FakeRaid'.

I set up the drives and used the fakeraid software in windows to create a healthy raid 1 array which I wrote some files to, to test that it worked.

I want to know if there is a way to make ubuntu see this as a single 'volume' and mount it. 

I have tried to use dmraid. Here are the various things I tried.

```
root@mahler:~# dmraid -r
/dev/sdc: nvidia, "nvidia_fcabiaba", mirror, ok, 976773166 sectors, data@ 0
/dev/sda: nvidia, "nvidia_fcabiaba", mirror, ok, 976773166 sectors, data@ 0
root@mahler:~# dmraid -s
*** Active Set
name   : nvidia_fcabiaba
size   : 976773120
stride : 128
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
root@mahler:~# dmraid -ay
RAID set "nvidia_fcabiaba" already active
RAID set "nvidia_fcabiaba1" already active
```

It would seem that dmraid detects the set correctly as a mirror set (or raid 1) and that it is active. however when I try to mount the raid 1 'disk' from /dev/mapper/nvidia_fcabiaba, I get this:

```
root@mahler:/# mount -t ntfs /dev/mapper/nvidia_fcabiaba /Files
NTFS signature is missing.
Failed to mount '/dev/mapper/nvidia_fcabiaba': Invalid argument
The device '/dev/mapper/nvidia_fcabiaba' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

However the drive is perfectly usable in windows and was formated using ntfs, how can linux not detect the ntfs file structure?

The general feeling I've got from reading the forums is that using the fakeraid is a bad way to go, however I don't know how to make it work in windows as well using just the linux software raid tools. Hardware raid is always an option, but the only pci controllers I can find with both support for windows and linux are ~130$ and I don't want to pay any more money so if I can get it to work with the fake raid or with pure software that would be fantastic.

Any Ideas? All I want is the raid 1 disk to be readable and writable from both linux and windows.

Thanks!

---

### Post by tamoneya on 2008-08-22
can you tell us the output of this command:```
ls /dev/mapper
```

---

### Post by fjgaude on 2008-08-23
Take a look at this post:

[http://ubuntuforums.org/showthread.php?t=893938&highlight=raid](http://ubuntuforums.org/showthread.php?t=893938&highlight=raid)

Use /dev/mapper to mount.

---

### Post by Mahler122 on 2008-08-25
I tried adding the line
```
/dev/mapper/nvidia_fcabiaba /Files default ntfs 0 0
```
To the end of my fstab file which is:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=5774daa3-f7c7-4d55-af5a-a36a0bf7ce10 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=71dfeba4-6144-4abf-985c-e4018c2c4c5b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
Nothing happened.

the output of ls /dev/mapper is as follows:
```
root@mahler:~# ls /dev/mapper
control  nvidia_fcabiaba  nvidia_fcabiaba1

```

---

### Post by tamoneya on 2008-08-25
> **Mahler122 said:**
> I tried adding the line
```
/dev/mapper/nvidia_fcabiaba /Files default ntfs 0 0
```
To the end of my fstab file which is:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=5774daa3-f7c7-4d55-af5a-a36a0bf7ce10 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=71dfeba4-6144-4abf-985c-e4018c2c4c5b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
Nothing happened.

the output of ls /dev/mapper is as follows:
```
root@mahler:~# ls /dev/mapper
control  nvidia_fcabiaba  nvidia_fcabiaba1

```

try this:```
sudo mount -t ntfs /dev/mapper/nvidia_fcabiaba1 /Files
```
Note the "1" that is added to the mount device.  Also you will need sudo for the proper permissions.

---

### Post by Mahler122 on 2008-08-25
Okay! 

The command ```
sudo mount -t ntfs /dev/mapper/nvidia_fcabiaba1 /Files
``` worked, and I was able to read and write to the array, as well as retrieve what I wrote while in linux in windows.

since nvidia_fcabiaba1 worked instead of nvidia_fcabiaba, I tried to add that to the fstab file instead, but it didn't mount automatically when I booted linux. The edited fstab is:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=5774daa3-f7c7-4d55-af5a-a36a0bf7ce10 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=71dfeba4-6144-4abf-985c-e4018c2c4c5b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/nvidia_fcabiaba1 /files1 ntfs defaults 0 0
```

How can I get linux to mount this drive on start up and put an icon in 'computer' and on the desktop?

---

### Post by Mahler122 on 2008-08-25
fyi, I did create /files1 in order to differentiate it from another disk called 'Files'.

---

### Post by Jim_1981 on 2008-10-05
You can get your drive to mount on startup by adding 

```
mount -t ntfs /dev/mapper/nvidia_fcabiaba1 /Files
```

to /etc/rc.local before the exit 0 line.

---

