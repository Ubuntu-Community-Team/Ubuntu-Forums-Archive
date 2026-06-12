---
title: "How To Format my USB Drive..."
date: 2008-08-16
forum: Hardware
---

### Post by Xero121690 on 2008-08-16
I'm new to Ubuntu and well..
Im having problems formatting my USB drive..
Its an 8 GB USB drive..
I cant seem to find a format button on the options :]
Can some one help me
Thanx.

---

### Post by K2712 on 2008-08-16
The easiest way to format drives is to use gparted:

```
sudo apt-get install gparted
```

After it is installed, open it via System->Administration->Gnome Partition Editor.

Select the flash drive from the drop down menu and format it to whatever file system you like.  Just be careful you are formatting your flash drive and not your hard drive.

---

### Post by cdtech on 2008-08-16
First make sure your USB pen is not mounted. Click on Places > Computer > Select USB pen > Right click > Select Unmount Volume.

Lets assume that /dev/**sdc1** is your partition name for USB pen (you can find yours by typing on a command line:
```
sudo fdisk -l
```
To format the device, type the following command (Open a terminal and type the command)
```
$ sudo mkfs.ext3 /dev/sdc1
```
**Caution:**
Be careful while entering the device/partition name; **the wrong name can wipe out your entire hard drive!!!**

Now use the "e2label" command to change the filesystem label on the newly created ext3 filesystem located on device /dev/**sdc1**:
```
$ sudo e2label /dev/sdc1 **usb-pen**
```
(Or whatever you want to name it)

You can also create an MS-DOS/Windows XP file system under Linux, enter:
```
$ sudo mkfs.vfat /dev/sdc1
```

Now your ready to use the USB pen drive.

Good Luck.........

---

### Post by Xero121690 on 2008-08-16
Thanks Man
That solved my problem :)

---

