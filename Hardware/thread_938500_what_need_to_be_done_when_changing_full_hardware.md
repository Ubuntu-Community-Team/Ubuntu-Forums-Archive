---
title: "what need to be done when changing full hardware??"
date: 2008-10-04
forum: Hardware
---

### Post by dinster on 2008-10-04
hi all

need your help here..

i need to move my nicely-setup-ubuntu from PC "A" to PC "B".. the latter has got newer specs..

question is how will ubuntu handles all the new hardware ??

will it be detected automatically ??

will it automatically remove all old drivers ?? 

i really do not want to fresh install ubuntu in my new PC ... 

pls help :confused:

---

### Post by cariboo on 2008-10-05
First of all remember Linux is not windows. When you change a motherboard on a windows system sometimes you get lucky and don't have to reinstall windows, but you do have to install drivers for all your peripherals. THen do the updates, because some manufacturers depend on Microsoft for drivers (notably USB2).

With a linux system all the open source drivers are already installed and just waiting for your hardware to be detected. Just have a look at /lib/modules. The only drivers you have to install are proprietary video drivers, and firmware updates for some of the cutting edge hardware that is out there, like the latest Intel e1000e network drivers.

So just hook up your old hard drive and you are good to go.

Jim

---

