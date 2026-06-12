---
title: "Wifi help"
date: 2010-11-01
forum: Hardware
---

### Post by Moldjelly on 2010-11-01
ok i have a Toshiba Satellite M505-S4940 and the wifi isnt working its on ubuntu 64bit and the wifi is a reltek card.If anyone can help me i would be happy to use ethernet and let them teamviewer the laptop

---

### Post by cipherboy_loc on 2010-11-01
Can you please post the output of lspci? lspci lists the devices connected to the motherboard, giving us the manufacturer, model, and type of the wifi card.

---

### Post by Moldjelly on 2010-11-01
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
02:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
02:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
02:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by TBABill on 2010-11-01
Please also post the output of ```
sudo lshw -C network
```

And which version of Ubuntu are you using? Did it work previously in the current version or in a prior version of Ubuntu?

---

### Post by Moldjelly on 2010-11-01
*-network DISABLED      
       description: Ethernet interface
       product: RTL8192E Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:d2:c4:55:71
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=rtl819xE latency=0 multicast=yes
       resources: irq:17 ioport:c800(size=256) memory:fdffc000-fdffffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:26:18:74:94:2f
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:e800(size=256) memory:fcfff000-fcffffff memory:fcfe0000-fcfeffff memory:febe0000-febfffff


and no it has not worked in any version of linux yet...and im using 10.10

---

### Post by ThatBum on 2010-11-01
I've heard that this card has problems with 64 bit. Go and make a 32 bit LiveCD and see if it works in live mode.

If you need 64 bit, then you might need ndiswrapper.

The Windows drivers for wireless device (Realtek RTL8192E) are [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=9&PFid=9&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8192E").

EDIT: I got the driver and took out the inf. Try using the attached inf with ndiswrapper.

---

### Post by Moldjelly on 2010-11-02
It says invailded driver

---

### Post by ThatBum on 2010-11-02
[COLOR=Red]Okay...the one I got from the zip was the 64 bit Windows 7 driver. Maybe ndiswrapper doesn't like the 7 one. Go try the download the Vista/XP one from the link in my last post, there's 5 infs to try there, for XP/Vista 32 and 64 bit, and Windows 2000, for some reason. 

If it still doesn't work, try a LiveCD of 32-bit Ubuntu and see if it works.

There's a big huge thread about this adapter [here]("http://ubuntuforums.org/showthread.php?t=1239342&highlight=RTL8192E").[/COLOR]

This is moot. I found there's a stock kernel module for this card.

Run "sudo modprobe r8192e_pci" and see if your wireless works in Network Manager.

If it does, make it autostart with boot by putting the module name (r8192e_pci) in /etc/modules.

The module is actually located in /lib/modules/2.6.35-23-generic/kernel/drivers/staging/rtl8192e/r8192e_pci.ko, a standard place for a kernel module. Why isn't this module auto-modprobe'd for people with this card?

EDIT: It occurred to me that I have 32 bit, and you might not have this module in 64 bit. Hm...

---

### Post by Moldjelly on 2010-11-02
Ok it works in 32 bit ubuntu

Thanks for everyone who helped =)

---

