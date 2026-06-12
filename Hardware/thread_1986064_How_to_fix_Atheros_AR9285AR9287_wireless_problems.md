---
title: "How to fix Atheros AR9285/AR9287 wireless problems"
date: 2012-05-24
forum: Hardware
---

### Post by jcer93705 on 2012-05-24
Hi guys I finally switch over. I tried Xubuntu 12.04 for over a week dual booting with Window 7. I fell in love with Xubuntu 12.04 everything is working correctly except I had to modified so I can have a stablet internet speed. Wow it was slow without doing so. Sometime it wont response. This is what I did. 

Create a new file /etc/modprobe.d/ath9k.conf:

sudo nano /etc/modprobe.d/ath9k.conf

Add the following line to it:

options ath9k nohwcrypt=1

So this is the fix for Atheros AR9287 wifi. 

Sourced: [http://linuxblog.avserver.info/how-to-fix-atheros-ar9285-ar9287-wireless-problems-in-ubuntu-1104/](http://linuxblog.avserver.info/how-to-fix-atheros-ar9285-ar9287-wireless-problems-in-ubuntu-1104/)

---

