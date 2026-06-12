---
title: "mounting USB driver as a Linux file system"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by tambidude on 2007-10-11
Hi,

I have a USB2 based external HD. so far I am mounting it as ntfs-3g type. It is working fine but
I want to mount it as a native linux file system as I have no plans of using it with Windows.
What are the steps? 
Also how do I mount the USB drive as say /usr/data every time the machine boots. 

thanks.

---

### Post by taurus on 2007-10-11
You must first format it to ext3 if you want to mount it as Linux filesystem.  Then, add an entry in /etc/fstab so it would be mounted automatically each time you boot Ubuntu.  

To convert it from ntfs to ext3, you need to unmount it first if it is already mounted.

```
sudo umount /dev/sdb1 (assuming /dev/sdb1 is your external drive)
sudo mk2fs -j /dev/sdb1 (_MAKE SURE_ it is /dev/sdb1...)
gksudo gedit /etc/fstab
```
Scroll down to the end and add this line to it.

```
/dev/sdb1   /usr/data   ext3   defaults   0   1
```
Save it.  Then, create that new directory, /usr/data.

```
sudo /usr/data
```
Reboot.

---

### Post by dannyboy79 on 2007-10-11
> **taurus said:**
> You must first format it to ext3 if you want to mount it as Linux filesystem.  Then, add an entry in /etc/fstab so it would be mounted automatically each time you boot Ubuntu.  

To convert it from ntfs to ext3, you need to unmount it first if it is already mounted.

```
sudo umount /dev/sdb1 (assuming /dev/sdb1 is your external drive)
sudo mk2fs -j /dev/sdb1 (_MAKE SURE_ it is /dev/sdb1...)
gksudo gedit /etc/fstab
```
Scroll down to the end and add this line to it.

```
/dev/sdb1   /usr/data   ext3   defaults   0   1
```
Save it.  Then, create that new directory, /usr/data.

```
sudo /usr/data
```
Reboot.

Unless your plugging in multiple different usb devices, it's always going to mount to say /media/disk (whatever the label of the device is) (ie i named my devices within windows and now they mount to /media/SPORT1GB/ etc etc)

I don't suggest using fstab for externally mounted devices because if it's not plugged in when you turn the machine on it's going to barf. You can use udev rules explained here: [http://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/](http://www.linuxquestions.org/questions/linux-general-1/make-removable-usb-hdd-mount-at-fixed-mount-point-511917/)

just my opinion

---

