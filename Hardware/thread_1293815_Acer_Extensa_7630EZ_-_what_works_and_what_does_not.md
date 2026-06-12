---
title: "Acer Extensa 7630EZ - what works and what does not..."
date: 2009-10-17
forum: Hardware
---

### Post by jevel on 2009-10-17
This is a post to try to help both myself and others that want to run Ubuntu on this bargain laptop, as I couldn't find much regarding this hardware, and several critical components does not work.

The most critical functions that do not work out of the box in 9.10 daily is:

[LIST]
[*]wireless network - the Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
[*]wired network - Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
[*]Acer shortcuts and keys - the special keys on the keyboard and shortcut keys does not work
[/LIST]

What I have tried so far:

As a tip to others that need network on this laptop: I use my HTC Touch HD as a USB network card to connect to the internet. Works out of the box, but can be potentially expensive depending on your data plan.

To get the wireless network running, I have tried the following:

[LIST]
[*]installed updated wireless drivers from linuxwireless.org
[*]installed linux-backports-modules-karmic
[/LIST]

Even though it seems that the ath9k driver should support the card, it will not show up under my configured interfaces, and the output from *sudo lshw -C network* gives

```
*-network UNCLAIMED     
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:ba000000-ba00ffff

```

To get the wired networking to run, I have tried the following:

[LIST]
[*] nothing
[/LIST]

To get the shortcut keys working, I have tried the following:

[LIST]
[*] nothing
[/LIST]

I will keep updating this til I have a fully working system. If anyone has tips and / or tricks and want to share them, I will add them to this post with references where needed.
 
-KJ

---

### Post by drunken-wallaby on 2009-10-29
Hi Jevel.

I have this laptop as well and I am using it with Archlinux (x86_64) for several weeks now.

While the atheros ar928x based wireless card works out of the box with 2.6.30.x kernels just fine, I did not managed to get this card recognized with any 2.6.31.x kernel. You can find the corresponding bug-report [**here**](http://bugzilla.kernel.org/show_bug.cgi?id=14402).

I would be happy if you could provide some feedback there since until now it seemed as if I was the only one experiencing this bug.

Other than that, the notebook pretty much just works, I have to admit though, that I don't plan to use the special keys so I haven't even tested them.

> **jevel said:**
> This is a post to try to help both myself and others that want to run Ubuntu on this bargain laptop, as I couldn't find much regarding this hardware, and several critical components does not work.

The most critical functions that do not work out of the box in 9.10 daily is:

[LIST]
[*]wireless network - the Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
[/LIST]


---

### Post by RSt123 on 2009-10-31
Hi!

With ubuntu 9.10 and  kernel 2.6.28-16 (which also comes with 9.10) I've a connection via eth0. But sound doesn't work with this kernel - it worked with ubuntu 9.04 and also workes with kernel 2.6.31-14 .

-- Richard

---

### Post by KlausU on 2009-12-19
Hi,

have you been successful with your attempts to get the WIFI/LAN (sound?) running? I am considering to buy this laptop and I want to run Ubuntu on it.

- Klaus

---

