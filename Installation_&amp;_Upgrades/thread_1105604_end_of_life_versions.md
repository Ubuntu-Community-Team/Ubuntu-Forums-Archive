---
title: "end of life versions"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by dpj23 on 2009-03-24
[FONT="Verdana"]O.K., I'm going to ask a basic questions about upgrading.

1. 7.10 is retiring on 4.19.. And whenever a version is retired I think about if I where running that version why would I have to upgrade at all..  Why would it be a bad thing to just keep on running that version for a year or so longer??? I understand you would miss some of the enhancements, but a configured OS maybe worth more than enhancements.    

2. Wouldn't it better as a end user to download and install the LTS server edition and then install gnome desktop and configure it to run as a desktop. Then I would have a version that I could run for 5 years instead of 3.  


It would be interesting to hear if someone has decided to stay longer on version past it's life cycle and if they ran into any problems.[/FONT]

---

### Post by x33a on 2009-03-24
as for the first point, support isn't just about enhancements, infact it's more about fixing bugs and security vulnerabilities. so you would be running a buggy and possibly less secure system without the updates. 

as for the server edition, you'll have to heavily tweak it for desktop usage.

---

### Post by eythian on 2009-03-25
> **x33a said:**
> as for the first point, support isn't just about enhancements, infact it's more about fixing bugs and security vulnerabilities. so you would be running a buggy and possibly less secure system without the updates.
(IMHO) security is really the main kicker here, but your other points are quite correct.

> **x33a said:**
> as for the server edition, you'll have to heavily tweak it for desktop usage.
Well, the tweaking should be done by installing the -desktop packages. And then you're not really running the server any more. There is no real difference between the server install and the desktop install, aside from the packages you have. In particular, they both pull from the same repositories. However, when the desktop version is EOLed, the desktop components won't see any more updates, however the server components may. For example, you won't get security updates to the firefox package, but you might get them to openssh-server.

---

### Post by cudBwrong on 2009-03-25
> **dpj23 said:**
> [FONT="Verdana"]O.K., I'm going to ask a basic questions about upgrading.

[ ... ]  

2. Wouldn't it better as a end user to download and install the LTS server edition and then install gnome desktop and configure it to run as a desktop. Then I would have a version that I could run for 5 years instead of 3.  


It would be interesting to hear if someone has decided to stay longer on version past it's life cycle and if they ran into any problems.[/FONT]

Forgive me if you already are aware of this, but note that the LTS long term support releases also come in desktop versions.  So if you would like to avoid a major upgrade as long as possible, you could choose an LTS desktop release, instead of trying to add desktop packages or configuration settings to a server version.  Of course, "Long" in LTS means even longer (two years extra) for the server releases. With the high frequency of security updates, and the plague of malware in the wild, I wouldn't want to go without the update notices.

---

