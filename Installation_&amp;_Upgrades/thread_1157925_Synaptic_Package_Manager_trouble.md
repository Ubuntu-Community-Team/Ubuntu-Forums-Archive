---
title: "Synaptic Package Manager trouble"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by Eric7772000 on 2009-05-13
I have been trying to install version 6 of Java on my machine, and have had nothing but headaches. But now the real problem is, now when I go to open my Synaptic Package Manager, I get this message:

  	 	 	 	 	   	 	 	 	 	 	  "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  
 E: _cache->open() failed, please report."


When I tried to run 'dpkg --configure -a', I was denied. I have to have "superuser" status. I built this machine with my own two hands...if I don't have "superuser" status on it, nobody does.

I really hope I didn't screw things up beyond repair. I have no idea what to do.

Please Help!!:confused:

---

### Post by Kevbert on 2009-05-13
Welcome to the forums.
With superuser status it should work. If you use
```
sudo dpkg --configure -a
```
and that works in terminal, then you've found a bug that needs to be reported in Lauchpad. It may also be worth running
```
sudo apt-get install -f
```

---

### Post by Eric7772000 on 2009-05-13
Oh! Hallelujah! Thank You,Thank You,Thank You!! I was really scared there for a minute!  *big sigh of relief* :D

---

