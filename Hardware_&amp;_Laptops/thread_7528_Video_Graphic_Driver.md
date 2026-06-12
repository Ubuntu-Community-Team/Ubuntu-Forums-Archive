---
title: "Video Graphic Driver"
date: 2004-12-08
forum: Hardware &amp; Laptops
---

### Post by ramin on 2004-12-08
Hi,

I would like to find the proper graphic video for a VIA KM400/KM400A/KM266 Pro motherboard.

When I installed Ubuntu, the install program picked up Vesa which has a very low resolution and a terrible refresh rate. I would appreciate it if someone could direct me to a download site that has a matching graphic driver?


Best regards,
Ramin.

---

### Post by p!=f on 2004-12-08
[QUOTE=ramin]Hi,

I would like to find the proper graphic video for a VIA KM400/KM400A/KM266 Pro motherboard.

When I installed Ubuntu, the install program picked up Vesa which has a very low resolution and a terrible refresh rate. I would appreciate it if someone could direct me to a download site that has a matching graphic driver?


Best regards,
Ramin.[/QUOTE]

What's your graphic card?
Feel free to post lspci output here.
Example:
```

:~ $ lspci
0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
**0000:00:02.0 VGA compatible controller: Intel Corp. 82865G Integrated Graphics Device (rev 02)**
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801BA/CA/DB/EB/ER Hub interface to PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:01:08.0 Ethernet controller: Intel Corp. 82562EZ 10/100 Ethernet Controller (rev 02)

```

---

### Post by ramin on 2004-12-08
Thanks for the response, I finally found this driver in this forum and used it with success. I still don't think is the best but OK. Here is the link I found:

[http://prdownloads.sourceforge.net/unichrome/via_drv.o-unichrome_X_r26-debian_sarge_xfree86-4.3.0.dfsg1-7.gz?download](http://prdownloads.sourceforge.net/unichrome/via_drv.o-unichrome_X_r26-debian_sarge_xfree86-4.3.0.dfsg1-7.gz?download)

Thanks again.

P.S. My motherboard is KM400 and the driver I need was via.

---

