---
title: "asus x556u no sound in ubuntu 16.04"
date: 2016-12-21
forum: Hardware
---

### Post by david-k42f on 2016-12-21
Hi all, I have installed ubuntu 16.04 on  an asus laptop model x556u and I'm having issues with the touchpad and sound, I have no sound from the speakers or earphones , also the touchpad is recognized as a PS2 mouse (but I have seen that there is allready a bug report about that).
Anyway , can anyone help with the sound issue?
Otherwise I'll be forced to install windows 10 and I really don't want to do that...

The laptop's hardware is as follows:[B]

CPU  [/B]Intel® Core? i5-7200U Processor, 3M Cache, 2.5 GHz up to 3.10 GHz 
 
**Memory  **8GB (1 x 8GB) DDR4 2133MHz OnBoard Memory, 1 x SO-DIMM socket for expansion up to 12 GB SDRAM 
 
**HD  **256GB SSD 
 
**Display  **15.6 Inch 16:9 HD (1366x768) LED Backlight 
 
**GPU  **Intel® HD Graphics 520 
 
**Optical Device  **8 x Super Multi Dual Layer 
 
**Webcam  **VGA Web Camera 
 
**Sound  **Built-in Speakers And Microphone SonicMaster  
**Network Card  **10/100/1000 Base T 
 **Wireless  **Yes, Integrated 802.11 b/g/n 
 
**Bluetooth  **Yes, Built-in Bluetooth? V4.0 
 
**External Ports  **1 x COMBO audio jack 
                1 x VGA port/Mini D-sub 15-pin for external monitor
                1 x USB 3.0 port(s) 
                1 x USB 2.0 port(s)
                1 x USB-C Gen 1 (up to 5 Gbps)
                1 x RJ45 LAN Jack for LAN insert 
                1 x HDMI 
 
**Card Reader  **Yes, 3 -in-1 card reader ( SD/ SDHC/ SDXC) 

Thank you for your time.
david

PS: I have checked the sound with a live session of ubuntu 16.04 booted through a usb key and the sound works... so weird why would it work in the live session and then in the installed ubuntu it won't??

---

### Post by david-k42f on 2016-12-22
Hi all, the problem is solved.
If you install ubuntu or any derivate of ubuntu in BIOS compatibility mode instead of UEFI mode it will cause hardware issues.
I installed again erasing all the disk a new installation of ubuntu 16.04.1 in UEFI mode and the sound works
david

---

