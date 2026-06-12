---
title: "Weather Report Applet"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by ForgivenByJC on 2009-05-03
I just upgraded from 8.10 to 9.04.  My desktop did so a little easier than my laptop.  Laptop is old (ECS Green732) but works very well.  When upgrading from 8.10 to 9.04 my gnome panel weather report applet stopped updating the weather on the laptop.  The desktop one works (so I know it is not a network firewall issue or a US National Weather Service (NWS) issue).  I tried to look through the logs, but did not find anything which made sense.  Have not been able to turn anything up on searches.  Ideas???  I am at a complete loss!

---

### Post by ForgivenByJC on 2009-05-09
My issue was solved by changing ~/.gconf/system to ~/.gconf/system.bak and then logging out and back in.  If you would like to follow what I did [https://bugs.launchpad.net/bugs/372647](https://bugs.launchpad.net/bugs/372647).  Hope this help people.  John

---

