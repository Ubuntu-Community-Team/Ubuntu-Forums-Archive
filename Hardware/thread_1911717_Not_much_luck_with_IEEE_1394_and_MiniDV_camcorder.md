---
title: "Not much luck with IEEE 1394 and MiniDV camcorder"
date: 2012-01-19
forum: Hardware
---

### Post by Saulevas on 2012-01-19
Hello, everyone,

I tried reading many posts regarding firewire issue on Linux Mint and Ubuntu, but had no luck connecting my MiniDV camera to my PC running Ubuntu 11.10. The thing is that by running lspci in terminal among other things I get:
05:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
This probably means that my firewire card is recognized by Ubuntu.
I install Kino and try to capture I get an error saying "raw1394 kernel module not loaded....". Ok, so I start Kino as root and get "No AV/C compliant cam connected or not switched on?" despite the fact that my cam is switched on. I tried it with two different cameras, both of them work fine in Windows.   
dvgrab (comes with Kino I suppose) is also installed. 
I read through this topic (it's on LinuxMint forum, but I guess both systems have much in common) viewtopic.php?f=49&t=42348&p=528509#p528509 but still had no luck.
What could be the problem? 


Looking forward to help.

---

### Post by doctorzeus on 2012-01-19
You may find [this]("flavio.tordini.org/firewire-mini-dv-cameras-on") and [this]("http://ubuntuforums.org/showthread.php?t=1391735") helpful..

Hope this Helps!

DoctorZeus

---

### Post by Saulevas on 2012-01-20
doctorzeus, thanks for your input. However none of this helps - I still get "No AV/C compliant cam connected or not switched on?".... :(

---

