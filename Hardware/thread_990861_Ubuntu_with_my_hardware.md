---
title: "Ubuntu with my hardware"
date: 2008-11-23
forum: Hardware
---

### Post by DazEllerington on 2008-11-23
Hello.

I'm switching from Windows to Ubuntu at present. However, like any of my other attempts to switch to a Linux, it's a pain! Things that used to take under 1 minute takes weeks and is quite frustrating.

What is a tool that can tell me the /dev/??? against a string that makes sense to humans? E.g. /dev/sda -- USB Memory Stick...or something?

This is since 4 simple USB mass storage devices, that I use fine under windows, are not usable in Ubunbtu, just says "can't mount file"

Also trying to connect a mobile phone over Bluetooth but kmobiletools is not intuitive. How am I supposed to know what /dev/xx it's on?

Thanks for your help and sorry that I'm very frustrated.

---

### Post by emuman on 2008-11-26
Same problem here. What device to use for usb or bluetooth connection?

---

### Post by damis648 on 2008-11-26
I am afraid I do not completely understand. What happens when you plug in the drive(s)? Can you access them from Place>[device name]?

---

### Post by Coreigh on 2008-11-26
Help us out here please:
- What Ubuntu are you using? Ubuntu, Kubuntu or Xubuntu?
- Which release number? 8.04? 8.10?
- What step have you tried?

the /dev letter only indicates which device it is "in line" for example first disk (device) sda, second sdb, third sdc, and so on. As damis648 says if you are logged in and the just plug in (and power on) the USB drive, and then open the places menu do any new items show up? On my Ubuntu 8.04 I actually get a new icon on the desktop when I plug in a USB drive. On the flip side do you get any errors when you plug in, or only errors if you try to manual mount?

---

### Post by starcannon on 2008-11-26
Being unable to mount the file system is not a common error for me; but it does occasionally happen. If these storage devices contain fat, ntfs, or other file systems that are prone to fragmentation, it may be a good idea to defrag the drives first, then give it another "plug-n-pray" go; if that does not resolve the issues, then some commands that may be useful are:
```

lsusb
lspci
sudo lshw
sudo fdisk -l

```One of those is sure to show /dev/xxx of your device.

Generally(i'm about to make a generalization, don't assume it to be a universal law) I have noticed that a usb storage device will show up on:
/dev/sdb
So lets say the usb storage device as 3 partitions, you would need to mount each partition, remember mount, mounts file systems NOT hardware; so you would mount say:
/dev/sdb1
/dev/sdb2
/dev/sdb3

Okay, so in our example we had 1 device with 3 partitions, you have 4 devices with at least 1 partition each, you would *likely* have a situation much like this:
/dev/sdb
/dev/sdc
/dev/sdd
/dev/sde
and of course you would have to mount the partitions on each device
/dev/sdb1
/dev/sdc1
/dev/sdd1
/dev/sde1
and so forth.

GL, don't get too frustrated, right now everything seems to take forever; but once you know what your doing, I think you will find that your system is more stable, and that you will get things done faster than you used to. Give yourself time to learn your Linux operating system, be sure to keep a windows box or partition up so that you can stay fully productive while your in the learning process, and in a matter of 8 to 12 weeks you may find that your asking for a guide to formatting and absorbing that old windows partition.

---

