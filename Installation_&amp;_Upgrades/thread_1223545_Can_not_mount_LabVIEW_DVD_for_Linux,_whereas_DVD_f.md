---
title: "Can not mount LabVIEW DVD for Linux, whereas DVD for Windows can be mounted"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by sese_k on 2009-07-26
Hi!

I already posted part of this as reply in an other thread ([http://ubuntuforums.org/showthread.php?t=1199844](http://ubuntuforums.org/showthread.php?t=1199844)), but I post it now in an own thread, because there were no replies so far and I think this is a better place for the issue.

So, my problem is the following: I want to install LabVIEW 8.6.1 on my Ubuntu 9.04. But when I insert the DVD and Ubuntu tries to automount the volume, a popup with this error message appears: "Cannot mount volume. Invalid mount option when attempting to mount the volume 'ASLSP09MacLinux'.". The problem only occurs with this particular DVD so far, for example I have no problem to mount the LabVIEW DVD for Windows. I tried then a manual mount of the drive with these commands (I'm pretty new to Linux, installed Ubuntu some days ago, but I think ISO9660 and UDF are the standard filesystems for DVDs/CDs?):

```
$ sudo mount -t iso9660 /dev/sr0 /media/cdrom
$ sudo mount -t udf /dev/sr0 /media/cdrom
```In both cases I get the same error message:

```
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```So I tried, what the above code suggested:
```
$ dmesg | tail
```This is the result:
```
[10968.396447] ISOFS: Unable to identify CD-ROM format.
[11035.652954] UDF-fs: No partition found (1)
```It seems, that when trying to launch with the ISO filesystem the format of the DVD can not be identified at all and with the UDF filesystem the DVD can be identified, but no partition is recognized. Is this interpretation correct? So, as it does not work with both of the filesystems, is it possible, that I need to install an additional filesystem? On the DVD is the Linux distribution of LabVIEW as well as the MAC distribution, is it possible, that the DVD has a MAC specific filesystem, which is not known to my Ubuntu?

Hope someone can help with this...

Cheers,

Sebastian

---

### Post by sese_k on 2009-07-27
Okay, it works now. As we found out, the DVD is formated with Mac OS extended filesystem, so you have to use Linux HFS+ filesystem to mount the drive. This is, what worked for me:
```
sudo mount -t hfsplus /dev/sr0 /media/cdrom
```As it seems, HFS+ is already included in the kernel although when listing the available filesystems with
```
cat /etc/fstab
```there was no entry showing "hfsplus". After mounting the DVD and listing the filesystems again  "hfsplus" was shown at the end of the list. 
I don't know, if there is any option to edit "/etc/fstab", so that an inserted Mac disc will be mounted automatically next time? If I find something I will post it here...

Cheers,

Sebastian

---

### Post by mb36 on 2011-11-28
I see you did not get any response to this until now. Anyway, I just ran into the same problem today and this post saved me. Thanks a million! :D

/Mårten

---

