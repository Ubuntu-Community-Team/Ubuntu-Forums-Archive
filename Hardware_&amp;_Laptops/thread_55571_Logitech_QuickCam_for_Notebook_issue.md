---
title: "Logitech QuickCam for Notebook issue"
date: 2005-08-09
forum: Hardware &amp; Laptops
---

### Post by e.tonelli on 2005-08-09
Dear all,

I had an old version of QuickCam 3000 and all were ok (perfect video grabbed from Gnomeeting), but now, I've obtained a new Logitech QuickCam for Notebook and, using the pwc driver (both the 2.6.10-5-686 included and the custom compiled 10.0.7a), the hotplug loads only the audio driver and seems to not recognize and then initialize the video part (no video device detected, no /dev/video0 created!)....I'm becoming crazy !!!

I opened the pwc.c source file and I check the "quickcam for notebook" USB hex address [vendor code - product code]:the product code doen not correspond to my own camera (even if it is a Logitech QuickCam fo Notebook Pro), so I've changed the source using the hw usb hex address read from lsusb. Now, if I plug-in the camera the video device is detected but still NOT registered as /dev/video0.....

could you help me ?

This is the tail -f /var/log/messages outputafter the plug-in:

[I]Aug  9 19:38:11 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 2
Aug  9 19:38:14 localhost kernel: Linux video capture interface: v1.00
Aug  9 19:38:14 localhost usb.agent[8896]:      snd-usb-audio: loaded successfully
Aug  9 19:38:14 localhost usb.agent[8896]:      pwc: already loaded
Aug  9 19:38:14 localhost usb.agent[8896]:      audio: blacklisted
Aug  9 19:38:14 localhost usb.agent[8916]:      pwc: loaded successfully
Aug  9 19:38:14 localhost usb.agent[8924]:      pwc: loaded successfully
Aug  9 19:38:14 localhost kernel: pwc Philips webcam module version 10.0.7-unofficial loaded.
Aug  9 19:38:14 localhost kernel: pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
Aug  9 19:38:14 localhost kernel: pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
Aug  9 19:38:14 localhost kernel: pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
Aug  9 19:38:14 localhost kernel: pwc Trace options: 0x00a1
Aug  9 19:38:14 localhost kernel: usbcore: registered new driver snd-usb-audio
Aug  9 19:38:14 localhost kernel: usbcore: registered new driver Philips webcam[/I]




As you can see...no /dev/video0 created.


This is the output of lsusb instead:


[I]Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:08ae Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000[/I]


And finally the dmesg output:

[I]usb 2-1: new full speed USB device using uhci_hcd and address 2
Linux video capture interface: v1.00
pwc Philips webcam module version 10.0.7-unofficial loaded.
pwc Supports Philips PCA645/646, PCVC675/680/690, PCVC720[40]/730/740/750 & PCVC830/840.
pwc Also supports the Askey VC010, various Logitech Quickcams, Samsung MPC-C10 and MPC-C30,
pwc the Creative WebCam 5 & Pro Ex, SOTEC Afina Eye and Visionite VCS-UC300 and VCS-UM100.
pwc Trace options: 0x00a1
usbcore: registered new driver snd-usb-audio
usbcore: registered new driver Philips webcam
[/I]

Emilio

---

### Post by sciboy on 2005-08-19
I'm in the same boat as you are, I believe its just that the model we are using is unsupported under linux at the moment.

I gave the qc-usb drivers a try with no luck either.
Though the microphone on it works. =/

Anyway, i would appreciate any help i can get, cause i can't afford getting another camera.

---

### Post by sciboy on 2005-08-20
Hmmm, judging from the other devices that use the same drivers under Windows and Mac, i would think that we may have some luck with pwc and pwcx.

Pwcx may work, but i am unable to test it. =P

---

### Post by WishMaster on 2005-08-21
I have a Logitech QuickCam Zoom
I've written a HOW-TO -->
[http://users.pandora.be/Nyx/Linux/LogitechZoomUbuntu.htm](http://users.pandora.be/Nyx/Linux/LogitechZoomUbuntu.htm)

---

### Post by anil_robo on 2005-12-03
My problem: Webcam doesn't work

My webcam: Logitech quickcam webcam

lsusb output:

```
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 046d:08ae Logitech, Inc.
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

I can't program or compile, and can't make anything out of programming code. I can do some commandline if given explicit instructions. I'd really appreciate if anyone can tell me how to get the cam working! The cam is the only thing that's forcing me to keep windows! :(

---

### Post by anil_robo on 2005-12-10
:) Finally I got the webcam working! The guide is [here!]("http://ubuntuforums.org/showthread.php?t=75284&page=1&pp=10")

Thanks to Arnieboy! :)

---

### Post by gabrielsaldana on 2006-12-08
> **WishMaster said:**
> I have a Logitech QuickCam Zoom
I've written a HOW-TO -->
[http://users.pandora.be/Nyx/Linux/LogitechZoomUbuntu.htm](http://users.pandora.be/Nyx/Linux/LogitechZoomUbuntu.htm)

The link is broken. Can you post how you got the QuickCam Zoom working?

---

### Post by stephenb on 2006-12-31
The link works if you add an "l" to htm at the end of the supplied address, i.e. so you get LogitechZoomUbuntu.html

---

