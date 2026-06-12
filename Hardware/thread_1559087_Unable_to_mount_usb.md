---
title: "Unable to mount usb"
date: 2010-08-23
forum: Hardware
---

### Post by kjartani on 2010-08-23
Hello

trying to mount usb 

"sudo mount -t usbdevfs none /proc/bus/usb"

gretting error

"mount point /proc/bus/usb does not exist"

As root when trying to make the directory "usb" Im getting strange error messages.

Can anybody help?

Regards
Kjartan

---

### Post by richs-lxh on 2010-08-23
Hi kjartani
Firstly, if you are just trying to mount a USB device, it should automatically open in Nautilus unless there is a problem.

Two commands to see what's plugged in to USB, and which drive is the USB drive.

1. lsusb will list Usb devices
2. sudo fdisk -l will list your harddrives/partitions

Once you know which drive is the Usb device you can mount it:

Example for a Linux (Ext3) formatted drive:
sudo mkdir /media/mypendrive
sudo mount /dev/sdb1 /media/mypendrive

---

### Post by kjartani on 2010-08-23
Thanks.


"1. lsusb will list Usb devices" works fine....  

"2. sudo fdisk -l will list your harddrives/partitions" works fine too....

but... I was trying ti run program UsbView and then I got the error message : "Cannot open the file : /proc/bus/usb/device

the directory usb doesnt exist....

I find this odd...

Kjartan

---

### Post by richs-lxh on 2010-08-23
Sorry, I'm not familiar with how Usbview works. I just use the command line.

---

### Post by Raizen44 on 2010-09-02
guys I have a question with Ubuntu 10.04. USB devices work fine, but whenever I plug them in I keep getting and error message saying "Unable to mount (name of USB device)". Though I am able to use the USB devices through the file manager. is something up with my system? I have the netbook edition on my laptop.

---

### Post by burdebc on 2010-11-06
I have been having the same problem for a while now and ran into a post that is seemingly unrelated but it works.  I just entered the following two commands and USBview worked.

sudo mount --bind /dev/bus /proc/bus
sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices

here is a link to the post:
[http://ubuntuforums.org/showthread.php?t=1493771&highlight=mount+point+%2Fproc%2Fbus%2Fusb+does+not+exist](http://ubuntuforums.org/showthread.php?t=1493771&highlight=mount+point+%2Fproc%2Fbus%2Fusb+does+not+exist)

---

