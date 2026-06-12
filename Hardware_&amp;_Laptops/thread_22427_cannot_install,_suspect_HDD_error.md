---
title: "cannot install, suspect HDD error"
date: 2005-03-27
forum: Hardware &amp; Laptops
---

### Post by Elwood on 2005-03-27
i have already set up partitions for use to install linux using partition magic.  a total of 10gig with 1gig of swap.  both of my hard drives are SATA and it is a brand new system.  when installing ubuntu, i cannot get any further than the "partition disks" step.  the only option it gives me is to manually set up partitions, and when in that menu, none of the options seem to actually be able to do anything.  i have been shown no indication that the installer has actually detected my hard drives.  please explain to me how i can get the ubuntu installer to recognize that i even have hard drives so taht i can execute an install.

---

### Post by dseomn on 2005-03-28
What is the SATA controller and/or motherboard? Is the SATA on (possibly disabled) RAID?

---

### Post by Elwood on 2005-03-29
my motherboard is an MSI motherboard.  it is an odd one simply because it is a micro-atx and uses a chipset other than nforce-4 for socket 939/pci-e.  i know for a fact that my HDDs are enabled because 1) in my bios they show up as separate IDE channels with the expected devices attached to them and 2) i already run 2 versions of windows in a dual boot using the first partitions of both hard drives.  im pretty sure that the issue is with the sata support in the installer, but i would like to know this for sure, and if i can still install ubuntu

---

### Post by dseomn on 2005-04-15
[QUOTE=Elwood]my motherboard is an MSI motherboard.  it is an odd one simply because it is a micro-atx and uses a chipset other than nforce-4 for socket 939/pci-e.  i know for a fact that my HDDs are enabled because 1) in my bios they show up as separate IDE channels with the expected devices attached to them and 2) i already run 2 versions of windows in a dual boot using the first partitions of both hard drives.  im pretty sure that the issue is with the sata support in the installer, but i would like to know this for sure, and if i can still install ubuntu[/QUOTE]
 I don't know if the motherboard will work with tweaking or at all, but I'd google, ask on the ubuntu-users mailing list, and/or try again in a year or so.

---

