---
title: "new install Feisty onto Compaq Evo fails to see disk"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by Godfrey Nix on 2007-06-09
Hi,
I have been using various flavours of Linux for many years. Today I finally decided to put feisty Fawn on my laptop - a Compaq Evo N1015v.

Loading from CD gave for a brief moment, a message relating to ali15x3 problem, but then it came up with the desktop so I went to install. After partitioning my disk and formatting it, the install failed as it could not mount the hard disk partitions. This was after it had wiped the disk, of course.

I remember, when first installing Fedora years ago I had to give "nomce ide=nodma pci=off"
in order that it could handle the disks (CD and hasr disk). I guess I need to do something similar, but what command do I need, and where in the starting up or install do I put it?

All help appreciated

---

### Post by Godfrey Nix on 2007-06-10
I thought I had it fixed by adding "nomce" on the boot, but I just confused myself. Successfully installed an old version 6 instead of Feisty Fawn. I still cannot get Feisty to install on my laptop. Gives messages like these -
[FONT="Courier New"]   ALI15x3 IDE Controller at PCI slot 0000:00:10.0 unable to derive IRQ not 100% native mode will probe IRQs later[/FONT]
Finally it reports that it was unable to load the device driver module.

Correspondence with other members of the local LUG have revealed that one other user has exact same problem with their N1015v and come to the same conclusion - go back to version 6.

---

