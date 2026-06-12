---
title: "Laptop Keyboard"
date: 2008-09-30
forum: Hardware
---

### Post by Sub101 on 2008-09-30
Hi, Ive had Ubuntu running on my laptop for about 2 years now with very few issues. However for some reason my internal keyboard has now stopped working. It works at Grub but beyond that it does not. 
  
I decided to attempt to reformat the partition and start again as I have no important data on here. So i used the Alternate CD but again the keyboard would not work. I thought any issues would not affect this boot so am now unsure on what to do. External keyboards do work and the keyboard does work from Vista where i am typing this from.

The thing that has confused me is that i have not changed anything, all i have done which was different from normal was use a OpenSolaris live cd. 

So if anyone has any ideas on this one? I am happy to reformat but am now unsure if it would resolve the problem.

Thanks for your time.

---

### Post by Sub101 on 2008-10-01
Well I managed to solve this one so thought I would explain how I did it. 

 To get the keyboard working was relatively simple really. I just reset the CMOS which seemed to fix the issue. 

 On top of that I have now installed OpenSolaris and there is no longer any keyboard issues.

---

### Post by DataMonkey on 2008-10-01
I am actually having the same problem at the moment. I've been running Gutsy for about a year or more now with no problems. Then a few hours ago the keyboard stops responding during a session. I wasn't changing anything system-wise, wasn't even in su mode.

I tried loading the defaults for the CMOS with no change. Did you hardware-reset the CMOS or just software?

I have also dpkg-reconfigured the xorg.conf with no change.

cheers

---

### Post by Sub101 on 2008-10-02
Not sure whether I hardware reset or software reset? Basically I unplugged all the power and main battery then opened it up and unplugged the BIOS battery as I couldn't find the jumpers on my laptop. Anyway I left it unplugged for 15 seconds and plugged it back in and it all worked fine. 

Is yours working at elsewhere like in Grub or is it completely system wide?

---

### Post by Chibi-Tatsu on 2008-10-20
I had this happen to me suddenly; anyone know what causes it?

External (USB) mice and keyboards work fine; internal keyboard works fine with GRUB.  But at the login screen and after... no dice.  It's really rather frustrating -_-;

---

