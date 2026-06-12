---
title: "Crossfire"
date: 2009-09-25
forum: Hardware
---

### Post by shaker108 on 2009-09-25
Hi,

I have built a new pc that I dual boot (windows 7 64bit/ubuntu 64bit) and I was wondering if crossfire works in Ubuntu? I don't really care about graphical performance when using Linux as long as the gui works (desktop effects would be nice too).

---

### Post by swoody on 2009-09-25
Are you referring to using hybrid-x wherein you use one built-in graphics card, and one discrete graphics card? Or are you referring to using two discrete ATi cards?

From what I can tell crossfire on two discrete cards *should* work in Ubuntu. Using the latest ATi Linux drivers, and using the Catalyst Control Center you should be able to enable crossfire. However, ATi has been known for their fairly bad linux support, and many people in the past have had troubles running simple ATi setups. Hopefully somebody who knows more specifics, or someone who has done it successfully can lend you a hand here :)

---

### Post by shaker108 on 2009-09-26
I'm going to use two regular graphics cards so there wont be any on-board GPU. Also its not important for me to enable crossfire in Ubuntu I just want to be able to use the GUI with two cards installed. But I guess that there wont be any problems.

---

### Post by swoody on 2009-09-28
Well, if they're not in Crossfire, you may have issues with 'multiple possible outputs' and not have your screen shown on your actual monitor. I had this issue running two Nvidia cards which were not in SLI. This is a pretty easy fix by specifying in your /etc/X11/xorg.conf file the UUID of the output/monitor you want to use. It has been some time since I've done this, so I can't give you a ton of details, but I know someone on here would be able to assist you if you encounter that issue. I don't think that this would be an issue with Crossfire enabled, though, as they would work together and only give you one 'output'.

---

