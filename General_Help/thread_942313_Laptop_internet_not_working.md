---
title: "Laptop internet not working"
date: 2008-10-09
forum: General Help
---

### Post by rangelbox on 2008-10-09
Just bought a dell inspiron 1525,Running vista.Setup my wireless network through the DSL modem everythings OK.Downloaded UBUNTU and internet does not work when i run it.???tonight is the first time im trying out this OS.Someone please help i wanna start doing cool things on it but i just cant with no internet when i switch to UBUNTU.   P.S i have my wireless card "ON" when i try to setup the internet with ubuntu   thanks alot guys:confused:

---

### Post by jonian_g on 2008-10-09
Provide more info. Which one of these wireless cards you have:

Dell Wireless 1390 802.11g Mini Card Wireless
Intel Pro/Wireless 3945 802.11 a/b/g Mini Card Wireless
Intel Pro/Wireless Next-Gen Wireless-N 802.11 a/g/n Mini Card Wireless
Dell Wireless 5720 EVDO Rev A mobile broadband mini-card
Dell Wireless 5510 HSPDA

If you don't know open a terminal in ubuntu and type:
```
lspci
```

---

### Post by roger_1960 on 2008-10-09
Hi

Are you runing the "Live" CD?  If so, be aware that it can be really slow to do anything.  Having said that:

Go sysytem-administration-network to get the network settings dialogue box

There should be a greyed out line saying "wireless connection"  If so, click unlock and enter your pasword. (grey should go away)  Select wirelessconnection and then check the "enable roaming mode" box

That could be it, unless of course the wireless isnt detected.......

---

### Post by rangelbox on 2008-10-09
Dell Wireless 1390 802.11g Mini Card Wireless

---

### Post by rangelbox on 2008-10-09
there is no wireless connection box just   wired connection and point to point connection

---

### Post by roger_1960 on 2008-10-09
I had a look in the other forums and found [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202e:%20R174291%20Driver%20Download/Extraction](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%202e:%20R174291%20Driver%20Download/Extraction)  which appears to relate to the problem.

I think the card is a BCM4311.  Have a look in the Networking & Wireless forum, or perhaps someone who has sorted his already can help!!

PS The first "sticky" in the networking forum relates to your problem as well.

---

### Post by rangelbox on 2008-10-09
thnks alot man.This little community of ubuntu clients is really crazyy!!lots of help and people to explain the information.Thanks again man have a good one

---

