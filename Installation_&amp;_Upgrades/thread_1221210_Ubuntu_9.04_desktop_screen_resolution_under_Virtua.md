---
title: "Ubuntu 9.04 desktop screen resolution under Virtual PC 2007"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by moxy_fruvus on 2009-07-23
I run Ubuntu 9.04 desktop in Microsoft Virtual PC 2007 SP1. I was able to install it using tips posted here and via blog entries at [www.arcanecode.com]("http://www.arcanecode.com") from April 2008. After installing 9.04 I found it ran only at 800 x 600 screen resolution. 
 
I was able to adjust the screen resolution in 9.04 by using the xorg.conf file from a working Virtual PC 2007 SP1 install of Ubuntu 8.04 desktop. There's lots of specific info that explains how to install and how to adjust the screen resolution of Ubuntu 8.04 desktop under Virtual PC 2007. 
 
To transfer the xorg.conf file into Ubuntu 9.04 I made a backup of my existing /etc/X11/xorg.conf file, e-mailed that file from one VPC session to another, copied the xorg.conf file into the /etc/X11 folder replacing the exisitng entry, and restarted the Ubuntu 9.04 session. When Ubuntu 9.04 restarted the GUI fired up using the same resolution I get under Ubuntu 8.04.
 
My real monitors run at 1152 x 864. I have Ubuntu 8.04 desktop running in VPC at 1152 x 864; this seems to work for Ubuntu 9.04. I suspect that when you configure the screen resultion for 8.04 on your machine you will end up with a different - and hopefully workable - screen resolution under 9.04.
 
Please don't ask me to post my xorg.conf file here. If you really want to work with Virtual PC 2007 it's worth it to spend a few minutes installing and configuring 8.04 desktop in your environment.

---

### Post by coolemon2006 on 2009-09-28
hey, can you send the link/step by step instructions about fixing this issue. Thanks a million

---

