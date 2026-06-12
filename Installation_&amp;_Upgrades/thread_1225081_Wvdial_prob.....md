---
title: "Wvdial prob...."
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by tanmoytherockstar on 2009-07-28
[B]Hi!!!!!!!
Its Tanmoy............
I have been using Windows XP for quite a long tym......But now I see UBUNTU much better......But the problem lies in the net connection......I have BSNL EVDO net modem and to connect it I need WvDial........but widout the net connection I am unable to install it.....
Please tell me, how can I download the prequired package using Windows XP and then install it in UBUNTU JAUNTY:confused::confused::confused::confused::confused::confused::confused::confused::confused::confused:[/B]

---

### Post by GeorgeVita on 2009-07-28
Hi **tanmoytherockstar**, from an older thread I copied the following:
> **GeorgeVita said:**
> ...It is a little bit difficult to restore the missing wvdial (in 9.04) **without having internet access to this pc**. Also we must say that this is a very strange situation. I managed to install, connect via wvdial and send this post. At first I downloaded the following packages (from a pc connected to the internet, any O.S.):

1. [http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download](http://packages.ubuntu.com/jaunty/i386/libxplc0.3.13/download)
2. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-base/download)
3. [http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download](http://packages.ubuntu.com/jaunty/i386/libwvstreams4.4-extras/download)
4. [http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download](http://packages.ubuntu.com/jaunty/i386/libuniconf4.4/download)
5. [http://packages.ubuntu.com/jaunty/i386/wvdial/download](http://packages.ubuntu.com/jaunty/i386/wvdial/download)

**Note that above are all for an i386 pc.**

I copied all to a USB memory stick, and then paste them to the ubuntu 9.04 running pc into **/var/cache/apt/archives/** directory using **sudo nautilus** from terminal. Then I installed all packages by double clicking the icon of each .deb package **in above order** (1,2,3,4 and finally 5) ignoring any message. Finally (after installation) I run wvdialconf, edit the /etc/wvdial.conf file and connected with **sudo wvdial**!

You can find a .zip file to [http://acomelectronics.com/GeorgeVita/restore_wvdial.html](http://acomelectronics.com/GeorgeVita/restore_wvdial.html)

Also search this forum for other info regarding your 'BSNL EVDO net modem' to be informed for other possible problems.

Regards,
George

---

### Post by vinutux on 2009-07-28
its Here [http://packages.ubuntu.com/jaunty/wvdial]("http://packages.ubuntu.com/jaunty/wvdial")

---

