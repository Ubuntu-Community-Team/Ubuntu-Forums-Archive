---
title: "Server 6.1 DG965RY 8 GB RAM"
date: 2007-12-29
forum: Hardware &amp; Laptops
---

### Post by donwoodsnet on 2007-12-29
Hello, I just joined today after using UBUNTU server 6.1 for about 9 months without any issues. It's been a real solid performer for me.

I have a situation where I need to increase my RAM to 6-8 gig because I need some additional VM’s for development purposes. I’m not 100% sure if this is an OS or a BIOS issue but, it appears it might be a BIOS issue. Here’s why. 

This is what I got:
Intel® Desktop Board DG965RY 
BIOS MQ96510J.86A.1663.2007.0319.1957
Intel Core2Duo processor
4 1-gig DDR2 533mhz DIMMS
4x250 Gig STA HD
DVD RW
1.4 Floppy

UBUNTU server 6.1
VMware Server 1.0.2
2 FreeBSD 6.1 VM's
4 W2k3 Server VM's

Yesterday I upgraded the RAM in the system to 8 BG using two PC5300 Kits (4 2-gig 633 mhz DIMMs) from Kingston that were flagged for use on my motherboard model. I know for sure it's the correct memory because I checked it out against the system board's reference manual and it checks out.

The unit POSTs just fine. I can get into the BIOS and the system sees the new memory at the correct speed but, when UBUNTU boots up it slows to a crawl. The VM's load extremely slow, so slow they barley run at all.:mad:

I removed two of the DIMMs and the OS boots fine just like with the old memory was installed.

I updated the BIOS to the latest on the INTEL website but it got worse. Even with 4 GB of RAM the system crawls when the OS boots up. I've tried several of the BIOS updates that came after BIOS MQ96510J.86A.1663.2007.0319.1957 with the same results therefore I had to fall off those BIOS's and maintain BIOS MQ96510J.86A.1663.2007.0319.1957. I haven't tried any prior to this rev.

I'm wondering if anybody else has seen a similar situation with UBUNTU!?! Also if this is an irresolvable issue can someone recommend a system board that will work with UBUNTU and 8 GB or DDR2 633 DIMMs?

---

### Post by dim_hyder on 2007-12-29
It appears that the default kernel is compiled for a max of 4Gig of RAM

See the following post:

[http://ubuntuforums.org/showthread.php?t=208719](http://ubuntuforums.org/showthread.php?t=208719)

Looks as if you'll have to recompile the kernel

Cheers,

Dim Hyder

---

### Post by donwoodsnet on 2007-12-29
Thanks for the heads up on the kernel. I'll check it out for sure.
It’s weird how top sees 8 GB when the system finally boots up. I'm wondering why the default 64bit server 6.10 kernel would have a 4 GB limit?

---

### Post by donwoodsnet on 2007-12-30
My Bad... It's the 32bit version :oops:

---

