---
title: "Wifi problems..."
date: 2006-06-21
forum: Hardware &amp; Laptops
---

### Post by snakedog on 2006-06-21
...I'm running Win2000 on an old Thinkpad 600X and just got Xubuntu installed from the standard "live" cd.  

Everything seemed ok when booting from the cd to Xubuntu, including the wireless card, an Avaya (Orinico Gold) 802.11b PCMCIA card.  But upon rebooting after installing Xubuntu to the hdd, no wireless card.  Nothing I can find.

Funny thing is that the same card works under Ubuntu on my other laptop, a Toshiba A45-S120.

Go figure...somebody...

---

### Post by ubercat on 2006-07-04
I've had nothing but problems with wireless under ubuntu and xbuntu 6.06.
Both laptops are Dell. Laptop one -- a Dell LS 400 (400 copermine) -- has a fresh install of xubuntu (from an ISO), and will either hang when 'loading hardware drivers', and once up and running fails to see its Belkin F5D6020 card now at all! It's not there period. Breezy ran with this card out of the box.

Laptop two -- a Dell L400 (700 coppermine) -- is running ubuntu from an ordered CD. Good news: it found the same card and I set up wep with no problems. Bad news: it drops the connection when idle constantly. I run a terminal with ping set at an interval to keep the connection alive.

This Belkin card worked flawlessly on Breezy (with little work) and on Hoary (with the Atmel-firmware package installed). They're broken under both versions of Dapper.

I've read other not so stellar reviews of WiFi under Dapper. Do a web search and you'll get the picture.  I'm about ready to go to another distro :: the OS is free, and I really like ubuntu, but time is worth something, too! I'll probably go back to breezy for sanity's sake (and a wireless connection!!)

---

### Post by Bezdomny on 2006-07-05
I wouldn't be too hasty at moving to another distro. I've had my fair share of non working wireless in quite a few, xandros, linspire, suse, gentoo to name but a few. 

The problem didn't go away with Ubuntu. It seemed to like the WG511v2T but ignored the WG511v2 (marvel chipset) and seeing as my wife stole the 'T' for her lappy (coz it had a silver bit) I had to get the other working.

Installed the windows wireless support from the dapper CD. 

Copied the XP drivers from the netgear CD to a dir on HDD.

Terminal and ran something like:

#sudo ndiswrapper -i /netgear.drv/WG511v2.INF

#sudo ndiswrapper -m

#sudo modprobe ndiswrapper


Magically the green light flickered to life and the orange connect light blinked. When I went back into network admin the wireless was listed. I set the parameters and everything worked fine. 

Maybe this will work for you if you haven't already tried it?

---

