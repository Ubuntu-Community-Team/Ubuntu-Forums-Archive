---
title: "Upgrading server hardware"
date: 2011-03-09
forum: Hardware
---

### Post by electric-wildflower on 2011-03-09
Hello everyone i was wondering if i could get some help tips, ideas etc on upgrading my desktop/server. Firstly here is the specs of the server.

Ubuntu 10.10 desktop edition.

Intel(R) Pentium(R) 4 CPU 2.40GHz.
256 x2 MB DIMM SDRAM low profile.
radeon ve 64 mb graphics card.
30 gb - ata hard disk.
30 gb - ata hard disk.
120 gb - ata hard disk.
standard dvd rom
standard floppy disk

I swapped this computer of my twin who was looking for a laptop and i had a old one lying around with roughtly around the same specs and i was looking to create a home media server. Now i have been looking at options on how to upgrade.

Firstly i am mainly looking to upgrade hard disks get some serious storage although ata is a old format but i have came across a few things that would let me connect sata hard disks here is a few things.

[http://www.vesalia.de/e_ide40sata2xconv.htm](http://www.vesalia.de/e_ide40sata2xconv.htm)

[http://cgi.ebay.co.uk/5-25-Molex-2-x-SATA-Power-Splitter-Cable-Y-Adaptor-/200520128177?pt=UK_Computing_CablesConnectors_RL&hash=item2eafee56b1](http://cgi.ebay.co.uk/5-25-Molex-2-x-SATA-Power-Splitter-Cable-Y-Adaptor-/200520128177?pt=UK_Computing_CablesConnectors_RL&hash=item2eafee56b1)

The question is would the desktop/server support these i know it says there is a bios on them which will help let you use larger hard disks but is it worth it or should i just buy a newer motherboard etc.

and whats the biggest supported size for sata. 

Also with the ram it is abit slow to start and log in but because it's left in the corner and will be in the loft or a cupboard or something once i move does it matter about upgrading the ram will i need to if i upgrade the hard disks.

any help would be appreciated thanks all.

---

### Post by HankB on 2011-03-09
What kind of media server? Are you thinking of serving files to another system like a DLNA server? Or are you thinking along the lines of a set top box where the output of the video card drives a TV monitor.

The biggest thing that jumps out is the lack of RAM. Unless you really need a GUI, I recommend running the server edition. That will make best use of available RAM by not loading the GUI.

I'm not aware of any limits on SATA disk size that Linux imposes. More likely older H/W might not work with newer larger drives. BIOS support could be an issue, but I think that if you are not booting off the drive that may not be an issue. Facing your situation, I would probably use the 120GB drive for a system disk or perhaps just the /boot partition and use a newer and faster HD for my home directory. Either option is almost trivially easy when installing Linux.

You might also consider a PCI SATA card (assuming you have extra PCI slots available.) 

HTH,
hank

---

