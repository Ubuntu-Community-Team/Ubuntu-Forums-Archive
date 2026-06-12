---
title: "Rescue ubuntu 8.10"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by maneski on 2009-01-01
How do i rescue ubuntu 8.10?

---

### Post by Herman on 2009-01-01
[Rescue your Linux system with a Live CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")

---

### Post by maneski on 2009-01-03
my problem is that, I cant get GUI interface anymore. How do I fix this.
Any code if I have to use the rescue cd?

---

### Post by Sef on 2009-01-03
1) Did you install anything just before this problem?

2) Did you do anything else?

3) What is your graphics card?

---

### Post by Pumalite on 2009-01-03
What amount of memory do you have and what iso did you install?

---

### Post by maneski on 2009-01-14
I am using Toshiba Satellite L305 with an intel graphics card.
HDD : 320
RAM: 4Gig

The last thing I did want installing softwares using the synaptic manager(I dont rem exactly what)
Any help?

---

### Post by northrkm on 2009-01-14
Im going to bump this... I have a friend that has a toshiba laptop that we tried installing linux on, and it won't work so i am interested in seeing this repair with linux solution.

@maneski did you have any trouble installing linux to begin with?

---

### Post by northrkm on 2009-01-14
I think they mean put the cd and reboot, and there is a repair linux option. I am assuming that it has the same function as "safe mode" for windows machines.

Edit- Upon restarting the system and going into the boot menu, there is the normal startup option and there is a copy of the same command, except there is (recovery mode) at the end of it. From there it will take you through all of the normal start-up processes and brings up a blue window with 4 or 5 choices. And you go from there. I am not sure what to do.

---

### Post by pdk on 2009-01-21
Hi 
You possibly had a crash during your update.
ALT + CTL + F2  to get a terminal. Become root and
recover from broken update in package manager
dpkg --configure -a
Peter

---

