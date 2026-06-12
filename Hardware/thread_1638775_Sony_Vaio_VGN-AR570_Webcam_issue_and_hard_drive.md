---
title: "Sony Vaio VGN-AR570 Webcam issue and hard drive"
date: 2010-12-06
forum: Hardware
---

### Post by Sphoneix on 2010-12-06
Hey all,

I am new to Ubuntu, I recently switched from Windows. I have two questions pertaining to my hardware. The first has to do with the webcam. It won't work. I believe this is the info for it (from hwinfo)

49: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_5ca_1839_noserial_if0
  Unique ID: cLrx.kDtW1p6CMlF
  Parent ID: k4bc.cO89g+iefn1
  SysFS ID: /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0
  SysFS BusID: 1-2:1.0
  Hardware Class: unknown
  Model: "Ricoh Unclassified device"
  Hotplug: USB
  Vendor: usb 0x05ca "Ricoh Co., Ltd"
  Device: usb 0x1839 
  Revision: "1.00"
  Speed: 480 Mbps
  Module Alias: "usb:v05CAp1839d0100dcEFdsc02dp01ic0Eisc01ip00"
  Driver Info #0:
    Driver Status: uvcvideo is active
    Driver Activation Cmd: "modprobe uvcvideo"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #42 (Hub)
.
.
. 
 
I looked at other threads and tried installing the kernels and all that but kept getting an error for the make and make install commands. Here is My code in terminal...

owner@owner-VGN-AR570E:~$ cd r5u870
owner@owner-VGN-AR570E:~/r5u870$ make
make -C /lib/modules/2.6.35-23-generic/build M=/home/owner/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /home/owner/r5u870/r5u870_md.o
In file included from /home/owner/r5u870/r5u870_md.c:55:
/home/owner/r5u870/usbcam.h:36: fatal error: media/video-buf.h: No such file or directory
compilation terminated.
make[2]: *** [/home/owner/r5u870/r5u870_md.o] Error 1
make[1]: *** [_module_/home/owner/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [all] Error 2
owner@owner-VGN-AR570E:~/r5u870$ make install
make -C /lib/modules/2.6.35-23-generic/build M=/home/owner/r5u870 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-23-generic'
  CC [M]  /home/owner/r5u870/r5u870_md.o
In file included from /home/owner/r5u870/r5u870_md.c:55:
/home/owner/r5u870/usbcam.h:36: fatal error: media/video-buf.h: No such file or directory
compilation terminated.
make[2]: *** [/home/owner/r5u870/r5u870_md.o] Error 1
make[1]: *** [_module_/home/owner/r5u870] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [all] Error 2

Any ideas what I'm doing wrong?

Also, when I installed Ubuntu I rushed through it a little bit and believe I did something wrong with the partitioning. I had a raid configuration that was set up on Vista with my two 100gb drives. But when I installed Ubuntu I somehow ended up partitioning it in a way where only one of the drives is being used. In the system > disk utility it shows both drives. One of them looks correct it shows
Usage = Filesystem
partition type = linux (0x83)
partition flags = bootable
type = ext4(version 1.0)
label = -
Device = /dev/sdb1
partition label = -
Capacity = 96GB
Available = -
Mount Point at /

The other however shows this...

Usage -
partition type = linux (0x83)
Partition flags = -
Device = /dev/sda1
Partition label = -
Capacity = 192GB

Sorry for the long post. Any help would be much appreciated.

---

### Post by Sphoneix on 2010-12-17
bump

---

