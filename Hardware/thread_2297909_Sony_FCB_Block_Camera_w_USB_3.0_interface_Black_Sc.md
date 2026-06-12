---
title: "Sony FCB Block Camera w/ USB 3.0 interface: Black Screen, No Video"
date: 2015-10-07
forum: Hardware
---

### Post by patrick_w3 on 2015-10-07
Hello forum gurus, 
 
I have been browsing the forums for some time now and have finally given in to creating an account. ):P

I am having some issues trying to get a SONY FCB-EV7300 block camera to work on my NVIDIA Jetson TK1 development board running Linux4Tegra (modified Ubuntu 14.04 LTS). I currently have the camera interfacing w/ an Aivion TL6035 USB 3.0 interface board (link: [http://aivion.de/files/tl_6035.pdf](http://aivion.de/files/tl_6035.pdf)) on both my Windows 10 64-bit system and modified Ubuntu 14.04 LTS system. My computer recognizes the camera module in Windows and DOES properly display output @ 1080P/30, but it does not work in Ubuntu. Below you will find my testing procedure and results. I would gladly appreciate it if anybody has an insight towards a solution to my problem.
 
============= Windows 10 64-bit OS =============

 
**The steps I followed to initialize the camera: **
-Check SW 1-2 ON and SW2-4 ON
-Plug in 5V external power from a large PSU (ample power) to the Aivion TL6035
-Plug in USB3 plug into isolated USB 3.0 port on my computer (No hub)
-Start up Sony FCB Control Software, Run Address Set Command, Run IF_Clear Command
-Check Register 74 (LVDS Mode) and make 00 (Single)
-Check Register 73 (Output Mode) and make 02 (Digital Output Enabled)
-Check Register 72 (Monitoring Mode) and make 07 [Full HD 30P (1920x1080P/30fps)]
-Power Cycle camera On/Off
-then look for video out using VLC and Windows Cam software.
 
In VLC, I was able to only get the first frame of the video out with the audio option selected. When the "audio" option was left empty, I was able to get slightly laggy but full 30fps 1080P video.
 
In Windows Cam software (native), the camera worked perfectly fine: no lag, FULL HD, no setup.  
 
============= Ubuntu 14.04 LTS ===============
 
Then when I try to run the EV7300 on my modified Ubuntu 14.04 LTS (Trusty Tahr/Linux4Tegra) ARM-embedded OS (armhf) Jetson TK1 Development Board, I get the following output from terminal: 
 
ubuntu@tegra-ubuntu:~$ lsusb
**Bus 002 Device 013: ID 04b4:01fc Cypress Semiconductor Corp.** (<-- *this is the interface board*) 
Bus 002 Device 012: ID 05e3:0616 Genesys Logic, Inc. 
Bus 002 Device 011: ID 05e3:0616 Genesys Logic, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 005: ID 046d:c077 Logitech, Inc. 
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ubuntu@tegra-ubuntu:~$ dmesg | grep video*
[    8.692945] usbcore: registered new interface driver uvcvideo
[   15.290126] uvcvideo: Found UVC 1.10 device Aivion-603-IF (04b4:01fc)
[  304.028861] uvcvideo: Found UVC 1.10 device Aivion-603-IF (04b4:01fc)
[ 1160.792109] uvcvideo: Found UVC 1.10 device Aivion-603-IF (04b4:01fc)
[ 1203.163564] uvcvideo: Found UVC 1.10 device Aivion-603-IF (04b4:01fc)

So we know that the system recognizes the AIVION Interface module for the EV7300.
 
Settings: USB 3.0 enabled, USB autosuspend OFF
Tried (*listed in degree of success*): guvcview, luvcview, vlc, cheese, wxcam, webcam
 
**Attached you will find a text file containing the output of my terminal command: [B][U][I]sudo guvcview --verbose

[/I][/U][/B][ATTACH]264846[/ATTACH]
 
With every program I run, I am able to get the first frame from the camera sporadically (seems like every few times I try). I believe there is some driver issue with a blocking call that won't allow the OS to grab any further video data. I may be wrong but am unable to progress past this stage in development.

---

