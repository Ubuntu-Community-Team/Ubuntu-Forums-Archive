---
title: "Atheros Wifi Card"
date: 2009-11-23
forum: Hardware
---

### Post by cjms85 on 2009-11-23
Hi all,

I'm a complete novice when it comes to Ubuntu, so please forgive me posting on a topic that has probably been covered to death.

I have a Fujitsu Siemens laptop with an Atheros AR5100 Wifi card, however after installining Ubuntu 9.10 Karmic Koala, Ubuntu does not recognise my wifi card.

Can someone please explain to me in very basic terms how to go about getting Ubuntu to recognise and utilise the wireless card?

Cheers,

Chris

---

### Post by Some Penguin on 2009-11-24
Having recently helped a friend of mine install Ubuntu 9.10 on a fairly ancient laptop and get a cheap CP Tech/Level One Cardbus adapter w/ an Atheros 5K chip, what I'm thinking is perhaps the kernel is properly detecting the wireless card but you don't know how to properly configure it to connect to a network, and would like something friendlier than the default wireless manager.  IIRC, we did have issues getting some hardware working (the touchpad in particular is, well, touchy) but the ath5k was actually working fine.

If it's being detected (some poking with 'dmesg', 'iwconfig', and/or 'ifconfig' would probably show a wmaster0 or wlan0 interface if it is...) you might want to look at

[http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html](http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html)

since wicd seems to be a very friendly program -- it shows you see the wireless networks it detects and easily filling in the fields to connect to any, and so forth.

---

### Post by JohnLinuxNoob on 2009-12-07
Hello. I am in need of some help. I recently had gOS installed on my Gateway LT3103u netbook. From what I understand, gOS is based off Ubuntu Hardy Heron. gOS works really well on my computer, with the sole exception of my wireless network card. The card is an Atheros AR5B95 Wireless Network Card. The problem initially was gOS did not even see the card there. The person who actually did most of the work on this install did get the os to recognize the fact that there is a wireless card, but I still can't log onto wireless networks. Can anyone help me?

---

### Post by cyberey66 on 2010-01-14
You have to install backports and then it will be recognized.

---

