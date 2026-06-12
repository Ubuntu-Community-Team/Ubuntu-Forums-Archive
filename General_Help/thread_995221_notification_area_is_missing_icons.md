---
title: "notification area is missing icons"
date: 2008-11-27
forum: General Help
---

### Post by meandi2 on 2008-11-27
My network-pictograms in the notification area are being stolen, and no alarm goes off.
I updated my ubuntu to 8.10 and some time after that my network-manager-gnome-pictogram went missing (applet-thingy).
I found a easy solution by installing wicd instead of the previous network-manger.
But now the wicd-pictogram is also missing from the notification area.

The only thing left in the notification area is the battery-level

ifconfig shows me being connected

and

/etc/network/interfaces:

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

so wicd is working (also shows up with "ps -A")
5394 ?        00:00:06 wicd

Any idea's on how to get it back would be helpfull

---

### Post by meandi2 on 2008-12-02
I do(did) a reïnstall to fix this. (2 bad no solution here)

---

