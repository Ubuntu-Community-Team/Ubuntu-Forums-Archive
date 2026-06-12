---
title: "Gateway W323 UI1 - installation/resolution help"
date: 2009-04-16
forum: Hardware
---

### Post by Joshkdmw on 2009-04-16
So, I'm trying to get 8.10 installed on a Gateway W323-UI1 laptop, and I've run into a problem:

The screen resolution. After system installation, the resolution automatically became set to 1600x1200. This would be fine, except it looks like a large portion of the screen is cut off - a large portion of the right and bottom of the screen. Everything that's showing looks just fine. I've tried resizing the screen to all the resolutions that are available to select. When I do, the screen becomes very jumbled and hard to see anything - like it's corrupted, or something.

Now, I couldn't see the box for selecting the resolutions, but I was able to use the command line to return it to 1600x1200, and it reverted to the state it was in before - readable, but cutting off some parts. I ran a full system update, hoping that some sort of patch would have fixed the problem. After \the updates were installed, I restarted - and the screen is very, very unuseable - corrupted, like before, but to a greater degree. I couldn't get the Terminal open. The problem persists upon a hard restart. I can still boot off of the live CD, so I can just reinstall if need be. But I'd still be dealing with this problem.

This probably matters:

When I go to the screen resolution settings, The monitor is listed as "Unknown", and the refresh rate is 0 Hz. When I hit "Detect Displays", nothing happens.

---

### Post by Joshkdmw on 2009-04-17
Also, I just tried running the laptop in safe graphics mode. This worked just fine - the whole scree was included, in full. This just seems weird to me - granted, I know very little of Linux in general.

---

### Post by GreenTaurus on 2009-05-01
I have this same laptop.  You must not be familiar with the UniChrome Pro video card in this laptop.

This site [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) has all the latest & greatest information, I use Ubuntu 9.04 (Jaunty Jackalope) and the following helps:

sudo nano /etc/X11/xorg.conf

             Section "Device"
                        Driver    "openchrome"
add this line ->        Option    "XaaNoImageWriteRect"
                        EndSection

Also, further down the page make sure you have

   Section "Device"
        Driver    "openchrome"
        Option    "SWCursor"    "true"
    EndSection

Make a backup, don't worry if you break it, and play around a bit, eventually you'll get it going, then make another backup of the xorg.conf :P

---

### Post by jjharr1 on 2009-08-10
I have the same laptop, but have been unable to locate compatible RAM.  Any suggestions.  I've only got 256Mb, so need to upgrade before ubuntu-ing it.

---

### Post by jeemar on 2009-08-18
GreenTaurus, 

I have the same laptop Gateway W323UI1 and have tried the above method you suggested. However, I still get the same problem. 

Here's a copy of my xorg.conf file that I've modified that doesn't work. 
.
.
.
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "openchrome"
    Option        "XaaNoImageWriteRect"
    Option        "SWCursor"         "true" 
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

-----
Here's the output after lspci: 

00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0c.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
00:0c.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
00:0c.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
00:0e.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)




I've also tried it with UseFBDev set to False. 
Still no luck. :(

---

### Post by JL32BiT on 2009-08-29
I'm also trying to get this laptop to work with Ubuntu and am having the same resolution troubles as the other users in this thread. I'm going to try editing xorg.conf tonight and I'll post what happens. Any other information as to why this is happening and what we can do to fix it would be appreciated.

---

