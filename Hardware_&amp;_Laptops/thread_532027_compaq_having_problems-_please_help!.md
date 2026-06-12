---
title: "compaq having problems- please help!"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by iDont on 2007-08-22
i have recently installed ubuntu for the first time and ive noticed something wrong with my sound.  my speaker setup is all wacked out.  instead of playing from only my speakers ,wich are plugged in through the headphone jack, it also plays from the speakers built in to my laptop.  anybody know whats up?

---

### Post by mstephens on 2007-08-22
Is this only a problem with Ubuntu ?

Normally jackplug sockets are wired up like a switch so that when you plug something in, the connection to internal speakers (or whatever) is physically broken. Most likely problem would be that the jackplug for the external speakers has not been pushed fully in.

---

### Post by iDont on 2007-08-22
dude, im not retarted, i know when something is plugged in or not.

---

### Post by fredj on 2007-08-23
You may not be retarded but I don't know how you expect us to help you since you don't
give any useful information.
If you want help then don't post your IQ. Post the make and model of your computer, the version
of Ubuntu that you are using and the name of the sound chip in your computer.
To get the name of the sound chip, open a terminal and type
sudo cat /proc/asound/card0/codec\#*
The first line of the output from this should give the name of your soundchip. If you don't get
any output from this then look under System->Preferences->Hardware Information for a 
soundchip name.
Your problem by the way is a common one especially in notebooks PCs.

---

