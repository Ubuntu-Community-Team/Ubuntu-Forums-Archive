---
title: "configure digital microscope in ubuntu"
date: 2017-12-01
forum: Hardware
---

### Post by spiridonios on 2017-12-01
Hello,

I obtained a digital microscope [ATTACH=CONFIG]277705[/ATTACH] and i try to make it work on my ubuntu studio computer. Didn't manage to do it till now, so any help would be appreciated.

I run ubuntu studio 16.04.3 LTS

Plugging the microscope in a usb port, makes it's led light to light on. No device is recognised through GUI though.

typing in terminal: lsusb i get

Bus 002 Device 009: ID a16f:0304  
Bus 002 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 003: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 03f0:1604 Hewlett-Packard DeskJet 940c
Bus 005 Device 002: ID 2109:0811 VIA Labs, Inc. Hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04fc:0801 Sunplus Technology Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

By unconnecting the microscope's usb cable and running the same command i understand that it is the Device a16f:0304
No description after the Vendor and product ids.

"sudo lshw | less"           gives me

*-usb:1
                         description: Video
                         product: USB2.0 UVC PC Camera
                         vendor: GenesysLogic Technology Co., Ltd.
                         physical id: 4
                         bus info: usb@2:1.6.4
                         version: 6.20
                         capabilities: usb-2.00
                         configuration: driver=uvcvideo maxpower=200mA speed=480

So the device is a UVC device. As suggested at [http://www.ideasonboard.org/uvc/faq/#faq1](http://www.ideasonboard.org/uvc/faq/#faq1), I had already run the command: 
lsusb -d 046d:08cb -v | grep "14 Video"

which gave me 

Couldn't open device, some information will be missing
      bFunctionClass         14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video
      bInterfaceClass        14 Video

I also found and run a command named "lsusb -v", which output a lot of info, but maybe it would be too much for a first post.

I understand that most likely some information is missing, but i can't say which. What i understood through my research is that 
it should work like any other UVC-compliant device and would be presented as video input in a program that is usually used with webcams. 
I tried with "cheese" and "guvcview", but no input is recognised. 

Any tip apreciated,

thanks

Spiros

---

### Post by mörgæs on 2017-12-02
A quick googling seems to indicate that the microscope is brand new, and as always with new hardware:

Have you tried how it works in a live boot of 17.10?

---

### Post by spiridonios on 2017-12-02
thanks for your reply morgaes,

I downloaded ubuntu studio and run it from a live dvd. Still i get the same results given by the above commands.
I installed it in windows in virtualbox just to see that i don't have faulty hardware, and it works ok in windows. 
So you suggest because of it being new hardware, it is not yet supported in ubuntu and there is not much i can do about it? 
Could you tell me what did you google and saw that it is new? I tried genesyslogic technology 6.20 and i found some data, but i didn't see anything imposing that it is newly manufactured.
I just saw some comments saying that they don't support linux. On the box of the product though, it says that the product works with linux..

---

### Post by mörgæs on 2017-12-02
> **spiridonios said:**
> 
I downloaded ubuntu studio and ran it from a live dvd. Still i get the same results given by the above commands.

Which release of Studio?

> **spiridonios said:**
> 
So you suggest because of it being new hardware, it is not yet supported in ubuntu and there is not much i can do about it? 

You can test a number of new distros / releases as mentioned above.

> **spiridonios said:**
> 
Could you tell me what did you google and saw that it is new?
I googled "a16f:0304". Gave only a few hits but they looked new to me.

> **spiridonios said:**
> 
On the box of the product though, it says that the product works with Linux
Not necessarily 16.04 but maybe something newer. You just have to keep testing.

---

### Post by spiridonios on 2017-12-03
Sorry i forgot to mention the version. I tried it with ubuntu studio 17.10.

I googled also a16f:0304 and came up to a [netherlands ubuntu forum]("https://forum.ubuntu-nl.org/index.php?topic=102544.0"). After some translation of the posts i saw that the author had opened vlc media player, clicked on video capture from the left menu, and he had the microscope recgnised as a microscope pc camera. I followed the same pattern and after a couple of vlc closing and restarting (trying to find out how it could maybe be recognised) i got picture from the microscope! Through vlc i was able to capture snapshots and videos. Then i closed vlc and tried again with "cheese" and "guvcview" and i had image in both of them! 

I have no idea what happened to actually make this time the microscope to get recognised, but it looks to work now. I also did a restart of my computer and i still have the microscope recognised. Magic! :)[ATTACH=CONFIG]277732[/ATTACH]

All this happened in ubuntu 16.04. I used the 17.10 as a live boot just for trial.

I mark the thread as solved, although i don't understand exactly how it got solved..

thanks again morgaes for your help!

---

### Post by kaefert66014235 on 2018-10-11
I think I have the same camera.

> [  +7,240936] usb 3-3: new high-speed USB device number 8 using xhci_hcd
[  +0,167317] usb 3-3: New USB device found, idVendor=a16f, idProduct=0304
[  +0,000004] usb 3-3: New USB device strings: Mfr=2, Product=3, SerialNumber=0
[  +0,000002] usb 3-3: Product: USB2.0 UVC PC Camera
[  +0,000002] usb 3-3: Manufacturer: GenesysLogic Technology Co., Ltd.
[  +0,046412] uvcvideo: Found UVC 1.00 device USB2.0 UVC PC Camera (a16f:0304)
[  +0,043517] uvcvideo 3-3:1.0: Entity type for entity Extension 2 was not initialized!
[  +0,000003] uvcvideo 3-3:1.0: Entity type for entity Extension 5 was not initialized!
[  +0,000001] uvcvideo 3-3:1.0: Entity type for entity Processing 3 was not initialized!
[  +0,000002] uvcvideo 3-3:1.0: Entity type for entity Camera 1 was not initialized!
[  +0,000145] input: USB2.0 UVC PC Camera: USB2.0 UV as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input27


And it works for me out of the box with
```
mpv /dev/video1
```
and also
```
vlc v4l2:///dev/video1
```

But when I try to use it with cheese or guvcview I get ton's of errors in dmesg those tools hang for 30 seconds and then the camera is regarded as disconnected.
> [  +3,363209] uvcvideo: Failed to query (GET_DEF) UVC control 11 on unit 3: -32 (exp. 1).
[  +0,221021] uvcvideo: Failed to query (GET_DEF) UVC control 11 on unit 3: -32 (exp. 1).
[  +0,067833] uvcvideo: Failed to set UVC probe control : -32 (exp. 26).
[  +5,041120] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
...
[  +5,120547] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
[  +0,512041] uvcvideo: Failed to query (GET_DEF) UVC control 11 on unit 3: -110 (exp. 1).
[  +5,120360] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
[  +5,117482] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
...
[  +5,119894] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
[  +5,119786] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
[  +5,119811] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
[  +2,343988] usb 3-3: USB disconnect, device number 5


The first time I connected and tried with cheese it worked, but then I searched for how to flip the image and I installed the package v4l-utils and ever since then (even though I uninstalled the package again) it will only work with vlc or mpv but none of the software that can control the webcam settings..

Anybody has any hint's for me how to get it working in cheese again?
Or maybe how to flip the image? This [https://help.ubuntu.com/community/Webcam/Troubleshooting#Picture_is_upside_down_or_mirrored](https://help.ubuntu.com/community/Webcam/Troubleshooting#Picture_is_upside_down_or_mirrored) says to use v4l2ucp but this doesn't give me a checkbox to flip..

---

