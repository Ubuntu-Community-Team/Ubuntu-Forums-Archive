---
title: "ACPI support on IBM T20"
date: 2004-10-27
forum: Hardware &amp; Laptops
---

### Post by stooksberry on 2004-10-27
I have an IBM T20 laptop (PIII-700, 512 ram) that I am having issue with power management. A stock ubuntu kernel will not load acpi/apm support. I can force acpi on during boot by adding **acpi=forced **to the kernel options in grub. The power management stuff then works great, but the system pauses every few seconds and my NIC MAC address shows up as FF:FF:FF:FF:... 

I have added **pci=noacpi** but still same results. Just setting acpi=on fixes the other issues but doesn't load acpi support. Also tried **apm=on** with no luck. Any ideas, this worked fine under Fedora 1 & 2 and Slackware 10.

---

### Post by Poldi on 2004-10-29
I have some Thinkpads as well (T20, T22, 390 and R40). on neither does any type of powermanagement work so far.

judging from my experience with other Linux, the T2* models should be usable with APM while the R40 (Centrino-based) has a good enough ACPI-implementation to use that.

I have tried the same as you have. now I am stuck. please keep us informed if you manage to improve the situation on your side.

kind regards,
Carsten

---

### Post by bsherman on 2004-11-01
Please see my post here: [http://ubuntuforums.org/showpost.php?p=9953&postcount=3](http://ubuntuforums.org/showpost.php?p=9953&postcount=3)

It details the method I used to use APM instead of ACPI on my IBM Thinkpad T23.

---

### Post by elempoimen on 2004-11-04
[QUOTE=bsherman]Please see my post here: [http://ubuntuforums.org/showpost.php?p=9953&postcount=3](http://ubuntuforums.org/showpost.php?p=9953&postcount=3)

It details the method I used to use APM instead of ACPI on my IBM Thinkpad T23.[/QUOTE]
 You know, I tried that on my T23.   I ended up with a PCI error:

*Address space collision on region 7 of bridge*

Additionally, the hotplug system errored out, not loading at all, just giving me an error with every initialization.  After a little troubleshooting, it was the *acpi=off* entry that did it.  *noacpi* seemed to have no effect on the system--and my suspend mode still didn't work.  Grr.

---

