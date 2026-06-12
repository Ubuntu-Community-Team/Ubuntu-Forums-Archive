---
title: "Dell Inspiron Mini 12 Ubuntu problems"
date: 2008-12-27
forum: Hardware
---

### Post by tigersuit on 2008-12-27
So I got myself a Mini 12 and was patient enough to wait for the Ubuntu version.

When I opened the box I was quite excited of the low weight, slim design and overall nice workmanship.

But when I booted it the first time after I had gone through Dell EULA, answered all the Ubuntu-dialogues, disabled the DELL desktop and set up WLAN, the hassle began.
Booting took about one minute, which imho isnt good but acceptable.
The Gnome desktop was sloooooooow. Way slower than it was in Ubuntu 8.04.1 on my five year old single core 1,5ghz 1gb RAM desktop.
It took another one and a half minutes to automatically log in to my Wireless LAN.
There were a lot of (for me) useless KDE programs installed.
Compiz was installed but didnt work because the display driver is blacklisted.
It took Firefox and Thunderbird almost a minute to load and while loading they showed distorted fragments of previously opened windows or a black window. This happens with every program and even the desktop menu.
Firefox also had the well known flash bug and disabling IPv6 didnt work at all.
Sometimes there are strange bars showing in Firefox when scrolling or even on the desktop after closing FF.

Switching to Xfce made the overall performance a bit faster but the graphics and Firefox problems are still there.
I found that I have several intel display drivers installed:

xserver-xorg-video-i740
xserver-xorg-video-i810
xserver-xorg-video-intel

Anyone knows a fix for this?

---

