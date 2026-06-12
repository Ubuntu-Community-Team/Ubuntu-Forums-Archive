---
title: "No propriety drivers are in use on this system"
date: 2010-04-03
forum: Hardware
---

### Post by sullenxone on 2010-04-03
Im semi-new to linux. and ive been learning how to deal with its work arounds when it confronts me with a problem. but im currently stuck on somthing that i would love some help with. im on my Dell Inspiron 1721, which uses broadcom bcm4311 wireless driver. i know the drivers come with ubuntu on installation. and i was previously able to use them, until i was in the middle of switching from ubuntu to windows xp. after i installed xp, i remembered why i got rid of windows in the first place and removed it and re-installed linux. when running off the boot disk. the drivers in System>Administration>Hardware Drivers are present and i can use them. but after i installed and running off hard disk i get a message in Hardware Drivers that says "No proprietary drivers are in use on this system". can someone please help me get my drivers (broadcom b43, STA) back so i can use my wireless again? any help is greatly appreciated. 

Note: (when installing both XP and ubuntu, i didnt partition i only formatted and used entire disk for both installations, so my disk was formatted for each installatoin(small harddrive so i thought it would be too difficult to manage space for two OS)).

---

### Post by mcoleman44 on 2010-04-03
sudo apt-get update
sudo apt-get upgrade
sudo reboot
The drivers should be listed when you log back in.

---

### Post by sullenxone on 2010-04-03
thank you so much. youve been a huge help. everything is fixed and working perfect. thank you again.

---

