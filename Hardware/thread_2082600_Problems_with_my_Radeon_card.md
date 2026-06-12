---
title: "Problems with my Radeon card"
date: 2012-11-09
forum: Hardware
---

### Post by SysBoot on 2012-11-09
Currently have Ubuntu 12.04 installed with Proprietary drivers from here:[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

The issue is that I can't play games they'll act like their opening up and then immediately close.

So I checked here: [http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

and I know it's a 57*** but I'm not sure which one I have. Is there to  check the model that doesn't involve taking the card out of my case?

Also thought these would be useful in determining why the games close:
[http://pastebin.com/EAqQ3TFr](http://pastebin.com/EAqQ3TFr) glfrx info(sp)
[http://pastebin.com/pWycJGvq](http://pastebin.com/pWycJGvq) Xorg file(I think)

Attached is a picture of amd catalyst control center information stuff. 


Help? :)

---

### Post by mzrk7 on 2012-11-10
run on terminal, and then copy and paste lspci -v

---

### Post by SysBoot on 2012-11-10
I fixed it by installing the drivers in the "additional drivers" app.

---

