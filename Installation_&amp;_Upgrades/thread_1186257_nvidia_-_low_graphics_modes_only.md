---
title: "nvidia - low graphics modes only"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by goslings on 2009-06-13
GeForce 4600 graphics worked under 8.10 attached to SGI monitor 
on boot up get message low graphic mode; faile to load
/usr/lib/xorg/modules/driver/nvidia_dr.so
nvidia (load failed;7)
no drivers 

can run in low graphics (sending this), but I want back my graphics that worked do well in Ubuntu 8.10 

So many post on Nvidia, everyone seems to have a different approach 
pls help - so much want to use Ubuntu 
but this fundamental out of the box failure is really putting me off
thanks
Ian

---

### Post by gradinaruvasile on 2009-06-13
Did u upgrade your system ?
If so, u should reinstall the drivers.

Go to Administration _> Hardware drivers
Dectivate the recommended driver IF it is activated. If not, leave it for now.


First generate a safe configuration fo your card
type

sudo dpkg-reconfigure -phigh xserver-xorg

in a terminal.

reboot

You should have a booting system.
Go to Administration _> Hardware drivers
Activate the recommended driver.

---

### Post by goslings on 2009-06-13
> **gradinaruvasile said:**
> Did u upgrade your system ?
If so, u should reinstall the drivers.
.
have to go and get my daughter will try in 30 mins but 
upgraded from 8.10 to 9.04 all was well compiz all etc 
now every time I try for 177 drivers or greater say cant install 
will try what you suggest and get back to you 
thanks

---

### Post by gradinaruvasile on 2009-06-13
U have an older card thats why u cant install. That is the reason for the existence of so many versions of the driver.

What options u have (recommended version)? U should install that one (should be 96 or 71 something)

---

### Post by goslings on 2009-06-13
> **gradinaruvasile said:**
> U have an older card thats why u cant install. That is the reason for the existence of so many versions of the driver.

What options u have (recommended version)? U should install that one (should be 96 or 71 something)

Annoying though because it all worked with 8.10 like a dream 
why should it be any different with 9.04 surely they maintain support as only a Sony machine from 2004?

---

### Post by goslings on 2009-06-13
[QUOTE=gradinaruvasile;7449434
You should have a booting system.
Go to Administration _> Hardware drivers
Activate the recommended driver.[/QUOTE]

ok thanks 
tried the above and I'm back to a decent resolution for the screen
my worry is that when I reboot again I'll be back where I was 
how do I ensure that it wont revert to the low graphics mode again 
regards
Ian

---

