---
title: "Yet another USB Hard-drive mounting question"
date: 2006-02-10
forum: Hardware &amp; Laptops
---

### Post by nmatheis on 2006-02-10
hello all

i am running breezy with ubuntu-desktop and kubuntu-desktop installed on an amd-64 machine.  i am fully upgraded as of today with a dist-upgrade.  yesterday, i was able to turn on my lacie 250gb usb external hd, and it "just worked".  mounted-up with no fuss.  the icon it mounted with was even labeled "Lacie".

today, i turn it on and nothing.  nada.  so i started poking around the forums a bit and found the following command to try:

```
nikolaus@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3348    26892778+   7  HPFS/NTFS
/dev/hda2   *        3349        9692    50958180   83  Linux
/dev/hda3            9693        9964     2184840    5  Extended
/dev/hda5            9693        9964     2184808+  82  Linux swap / Solaris

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       30401   244196001    c  W95 FAT32 (LBA)

```

i am able to edit** /etc/fdisk** with this info and get the hd to mount/unmount on usb0.  the problem is, when i restart the machine the hd path changes.  the first time i ran **sudo fdisk -l** it came up as **/dev/sdd1**.  the next time i rebooted, it came up as **/dev/sda1**.  this time it came up as above (**/dev/sde1**).  so if i want to mount the drive, i have to keep using the **sudo fdisk -l** command and then editing my **/etc/fstab** file every time.  

so how can i fix this permanently???

here are my **/etc/fstab** entries:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sde1        /media/usb0    vfat    rw,user,auto	0       0

/tmp/app/1/image /tmp/app/1 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/2/image /tmp/app/2 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/3/image /tmp/app/3 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/4/image /tmp/app/4 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/5/image /tmp/app/5 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/6/image /tmp/app/6 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
/tmp/app/7/image /tmp/app/7 cramfs,iso9660 user,noauto,ro,loop,exec 0 0
```

so my main goal will to have the drive mount automatically (preferrably as "Lacie")when i plug it in every time, no matter whether i rebooted or not.

thanks for any help!!!
nikolaus

---

### Post by nmatheis on 2006-02-11
bump for some help with this problem :)

i have played around with fstab for the /dev/sd** file systems with no success.  in ubuntu i can get the usb hd to mount by checking the path with **fdisk -l** and using the command **mount /dev/sd**** (whatever the path is as shown in the fdisk report).  in kubuntu i can't get the thing to mount up with the mount command.  i keep getting an error message stating something like "Filesystem cannot be mounted.  I cannot determine the file type."  something like that anyway.  so to mount it, i have to login to ubuntu and use the command line. 

so any help would be great!!!

---

### Post by ScarletEmerald on 2006-02-11
Don't know if this is the right solution or not, but you might want to look into something called "udev".  I don't know much about it, but it seems to do what you need regarding the persistent device naming.

---

### Post by nmatheis on 2006-02-12
i just looked and **udev** is already installed.  so i don't think that's the problem (unless i need to sonfigure it somehow).  i got to thinking that maybe upgrading to a new kernel is the problem, so i rebooted with the previous kernel (the one with which i had usb hd success) but with no luck.

---

### Post by nmatheis on 2006-02-16
hello again!
so since this problem first occured, i have performed a reinstall of breezy ubuntu x64 edition and then apt-get update followed by apt-get upgrade.  i was able to get the usb drive to automount for about a week, and now it has failed to automount again.  i restarted the computer with no luck.  i have not changed **/etc/fstab** at all.  i can get the usb drive to mount by using the command **pmount /dev/sd*1** (whichever sd*1 the drive mounts at that time, usually sdd1 or sde1).  i'd rather get the drive to automount if possible or at least have a graphical mounting program (like pmount in dsl, which lists all drives and lets you click a button to mount/unmount them).

so if anyone has advice on how to get the drive to automount again - or at least knows of a package i can install that will give me a mount/unmount gui without having to bother with the commandline for **fdisk -l** and then ** pmount /dev/sd*1**.  i don't mind doing that necessarily, but i have two kids and a sig-fig to worry about using the usb hd, as well.  my son will probably dig using the commandline to mount the drive, but i don't think my daughter or my sig-fig will want to use the commandline.

thanks!
nikolaus

---

### Post by nmatheis on 2006-02-16
hello again!

i have performed a reinstall (probably a week ago) with ubuntu breezy x64 version.  after install, i used apt-get update and apt-get dist-upgrade.  for about a week the automount feature worked.  two days ago, it stopped working again, and i have to manually mount mu usb hard drive.

as stated before, i use **sudo fdisk -l** to find which partition the usb hd is on (usually /dev/sdd1/ or /dev/sde1) and the use **pmount /dev/sd*1** (whichever partition i get from **fdisk**).  this works for me, but i have other users on the computer who use the usb hd who will not want to use the commandline to mount the drive.  so i would like to get the automount feature working again, and any advice along those lines would be great!

alternatively, is there a package i can install which will give me a gui for mounting/unmounting drives.  i've tried dsl on my old laptop and liked the **pmount** gui in the dsl menu - brings up a gui listing all the drives and includes a button for mounting/unmounting them.   i think in lieu of automount, software with a  for gui mount/unmount would be great!  

so, any help would be appreciated!

thansk!
nikolaus

---

### Post by trelirodia on 2006-03-01
Dear Nikolaus, 

you might want to have a look at these two links below. 

The first one mentions how to write rules for udev to solve your problem. It will basically help you assign a stable /dev link to your device so that you can permanenty add it to your fstab file and do not have to worry about mounting it everytime. It has worked very well for me. 

[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

Below is a thread where the discussed the same problems and suggested a much simpler solution to the problem. I just found that so I've only tested it really briefly and I am not sure how well it works, but it is definetely worth a shot. It is much simpler than writing udev rules. 

[http://www.ubuntuforums.org/showthread.php?t=64674](http://www.ubuntuforums.org/showthread.php?t=64674)

Best of luck :-)

---

