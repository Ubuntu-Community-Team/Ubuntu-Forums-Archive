---
title: "Ubuntu 10.04 LTS Proprietary Wireless Driver"
date: 2010-05-30
forum: Hardware
---

### Post by joebobthe13th on 2010-05-30
I installed Ubuntu 10.04 LTS, and everything was working perfectly after installing the proprietary wireless iInternet driver. However, after running the Update Manager, the driver wasn't working (under the wireless networks it said "Disconnected".) It was also no longer listed under the Hardware Drivers utility. Because I'm on a laptop, not having wireless internet is a rather large issue. How can I make the driver available to install once again?

---

### Post by efflandt on 2010-05-30
You have given us no clue what wireless device you have, or what driver you installed.  At least paste what **lspci** shows it is, if not the relevant part of **sudo lspci -v**.

---

### Post by joebobthe13th on 2010-05-30
Sorry, your absolutely right. Here is the full output of lspci:

"00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 10)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 01)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
03:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
03:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
03:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)"

---

### Post by joebobthe13th on 2010-05-31
Ok, I figured out a solution but I still haven't nailed down the source of the error. When I start up my computer I get 5 options in the boot menu:
Ubuntu, with Linux 2.6.32-22-Generic 
Ubuntu, with Linux 2.6.32-22-Generic with Recovery Mode
Ubuntu, with Linux 2.6.32-21-Generic 
Ubuntu, with Linux 2.6.32-21-Generic with Recovery Mode
Microsoft Windows XP Home Edition

When I run 2.6.32-21, I get the wireless working like normal, but when I run -22 it doesn't work. Other than that the two editions seem identical. So, what should I do? Should I delete -22 and -22 Recovery from my boot menu? If so, how? 

Furthermore, I'm not sure what to do about the thread. Should I close it and mark as solved, or move it to a different section?

Thanks in advance.

---

### Post by dino99 on 2010-05-31
kernel 32 is known to have some issues, you can try newer packages from this ppa:

[https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

try some packages: firmware-b43-installer wifi-radar, ndiswrapper-dkms

---

### Post by efflandt on 2010-05-31
Had you activated the Broadcom B43 wireless driver?  I have one Compaq laptop with similar hardware.

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Although, my wireless is slightly different Broadcom that seems to work  fine in 10.04 with either kernel.  Not sure if it matters, but I use **nomodeset** kernel boot parameter due to some issues I have had with other legacy ATI video, and I am now able to suspend in 10.04, which is something I was unable to do in 9.10.  Do you see any errors in dmesg about your wireless?

```
efflandt@efflandt-V2000:~$ dmesg | grep b43
[    1.756826] b43-pci-bridge 0000:05:02.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   18.845370] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   19.071945] Registered led device: b43-phy0::radio
[   19.680126] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   19.682534] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   19.687411] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   19.692477] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   19.812073] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

```You might open Synaptic and see if it still shows b43-fwcutter installed.  And under System > Preferences > Network Connections make sure that **Connect automatically** and **Available to all users** are checked for your wireless connection.

---

### Post by joebobthe13th on 2010-05-31
Dino99: I couldn't find any of the packages you recommended in the link you gave me.

efflandt: When I run dmesg | grepb43 on the Linux version that has internet, I get almost the same output as you do. However, when I run the command on the internetless side, I get nothing. When I run "sudo apt-get install b43-fwcutter" it says that the package is already install, but I don't know how to activate it. Under System > Preferences > Network Connections **Avaliable to All Users** was not checked, but doing so did not help.

---

