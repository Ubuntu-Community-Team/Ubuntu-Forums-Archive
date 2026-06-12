---
title: "Driver samsung ml 1860"
date: 2011-09-27
forum: Hardware
---

### Post by francescoo87 on 2011-09-27
HI! I have some problems with the driver of samsung ml 1860. I have an Ubuntu 10.04.
I downloaded both smartpanel_0.95.tar.gz and unifiedriverlinux_0.95.tar.gz, then I followed the instrunctions foud here: [http://www.samsung.com/hk_en/consumer/computer-peripherals/printers-multifunction/monochrome-laser-printers/ML-1860/XSS/index.idx?pagetype=prd_detail&tab=support](http://www.samsung.com/hk_en/consumer/computer-peripherals/printers-multifunction/monochrome-laser-printers/ML-1860/XSS/index.idx?pagetype=prd_detail&tab=support). But neither the "autorun" of unifiedriverlinux nor the "install.sh" of smarpanel work. How can I get out of this mess? 
Thanks a lot!

---

### Post by ferraz75 on 2011-09-29
Hi!

I had the same problem and that's what I've done:

1.- Unpack the file (a folder called 'cdroot' will appear)
2.- In the 'Terminal' go to the folder where you have the folder 'cdroot' and write: 
     sudo cdroot/autorun 

Its obvious that you can do it in some other (and faster) way, but as ubuntu freshmen that's the best way that I've found :).

Ferraz

---

