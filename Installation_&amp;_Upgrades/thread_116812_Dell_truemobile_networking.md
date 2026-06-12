---
title: "Dell truemobile networking"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by sonyfx210user on 2006-01-13
HI,
If I use live cd then the my dell truemobile 1150 card seems to work. If I install Ubuntu on hard disk then the card does not work. Any pointers?

---

### Post by curtis on 2006-01-13
Does it contain the Broadcom 4306 chipset?
If so, you may need to use Ndiswrapper.
But it working on the Live CD is strange, maybe it is a Intel Pro Wireless chipset.
Sorry but I could not help any more.

---

### Post by dsjas297 on 2006-01-13
Googling around, I found that your card uses a Hermes chipset. Search on Google to see if you can find any drivers.

---

### Post by sonyfx210user on 2006-01-15
OK I seem to have it working now. I was trying out different things since this is the first time I am using the debian based linux. I used synaptic to download the software for prism2. That seems to have fixed the problem.

Are there any gui based wireless network configuration toolds other than System-> Administration-> Networking

---

### Post by toorima on 2006-01-15
sudo apt-get install network-manager
put nm-applet in System-Preferences-Sessions-Startup Programs with order 10 to make it autostart

---

