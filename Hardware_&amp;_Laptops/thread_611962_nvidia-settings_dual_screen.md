---
title: "nvidia-settings dual screen"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by yon2501 on 2007-11-13
ok so i upgraded to 7.10 but now i cant get my dual monitors working right with nvidia-settings manager. i want it set up with my laptop so that i can just plug it in and turn it on with dual screens but it acts as a normal single screen when not plugged thats how i had it before with 7.04. when i get the resolutions and the screen positions how i want them and hit apply it says meta mode error. says i cant have the same metamode for both screens but ive tried setting new meta modes but they dont work either. any ideas?

---

### Post by reedmb on 2007-11-15
Saw your inquiry. I do not have your precise answer. The type of message you received suggests a configuration issue. Manually changing your xorg.conf file may be most practical route with possible use of nvidia-settings.

These links at nvidia.com may contain your solution.
This is master list of versions:  [ftp://download.nvidia.com/XFree86/Linux-x86/](ftp://download.nvidia.com/XFree86/Linux-x86/) 
Using latest version as model:  [ftp://download.nvidia.com/XFree86/Linux-x86/100.14.23/README/README.txt](ftp://download.nvidia.com/XFree86/Linux-x86/100.14.23/README/README.txt) 
In this readme look at chapter 13, specifically 13.C
This is some of your metamodes information.
Info in 13 and FAQ below it may help.

Some freindly commentary:
Remember, various config keywords and attributes work together. Many problems are due to improper coordination of attributes and keywords sometimes in different sections. YOur friend is: make notes and change one thing at a time!
Since you upgraded Ubuntu version did you retain copy of previous xorg.config to use as a model for new Ub version? Also, I have not researched, since I'm still at V7.04, but I imagine V7.10 uses different version of nvidia drivers - different drivers sometimes mean new or changed keywords or attributes. And if new driver installed is it correct for your GPU and monitors? Nvidia made some changes earlier this year that resulted in non-standard package names. Standard practice would be if Ub installer could not interpret your xorg.conf it will give you a default one so you at least have a monitor to figure it all out! If you're lucky the attributes/keywords installer can not interpret are commented out and there waiting for your repair.
Cheers

---

### Post by yon2501 on 2007-11-16
well 7.10 has a screen manager built in this time round but no offense to the guys who made it but compared to the nvidia settings manager it sucks. but i think it may be interfering with nvidia settings in some way this morning i noticed that my login screen is actually a much lower resolution then when i log in, and i found out that its because of the way the ubuntu screen manager is set up. but when i tried to change it the resolution on my desktop messed up too. No i dont have the old .xorg file i only backed up my music movies and graphics work on my external when i upgraded. oddly enough the clone output function on nvidia settings still works without issue.

---

### Post by buntunub on 2007-11-16
This is a BIG issue with 7.10. MANY posts about this on these forums. Try turning off Xinerama and setup your screens normally, then save xorg.conf and restart X. Play with your settings till you get it right.

---

### Post by yon2501 on 2007-11-16
how do you turn off Xinerama?

---

