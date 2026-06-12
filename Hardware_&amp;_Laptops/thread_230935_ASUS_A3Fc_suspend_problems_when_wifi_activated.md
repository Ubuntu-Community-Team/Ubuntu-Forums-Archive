---
title: "ASUS A3Fc suspend problems when wifi activated"
date: 2006-08-06
forum: Hardware &amp; Laptops
---

### Post by mikosan on 2006-08-06
Hi,

I have installed Ubuntu 6.06 on following [ configuration]("http://www.asus.com/products4.aspx?l1=5&l2=24&l3=0&model=1132&modelmenu=1"). Everything worked almost out of box. i915 was needed  and to get suspend to RAM working I had to add acpi_sleep=s3_bios to kernel parameters. So far so good. 

However, this only works when Wifi (Intel PRO 3945) is disabled from bios. 
I did a small test:

1,I enabled this wifi card and booted into single user mode.
2,I put ipw3945 into blacklist.


After running /etc/acpi/sleep.sh and following attempt to resume laptop system hangs somewhere and I've got absolutely no reaction from it. 

I attached logs from dmesg and output from lspci -v

any help appreciated,

mikosan

---

