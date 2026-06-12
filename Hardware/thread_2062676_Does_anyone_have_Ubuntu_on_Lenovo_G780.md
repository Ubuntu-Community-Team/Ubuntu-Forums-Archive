---
title: "Does anyone have Ubuntu on Lenovo G780?"
date: 2012-09-25
forum: Hardware
---

### Post by fiftyeightz on 2012-09-25
I've notice this 17 inch laptop which looks interesting, I've been considering a big laptop and this one has Intel graphics so a least there are no Optimus problems.

---

### Post by BrianBlaze on 2012-09-25
I know this doesn't help much but I have a G570 15 inch and it works great :)

---

### Post by ld114 on 2012-09-26
Same here. G570 works fine with 12.04 - except for the onboard microphone, but that's no big deal.

---

### Post by ld114 on 2012-09-26
Meant to say that Lenovo's are known to be linux friendly - that's why I opted for one.

---

### Post by fiftyeightz on 2012-09-26
thanx, my worry now is the wireless.

It's only written for the G780 "Lenovo BGN wireless".

That's not telling me much, from what I know often for laptop companies they often do not manufacture their own wireless device.

Do you know if there's a way to find out which wireless is it and if I should worry about it

---

### Post by ld114 on 2012-09-26
This is probably all right. The datasheet for the G570 says just "802.11bg/bgn WiFi", but lspci returns "Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter". Though there is always a risk, there have been no wifi issues with the G570 - wireless works straight away with 12.04 (and Debian Squeeze). 

The only way to be absolutely sure is to boot up the laptop you are keen on in a store with an Ubuntu live USB stick and then do lspci in a terminal. This will tell you what all the controllers are.

---

### Post by kurru on 2012-09-27
I have g780 and Kubuntu 12.04. What is your question?

Wireless is just fine, however when you install kernel out of the repository you will need to re-install wifi, so prepare with downloading the driver.

Cable LAN will not work, neither I could make the nVidia 630M to work. But the main advantage of this laptop is the BIOS setup, where you can disable dedicated graphics.

---

### Post by kurru on 2012-09-27
lspci:


00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 08)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

---

### Post by OrangeCrate on 2012-09-27
Out of curiosity, besides this one, how many threads like this do you need at one time?

**Lenovo BGN Wireless, ubuntu friendly?**

[http://ubuntuforums.org/showthread.php?t=2063080](http://ubuntuforums.org/showthread.php?t=2063080)

**Which to buy? Inspiron 17R or Latitude E5530?**

[http://ubuntuforums.org/showthread.php?t=2057402](http://ubuntuforums.org/showthread.php?t=2057402)

**Dell Latitude or Lenovo Thinkpad?**

[http://ubuntuforums.org/showthread.php?t=2062675](http://ubuntuforums.org/showthread.php?t=2062675)
[B]
Buying laptop, wireless device model vs chipset[/B]

[http://ubuntuforums.org/showthread.php?t=2057395](http://ubuntuforums.org/showthread.php?t=2057395)

I've participated in a couple of them, but I'm a little confused with where all this is going, so, I think I'm done.

Good luck!

---

### Post by fiftyeightz on 2012-09-30
Yep sorry about that.
Usually when I open one thread with many questions people tell me to split it to more than one thread then that's what I did.

I changed my open a couple of times as well that's why there are so many threads.

anyway kurru thank you a lot for the info!

---

### Post by kurru on 2012-10-08
I have Kubuntu 12.04 on the Lenovo G780. It was unstable with Unity.
Anyway it is a very good notebook, and good price/value.

---

### Post by Beanmonster on 2012-10-20
I have tried Ubuntu Desktop 12.04 and the recently released 12.10.


[LIST]
[*]Wireless does not work out of the box. (Needs driver)
[*]Neither does the ethernet. (Needs driver too)
[*]Still can't get the graphics GT 630M going.
[/LIST]
Nonetheless it is an amazing piece of hardware for the price I paid.

---

### Post by _asc_ on 2012-10-27
Hello,

how did you install the drivers for Wireless and Ethernet? A friend of mine has the Lenovo G780 too and we installed Ubuntu 12.10. Unfortunately, there is no driver listed when we go to "System Settings -> Software Sources -> Additional Drivers", so I do not know how to activate them.

lshw -c network gives us

```
 *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 08
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d3900000-d393ffff ioport:2000(size=128)
  *-network
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:d3800000-d3803fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 08:ed:b9:a3:da:89
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.5.0-17-generic firmware=N/A multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by kurru on 2012-11-14
The wifi should work out of box after installation either 12.04 or 12.10.

When I upgraded to edge kernel, the wifi stopped to work, and then I had to install the broadcom driver but have to check how - I guess a deb package was available.

nVidia promised support for GT630M after Linus showed middle finger to them.

---

### Post by markb69 on 2012-12-21
I have the Lenovo G780 running Ubuntu 12.10. I am using Gnome Shell 3.6 and Cinnamon Mint. I have occasional crashes but I get these with Shell on my desktop too. I suggest re-enabling Ctrl+Alt+Backspace in System -> Keyboard layout -> Options to make recovery from Shell crashes easier. Everything worked right out of the box: Nvidia, wifi, sound, usb, etc. I couldn't get the USB flash drive to boot so I ended using the Wubi installer in System 7 boot to install Ubuntu. The only issue I have is the usb wireless mouse I have has to be manually inserted/removed several times for the system to recognize it. If I come up for a fix for this I will post the steps to correct it. I also use the Jupiter indicator to manage cpu power/devices [http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html](http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html) . All in all I am very happy with the laptop. It came with System 7 but I rarely boot into it. To set your laptop to always run Ubuntu I found the easiest thing to do was boot in System 7/8 and set the System boot options to run Ubuntu first. Works great. I couldn't get it to work in grub. I think I have had to boot into Windows 7 once to run Turbotax. Otherwise I have been using Shell to do all my web dev work. I wrote several Shell extensions to make the UI more appealing for laptop users. [https://extensions.gnome.org/accounts/profile/mbokil](https://extensions.gnome.org/accounts/profile/mbokil)

---

