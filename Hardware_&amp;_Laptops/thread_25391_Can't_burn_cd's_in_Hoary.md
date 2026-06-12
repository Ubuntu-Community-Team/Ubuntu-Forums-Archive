---
title: "Can't burn cd's in Hoary"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by jeremy on 2005-04-10
I did a fresh hoary release install a couple of days ago, and since then cannot burn cd's, have tried both gnobaker and k3b and all I get is an I/O error.

user@ubuntu:~$  sudo hdparm /dev/scd1

/dev/scd1:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

I don't know why my IDE burner is scd1, in warty it was hda. I have 2 SATA HD's

---

### Post by heimo on 2005-04-10
I don't have solution to your problem, but at least some information you probably can use. I have similar setup, two SATA disks and one IDE CDRW burner in first IDE channel as a master. I'm using HH, but not from the release CD, earlier pre-release. 

Hard disks are /dev/sda and /dev/sdb, and CDRW drive is /dev/hda, as I'd expect it to be. And the burner is working correctly. ```
hdparm /dev/hda
```

gives me:

```
/dev/hda:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

```

whether the cd is on or off the drive.

```
sudo lsmod | grep cd
``` 

gives me (among some other lines):

```
ide_cd                 41700  1 
ide_core              129356  5 usb_storage,via82cxxx,ide_generic,ide_disk,ide_cd
cdrom                  40220  1 ide_cd
```

So the line:
```
 HDIO_GETGEO failed: Invalid argument
``` 

which on hard disks gives the drive geometry data, doesn't seem to indicate problem on cd-drives. Maybe you could check that /dev/cdrom is a symlink to your cd drive? On my case it is:

```
ls -al /dev/cdrom 
lrwxrwxrwx  1 root root 3 2005-04-10 06:23 /dev/cdrom -> hda

``` 

Using: cat /proc/sys/dev/cdrom/info I get:
```

CD-ROM information, Id: cdrom.c 3.20 2003/12/17

drive name:             hda
drive speed:            0
drive # of slots:       1
Can close tray:         1
Can open tray:          1
Can lock tray:          1
... [and so on]

```

---

### Post by mackstann on 2005-04-10
I have two normal IDE hard drives, hda and hdb, and my burner is hdd (must have set it to slave for whatever reason).  My /dev/cdrom correctly points to /dev/hdd -- make sure your /dev/cdrom points to the right place. Not exactly a necessary thing, but might as well make sure it's correct.  cdrecord seemed to be pretty confused no matter what I tried, until I remembered something and it worked:

cdrecord dev=/dev/cdrom [....]

For example, 'cdrecord dev=/dev/cdrom -scanbus' should correctly list your burner.

You can modify the default device globally by editing /etc/cdrecord/cdrecord and setting CDR_DEVICE to /dev/cdrom, or you can just modify it in your own environment by setting $CDR_DEVICE in your shell init scripts.

... but uh, neither of those seem to be working for me.  Weird.  Annoying.  Anyways, the dev= method still works.

---

### Post by jeremy on 2005-04-11
Thank you both for your answers, yesterday I bit the bullet and reinstalled hoary, I don't know why but this tiime it has correctly identified my IDE cd and dvd drives as hda & hdb (SATA HD's are sda & sdb), with DMA on they work perfectly.

---

