---
title: "Can't Access Peripherals"
date: 2008-08-31
forum: General Help
---

### Post by KTK on 2008-08-31
I'm running Hardy on a fairly new Dell dual-core machine. All seems well, *except . . .*

The system will recognize but not read I/O peripherals. The Dell tower has a multi-card reader installed, and I have also tried using a standalone USB multi-card reader. In addition, I pulled two hard drives off my old machine in order to transfer some data files; I have been trying to access them by installing them in a standalone drive holder with a USB cable. I use thumb drives in the USB port for file transfer. And don't even get me started on the iPod . . .!#-o But, while the computer is aware of each of these devices when they're connected, it will not read/write any of them.

On my desktop, I do get icons for each such peripheral: the iPod shows up, each of the card slots in the multi-card reader is listed separately as "USB drive", the thumb drive is listed as "2.0 GB Media", and the data partition on the USB-linked drive is also listed. But I get a different error message whenever I try to access any one of them.

The thumb drive tells me "Couldn't display /media/disk. There is no application installed for this file type."

The multi-card reader slots give me a similar message when I put a card in.

The iPod appears on the desktop and in gtkpod and Amarok (I have them both installed). But when I try to access it through the media players, I get a message "Could not mount IPOD" or "Could not find iPod directory structure at '/media/ipod'."

Every partition on the external hard drives appears in "Computer" as a separate drive, under the names of the partitions I assigned to those drives originally, on the old machine (so it *must* be recognizing them - same with the iPod, which it refers to under the drive name I assigned to the iPod when I initialized it through iTunes). But I get the "No application" error when I try to access the data.

And so on.

When I right-click these icons, the "Properties" tabs show "size unknown", "type unknown" "permissions unknown" (and this even though the icon itself gives the size of the module as its name ["1.0 GB Media", "2.0 GB Media", etc.]). I have tried doing chown /media/disk or whatever, but it still shows "permissions unknown". I have tried mounting the volumes, but it either makes no difference or the computer actually shows them as mounted but still refuses to read them.

What am I doing wrong?

Thanks.

---

