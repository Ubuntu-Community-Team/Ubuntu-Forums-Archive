---
title: "Some problems and questions"
date: 2008-09-17
forum: General Help
---

### Post by Opencan on 2008-09-17
First of all, i have issues with the sound - Sometimes it works some times it doesn't. For instence, now it doesn't and yesterday it did.
Right now I can hear while speaking to the microphone but programs like XMMS doesn't play sound. I've downloaded the restricted codecs for Ubuntu and Kubuntu from Synaptic.
I got 2 sound cards, so it might be the cause. I own some RIO onboard one that I'd like to disable and a Creative Live Platinum that I rather use.

Second, I'm looking for a way to be able to log on my second hard drive without typing in the admin password, how can I do that?

Third, I'm looking for a way to view .php files from the computer. I'm building a website and it will be much easier to view it from the computer than uploading it to a server first. On the same note I'm looking for an FTP accessing program.

Forth, I can't play videos, it looks like I'm missing codecs or something.

Fifth, I'm connecting to the internet by a script my ISP sent me. I need to type "sudo cable-start" each time to connect to the internet. Is there a way to make it go off automatically at the start-up stage?


Thanks :D

---

### Post by jken146 on 2008-09-17
> **Opencan said:**
> Second, I'm looking for a way to be able to log on my second hard drive without typing in the admin password, how can I do that?  Please open a terminal (Applications -> Accessories -> Terminal) and post the outputs of ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```

> Third, I'm looking for a way to view .php files from the computer. I'm building a website and it will be much easier to view it from the computer than uploading it to a server first.  Install Apache and PHP as per [here]("http://www.howtoforge.com/ubuntu_lamp_for_newbies") -- you might not need mySQL though.

> On the same note I'm looking for an FTP accessing program.  I don't use any myself, but have a look in Applications -> Add/remove...

> Forth, I can't play videos, it looks like I'm missing codecs or something.  Try ```
sudo apt-get install ubuntu-restricted-extras
``` and see if that fixes everything.

---

### Post by Opencan on 2008-09-17
1.The first command didn't work. (Using Gusty Ribbon if it matters)
the second gave this:
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=6c3e2ec2-536d-43ca-83ce-f78134b60bb3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=0b9d693b-61ff-4b48-81ea-0d7ac6631908 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

3. I will :D

4. Already installed. Suddenly videos work  O.o


Thanks for the quick reply :D

---

### Post by jken146 on 2008-09-17
Sorry about that, it was a typo.  :oops:  ```
sudo fdisk -l
``` is what it should have been.  Please post the output of that :)

---

### Post by Opencan on 2008-09-17
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xace22e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf793f793

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9682    77770633+  83  Linux
/dev/hdb2            9683        9964     2265165    5  Extended
/dev/hdb5            9683        9964     2265133+  82  Linux swap / Solaris

---

### Post by jken146 on 2008-09-17
OK, first create a mount point for this other partition, sda1 (I'm assuming you want to call it windows but use whatever you like).
```
sudo mkdir /media/windows
```
Then add a line to fstab to tell it to mount automatically.  ```
gksudo gedit /etc/fstab
``` and add ```
/dev/sda1 /media/windows ntfs defaults 0 0
``` to the bottom of the file.  Save, quit gedit and type ```
sudo umount /dev/sda1
sudo mount -a
``` to unmount the partition if it's already mounted and then mount it (again) according to the rule in fstab.

---

