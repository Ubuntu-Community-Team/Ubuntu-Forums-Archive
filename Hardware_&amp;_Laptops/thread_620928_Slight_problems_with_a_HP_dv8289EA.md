---
title: "Slight problems with a HP dv8289EA"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by 1/0 on 2007-11-23
I got me a HP DV8289EA. Most things went fine with the install (Kubuntu 7.10) but these problems remain:


1) At boot the startup freezes at the grub menu. I have to press escape and then manually select the boot option in order to continue the boot. I've tried acpi=off and noacpi but no success... I guess it figures since it stalls at the Grub menu and not after. 


2) Just after grub I get this:

```

Starting up ...
[     50.372142] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c:0]
[     50.372213] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c:0]
[     50.372278] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c:1]
[     50.372344] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c:1]
[     50.372409] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c:2]
[     50.372474] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c:2]
[     50.372627] PCI: Cannot allocate resource region 0 of device 0000:06:1c:0]
[     50.436469] PCI: Failed to allocate mem resource #6:20000@d000000 for 0000:0

```

I've found a bug report on it but I still don't know what this means...


3) After that I get a popping sound such as the one described with the hard drives. At first I thought it was the speakers but then I realized its not only the speakers doing this. Its almost a knocking sound since it repeats it self like knocking fast on a door.

If you got some suggestions or info, I'm at all ears.

---

