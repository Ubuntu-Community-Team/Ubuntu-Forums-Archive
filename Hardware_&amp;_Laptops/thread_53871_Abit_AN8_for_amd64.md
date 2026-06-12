---
title: "Abit AN8 for amd64?"
date: 2005-08-02
forum: Hardware &amp; Laptops
---

### Post by matsur on 2005-08-02
Hi all,

First post here. I'm about to do my first amd64 build, and wanted to make sure the mobo and video card are compatible before taking the plunge. Originally I wanted to run NetBSD on this machine, but it looks like compatibilty is lacking in that department.

For the mobo, I was thinking I would get a ABIT AN8 Socket 939 NVIDIA nForce4 ATX board. Would everything (audio, NIC, FireWire, USB etc.) be supported out of the box? With moderate tinkering? At all? Does AMD's Cool 'n' Quiet work on Ubuntu?

The video card on my list is the XFX PVT43PUD Geforce 6600 256MB DDR PCI Express x16. This is a dual head DVI card. How hard would it be to get two displays working on it? (sort of elated, and silly, question... would it be possible to run VMWare /Windows on one screen and X on the other? :-))

Thanks in advance for your help,
matsur

---

### Post by mo_x on 2005-08-03
I have a gigabyte k8nf-9 scoket 939 nforce4 motherboard. The audio, ethernet en usb are working ok, some moderate tinkering for audio en ethernet. I am using the nvnet driver from nvidia. Firewire I have not tried. The powernowd deamon for the cpu frequency does not seem to work for my processor, an AMD64 3000+ Venice. But I think that is solved in newer versions of the kernel. I think the board you mentioned uses the same ethernet chip but has a different audio chip. I have a Geforce 6200 16-TC PCIe that works fine, I don't know about dual head.

---

