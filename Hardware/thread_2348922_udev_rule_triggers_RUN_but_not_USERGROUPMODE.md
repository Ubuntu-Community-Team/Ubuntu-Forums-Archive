---
title: "udev rule triggers RUN but not USER/GROUP/MODE"
date: 2017-01-09
forum: Hardware
---

### Post by schmidtbag on 2017-01-09
I have been trying to set up certain devices to be accessible only to one specific user (for example, a flash drive, a mouse, or a Bluetooth dongle) while inaccessible to other users. I've been trying to do this using udev rules. Even though the rules appear to trigger, there doesn't seem to be any change in the results. Here is an example that I've been trying to use:
```
SUBSYSTEMS=="usb", ATTRS{idVendor}=="04b3", GROUP:="user2", OWNER:="user2", MODE="0660"
```
If I use something like "RUN+=", that does in fact trigger, but the USB device is still usable to everyone and I don't know how to prevent that. Using "udevadm control --reload-rules" hasn't changed anything.  Unplugging and re-plugging the device doesn't change anything either.

---

### Post by pdc on 2017-01-10
for me, this is a really complicated area; I keep meaning to attempt to set up assigned IDs for my 2 printers:

I had saved some references: [http://wirespeed.xs4all.nl/mediawiki/index.php/Figuring_out_udev_rules](http://wirespeed.xs4all.nl/mediawiki/index.php/Figuring_out_udev_rules) has a lot in it: is there anything of use there?

---

### Post by zhangweiwu on 2017-01-10
You mapped to USB the USB device itself, not the device that is connected with USB, since one USB product with one vender + one ID can have multiple devices under it - e.g. my N700 mouse (with a Windows key on it) has both /dev/mouse7(mouse) and /dev/event7 (a keyboard), two devices under one USB device.

You need to map to the underlining device. For example, a usb flash drive should look like this:

```
SUBSYSTEM=="block", ATTRS{idVendor}=="090c", GROUP:="weiwu"
```

Note that the subsystem is block, not usb.

There are 100 types of "udev rules not working", can you kindly change your subject to something like "udev rule triggers RUN but not USER/GROUP/MODE", for future Google searchers?

To find out the right subsystem, do this on the device you desire. e.g. for a usb flash drive:

```

$ udevadm info /dev/sdb
P: /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/host3/target3:0:0/3:0:0:0/block/sdb
N: sdb
S: disk/by-id/usb-090c___B1605011200075-0:0
S: disk/by-path/pci-0000:00:14.0-usb-0:1:1.0-scsi-0:0:0:0
S: jl
E: DEVLINKS=/dev/disk/by-id/usb-090c___B1605011200075-0:0 /dev/disk/by-path/pci-0000:00:14.0-usb-0:1:1.0-scsi-0:0:0:0 /dev/jl
E: DEVNAME=/dev/sdb
E: DEVPATH=/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/host3/target3:0:0/3:0:0:0/block/sdb
E: DEVTYPE=disk
E: ID_BUS=usb
E: ID_INSTANCE=0:0
E: ID_MODEL=_
E: ID_MODEL_ENC=\x7f
E: ID_MODEL_ID=1000
E: ID_PART_TABLE_TYPE=dos
E: ID_PART_TABLE_UUID=051a726b
E: ID_PATH=pci-0000:00:14.0-usb-0:1:1.0-scsi-0:0:0:0
E: ID_PATH_TAG=pci-0000_00_14_0-usb-0_1_1_0-scsi-0_0_0_0
E: ID_REVISION=1100
E: ID_SERIAL=090c___B1605011200075-0:0
E: ID_SERIAL_SHORT=B1605011200075
E: ID_TYPE=disk
E: ID_USB_DRIVER=usb-storage
E: ID_USB_INTERFACES=:080650:
E: ID_USB_INTERFACE_NUM=00
E: ID_VENDOR=090c
E: ID_VENDOR_ENC=090c
E: ID_VENDOR_ID=090c
E: MAJOR=8
E: MINOR=16
E: SUBSYSTEM=block
E: TAGS=:systemd:
E: USEC_INITIALIZED=14318510816

```

---

### Post by schmidtbag on 2017-01-11
I fixed the post title.

Changing the "SUBSYSTEM" didn't help.  Whether I use a flash drive (SUBSYSTEM="block") or a USB mouse (SUBSYSTEM="input") I'm still able to access the devices with other users, even when unplugging them, plugging them back in, and reloading the rules.

---

### Post by zhangweiwu on 2017-01-12
It works for me. Evidence:
```

weiwu@weiwu-HP-EliteBook-840-G2:/etc/udev/rules.d$ cat flash_drive.rules
SUBSYSTEM=="block", ATTRS{idVendor}=="090c", OWNER:="weiwu", GROUP:="weiwu", MODE="0660", SYMLINK+="boot_usb"
weiwu@weiwu-HP-EliteBook-840-G2:/etc/udev/rules.d$ ls -lh /dev/boot_usb 
lrwxrwxrwx 1 root root 4 Jan 13 09:49 /dev/boot_usb -> sdb1
weiwu@weiwu-HP-EliteBook-840-G2:/etc/udev/rules.d$ ls -lh /dev/sdb1
brw-rw---- 1 weiwu weiwu 8, 17 Jan 13 09:49 /dev/sdb1

```

Also, permission of accessing the device is different than permission accessing the device's files, in the case of USB flash drive. It was designed in a strange way - to my knowledge, mounting was not done by a root-previlliaged mount service on behalf of a user - it is done as root itself. This configuration only changes the permission on the device, not the permission parameters used to mount it.

Also, in the case of mice, they are probably connected to X11 through a special user - perhaps root - despite who is currently logged in. Root have access to everything.

---

### Post by schmidtbag on 2017-01-13
Yeah, I had a feeling the mouse is controlled by root since X11 itself is.

I used ls to check the permissions of my drive and it does appear the udev rules are in fact working.  Just kind of weird that it doesn't seem to actually do anything - I'm still able to load the flash drive as a different user.

Oh well, I guess you did your part.  Thanks for the help anyway.

---

