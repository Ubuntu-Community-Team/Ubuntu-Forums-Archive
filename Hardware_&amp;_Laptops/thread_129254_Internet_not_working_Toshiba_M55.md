---
title: "Internet not working Toshiba M55"
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by minhaferzz on 2006-02-13
I've been reading through a lot of threads and see people having success with the Intel 2200bg card, but unfortunately I don't.  The card is recognized and connects to my router without a problem, but the internet connection is intermittent at best and works for a maximum of 5 minutes.  I then attempt to deactivate and activate the wireless card and it may connect to the internet then.  It's capable of going to the router's admin page, but nothing from the net.  I'm also having trouble with the wired ethernet card.  It's a Marvell Yukon card and I'm not having any luck with it at all.

---

### Post by mdmarmer on 2006-02-13
Try adding a boot parameter to /boot/grub/menu.lst

edit the file as root and add a parameter such as acpi=off

I have M45-S331 and I boot with nofloppy acpi=off

Mike

---

### Post by drakeoutlaw on 2006-02-14
I had a similar problem with Intel 2200bg built in card. At long range the signal weakened and the machine would freeze. I downloaded latest ipw2200 driver from sourceforge, compiled and installed it and that fixed all problems. Go to [http://ipw2200.souceforge.net](http://ipw2200.souceforge.net) 

1.0.8 version works well.

Follow directions very carefully. Also download new firmware and 80211 as recommended in the install directions.

---

