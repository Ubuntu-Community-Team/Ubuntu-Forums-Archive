---
title: "HDD Mounting"
date: 2008-11-10
forum: Hardware
---

### Post by Dilburger on 2008-11-10
I have an Iomeaga external HDD. I formatted it with fat32 when i had VIsta on, I have recently installed 8.1 ubuntu and when i try to access the HDD an error prompts saying that it can not be mounted.

---

### Post by shacristo on 2008-11-10
What exactly is the error it gives?

---

### Post by Dilburger on 2008-11-10
it literally says that can not mount volume

---

### Post by Coreigh on 2008-11-10
Are you trying to mount the drive through the GUI "places" menu with connect, or from the command line?

Is the external drive a USB device. When I plug in a USB drive when I am already logged in (Ubuntu 7.10 desktop) it gets automatically mounted as /media/disk.

Could you post the error message word for word?

---

### Post by Dilburger on 2008-11-10
Yes i am going through places, I am not to experienced with the command line yet... Yes the drive is USB. and the ERROR is...

Cannot Mount volume.
Unable to mount the volume "name"

---

### Post by Coreigh on 2008-11-10
Plug the drive in and have it powered on (if not already)

open a terminal window and type the following:
```
 sudo fdisk -l
```
you will be asked for your password, this is your normal login password.

Please post the output of that command. It will list all available volumes (disks) to be mounted.

---

### Post by Dilburger on 2008-11-10
so far so good? and I really do not want to lose the data on the drive... if possible.

dilburger@Dilburger:~$ sudo fdisk -l
[sudo] password for dilburger: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe844d59d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19128   153645628+  83  Linux
/dev/sda2           19129       19457     2642692+   5  Extended
/dev/sda5           19129       19457     2642661   82  Linux swap / Solaris

Disk /dev/sdb: 8254 MB, 8254390272 bytes
16 heads, 32 sectors/track, 31488 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xe868e868

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       31488     8060912    b  W95 FAT32

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08ab967c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS
Note: sector size is 4096 (not 512)

Disk /dev/sdd: 159.8 GB, 159840301056 bytes
26 heads, 50 sectors/track, 30018 cylinders
Units = cylinders of 1300 * 4096 = 5324800 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30019   156093788    b  W95 FAT32

---

### Post by Dilburger on 2008-11-10
oh here is another error. From same mounting problem.

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by Coreigh on 2008-11-10
That output indicates there are 4 hard disks sda, sdb, sdc and sdd. sdb and sdd each have a Windows partition. sdb is small about 4gb and sdd is large about 80gb. To mount from the command line, make a mount point, a folder to mount on in the mnt directory:
```
mkdir /mnt/usbdisk
```
To mount the disk:
```
sudo mount /dev/sdd1 /mnt/usbdisk
```

or /dev/sdb1 if you want the smaller disk.

post the error if you get one.

Does this external drive work on a windows computer?

---

### Post by Dilburger on 2008-11-10
Yes it worked fine when my computer was windows. I did get an erroe....

dilburger@Dilburger:~$ mkdir /mnt/usbdisk
mkdir: cannot create directory `/mnt/usbdisk': Permission denied

dilburger@Dilburger:~$ sudo mount /dev/sdd1 /mnt/usbdisk
[sudo] password for dilburger: 
mount: mount point /mnt/usbdisk does not exist

---

### Post by shacristo on 2008-11-10
You'll need to put sudo in front of that first command, then try again.

---

### Post by Coreigh on 2008-11-10
right sorry, put the sudo in front of the mkdir command.

sudo is a command that works like "run-as" so it tells the computer to execute the command as a privileged user and it takes your password as an identifier for who is asking. mkdir as you can probably guess is "make directory."

---

