---
title: "HP zv5240us wireless"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by phantasmik on 2006-06-13
I got ubuntu up and working great on my laptop everything appears to be working flawlessly however the only thing that isnt working is wireless, it has a broadcom 54g built in wireless card, I followed the howto for setting up ndiswrapper however I am having no luck with that. is there anything else I can do? or am i doomed to have no wireless

I feel as though im sooo close, my wireless card light lights up whenever I open up the properties in my network settings

Alright sorry for posting this, the howto using fwcutter worked!!! after screwing with it some more

but could anyone tell me how to run network-manager

---

### Post by nwbearcat84 on 2006-07-01
Hey, I also have a hp zv5240us laptop and was wondering what steps you took to get your card to do that much with ndiswrapper?  I have not tried ndiswrapper with Ubuntu yet, however, I have tried just about everything with the fwcutter.  I got to the point where it would recognize the card, scan for networks and find them, but would not connect to my router (using the same network settings I used for a wireless card on one of my other computers).  Also, I know for a fact the cards in the cards will work (not easily) as I had it working one time with Mandriva 2005.  As for the network manager, what kind of router are you trying to connect to?

---

### Post by K.Mandla on 2006-07-01
There's a page in the wiki that talks about different ways to get a Broadcom card working.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

There are also a lot of howtos for specific models of Broadcom cards. Just search for "Broadcom howto."

---

### Post by nwbearcat84 on 2006-07-01
Yes, I had been searching through all of the "How To" forums for several days now (with no luck on the card working).  I still have not actually connected to the network (which is driving me crazy; I know it SHOULD work... I've even written some of my own scripts to get it to connect).  For phantismik, check this forum out [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174)  After following these steps--some are steps a lot of other forums leave out--my card became more responsive than I have seen it on any other attempt.

---

