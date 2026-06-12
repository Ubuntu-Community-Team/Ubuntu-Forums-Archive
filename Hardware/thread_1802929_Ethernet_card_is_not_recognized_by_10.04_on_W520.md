---
title: "Ethernet card is not recognized by 10.04 on W520"
date: 2011-07-12
forum: Hardware
---

### Post by thlin on 2011-07-12
Hi,

I got a ThinkPad W520 with i7-2720QM, NVIDIA Quadro 1000M and OCZ Vertex 3 SSD. After installing 10.04 on it the Ethernet card is not recognized by Ubuntu. I have tried "modprobe e1000e" but it did not work. I got only lo and pan0.

Then I tried 11.04 but the laptop hung on booting, not even installing it!!

So, I would like to have actually more than one question.

what version of Ubuntu is W520 friendly? 10.10?
since it is certificated [http://www.ubuntu.com/certification/hardware/201103-7374](http://www.ubuntu.com/certification/hardware/201103-7374)

and how do I setup my Ethernet card under 10.04?

why 11.04 hung on booting? because Nvidia Optimus or SSD?

Thanks!

---

### Post by thlin on 2011-07-13
install at first the driver directly from Intel (the driver is copied, since I have no network access)
[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3299&lang=eng&OSVersion=Linux*&DownloadType=%0ADrivers%0A](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&ProdId=3299&lang=eng&OSVersion=Linux*&DownloadType=%0ADrivers%0A)

after having network I updated system with new kernel 2.6.35 via backport package, so that I have TRIM support for SSD.

---

