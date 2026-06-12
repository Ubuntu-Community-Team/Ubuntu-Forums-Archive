---
title: "HP Mini 110 Series Experience"
date: 2012-05-27
forum: Hardware
---

### Post by Josemr on 2012-05-27
Hello to all Ubuntu Community and Staff, I just want to share my experience with a Netbook and how the hardware was detected and managed by two popular Linux distros. My Netbook is the HP Mini 110-3530NR to be more specific and i'm currently using Ubuntu 12.04 LTS on it:), after tried few distros I opted for Ubuntu because is almost packed with essentials apps and the Ubuntu software center is awesome just search your favorite app and just click install with no commands hassles, and trying or figuring how to install an app, <- I know I sounded kinda lazy here but a centralized software center with install support is awesome :wink:
Well the only disappointments with Ubuntu under my Netbook is that I can't transfer my pictures from my Camera's SD Card to my Netbook, [COLOR=darkred]however my built-in Flash Reader is not even detected by the System(Fixed, notes at bottom),[/COLOR] and I had to buy an USB to SD Card Reader and fortunately worked on the fly, [COLOR=darkred]and the Graphics are still in unknow status even with the system up to date, but detected by the system(Fixed with mesa-utils), [/COLOR]
 
Finally there is the lspci and lsusb output from my HP Mini Netbook:
 
======================================================================
HP Mini 110-3530NR Netbook (Ubuntu 12.04 LTS)
======================================================================
Ubuntu 12.04 LTS lspci Output:
jose@Jose-HP:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
jose@Jose-HP:~$ 
======================================================================
Ubuntu 12.04 LTS lsusb Output:
jose@Jose-HP:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 5986:0314 Acer, Inc 
jose@Jose-HP:~$ 
======================================================================
Ubuntu Additional Notes:
[COLOR=darkred]Graphics: Unknown, Experience: Standard(Fixed with mesa-utils) Now: Graphics: Intel(r) IGD x86/MMX/SSE2, Experience: Standard[/COLOR]
[COLOR=darkred]Broadcom BCM43xx WiFi works right out of box (Live or Installed), but the WiFi status Led remained in Off (orange) but WiFi connection was established, after full system update the WiFi status Led (Off=orange, On=white) started working properly. I figure that after the full system Update the Broadcom STA Wireles Driver has been Updated\Installed.[/COLOR]
USB Flash Reader undetected by the system(addiotional notes at bottom)
End
======================================================================
 
======================================================================
HP Mini 110-3530NR Netbook (Fedora 16)
======================================================================
Fedora 16 lspci Output:
[liveuser@localhost ~]$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
[liveuser@localhost ~]$ 
======================================================================
Fedora 16 lsusb Output:
[liveuser@localhost ~]$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 125f:0000 A-DATA Technology Co., Ltd. 
Bus 001 Device 003: ID 5986:0314 Acer, Inc 
Bus 001 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
[liveuser@localhost ~]$ 
======================================================================
Fedora Additional Notes:
Graphics: Intel® IGD, Experience: Standard
[COLOR=darkred]Broadcom BCM43xx not prompted for install under Live but detected by the system, later Fedora was installed, driver not prompted for install, WiFi not working(Fixed with Kmod-wl)[/COLOR]
USB Flash Reader detected by the system and working.
End
======================================================================
 
I'm quite happy with my Ubuntu setup and I hope they will continue discovering and supporting the undetected hardware from legacy to recent, also including and prompting for install proprietary communication\connectivity drivers is a must nowadays, as for my personal opinion I like to get all my builtin hardware working after installing an Operating System, but ofcourse connectivity is the priority for install updates, and other drivers manually when needed.
 
Regards! and I'm sorry for my English ):P
Jose (PR)
 
======================
I suddenly noticed that the Flash Reader was having detection issues and worked sometimes and the system are in its 100% integrity, apparently this built-in Alcor Micro Flash Reader activates when the card is hardly inserted, so I figured is a hardware issue and yes it was a hardware issue, so I carefully cleaned every the contacts and checked every solder joints and fixed the weak ones on the internal Flash Reader, now the Flash Reader Activates instantly :D

---

### Post by GugaBFigueiredo on 2012-06-07
Hey there Josemr

So hear my situation and see if u can help me.

I recently got a HP Mini 110-1125Nr with windows7 basic on it... 
And i decided it would be better to run it with ubuntu. So i proceeded to make a live usb installer so i could put it in my netbook.

During installation i chose to erase all partitions and keep only ubuntu on it. Installation went fine, until it asked me to reboot the netbook.
I took out the flash-drive and restarted the netbook to a black screen with a blinking line.

I tried than to restart the netbook with the flashdrive plugged in, and it worked, only my built-in wireless wouldnt work, so i couldnt get all updates and drives, which aparently i need in order to use the wireless in the first place.

So now i have this netbook that will only boot with the flashdrive plugged in and no wireless... since u've been able of properly installing it on your machine... could u tell me where did i go wrong... and what can i do to solve this?

---

### Post by GugaBFigueiredo on 2012-06-08
Just thought I should add..

I've already tried to reinstall ubuntu on the netbook twice, with no success.
Even remade the live sub device once.
Thought of trying different versions of linux... like Lubuntu, Xubunt, etc.

---

### Post by Josemr on 2012-06-20
Hi there. I'm sorry for my late response, I can further help you on on setup your wireless issue, just post the output from the following command "lspci" to determine what is the wireles nic installed on your HP Mini.

```
lspci
```

---

### Post by jaswic on 2012-09-27
> **GugaBFigueiredo said:**
> Just thought I should add..

I've already tried to reinstall ubuntu on the netbook twice, with no success.
Even remade the live sub device once.
Thought of trying different versions of linux... like Lubuntu, Xubunt, etc.

I have had the same issue. I have an HP Mini 110 also. It used to have a 8GB SSD but it died. I replaced it with a 160GB hard drive that I had laying around. The HP mini will boot fine from the liveCD (on USB) but when reboot after install, all I get is black screen and on blinking "underscore"-like cursor.

I have tried Fedora and Ubuntu and both give the same symptom. I think it is related to the video driver after reading on a GRUB form. However, I don't know how to fix this issue.

Has any one figured this out?

---

