---
title: "WIFI on Compaq nx7017 (ubuntu 6.10)"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by ankan on 2007-01-23
Hello, good afternoon.

I've just installed Ubuntu 6.10 on my compaq nx7017 laptop and after beeing away from the linux scene since 2001 it sure feels good to be back on track. There is, as expected, some minor problems to deal with, and the first one is to get the wifi going.

I've been googling the problem for quite a few hours today and find loads of results and tutorials, but I just cant get my head around how to get stuff to work anyway, so I figure that someone here might be able to point me in the right direction. 

From my old windows xp configuration I think i recalled having a ipw2200 wireless network card, and when entering  "lsmod | grep ipw" as root i get something like 
"ipw2200  234243 0
ieee80211 35235  1 ipw2200"

so it seems ubuntu found the card and the driver, right?

The next is how to configure the card, when going to "system -> administration" in X  the only networking applications i find are "networking" and "network tools", but none of these seem to do the job i am looking for. When pressing hte "networking" icon an application opens up with "wireless connection", "wired connection" and "modem connection". I press the "wireless connection" and I can fill out information about my home wireless which is run against a dhcp-router. I press OK and then I don't know what to do. The computer does not connect to the network (at least, I cannot connect to the internet) and I am stuck.

It seems obvious to me that I am missing something crucial but I cannot figure out what, and thus I ask here. Also, even if this might work it is only a semi-good sollution since you have to supply the ssid name before beeing able to connect to the network. How would i do if I want to search for a wifi network to connect to (as on a hotel or at the university?).

I found a tutorial on [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html) where there seems to be such a tool, but I cannot find it on my computer and the steps taken in that tutorial does not seem to help me on my quest to get the wireless working.

Hope that someone here will know what to do, 
sincerely
anders

---

