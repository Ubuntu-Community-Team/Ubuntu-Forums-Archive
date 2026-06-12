---
title: "Atheros 802.11 not working"
date: 2009-04-18
forum: Hardware
---

### Post by MinatureCookie on 2009-04-18
Hey, just recently installed Ubuntu over Windows, and I cannot connect to the internet...
It was working before on Windows, and I've done all I can to see the problem on Ubuntu, but I'm still kinda new.
So I'm looking at "Hardware Drivers" and it's telling me that there's a driver for "Atheros 802.11 wireless LAN cards", and that it's active.
I've also got in the network bit, a wireless connection with my correct SSID and WEP code in all the correct places - but it just won't connect...
I typed into the Terminal...:
sudo lshw -C network
and it told me that the wireless thing is under "*-network UNCLAIMED"

What any of that means, I have no idea - but I'm hoping it will mean something to some Ubuntu-geniuses?
And any sharing of that knowledge would be largely appreciated ;)

(As another problem, maybe somehow relevent, my largest screen resolution is 800x600, annoyingly for some reason.. Relevent at all?)

---

### Post by mikewhatever on 2009-04-18
Why don't you post the output of the above mentioned command.

---

### Post by hotweiss on 2009-04-19
What notebook do you have? Your wifi is probably not working because of an ACPI issue.

What video card do you have?

---

### Post by zerosoul on 2009-04-19
Im having the same problem with my wifi card Atheros 5007... but then this card has been a problem for a long time... Backtrack 3 final managed to solve the problem but i not know what they have done to get it working

---

### Post by lisati on 2009-04-19
I'm mildly curious: what flavour atheros? The information might help others suggest a solution. (BTW, I'm not talking about the 802.11 bit)

---

### Post by dodle on 2009-04-19
Have you tried using the Windows driver with ndiswrapper?

---

### Post by MinatureCookie on 2009-04-19
Fujitsu Siemens Esprimo Mobile v5515.
I haven't tried a Windows driver with an ndiswrapper, but I honestly wouldn't know where to look for a Windows driver.. To Google I suppose.
As to what flavour of Atheros, I don't know - it's an inbuilt thing in the laptop, and all I know I posted in the first post.
I will print out all of the output of that command, yeah - I just only did what I thought was vital as I have no way of copying and pasting it over, I have to write it down word-for-word...:
*-network UNCLAIMED
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:02:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix cap_list
configuration: latency=0

*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 82:65:2a:b5:f0:56
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by zerosoul on 2009-04-19
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Askey Computer Corp. Unknown device 7128
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at ff2f0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

---

### Post by Shad0wZ on 2009-04-19
> **lisati said:**
> I'm mildly curious: what flavour atheros? The information might help others suggest a solution. (BTW, I'm not talking about the 802.11 bit)

How would you be able to track this?
I'm having the same problem as the OP, but with another laptop.

---

### Post by MinatureCookie on 2009-04-19
Don't mean to "bump" but.. Does anyone have any idea? Not having the internet is sort of annoying :-/

---

### Post by hotweiss on 2009-04-20
> **MinatureCookie said:**
> Fujitsu Siemens Esprimo Mobile v5515.
I haven't tried a Windows driver with an ndiswrapper, but I honestly wouldn't know where to look for a Windows driver.. To Google I suppose.
As to what flavour of Atheros, I don't know - it's an inbuilt thing in the laptop, and all I know I posted in the first post.
I will print out all of the output of that command, yeah - I just only did what I thought was vital as I have no way of copying and pasting it over, I have to write it down word-for-word...:
*-network UNCLAIMED
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:02:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix cap_list
configuration: latency=0

*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 82:65:2a:b5:f0:56
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

Here you go:

[http://linuxwiki.de/LutzWillek/V5535](http://linuxwiki.de/LutzWillek/V5535)

The above guide will show you how to get everything working. Please note that you will need a LAN internet connection just to get through some of the installs. Installing the wifi drivers is just a matter of copying and pasting commands into terminal. Installing the graphic card drivers might be a little more complicated, so you can also try these English help links:

[http://ubuntuforums.org/showthread.php?p=4697207](http://ubuntuforums.org/showthread.php?p=4697207)

[http://ubuntuforums.org/showthread.php?t=615094](http://ubuntuforums.org/showthread.php?t=615094)

---

