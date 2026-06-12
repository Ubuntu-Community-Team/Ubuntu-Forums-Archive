---
title: "Network Manager messing up wireless card?"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by Tsjies on 2007-02-27
Really need some help here because I can't believe what happened to me: I installed Network Manager and the Gnome applet. Just followed the book. Restarts and everything and I could see the applet, use it but could never connect to my AP. Couldn't find help on the internet so removed NM again, restored my interfaces file and never got my Wifi working again. Even reinstalled Dapper, thinking some crap must have stayed behind but that didn't help. No wifi. Tried the network card on another laptop and it wasn't recognised on that one either so I decided the card was broken even though the lights show activity.

Stupid me, tried the same thing again tonight with another card (a cisco aironet 350) and the same thing happened again.

I cannot imagine that both the cards are broken but after reinstalling ubuntu and on another system they don't work anymore so ....

Help realy appreciated.

Tsjies

---

### Post by kpkeerthi on 2007-02-27
Can you post the contents of /etc/network/interface?

---

### Post by Tsjies on 2007-02-28
This is the content of the interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-essid xxxxxx
wireless-key xxxxxxxxxxxxxxxxxxxxx

auto eth1

---

### Post by oranguman on 2007-03-01
try 

sudo gedit /etc/network/interface

then comment out (add # to start of lines) the lines about eth1, leaving your interfaces file looking like this:
  


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


#iface eth1 inet dhcp
#wireless-essid xxxxxx
#wireless-key xxxxxxxxxxxxxxxxxxxxx

#auto eth1




then reboot your computer. this may fix the problem.

---

