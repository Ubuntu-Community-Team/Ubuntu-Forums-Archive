---
title: "No NetworkManager Icon After Install"
date: 2010-02-19
forum: Hardware
---

### Post by Gary Jugert on 2010-02-19
I have searched the forums here and don't seem to find a solution to this problem. I don't have the little TVs I should have on the top task panel to assist in connecting to the internet. I've installed Ubuntu 9.10 as a dual boot on an HP Vista machine. The only thing I have is an antenna looking icon that says "No Network Connection." 

When I right-click add to panel, NetworkManager is not an option. Is it possible Ubuntu isn't recognizing my wireless card?? Help! If I can't get this fixed, I'll have to give up on Linux.

---

### Post by cchhrriiss121212 on 2010-02-20
That antenna icon is network manager, you just left click on it in order to see what network signals it is picking up. If there are none there it seems like your wireless card is not automatically recognized as you thought. This is a common problem with Ubuntu but it can usually be fixed.
Try finding out what wireless device you are using and then search for that on the forums. I had mine working after adding an extra line to etc/modules. It was automatically picked up in 9.04.

In the future it would be a good idea to try out Ubuntu using the live cd environment before installing.

---

