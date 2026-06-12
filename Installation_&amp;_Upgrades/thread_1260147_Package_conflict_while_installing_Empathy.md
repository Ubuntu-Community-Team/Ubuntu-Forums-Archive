---
title: "Package conflict while installing Empathy"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by mohammedali on 2009-09-07
Hi all,

I installed ubuntu 9.04 (jaunty) server in my Desktop and installed Empathy based on the instruction given[ here]("http://live.gnome.org/Empathy/Install").Now Empathy is working , but no sounds.When I update the source list by issuing the command 'sudo apt-get update' it showing some conflict .The details are given below :

mohammedali@MyServer:~$ sudo apt-get install empathy telepathy-gabble telepathy-mission-control telepathy-stream-engine telepathy-butterfly python-msn
[sudo] password for mohammedali: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
empathy is already the newest version.
telepathy-gabble is already the newest version.
telepathy-stream-engine is already the newest version.
telepathy-butterfly is already the newest version.
python-msn is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  [COLOR=Red]telepathy-mission-control-5: Conflicts: telepathy-mission-control but 4.67-3ubuntu1~ppa9.04+1 is to be installed
E: Broken packages[/COLOR]
 can anybody help ?

---

