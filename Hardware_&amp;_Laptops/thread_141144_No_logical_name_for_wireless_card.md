---
title: "No logical name for wireless card"
date: 2006-03-07
forum: Hardware &amp; Laptops
---

### Post by Papa-san on 2006-03-07
I hate to be the one to start a thread, but I have searched under everything I can think of... I have Breezy Badger 5.10, and no clue as to what I am doing with it...
I have a Dell Lattitude C-610 laptop with an internal wireless card. 
I have found the wireless troubleshooting guide, and have followed it as far as I can.
When I ran "lshw -C network", the card is found, but there is no listing under 'logical drive' nor is there a driver associated with it.

I have found the PCI ID (14e4:4320) (rev 02) as reported through "lspci -n"
It appears to have memory assigned to it

When I run "sudo iwconfig" it doesn't get listed...

I have the driver for this pci id that I got from ndiswrapper downloaded to my desktop, but do not know what to do with it.  I haven't ever looked into any linux code before, so I am as new as they get... (sorry):rolleyes:

---

### Post by Papa-san on 2006-03-07
sudo lshw -c network got:
0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
        Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card
        Flags: bus master, fast devsel, latency 32, IRQ 11
        Memory at f8ffc000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

Several of the results showed the "capabilities<available only to root>" designation.
Am I missing something? I thought the 'sudo' was access to root?!?

---

### Post by Lambert on 2006-03-07
See this link for installing windows driver with ndiswrapper

[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper")

lshw just shows the device is inserted into the os and reocgnized. Device won't list with iwconfig or receive a logical name until you have a functional driver running for the device.

---

