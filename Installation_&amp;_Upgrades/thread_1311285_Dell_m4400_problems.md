---
title: "Dell m4400 problems"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Trevor Johnston on 2009-11-02
So I tried to install 9.10 on my Dell precision m4400 but it didn't go down as planed. When I did boot from CD, it showed the restricted drivers that I should install to connect to the Internet and use my graphics card. But when I did a full install nothing came up and I couldn't connect to the internet or search for wireless networks. Fixable?

---

### Post by Trevor Johnston on 2009-11-02
No one wants to help a Dell...T.T

---

### Post by encompass on 2009-11-11
I love dell.
Could you tell some more inforamtion about your Dell M4400?
Do you know what wireless card it has and so forth.
Another helpful pointer is pasting the output of this command if possible.
lspci

---

### Post by cbxConus on 2009-11-17
Hei,

I just installed Ubuntu on my Dell m4400.
I never used Ubuntu before but would like to test and use it more in the future.

Have exactly the same problem as discribed above:
"I cannot switch my Wifi on or search for networks."
It seems that the Wifi driver is not installed.


My laptop data:

model: Dell M4400
processor: Intel(R) Core(TM)2 Duo CPU   T9400 @2.53GHz  2.54 GHz
memory (RAM): 4.00 GB
system type: 32-bit Operating System

opperating system: Ubuntu 9.10
network adapter: dell wireless 1510 Wireless-N Wlan minicard


If more data is required feel free to contact me...
Already much thanks for helping me out!


Regards,

cbxConus

---

### Post by encompass on 2009-11-17
if possible, could you give the output of this command from the program called terminal.
Click on applications... accessories... terminal...
and type...
lspci
copy all of that... and send it in as a response to this thread.

---

### Post by cbxConus on 2009-11-18
Sure it is possible, this is what comes out:

coen@coen-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G96M [Quadro FX 770M] (rev a1)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
03:01.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
coen@coen-laptop:~$ 

Thanks alot for the respons,

---

### Post by cbxConus on 2009-11-19
I fixed it!!!

Very strange but after a while it seemed that I couldn't install any thing on Ubuntu. I reinstalled Ubuntu and than I was able to install software such as Flash for Mozilla Firefox etc.

I tried the Hardware Driver installer of Ubuntu and it showed the link to install my Wifi-Driver, but after the first install (before reinstall) I wasn't able to see that link. So probably something went wrong during install.

Thanks a lot for the help though,
I'm looking forward to test Ubuntu and hopefully switch to Ubuntu and Wine combination to do my every day work.

The only software that I'm missing is a free 3D cad application that is more dimension stable as Blender. A replacement for Solid works would do the trick... any one a tip???

Thanks alot for the help!

---

### Post by tkoopa on 2010-03-01
On another note, I had a lot with CPU scaling on my m4400.
I tried all sorts of tweaks within Ubuntu + disabled speedstep but nothing seemed to work, after a few hours of work it would always slow down to a creep and the CPU scaling applet would not let me go above 800Mhz. I found out in the BIOS after rebooting just after a slowdown that the CPU had actually stepped down to 400Mhz.

Anyway I finally solved the issue permanently by updating the BIOS to version A19 off the Dell website (was on A11). Apparently they have updated the thermal table and the medium speed setting for the CPU fan, so I strongly recommend this.

---

### Post by encompass on 2010-03-01
Cool, thanks for the heads up.

---

### Post by tkoopa on 2011-08-27
My m4400 was still overheating from time to time. I ended up buying a laptop stand with fans for extra ventilation, that completely solved the problem.

---

