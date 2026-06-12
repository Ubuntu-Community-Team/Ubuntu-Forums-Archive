---
title: "Fujitsu FMV Deskpower LX70X/D with ubuntu?"
date: 2010-01-17
forum: Hardware
---

### Post by yoalieh on 2010-01-17
Hello to everybody, this is my first post.

I bought a Fujitsu FMV Deskpower LX70W/D on May 2007 in Japan, and brought it to México. 

The specs of this machine are:
[http://www.fmworld.net/product/hard/pcpm0704/deskpower/lx/method/index.html](http://www.fmworld.net/product/hard/pcpm0704/deskpower/lx/method/index.html)

I has trouble since the kubutun distro of then, because only 64 bits runs, troubles with hard drive modules, the video capture card was non functional, intel graphic card drivers were in development then, the wifi card and ethernet card, and sound card were faulty, etc. I tested with many distros, with the same results.

I made it work in a suboptimal way and upgraded the system many times until intrepid, when the upgrade finally broke many functions like printing. I reinstalled using Lucid Alpha 2, and was pleased to see almost all problems are fixed now. 

There are still some problems with evdev, as the mouse, (of a  RF Keyboard/Mouse Combo) is not working and the remote controller has many unmapped keys. 

I used some usb mouses to test, but a single random app captures the mouse clicks. I disabled automatic evdev input in xorg.conf, and configured mouse, keyboard and controller manually and this click grabbing stopped, but I can't get the RF Mouse to work. It seems evdev is confusing X and Y axis with two non-existant extra buttons. I need to try some alternatives, or post a bug with no proposed fix.

I haven't tested the pccard bus, the spdif output (no hardware to test), firewire or the native video capture card. Also, this system seems to have some kind of prepaid card for internet television, but I doubt it is usable in México, so I'm planning on removing it. I'm using an old bt878 and it's working.

This post is to register what I've discovered of this machine, as all its documentation is in japanese, and there's not too much info available in using linux with it. I'll be updating the post with other findings I get.

Also, if somebody is already using this computer, or is willing to help, please feel free to write. Maybe a japanese user can help with the documentation.

---

### Post by yoalieh on 2010-02-18
I hacked my way in the pci cards. It used a Pixela PIX-P6W for tv-tunner; it's not supported in linux. The Satelite card, a Pixela's PIX-DT012, is for Japan's BS110 Digital Television service, not available here, and not supported in linux. Both cards are gone. I tested a bt878, and it worked.

After removing the cards, i saw the mobo uses a riser for the pci cards, and in the riser is a small card: a well supported Atheros AR5001.

The riser can be removed and it has a 16X PCI Express Slot, and also covers the HDMI connector of the panel. I think I can finally add an NVIDIA card for gaming. But now I need a new PCIe riser, and a new way to get wifi and TV.

I tested PCMCIA slot with a TV capture saa7134 cardbus card, and works like a charm.

I got another round in trying to configure the RF mouse with udev, but I didn't find a way for making it work. Even when I move the mouse using a program to test evdev devices, X and Y movements. Reported as bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523683](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/523683)

---

