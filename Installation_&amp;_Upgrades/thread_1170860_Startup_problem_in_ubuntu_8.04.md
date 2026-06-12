---
title: "Startup problem in ubuntu 8.04"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by theio_vrefos on 2009-05-26
My little sister has a dual boot windows XP / 64bit ubuntu 8.04 installed on her computer. Everything worked perfectly fine, until earlier today. 

After the ubuntu logo shows up with the loading bar, the screen disappears and only a flashing cursor is visible on a black background. 
I used the latest recovery option and i seem to get segmentation faults. I constantly get the message: "init[1] general protection rip". 

Anyone got any ideas about the cause of this error? It's not my computer, so it's hard to guess, but she usually applies any new updates. Maybe that's the problem. I'm thinking of booting with a live cd, mounting the hard disk and then re-applying the updates, but i don't have a clue about how to perform that last part :p

---

### Post by theio_vrefos on 2009-05-27
I'm going to try and bump this!

---

### Post by Sef on 2009-05-27
1) Please wait at least 24 hours before bumping your thread if no answers have been received.  Bumping too soon can get one a warning or infraction, but none will be given this time.

2) What is the graphics card?

---

### Post by theio_vrefos on 2009-05-27
> **Sef said:**
> 1) Please wait at least 24 hours before bumping your thread if no answers have been received.  Bumping too soon can get one a warning or infraction, but none will be given this time.

2) What is the graphics card?

1) I'm sorry, i wasn't aware of the bumping rules. Won't happen again. 

2) NVIDIA geforce 6600.

---

### Post by theio_vrefos on 2009-05-28
Bump!

---

### Post by theio_vrefos on 2009-05-31
Alright, i'll try one final bump.  
After some googling, i found [this]("http://forums.slamd64.com/viewtopic.php?f=4&t=1206").
It's pretty much the same problem i'm getting. It says [here]("http://bugs.slamd64.com/show_bug.cgi?id=375") that he managed to fix the error: 

> I did manage to rescue the system by booting the 12.0 install CD, then mounting the root volume (/dev/sda3 in my case) and using the "ROOT=/mnt upgradepkg" trick to return to sysvinit-2.86-x86_64_slamd64-8.

However i am unaware about which package to install. I found a package that the description said that it "boots up the system" and used dpkg, but it didn't work, it gave me a bunch of segmentation faults. 
Is there any way to use apt-get in a similar way?

---

