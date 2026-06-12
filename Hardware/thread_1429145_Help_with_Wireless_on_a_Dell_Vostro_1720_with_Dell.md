---
title: "Help with Wireless on a Dell Vostro 1720 with Dell 1510 with Broadcom BCM4322 Chipset"
date: 2010-03-13
forum: Hardware
---

### Post by LordDelta on 2010-03-13
Greetings, Looking for some help with a wireless card.

I realize there are a number of Vostro threads around here, have looked at them none of them seemed to have been of any help. I did post my question on one of these threads previously, but perhaps due to the long nature of the thread it was not answered.

I would really appreciate the help.

As the title of this thread indicates, this is about a Dell Vostro 1720 laptop, ordered with a Dell 1510 Wireless 802.11 a/b/g/n wireless card using the Broadcom BCM4322 chipset.

According to this:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

I should be fine, with the exception that my card doesn't seem to exist, that is the controller seems to be there, but apparently it isn't there physically?

There is a switch on the side of the laptop for the wireless card, however I left it on from when it operated successfully in Windows 7.

It seems that my problem is the apparent lack of an interface, i.e. something named "wlan0" or similar, however I don't understand how to rectify this situation, nor whether the problem is this simple or not.

Following the troubleshooting manual, from section 4.1.1. PnP:

The output of sudo lshw -C network is:

```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:26:b9:9e:69:b9
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.8 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:32 ioport:4000(size=256) memory:fe004000-fe004fff(prefetchable) memory:fe000000-fe003fff(prefetchable) memory:fe020000-fe03ffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f6000000-f6003fff

```

As you can see the difference between my wired (which works) and wireless (which doesn't work) is two-fold, the wired has the "physical" capability whereas the wireless doesn't, and the wired also has a logical name, whereas the wireless doesn't.

Also, taken as a suggestion from a different the output of lspci -v for the Broadcom Controller:

```

0e:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Dell Device 000d
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f6000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 17-c4-0b-ff-ff-fe-f1-6b
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: wl
	Kernel modules: wl, ssb

```

This is with the B43 (fwcutter) driver installed, similar results are obtained with the Ubuntu-developper tested STA driver.

I am not that knowledgeable about this, I would love to learn though, and love even more to fix my issue.

Thanks!

---

### Post by LordDelta on 2010-03-13
I forgot to specify I asked the synaptic manager as of today to ensure all updates were applied to my system, I have Ubuntu 9.10 Karmic Koala installed.

And that this command:

sudo pccardctl ident

Does absolutely nothing, other than the prompt for my password.

---

### Post by Anniepoo on 2010-06-04
Did you find a solution to this? This post is from last march.

I'm having exactly the same problem on a fresh install of wubu on a vostro 1720.

I have wired connect, but no wireless.

The wireless power light is off. adapter switch is on, adapter runs fine under windows XP boot.
~$ sudo lshw -C network

  *-network
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f6000000-f6003fff

---

### Post by Youresorock on 2010-06-18
I have the "Broadcom Corporation **BCM4322** 802.11a/b/g/n Wireless LAN Controller (rev 01)" hardware in my iMac 24" and it also doesn't work.

The Hardware Drivers app shows the Broadcom B43 driver installed and in use, but it doesn't create a wlan0 to use.

10.04 x64

---

### Post by Bucky Ball on 2010-06-18
There should be no problem with this card. Broadcom is now well supported. B43 is correct. Make sure you have a cable in and:

System->Administration->Update Manager. Then ...

System->Administration->Hardware Drivers. Anything disabled in there?

In a terminal, paste these two commands one after the other, return in between:

```
ifconfig
iwconfig
```... and post the results of both.

If you are using Network Manager, make sure your details match your router (ESSID, security key and type).

---

