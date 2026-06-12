---
title: "Ubuntu and wireless on my laptop..."
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by thestratocaster on 2007-10-15
Hi there,

I hope this is in the right area.  I am new to Linux/ubuntu so please go easy on me with jagon/terms. :)

I  have just installed on my laptop (Compaq Presario v2000) Ubuntu 7.04.  I have installed all the latest updates etc.

Previously I had Microsoft Windows XP Home edition installed on it, and I connected to my home network via wireless, with no problems.  The little blue light above the keyboard would turn on when I was connected wirelessly.  Now I am using ubuntu I am having difficulty getting the wireless to connect.

Can anyone please help me?

Thanks :guitar:

TheStratocaster

---

### Post by EngDrewman on 2007-10-15
what model of wifi card do you have? If you don't know, there may be a label on the underside of your laptop that should contain that information. If you can't find that label, then at the terminal type ```
sudo lspci
``` and post the result here

---

### Post by thestratocaster on 2007-10-15
Hi Thanks for your quick reply! Here is the information you requested:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

cheers!

---

### Post by cudaman73 on 2007-10-16
You've got a broadcom chipset.

Those, unfortunately, don't work out of the box with Ubuntu.

There is, however, a solution.

Try working through:

[http://ubuntuforums.org/showthread.php?t=197102&highlight=BCM4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=BCM4318)

And lemme know how that goes. I'd go for option 2 (It's what I do on my laptop, it has a Broadcom Chipset as well). You do get a full 54 mbps connection, which is important.

---

### Post by EngDrewman on 2007-10-16
ah you have the Broadcom 4318- the same card I have. Unfortunately the 4318 is one of the few Broadcom cards that the native broadcom linux driver does not support, but the the kernel still tries to load the bcm43xx driver anyway. To get Linux to stop loading that driver, type ```
sudo gedit /etc/modprobe.d/blacklist
``` and add ```
blacklist bcm43xx
``` to the end of the file. Save the file and reboot your computer.

Now, because there is no native linux driver for your card, you will have to use your windows driver with a utility called ndiswrapper to get it to work. So at the terminal type ```
sudo apt-get install ndiswrapper-utils-1.9
``` to install ndiswrapper. (Note to anyone else that might be reading this at a future date- eventually ndiswrapper will advance to a new version and the line of code above will no longer work. Search synaptic for ndiswrapper and install it that way).

Once you have ndiswrapper installed, locate your windows driver and put it in a convenient location such as your home folder (you won't have to keep it there when ur done). The two files you will need are bcmwl5.inf and bcmwl5.sys. Now, at the terminal, type ```
sudo ndiswrapper -i bcmwl5.inf
``` assuming you put the driver files in your home folder. If you put them somewhere else, change bcmwl5.inf in the line above to the path to the driver. To verify the installation worked, type ```
sudo ndiswrapper -l
``` It should say "Driver present, hardware present." If it did, then type```
sudo modprobe ndiswrapper
``` to bring your wireless card to life. If it did not, post the error message.

---

