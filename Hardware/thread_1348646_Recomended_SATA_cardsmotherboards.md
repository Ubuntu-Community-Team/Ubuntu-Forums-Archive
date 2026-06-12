---
title: "Recomended SATA cards/motherboards"
date: 2009-12-07
forum: Hardware
---

### Post by epsolon77 on 2009-12-07
I was looking to see if anyone had recommendations on SATA controllers or motherboards with sata banks on them.  Ideally I would like the sata ports to support hot-swap.  Anyone have any products they recommend?

---

### Post by paulisdead on 2009-12-07
Anything with an Intel chipset will support hot plug, so long as you have AHCI turned on in the bios.

If you're interested in RAID cards I've found anything from 3ware starting with the 9500 series and up works great under Linux.  Just avoid the old 8506 cards that had corruption issues under Linux.

Also the ARC series of RAID cards from Areca have fantastic Linux support as well.  Both 3ware and ARC cards can hotplug drives.

---

### Post by epsolon77 on 2009-12-08
Forgive my lack of faith paulisdead, but where did you get the information that all intel chipsets support hot plug capabilities on the motherboard.  I am having difficulty finding any reference point confirming this, even directly from the manufacture.

---

### Post by paulisdead on 2009-12-08
Before their domain got jacked, [http://linux-ata.org/](http://linux-ata.org/) used to have a compatiblity list just for this, that had Intel's controllers listed as supporting hotplug.

Plus, I've actually tried this myself on I don't know how many intel motherboards, and it's always worked, you just have to AHCI on.  Seriously, I've done this on numerous boards from Asus, MSI, Gigabyte, and Supermicro, for the last few years, and hotplugging always worked with the Intel chipsets.

You do have to make sure you're plugged into the right controller, though.  As quite a few motherboards have additional ports through another controller, such as jmicron or somebody else, and I haven't tested hotplug on their chipsets.

You're not likely to see this on Intel's site, since it's a driver bundled with the Linux kernel that does all this.

---

### Post by epsolon77 on 2009-12-08
> **paulisdead said:**
> Before their domain got jacked, [http://linux-ata.org/](http://linux-ata.org/) used to have a compatiblity list just for this, that had Intel's controllers listed as supporting hotplug.

Plus, I've actually tried this myself on I don't know how many intel motherboards, and it's always worked, you just have to AHCI on.  Seriously, I've done this on numerous boards from Asus, MSI, Gigabyte, and Supermicro, for the last few years, and hotplugging always worked with the Intel chipsets.

You do have to make sure you're plugged into the right controller, though.  As quite a few motherboards have additional ports through another controller, such as jmicron or somebody else, and I haven't tested hotplug on their chipsets.

You're not likely to see this on Intel's site, since it's a driver bundled with the Linux kernel that does all this.

Thanks for the update.  I actually went drudging through Intel's Chipset manuals while waiting for the Comcast guy to show up at one of our sites here, and found where it states that they are hotplug capable.  Apparently motherboard manufacturers don't talk about this feature much, but now that I know I can look into the chipset features and find out that will help greatly.  Thank you again.  

Does anyone know any AMD boards that support hotplug?  I don't mind using Intel stuff, just like to know what's out there.

---

