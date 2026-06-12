---
title: "system crashed before finishing upgrade"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by k956411 on 2008-12-14
Last night i decided to upgrade my system to 8.10 using synaptic and all seemed to go according to plan for most of it.
Unfortunately when it was saying about 20 mins to go my computer froze up completely.
I don't think it was the updater that froze the system because it happened just as i started a different app (movie player)
I left the system for ages to see if it would recover but it didn't and i ended up having to hard reset.
Ubuntu seems to be running fine but obviously some of the updated packages didn't get installed. 
synaptics now says its all up to date.
is there anyway i can verify what has installed correctly and what isn't or even get the system to re run the upgrade?

---

### Post by Pumalite on 2008-12-14
Try:
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by k956411 on 2008-12-15
Thanks that did the trick.

a bunch more stuff got installed and everything seems good now

---

### Post by arjay27529 on 2008-12-15
had the same problem.  followed instructions listed in previous reply.  got message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

does this mean that it is really now complete?  while it has booted, it took some doing to get it to boot.  had to go through several recovery steps to get it to boot.  so is it done?

---

### Post by abn91c on 2008-12-15
> **arjay27529 said:**
> had the same problem.  followed instructions listed in previous reply.  got message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

does this mean that it is really now complete?  while it has booted, it took some doing to get it to boot.  had to go through several recovery steps to get it to boot.  so is it done?

yes you are done, reboot and see what happens, just to make sure do sudo dpkg --configure -a, if you get no errors then you are good.

---

### Post by arjay27529 on 2008-12-16
abn91c

thank you.  i attempted to shut down for the night but the system automatically rebooted.

everything seems perfectly normal now. even seems a bit faster.

thanks again!!!

---

