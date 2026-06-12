---
title: "Shuttle SK43G SATA Issues"
date: 2009-03-20
forum: Hardware
---

### Post by cypherus on 2009-03-20
Hello,

I am having issues installing Ubuntu on my Shuttle SK43G mini-computer.  I have upgraded the BIOS to the newest version, but that didn't fix this problem.  I am having issues with the computer not picking up the SATA hard drive in any way. I did find [**this article**]("http://global.shuttle.com/support_faq_detail.jsp?PI=479&PFI=899") from their website...it appears that drivers must be loaded for Windows in order for it to detect the drive?  When I run the Ubuntu 8.10 installation disc, when the partition manager section comes up there is nothing found.  Any ideas?

Thanks.

---

### Post by cypherus on 2009-03-21
Can someone please help me with this?  It's really important.  Thanks.

---

### Post by cypherpu on 2009-10-30
I hope you have found a solution to your problem (as your email was from 2005. If you haven't, there are a few issues:

1) the sata drives must be configured to limit their IO to 1.5 GB/s, usually by jumpers on the drive.
2) Go to the BIOS Setup Utility/Integrated Peripherals/VIA OnDhip IDE Device.
Select OnChip SATA/Enabled
Select SATA Mode/RAID

You should be good to go.

> **cypherus said:**
> Can someone please help me with this?  It's really important.  Thanks.

---

