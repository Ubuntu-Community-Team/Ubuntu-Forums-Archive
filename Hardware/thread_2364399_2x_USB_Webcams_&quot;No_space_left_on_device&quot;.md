---
title: "2x USB Webcams &quot;No space left on device&quot;"
date: 2017-06-22
forum: Hardware
---

### Post by schmidtbag on 2017-06-22
I am working on a project involving 2 webcams, and no matter what application I use (ffmpeg, gstreamer, qv4l2, etc) I get some error regarding there not being enough space on the device (despite it being a webcam).  For example:
```
[video4linux2,v4l2 @ 0x5573a3e67580] ioctl(VIDIOC_STREAMON): No space left on device                                                                            
/dev/video2: No space left on device 
```
I heard of the trick to run "rmmod uvcvideo" and then run "modprobe uvcvideo quirks=128" but that didn't do anything.

I have tried lowering the webcams to 640x480 @ 5FPS with both MJPEG and YUYV outputs, and I still get the error.  That being said, I know for a fact there is enough bandwidth because these cameras can handle 1080p @ 30FPS.

If I plug both cameras into USB ports distinctly separate from each other, they will both work at the same time.  But there's a caveat to this situation: I'm planning on running these cameras on an ARM platform, where I don't have any spare USB ports to switch to.


Is there a way I can force this error to be ignored?

---

### Post by yancek on 2017-06-22
You posted the output but not what you did to get it.  Run some command from a terminal?

Video devices generally start with /dev/video0 so if you are using video2 that would generally mean a third device.  What does ls /dev/video* show?

---

### Post by ian-weisser on 2017-06-23
Please also show us the complete output of:
```
df
df -i
```

---

### Post by schmidtbag on 2017-06-23
@yancek
It doesn't matter what command I run, *all* of them ultimately say the same error.  But the one I quoted specifically was from ffmpeg.  The command itself I know for a fact is irrelevant.  The problem is that the USB controller is, in theory, overloaded.  However, I have heard how some Logitech webcams are known to grab all the USB bandwidth despite not all of it being used.  I don't know which models in particular do this, but I am using Logitech webcams.

@ian-weisser
This isn't a disk problem.  It's saying /dev/video2 is out of space, not my drives.

---

### Post by ian-weisser on 2017-06-23
We didn't say it was a disk problem.
df provides data for more than drives....

---

### Post by schmidtbag on 2017-06-23
Well when I run "df -i", I'm still only seeing disk info:
```
Filesystem            Inodes  IUsed     IFree IUse% Mounted on
dev                  2046397    481   2045916    1% /dev
run                  2056757    736   2056021    1% /run
/dev/sda4            2611200 261517   2349683   11% /
tmpfs                2056757     27   2056730    1% /dev/shm
tmpfs                2056757     15   2056742    1% /sys/fs/cgroup
//192.168.0.2/RAID  30523392  18289  30505103    1% /media/dull
tmpfs                2056757     22   2056735    1% /tmp
/dev/sda2           52890284 164314  52725970    1% /media/Windows
/dev/sdb1          294726624  78028 294648596    1% /media/Win_Games
/dev/sdb2                  0      0         0     - /media/Lin_Games
tmpfs                2056757     31   2056726    1% /run/user/1000
```

---

### Post by gsahli on 2017-06-24
Does this look helpful? (do you need to modprobe a specific driver?)
[http://www.linuxintro.org/wiki/Set_up_a_Webcam_with_Linux](http://www.linuxintro.org/wiki/Set_up_a_Webcam_with_Linux)

---

### Post by schmidtbag on 2017-06-25
Unfortunately, "uvcvideo" is the only driver associated with my webcam.  I don't have another driver to modprobe.

```
12: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: KRJj.u_Kc2Txp_Z7
  Parent ID: uIhY.2tQ6Pg4OXh2
  SysFS ID: /devices/pci0000:00/0000:00:07.1/0000:11:00.3/usb3/3-1/3-1:1.0
  SysFS BusID: 3-1:1.0
  Hardware Class: unknown
  Model: "Realtek USB Camera"
  Hotplug: USB
  Vendor: usb 0x0bda "Realtek Semiconductor Corp."
  Device: usb 0x57e8 "USB Camera"
  Revision: "0.07"
  Serial ID: "200901010001"
  Driver: "uvcvideo"
  Driver Modules: "uvcvideo"
  Device File: /dev/input/event8
  Device Files: /dev/input/event8, /dev/input/by-id/usb-Generic_USB_Camera_200901010001-event-if00, /dev/input/by-path/pci-0000:11:00.3-usb-0:1:1.0-event
  Device Number: char 13:72
  Speed: 480 Mbps
  Module Alias: "usb:v0BDAp57E8d0007dcEFdsc02dp01ic0Eisc01ip00in00"
  Driver Info #0:
    Driver Status: uvcvideo is active
    Driver Activation Cmd: "modprobe uvcvideo"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #7 (Hub)

```

---

### Post by schmidtbag on 2017-06-27
So here's something interesting...

I tried testing the webcams on a Haswell-based laptop.  Even without modprobbing uvcvideo, I was able to run both webcams at the same time, as long as I limited the framerate.  This is odd, because the official uvcvideo website says framerate is less likely to make a difference than resolution, where apparently for these cameras its the exact opposite.  When checking lsusb, both ports I used were from the same bus.

Apparently, not all USB ports are created equal.  Unfortunately that doesn't help me, because I'm expecting to use an ARM platform.  I'd rather not buy another device in the hopes that it will either have multiple USB busses, or, the internal hub will cooperate.  That's a bit of a gamble.

---

