---
title: "Ubuntu BB 5.10 Internet Access Help!"
date: 2005-11-07
forum: General Help
---

### Post by zdziczek on 2005-11-07
Ok I installed Ubunto Breezy Badger 5.10 onto a PC recently and the install went very smooth.  All I need to get going is internet access.  This computer was recently part of a server in a computer lab for a University and will be once I get this going I just have a few questions.  First off, I would say im about a 8 out of 10 (10 being a computer science grad, 5 being an average college student) in PC or windows knowledge and im just getting into linux.  I run a linux lab right now but I would like to upgrade to ubuntu from debian.  I installed Ubuntu but when network setup came up I tried to let it do it automatically but that failed so I hit 'do it later' and finished the install.  I guess my main question is what command or program should I use to set up the network settings?  I have looked in the network settings thing but didnt really know what to enter in there my linux knowledge is at about a 2 or 3 right now).  This computer is currently hooked up to about 10 other computers and would need to share there files as well (can post in a different thread if this is too much work).  For now I was wondering if anyone could show me how to gain internet access for this one computer for now or maybe even just point me in the right direction.  I have googled this but to no avail.. Any help is appreciated.. Thanks

(Let me know if you need any other info).

---

### Post by matthewv on 2005-11-07
How is the computer supposed to be accessing the internet. Does it have a separate modem, or..??

---

### Post by zdziczek on 2005-11-07
Sorry this computer will be accessing the internet via a working ethernet jack in a campus building.  Dont know if its T3 or what but I know its ethernet.

---

### Post by zdziczek on 2005-11-07
I guess im just curious as to whether ubuntu automatically detects and assigns internet properties or if i have to do it myself.  If i have to do it myself i would like maybe a step by step guide on how a newbie would do this.. if not its ok..

---

### Post by zekolas on 2005-11-07
It depends, if your network router/switch is set up for DHCP then linux will get an ip adress, gateway, dns adress from the router and this should not be a problem. However if your network is not set up for DHCP acess then you will have to staticly assign linux an ip adress ect.

Ubuntu defaults to use dhcp so if that is failing I would check out two things. Is your network card detected and working properly, or I would check with the network administrator to get the needed information to set up a static ip adress for the box.

---

### Post by zdziczek on 2005-11-08
[QUOTE=zekolas]It depends, if your network router/switch is set up for DHCP then linux will get an ip adress, gateway, dns adress from the router and this should not be a problem. However if your network is not set up for DHCP acess then you will have to staticly assign linux an ip adress ect.

Ubuntu defaults to use dhcp so if that is failing I would check out two things. Is your network card detected and working properly, or I would check with the network administrator to get the needed information to set up a static ip adress for the box.[/QUOTE]

All right, ill get back to you with that info.. This might be too hard for me to do.. ughhh

---

