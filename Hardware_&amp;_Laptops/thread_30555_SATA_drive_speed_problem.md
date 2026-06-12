---
title: "SATA drive speed problem"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by bihan on 2005-04-29
Hi all,

I installed Kubuntu 5.04 yesterday.
I wanted to check my harddisk speed.

hdparm -t /dev/sda returns a write speed of 14 MB/s... I thought that SATA disks were a bit faster.

It seems that my disk is configured to use the 16 bit mode, I tried hdparm -c1 and it returns an error like "ioctl() not supported device for operation"

I had the same problem with my former fedora, when I tried upgrading the kernel. My drive worked correctly (50 MB/s write speed) on 2.6.9 but not with the more recent versions. I tried many kernel compilations to workaround the problem but none of them worked...

my drive is a Seagate barracuda 120 GB
my motherboard is an ASUS A7N8X deluxe

any ideas ?

bihan

---

