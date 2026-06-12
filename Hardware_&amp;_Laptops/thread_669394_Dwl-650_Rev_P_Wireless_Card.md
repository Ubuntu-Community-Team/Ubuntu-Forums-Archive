---
title: "Dwl-650 Rev P Wireless Card"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by jic1997 on 2008-01-16
Hello All,

I'm new to Ubuntu and would like to make it work.  However, I can't seem to get the above-referenced card to work at all.  I've tried using ndiswrapper and ndisgkt to install the windows drivers.  When I run iwconfig I get an wifi0 and wlan0, both say managed. when I run ndiswrapper -l  I get "netprism: driver installed."  when i go to ndisgkt and try to install the windows drivers (after having placed the .inf & .sys files into my home directory from the windows disk,) I get a message that says "driver already installed," but nothing shows up in the ndisgkt display as an installed driver.....can anyone give a clue as to what to do?  Thanks, Jim Collins

---

### Post by DonCoryon on 2008-05-13
I am having the same problem. Did you ever get this card to work?

I'm running a Persario 900us notebook with a Dlink dwl-650 rev p wireless card. I have installed ndiswrapper and when I run [INDENT]ndiswrapper -l[/INDENT] I receive 

[INDENT]netprism: driver installed
[/INDENT]

---

### Post by rpwdh on 2008-05-13
Ok... I'm a total n00b with Umbuntu but I had a terrible time getting my broadcom card to work. It seems that you have to start with a hard wired connection so the system can go out and fetch the firmware.

I banged my head against a wall for two days and was about to give up before I found this out. ](*,)

Your sustem may download all kinds of updates first but that's ok too.

Good luck! \\:D/

---

### Post by DonCoryon on 2008-05-13
When you say start with a hard wired connection, do you mean I must be connected to the internet via my regular Ethernet connection as well as have a wireless router available at the same time?

If so that would pose a problem. At home I only have a regular Ethernet router. I am planning on using the Wifi at the library, Starbucks, etc...

---

