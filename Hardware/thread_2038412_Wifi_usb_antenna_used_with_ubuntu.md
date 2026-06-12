---
title: "Wifi usb antenna used with ubuntu"
date: 2012-08-06
forum: Hardware
---

### Post by darthpbal on 2012-08-06
I'm trying to use a netgear N300 wireless usb adapter (WNA3100 if you need that) with my ubuntu desktop and my machine isn't recognizing it. I wanted to know if there was a driver that I can download and install or something? Any help is greatly appreciated. :)

---

### Post by lukeiamyourfather on 2012-08-06
As far as I know there's zero official support for Netgear adapters on Linux. I bought a wireless adapter some years ago which was my first and last adapter from Netgear after I found out it was supported only under Windows. Though it looks like some users have been able to get them working (depending on the specific model). The video is old but you get the idea.

[http://www.youtube.com/watch?v=DNR0Wvg1k5I](http://www.youtube.com/watch?v=DNR0Wvg1k5I)

---

### Post by ajgreeny on 2012-08-06
It may be worth trying with ndisgtk, available in the repos.  This will add a Windows Wireless Drivers item to your menu (or the dash in 12.04) which may allow you to use the Windows drivers, or at least the **WNA3100.inf** file that should be on the CD (for windows) that came with the adapter, or if not can probably be found on the web.

I have to use that manner of installing the driver for my Netgear WG511v2 pcmcia card, but once installed that way it works extremely well.

See [http://ubuntuforums.org/showthread.php?t=1946875]("http://ubuntuforums.org/showthread.php?t=1946875&page=2") for one successful attempt, and this googlubuntu page for lots more info. [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=WNA3100&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=WNA3100&as_qdr=all&sa=Google+Search&lang=en")

---

### Post by gordintoronto on 2012-08-06
Perhaps this will help:
[http://ubuntuforums.org/showthread.php?t=1695036](http://ubuntuforums.org/showthread.php?t=1695036)

---

