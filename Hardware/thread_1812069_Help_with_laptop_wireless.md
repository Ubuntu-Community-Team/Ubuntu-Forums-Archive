---
title: "Help with laptop wireless"
date: 2011-07-25
forum: Hardware
---

### Post by jcrobinson on 2011-07-25
I've reviewed several of the other people having problems with their laptop's built in Wifi, and none of their fixes seem to have helped, so hoping for some help of my own.
 
It shows "device not ready (firmware missing)
 
Going to Additional Drivers shows "Software Modem" as a propritary driver, and that it is currently installed and in-use.
I have also used ndisgtk ([http://jak-linux.org/projects/ndisgtk/](http://jak-linux.org/projects/ndisgtk/)) to install a .inf file for what SHOULD be the driver for this systems wireless device, from the manufacturer, and STILL no progress :-(
 
Also, it's a Compaq Presario V5000 serise.
 
Here is the output from the sudo lshw -C network command.
 
```
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: [EMAIL="pci@0000:06:02.0"]pci@0000:06:02.0[/EMAIL]
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: [EMAIL="pci@0000:06:06.0"]pci@0000:06:06.0[/EMAIL]
       logical name: eth0
       version: 10
       serial: 00:16:d4:3d:4e:15
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:14:a5:e3:6f:23
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-10-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```
 
Any help greatly appreciated, thanks!

---

### Post by jramshu on 2011-07-26
Are you using a USB card right now? The reason I ask is it shows a Broadcom device.
I don't see the vendor name or product name for the one that is disabled.

---

### Post by jcrobinson on 2011-07-27
Nope. USB Flash drive might have been plugged in when I ran that, but definatly not any USB wireless devices.
 
It's also worth mentioning; I have looked into the BIOS and the wireless is enabled on the motherboard, and I've tried using the physical switch on the laptop to no avail.

---

### Post by jramshu on 2011-07-28
> *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0200000-c0201fff

This is the wireless device then, Broadcom B43 series. I'm not sure what effects the ndiswrapper stuff you installed will effect the device, you will probably have to uninstall them. The opensource drivers work great for me on the same device on an old Dell.

Open terminal and try to install this:
```
sudo apt-get install b43-fwcutter
```
The above will install the firmware for the b43 wireless device. Sometimes you will have to restart the machine to get it to work. 

If it still doesn't work then type this in terminal:

```
rfkill list
```

This will tell you if it is being hard blocked(switch turned off) or soft blocked(disabled by software).



You will probably need to read this documentation also.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by jramshu on 2011-07-28
Wait a minute, which version of Ubuntu are you using? If you are on 11.04 the command to install the firmware will be different. It will be this:

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

As a note, please always let everyone know which version of Ubuntu you are using as some things may be slightly different. 

Thanks.

---

### Post by jcrobinson on 2011-07-28
It is 11.04.
Thanks for all the help. I'll let you know in if it works, I dont have a chance to try it right this moment, but I certianly will!
 
Thanks again.

---

