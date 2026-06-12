---
title: "ACPI Gateway 200x"
date: 2005-03-16
forum: Hardware &amp; Laptops
---

### Post by briguy on 2005-03-16
I've recently installed Hoary, replacing FC2 on my Gateway 200x.  This laptop has a notoriously bad ACPI (no battery info under linux), which I fixed in Fedora by including the dsdt table in a custom kernel.

When I installed Ubuntu 5.04 preview, the battery info was there however it was garbled.  cat /proc/acpi/battery/BAT1/state showed most of the right info except rate, remaining capacity and voltage were incorrect.  

I tried to follow the instructions found here and at [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml) for putting the dsdt into initrd to no avail (I downloaded the table from [http://acpi.sourceforge.net)](http://acpi.sourceforge.net)).  I also tried compiling a custom kernel, however that is proving to be a much bigger challenge than it was with FC2.

dmesg | grep acpi produces about fifty lines of: "ACPI: acpi_ec_space_handler: bit_width should be 8"

I would appreciate any information from anyone who has solved this problem on this or any other laptop!

---

### Post by briguy on 2005-03-18
Hokay, fixed it.  I needed to put the .aml file into initrd, not the .asl file.  Doh!

---

