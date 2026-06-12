---
title: "YUY2 support for SiS Graphics chip?"
date: 2006-10-18
forum: Hardware &amp; Laptops
---

### Post by gsham on 2006-10-18
I am running Xubuntu, and have run across a problem while trying to use tvtime:

```
gsham@roombox:~$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/gsham/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

gsham@roombox:~$ 
```

problem: I am using the sis graphics chip built in to my motherboard, and the "sis" driver under X.  so obviously the suggested remedies are lacking.  I know that I was able to use tvtime with slackware and fedora core 4 using the "sis" driver, so I assume the chip/driver supports YUY2, but how do I enable this support?  

or alternatively, what is a good tv tuner program that I can use that doesn't require YUY2?

---

### Post by gsham on 2006-10-18
nevermind, it seems that xorg defaulted to vesa instead of sis.  changing the driver entry in the xorg.conf file from vesa to sis fixed it.

---

