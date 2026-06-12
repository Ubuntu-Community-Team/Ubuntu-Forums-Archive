---
title: "Bluetooth Mouse?"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by Nate Finch on 2007-01-08
I have an integrated bluetooth module in my laptop (a dell 9300).  I can't seem to find any UI for configuring bluetooth, or even turning it on or anything.   Looking in the help gets me to some command line stuff, but not really enough explanation to know where to start.  Searching the boards gets me lots of hits on getting bluetooth internet working, etc, but not anything as simple as just connecting a device (like my MX900 mouse).
 
I tried some steps that someone posted for connecting a phone, but it doesn't seem to be working.

Any help would be appreciated.

I'm running 6.10 if that helps.

-Nate

---

### Post by MikeBuffer on 2007-01-09
I found that all that was required to connect a bluetooth mouse was to put it into "find me" mode and run this command in a terminal window:

**sudo hidd --search**

My system is different to yours, however. I have a Dell Latitude D620 with integrated Bluetooth, on which I have installed 6.10 (64-bit version). Bluetooth was enabled by default (status light on as soon as I installed ubuntu) and HIDD, the bluetooth mouse/keyboard daemon, was also preinstalled. Bluetooth device management is activated under System - Administration - Services.

It would be nice if there was a GUI for enabling/disabling bluetooth devices. Anyone know of one?

Mike.

---

### Post by tonyric on 2007-01-09
I have some info and pointers to what I use on my D820 as the basis for any distro I use. 

NOTE: in further releases of KDE, Bluetooth GUI control will be included. I tried Sabayon or maybe it was OpenSuSE for a bit and the latest installs allowed gui control and detection of my bluetooth mouse.

Tony

---

### Post by Nate Finch on 2007-01-09
Thanks Mike, I'll give that a try when I get home.  Hopefully it'll just be that easy :)   

It's possible my bluetooth was enabled when I installed.... there just was no way for me to know (I don't remember if the bluetooth light on my laptop was on or not... but there should be some software indication as well).

-Nate

---

