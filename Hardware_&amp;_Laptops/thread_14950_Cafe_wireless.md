---
title: "Cafe wireless"
date: 2005-02-10
forum: Hardware &amp; Laptops
---

### Post by stevetxt on 2005-02-10
I don't have a wireless connection at home, but sometimes use one in a cafe, airport, or hotel.  I bought a d-link dwl 650 pcmcia wireless card for my laptop having read that one is well supported in Ubuntu (mine has an atheros chipset).  The card itself does indeed seem to be well detected and configured by Ubuntu hotplug stuff.  However, since I use it in a different location each time, it seems to need to know the name of the network (ESSID) wherever I am.  I got it to work my typing "iwlist scanning" in a terminal, which gave me the name of the cafe's network.  Then I went to the gnome computer > system configuration > networking graphical menu screen and put that name in the configuration.  

Is there an easier, more cohesive way to do this.  Is there one way that would be all graphical and another way that would be all command line?  Is there a way to have the scanning automatic as it is with a Windows XP or MacIntosh OSX system?  

I'd be interested to hear how others solve this problem.

Steve

---

### Post by az on 2005-02-11
apt-cache show waproamd

---

### Post by cblack on 2005-02-11
[waproamd](http://0pointer.de/lennart/projects/waproamd/)  has a few security issues. The author of the program suggests switching to wpa_supplicant. 

You could also give [NetworkManager](http://people.ubuntu.com/~thom/network-manager/)  a try.

---

