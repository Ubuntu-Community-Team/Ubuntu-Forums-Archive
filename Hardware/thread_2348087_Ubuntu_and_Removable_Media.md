---
title: "Ubuntu and Removable Media"
date: 2016-12-31
forum: Hardware
---

### Post by yuklop on 2016-12-31
Dear All,

What is the score with Ubuntu and Removable Media (USB / SD cards?)

As far as I can tell it doesn't really work. I am using 16.10, but I also have laptop on 14.04LTS and neither PC can cope with USB sticks or SD cards. Usually I can mount them and delete the contents, but then trying to paste something new onto a USB stick or SD Card, get a read only error. Can't change permissions as filesystem is read only. Can format it. Sometimes works for a bit, but then some file copying error or other. Then back to read only error. Muck around with chmod or chown without any luck. Read the all the first 2 pages of google results on Ubuntu and USB sticks trying everything in those threads...and there are a lot of threads. Partial success. But so far I still haven't copied a 2Gb folder to either 2 different (tested working) USB sticks or 2 different SD cards. Restart PC a couple of times. Partial success.

Probably I will figure this out in the end... but what the hell! It can't really be so hard to copy a folder to a USB stick. It cannot be worth 2 hours I've spent on this thorny issue so far.

So what is the score with USB / SD cards? Are they not really supported. Or is it just accepted that they work crap with Ubuntu. For me its the single biggest frustration with Ubuntu. These things really should just work - and work without having to go anywhere near the terminal if Ubuntu wants to expand its userbase.

Do you all experience similar or is there some universal fix that I just missed?

Happy New Year,

Dan

---

### Post by SeijiSensei on 2016-12-31
Most times when you attach a USB device as an ordinary, non-root user, it will be mounted to /media/username/devicename and owned by username.  If the device is formatted with something like FAT32, you should have full permissions to all the directories and files.  If it's formatted as ext[234], and some or all of the files are owned by someone else, e.g., root, then you won't be able to delete them since you don't own them.  So if you have a blank USB device, you should have full rights to the device once you insert it into the port, and it is mounted at /media/username/something-or-other/.

You can use "sudo" to acquire root privileges and do whatever you want to the device.  For instance, suppose you have a USB stick that Ubuntu recognizes as /dev/sdb1.  If you insert it in the machine, it will be automatically mounted under /media/username.  To reformat that device with FAT32, you could then use
```

cd /
sudo umount /dev/sdb1
sudo fsck -t vfat /dev/sdb1

```
That will unmount the device and format it with FAT32 ("vfat").  I presume it's possible to do this from the GUI with something like gparted, but I find the terminal much easier and quicker than clicking around in a GUI.  YMMV.

If you are mounting a device like an external drive, your options depend a lot on what filesystem it has, and how it was mounted.  I assume you have already read the relevant documentation before posting here, but if not, take a look at

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by ajgreeny on 2016-12-31
There is no problem using USB cards or flash drives, or even external hard disk drives in Ubuntu provided you use them properly and particularly, you unmount them properly before removing them. I have used many of them for over 11 years in Ubuntu with no difficulties of any sort.

What filesystem is on these cards that will not mount properly and allow you to use them as you wish?
Normally they are fat32 and mount read/write when inserted, but if they are larger than 32GB they may be exfat which will not work properly without you installing **exfat-utils** and **exfat-fuse**.

Also, if you have formatted them as ntfs and not unmounted them properly in either Ubuntu or Windows, you will certainly have problems using them.

With one of the problem cards attached/inserted run command ```
sudo fdisk -l
``` and copy back the output here.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

