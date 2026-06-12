---
title: "HP Pavillion dv9000 webcam"
date: 2009-08-30
forum: Hardware
---

### Post by dan724 on 2009-08-30
Hello all, I recently installed ubuntu 9.04 on my HP Pavillion dv9000. This laptop uses an amd64 processor. This laptop comes with a built in webcam above the screen. I have not been able to get this webcam to work. I believe I am missing kernel drivers for it (correct me if I'm wrong). The file "/dev/video0" does not exist. I have loaded the kernel modules v4l2_int_device, v4l2_common, v4l1_compat, uvcvideo, and videodev. I have tried using aMSN, Ekiga, Camorama and Cheese to access the webcam. None of them see the webcam. I have found the following drivers: [http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/](http://download.tuxfamily.org/arakhne/pool/r/ricoh-webcam-r5u870/) however those are for an old kernel and I would really prefer not to downgrade my kernel just to get my webcam working. I'm also not even sure the deb packages there would work as they are for an i386 and this laptop is an amd64. Can anyone get my webcam working?

The following is the output of lsusb:
```
joel@joel-laptop:~$ lsusb
Bus 002 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:1810 Ricoh Co., Ltd 
joel@joel-laptop:~$
```and this is the output of lspci:
```
joel@joel-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
joel@joel-laptop:~$ 

```

---

### Post by sanad1995 on 2011-03-09
Same problem D:! Need solution!

---

### Post by ntzrmtthihu777 on 2012-05-28
Similar problem, same machine.

When I run guvcview sometimes the webcam doesn't activate. When from I run it from terminal and it doesnt work this is the output:
[FONT=Courier New]
anonymous@anonymous:~$ guvcview
guvcview 1.1.3
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
video device: /dev/video0 
/dev/video0 - device 1
Init. HP Webcam (location: usb-0000:00:04.1-2)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/24, 1/20, 1/15, 1/10, 1/5, 1/1, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/24, 1/20, 1/15, 1/10, 1/5, 1/1, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/24, 1/20, 1/15, 1/10, 1/5, 1/1, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/24, 1/20, 1/15, 1/10, 1/5, 1/1, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/24, 1/20, 1/15, 1/10, 1/5, 1/1, 
checking format: 1448695129
vid:04f2 
pid:b023 
driver:uvcvideo
VIDIOC_STREAMON - Unable to start capture: Cannot send after transport endpoint shutdown

[/FONT]Similar issue with cheese, but I never checked the terminal output (I switched from cheese to guvcview early on in the hope that it would fix this issue, plus cheese's video capture is very laggy, guvcview captures beautifully when the above problem doesn't occur)

Additionally, after the above failure, I tried again and got this error:

[FONT=Courier New]guvcview 1.1.3
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
video device: /dev/video0 
/dev/video1 - device 1
ERROR opening V4L interface: No such file or directory
Init video returned -1
Terminated.

[/FONT] And /dev/video0 does not exist, but /dev/video1 does?!?! whats going on?

---

### Post by mörgæs on 2012-05-29
Guvcview 1.1.3 is an old version, and many important bug fixes have been added. It also indicates that your Buntu version is old.

I suggest you begin with a fresh install of 12.04, which will (among other things) bring you Guvcview 1.5.3.

---

### Post by ntzrmtthihu777 on 2012-05-29
> **mörgæs said:**
> Guvcview 1.1.3 is an old version, and many important bug fixes have been added. It also indicates that your Buntu version is old.

I suggest you begin with a fresh install of 12.04, which will (among other things) bring you Guvcview 1.5.3.

Yeah, 10.04. I'm planning to upgrade. Could you offer some advice? My machine has a AMD Turion 64 X2, which I assume means it supports a 64 bit os. I currently have 2 gigs of memory, wish I could upgrade but all my research says a HP dv9000 max ram is 2 gigs. My understanding is that a 64 bit os allows a greater use of available ram, but that is still limited by the mobo. Is there a way around this in the latest ubuntu?

How would I upgrade? My optical drive don't work (planning on replacing it, but I'm on a budget, I live in a homeless shelter and work for their Labor Force temp service for $150/wk, plus room and board) and when I tried to install 10.04 via usb thru unetbootin it hung up after step 3 (keyboard layout/map/region). I ended up having to use a sata-to-usb adaptor and installing it from disk on another laptop (company). That was a pain and very tedious. Is there another way to do it?

Just for documentation:
I opened a file browser with gksudo nautilus and navigated to /dev/ and watched what happened as I repeatedly ran and closed guvcview. What I noticed was this:

Well! It refuses to work wrong when I want it to! I'd give specifics, but what happened is when the first error I posted happens a new file /dev/video1 is created, and between the two errors /dev/video0 disappears, resulting in the last error.

---

### Post by mörgæs on 2012-05-29
Try for example a 64 bit alternate ISO. There is no need for more memory.

Unetbootin is a great tool. Are you using the latest release?

---

### Post by ntzrmtthihu777 on 2012-05-29
Yes it is, it worked fine with lupu 5.2.8
I don't know how to check what version, its the one straight from the synaptics, when I ran guvcview from terminal it gave me the version, but unetbootin doesn't. How do I check?

---

### Post by mörgæs on 2012-05-29
If it has worked before then just give it a try with the alternate ISO.

---

### Post by ntzrmtthihu777 on 2012-05-31
If you rename /dev/video1 to /dev/video0 it will run a few times before it gets changed to /dev/video1 again.

---

### Post by ntzrmtthihu777 on 2012-06-04
Got a slightly better workaround, still treating the symptom and not the disease, but it works, mostly.

Create a blank document in your home folder named video1_fixer.sh (you can name it something else, but make sure the change is consistent) and paste this into it:

[FONT=Courier New]#!/bin/bash

echo `sudo rename s/1/0/g /dev/video1`
echo `guvcview`[/FONT] 

Save it and make it executable. (you can use cheese or whatever too, I just use guvcview because it works better on my machine)

Create a file named Guvcview_fixed.desktop in /usr/share/applications and paste this into it (again, rename as you please, just be consistent):

[FONT=Courier New][Desktop Entry]
Type=Application
Terminal=true
Icon=/usr/share/pixmaps/guvcview/camera.png
Name=Guvcview_Fixed
Exec=/home/your_name/video1_fixer.sh
Name=Guvcview_Fixed
Name[en_US]=Guvcview_Fixed

[/FONT] (You can use a different icon too, this is just my setup)

Drag the resulting Launcher to the task-bar for quick access. This renames /dev/video1 to /dev/video0 and then launches guvcview, but you need to give it your password in terminal.

I'm going to work on this and polish it untill it works smoother. Hopefully I'll learn more to treat the underlying cause directly.

---

