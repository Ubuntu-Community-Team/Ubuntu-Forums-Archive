---
title: "Intel Wireless 2200 a/b/g not working!!! (Asus Z33A - Gutsy)"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by jferreir on 2008-01-09
I'm using an Asus Z33A with an Intel 2200 a/b/g wireless card running on Ubuntu 7.10. I can't get my wireless internet to work - the blue LED is off which indicates that the wireless card is not turned on. The guys at the IT help desk helped me diagnose the problem - the 'kill switch' might be on which is why I cannot enable the wireless via Fn + F2.

There have been known issues with this card and the associated kill switch, but I haven't been able to find a solution that works. I switched to Linux from XP about a week ago, and the wireless card worked fine after the install. It crapped out this morning for no apparent reason (nothing was installed and nothing was updated). This is the only major issue and I can still connect to the internet via a wired connection. I'm not dual-booting with XP, so logging into XP and re-enabling the radio switch is not an option. The BIOS is updated, but I know that the driver for the wireless card was updated this past August. Since I'm not running XP, I'm not sure how to install it or if I even need to (since it was working earlier).

I tried entering the following commands to disable the kill switch but I received the "permission denied" error message.

sudo echo fsam7400 >> /etc/modules
sudo echo options fsam7400 radio=1 >> /etc/modprob.d/options

I'm a complete computer noob (no comp background), and I switched to Linux for increased stability over XP (not a wise choice in hindsight). If you need any further information, please ask, and kindly remember that I need idiot proof instructions. Any help is greatly appreciated!!

THANKS!!!!

---

### Post by BUGabundo on 2008-05-12
did u manage to make this work?
I bought a new laptop and am having the same problem with an ASmobile (an Asus barebone)

---

