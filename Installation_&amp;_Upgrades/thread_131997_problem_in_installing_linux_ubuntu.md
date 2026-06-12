---
title: "problem in installing linux ubuntu"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by AshishKakar on 2006-02-17
i tried installing linux ubuntu 5.10 on my acer laptop and when i press enter at the boot the computer loads two gz files and then it gives a message like:
"Uncompressing linux... Ok. Loading kernel." 
However this screen stays for around 25 minutes(dint have any more patience). i have enough memory(512mb) so that cannot be an issue. i even tried typing the command:
linux vga=771
at the boot. i was also conected to broadband. the screen went blank. can anyone tell me why there is no other display on the screen for 25 minutes?? or is it sposed tob this way???
thnx.

---

### Post by aysiu on 2006-02-17
It's not *supposed* to be that way.

The first problem sounds as if you may have a corrupted CD.

The second problem is a screen resolution thing. If you have a blank screen, try pressing Control-Alt-F1 and then logging in and typing ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by eAi on 2006-02-18
I'm having exactly the same issue, though I'm using the live cd not the install cd.

I'm using an acer laptop too (a TravelMate 4100). I get to the very first boot logo screen, hit enter and it does two loading... lines then does "Uncompressing linux... Ok. Loading kernel." and just stops, just like AshishKakar has. I've left it for 20 minutes and nothing has happened, the CD isn't being read, and the hard drive seems inactive. I've tried using "live-expert" which is identical. None of the options in the help seemed applicable.

I've tried 3 different live cds (all 5.10, ordered via ship-it) all have the same issue.

Anyone got any ideas?

---

### Post by AshishKakar on 2006-02-19
AWESOME!!!
hey eAi, ... i actually found the problem... i own a acer travel mate 3210 so i found that for my laptop i have "to pass the kernel a parameter noapic or the kernel will hang right on boot". u can search this site for more information on installation on your laptop.
[http://www.linux-on-laptops.com/acer.html](http://www.linux-on-laptops.com/acer.html)

---

