---
title: "Help,Added 2Gb ram but I cannot boot 64bit Hardy"
date: 2008-09-03
forum: Hardware
---

### Post by Shadowmeph on 2008-09-03
it is strange right now I am using the live cd and there is no problems at all with me running 4GBs ram, but if I were to reboot and try to get into my 64bit Ubuntu hardy it will load up to just before it shows the desk top then my computer will freeze.
If I switch the Ram with old ram and ran just 2 Gbs it boots and if I run just 2Gb's of the new ram there are no problems, but if I run all 4GBs it will load up to just before it shows the desk top ,I checked my bios and it shows all 4 GB's of the ram I also had the ram tested and it is fine. is there something in the Ubuntu config somewhere that I have to change?

---

### Post by IntuitiveNipple on 2008-09-03
When you use the LiveCD it probably uses different video drivers than you've got installed.

What most likely causes this is the video card needing to allocate a large range of PCI IOMEM but, because you've got 4GB of RAM installed, there is not enough free IOMEM address space below the 4GB boundary for the PCI IOMEM window - video devices usually need 256MB or 512MB.

When the PC only has 2GB of RAM, there's a window of 1.25GB available for PCI IOMEM. With 4GB of RAM, 1GB is mapped above the 4GB boundary, leaving just 256MB of PCI IOMEM space between the 3GB and 4GB boundaries.

As all PCI devices in the system have to share this space, and the video device isn't the first to request an IOMEM allocation, the system doesn't have enough IOMEM space and the video device doesn't get any.

That means it will only operate in text and low-resolution graphics modes. When a high-resolution mode is attempted it can't do it, and fails the way you describe.

There isn't a solution at present. I'm currently putting the finishing touches to new Linux kernel PCI IOMEM allocation system that works as well as, if not better than, Windows. That won't appear in mainline for a few months though, and I doubt it'll get backported to existing releases.

---

### Post by Shadowmeph on 2008-09-04
> **IntuitiveNipple said:**
> When you use the LiveCD it probably uses different video drivers than you've got installed.

What most likely causes this is the video card needing to allocate a large range of PCI IOMEM but, because you've got 4GB of RAM installed, there is not enough free IOMEM address space below the 4GB boundary for the PCI IOMEM window - video devices usually need 256MB or 512MB.

When the PC only has 2GB of RAM, there's a window of 1.25GB available for PCI IOMEM. With 4GB of RAM, 1GB is mapped above the 4GB boundary, leaving just 256MB of PCI IOMEM space between the 3GB and 4GB boundaries.

As all PCI devices in the system have to share this space, and the video device isn't the first to request an IOMEM allocation, the system doesn't have enough IOMEM space and the video device doesn't get any.

That means it will only operate in text and low-resolution graphics modes. When a high-resolution mode is attempted it can't do it, and fails the way you describe.

There isn't a solution at present. I'm currently putting the finishing touches to new Linux kernel PCI IOMEM allocation system that works as well as, if not better than, Windows. That won't appear in mainline for a few months though, and I doubt it'll get backported to existing releases.

wierd I posted a reply and it didn't show up.
ok what you are saying actually makes total sense this is to bad for me because I was really looking forward to having the extra ram :( 
Hurry up and get it up and working ( Just kidding ) thank you for your reply and good explanation, I guess that I will just have to open my Computer up and remove the extra sticks ( Bummer) lol

---

