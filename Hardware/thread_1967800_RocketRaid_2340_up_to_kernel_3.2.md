---
title: "RocketRaid 2340 up to kernel 3.2"
date: 2012-04-28
forum: Hardware
---

### Post by paranoidi on 2012-04-28
Personally I'm never going to buy another highpoint product again nor recommend one, at least as long as they are not natively supported by the linux kernel. Their support is just plain awful. Don't expect them to provide any support year or so after introducing the product.

So, let me help my fellow sufferers a bit by providing a patch file to get latest rr2340 driver to Ubuntu 12.04 (kernel 3.2). This was made possible by Nagilum's rr2320 patch file I found from [http://cakebox.homeunix.net/wordpress/?p=227](http://cakebox.homeunix.net/wordpress/?p=227)

Instructions:

Get the latest sources from [http://www.highpoint-tech.cn/BIOS_Driver/rr2340/Linux/rr2340-linux-src-v1.7-090925-0900.tar.gz]("http://ubuntuforums.org/wget%20http://www.highpoint-tech.cn/BIOS_Driver/rr2340/Linux/rr2340-linux-src-v1.7-090925-0900.tar.%20gz")

Use the attached patch file (get rid of .txt extension):

~/rr2340-linux-src-v1.7# patch -p1 -i rr2340-linux-src-v1.7.patch

And follow the normal annoying installation procedure.

---

### Post by littletux on 2012-06-24
This Patch doesn't work in all cases, because the make patchkernel command, for add the driver as a kernel-patch says kernel not supported.

It would be really great if this also would work

---

### Post by Spike42 on 2012-10-03
Works with Ubuntu 12.04.1 LTS Server AMD64 (Kernel 3.2.0-31-generic).
Thank you very much!

---

### Post by archenroot on 2012-12-30
Hi, I am going to buy this RAID driver, but cannot find driver for 3.4.x kernel. The original site with drivers seems to be down. Could someone upload the latest driver and patch?

Thank you.

Ladislav

---

### Post by paranoidi on 2012-12-31
Attached the driver. Don't blame me if you have bad time with this card ...

---

### Post by whyacow on 2013-02-23
Any chance of getting one for the rr2340 on the 3.5 kernel?

---

### Post by william.viker on 2013-12-15
> **whyacow said:**
> Any chance of getting one for the rr2340 on the 3.5 kernel?

[http://ubuntuforums.org/archive/index.php/t-1899544.html](http://ubuntuforums.org/archive/index.php/t-1899544.html)

---

