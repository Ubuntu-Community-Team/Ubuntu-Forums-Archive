---
title: "Port 1394 not detected"
date: 2016-09-17
forum: Hardware
---

### Post by Jorhel on 2016-09-17
Hi,
I'm trying to upload video material from a canon 850vi videocamera to my computer. the cable goes to the Port 1394 but when I plug it in nothing happen.
Meaning the device does not appear in the lift pane of the file manager like other devices plugged through USB port do.
It does not get detected as a camera by the digikam application either (that might be normal since it's video...)
I also installed Openshot video editor but it does not find it either. a bit of reading made me think the maybe something is missing in the kernel installation 
Command lspci return```
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0a.0 Communication controller: LSI Corporation V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB controller: VIA Technologies, Inc. VT82xx/62xx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB controller: VIA Technologies, Inc. VT82xx/62xx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB controller: VIA Technologies, Inc. VT82xx/62xx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB controller: VIA Technologies, Inc. VT82xx/62xx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102/VT6103 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200 PRO] (Secondary) (rev 01)


```
the verbose version  for the firewire
```
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. A8V/A8N/P4P800/P5SD2 series motherboard
    Flags: bus master, medium devsel, latency 32, IRQ 19
    Memory at e6001000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at a800 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci


```
and lspci -k 
```
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
    Subsystem: ASUSTeK Computer Inc. A8V/A8N/P4P800/P5SD2 series motherboard
    Kernel driver in use: firewire_ohci


```

The access denied appear on every line so I imagine it is not relevant to the problem since USB ports and screen are working fine.

Could somebody shed some light?

thanks

---

### Post by Bucky Ball on 2016-09-17
I can't help, but I can add this: why are you bothering with what USB ports are doing and whether the camera appears like any other USB device in the file manager? You are using Firewire. No, the device will not pop up in a file manager. Different kettle of fish. Not related. 

So, for clarity, your Firewire device does not appear in your software apps when plugged in despite the fact the OS recognises it is there and appears to have the correct driver for Firewire. It is appearing everywhere else as it should so would start looking for why it's not showing up in your software apps and forget digging around with USB. Good luck. :)

* Just a thought. What are you recording to on the camera? An SD card? If so, why not simply pull that and plop it in the computer and you're away. If you are using larger SD cards, you'll need to install exfat-fuse and exfat-utils for it to be recognised.

---

### Post by Jorhel on 2016-09-18
Thanks,
The camera is recording on a tape and you can't get them anymore not easily anyway so I want to "empty" them on the computer to be able to reuse them.
I just mentioned the USB because I though that would work the same way...

---

### Post by Bucky Ball on 2016-09-18
Hmm. Yes, I have a camera like that, a DV camera I think you might be talking about, small cassette like vid casing? Haven't used in ages but worked fine for me way back in 10.04! (Maybe even earlier.)

Haven't tried it in 16.04 because I get issues booting whenever I install the firewire card in my new desktop to plug the camera into it, so never got as far as the camera and software. I've been meaning to fiddle about with it again but been a bit busy. Might have a sniff this week, but as for your issue, not sure what's happening there unfortunately.

From memory, I was using Kdenlive? It's in the repos, also from memory ...

Good luck and if you have no further action on the thread in 12 hours from your last post, feel free to just post 'bump' in a post and that will get you back to the top of the list again.

---

### Post by grege2 on 2016-09-19
I have not done this in years but there are extra steps involving permissions.

You might not need all of this, but have a read

[https://help.ubuntu.com/community/HowToCaptureDigitalVideo](https://help.ubuntu.com/community/HowToCaptureDigitalVideo)

---

### Post by grege2 on 2016-09-19
And once it is working it works well. The captured video stream in Kino automatically identifies scene changes and creates a series of files that can then be used in a video editor like Openshot.

---

### Post by Bucky Ball on 2016-09-20
Depending on the camera, you should have access to the transport controls directly from Kino. I did when I was using mine about six or seven years ago.

A few point to keep in mind when you get this working: as you are transferring from DV, it is not like grabbing a file and drag/dropping it, as you probably know. DV won't work like that as it is linear media (not random access). For instance, if you want to see from timecode 1:00:05, you will need to FF or REW to get there. You can't pop in the timecode and you're there. The camera will have to physically manipulate the tape to get you to where you want to be.

You are going to want to view the footage on your computer directly with the camera being on and plugged in and preferably with transport (play, stop, FF, REW, etc.) controls available from the computer, cut the bits you want and archive them. 

You don't want the dross and off cuts (cutting room floor stuff). Waste of space and resources. Kino is perfect for rough cutting clips from raw footage and hopefully will recognise and give you access to the transport controls on your DV cam. If it doesn't, you will need to grab whole chunks rather than useable clips then cut them down once digitised (on the computer). 

Good luck.

---

### Post by Jorhel on 2016-09-20
Trying to install kino now getting a warning about untrusted package "curl kino"
```
~$ sudo apt-get install kino
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  curl
Suggested packages:
  vorbis-tools sox mjpegtools lame ffmpeg2theora
Recommended packages:
  ffmpeg
The following NEW packages will be installed
  curl kino
0 to upgrade, 2 to newly install, 0 to remove and 14 not to upgrade.
Need to get 4,142 kB of archives.
After this operation, 8,756 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
WARNING: The following packages cannot be authenticated!
  curl
Install these packages without verification? [y/N] N
E: Some packages could not be authenticated


```

Should I take the risk and type y?

---

### Post by Bucky Ball on 2016-09-21
Are you installing this directly from the official PPA and NOT via a third-party PPA you have manually added to your sources? If so, go ahead and install. If no, remove the third-party PPA and install from the official repositories.

---

### Post by Jorhel on 2016-09-21
Thanks,
Once I got kino installed it detected the camera. So the problem wasn't the IEEE 1394 problem was having the right software to use it properly.

---

### Post by Bucky Ball on 2016-09-22
Great news and thanks for marking as solved. Enjoy. :)

---

