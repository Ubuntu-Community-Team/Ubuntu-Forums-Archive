---
title: "ATI Driver SNAFU"
date: 2011-03-11
forum: Hardware
---

### Post by Briasaurus Rex on 2011-03-11
So, a while back I confused the proprietary ATI driver for my Radeon 5600 by messing with the Ubuntu resolution settings and the ATI control center resolution settings at the same time. Not my brightest moment. Afterwards, the ATI control center ceased to open, claiming there were no drivers. Aside from being unable to access the control center, I lost no functionality.

Eventually I decided to reinstall the drivers to fix the control center. I followed the directions on [this page with a really long url]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch") to reinstall the drivers.

Now, when I boot up, I get a flash of the Ubuntu loading screen and then deep, unrelenting black.

So it seems I totally screwed up the driver situation. Any idea how to reconfigure them?

---

### Post by Farwalker on 2011-03-11
I had this exact same problem yesterday. When your system is booting, select the 'Recovery Mode' option at the grub menu. Tell it you want a root prompt. Then run ```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
``` and reboot. That should fix it!

---

### Post by Briasaurus Rex on 2011-03-14
Success! Thanks, pal!

---

