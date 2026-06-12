---
title: "USB 2.0 Woes on Multiple Machines"
date: 2004-11-26
forum: Hardware &amp; Laptops
---

### Post by lt_kije on 2004-11-26
All-

I've been a Debian user for a coupla years, now, and I just flipped out when I installed Ubuntu -- I couldn't believe the quality of work. This is a great distro; I can't say I've had *any* problems...until now. I recently purchased a USB2.0 external hard drive enclosure and would like to upgrade both of my older computers to USB2.0. I bought two pretty standard 4-port USB2.0 PCI controllers and expected to just plug them in and roll. My first computer, a home built set up (don't have the details with me right now) just wouldn't recognize the new card. I hopped on IRC and had my hand held for a few minutes, but nothing seemed to help -- lspci didn't see the card as USB2.0, modprobing the ehci_hcd module didn't make the kernel see devices connected, etc.

Now, I'm installing a slightly different card (also 4-port USB2.0 PCI) in a Dell Dimension 8200. Same deal. lspci sees a USB controller (rev 04). Modprobing usb-storage and ehci_hcd don't help. lsusb -v sees a bunch of 1.00 and 1.10s in the bcdUSB line. In short, the card also doesn't seem to be working in this set up.

I've never had hardware issues like this -- everything from MP3 players to NVIDIA cards has worked great for me under Linux. I still would like to see if a live cd can detect the USB2.0 card; I don't have a disc available right now, but I'll check when I can. I'm suspicious that the kernel (2.6.8.1-3-386) might be getting in the way -- I've heard taht there are/were some issues around this revision. I also wonder if outdated BIOS on either my Dell or the homebuilt could be contributing to the mess.

Any thoughts? Similar experiences? Is this a kernel thing? BIOS? Is it ($DEITY forbid) an Ubuntu thing?

Thanks for the help -- my local LUG couldn't figure it out....

---

