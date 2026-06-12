---
title: "Just Getting Started... Getting Nowhere...."
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by Swanbot on 2008-12-03
So I have done some searching, and I think I am in so deep with problems that I do not even know where to start. I am running Ubuntu for the first time on a Dell Latitude D800 that normally runs Windows XP. For starters I want to do a full install (removing XP completely) but once I boot into Ubuntu I do not see where to do this. I try opening the disc but get "Error: Cannnot find autorun program." I also cannot connect to the internet and all options for connections are greyed out (I have wireless connection normally). Also it wants me to Activate some drivers, but even after authenticating the session clicking Activate does nothing. As you can see I am in rather over my head. One thing I have considered is maybe I need drivers from Dell? Any ideas or any answers to any of these painful questions would be greatly appreciated. Thank you!

Edit: This is 8.10, which I think is why a lot of what my search results don't match what I am seeing on screen.

---

### Post by inobe on 2008-12-03
hi, i will try to help.

first tell us what was in drivers you enabled ?

also it would be a good idea to go wired internet in case we need to install firmware.

edit: in restricted drivers' was broadcom present ?

if not, refer to this post

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=833797](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=833797)

---

### Post by Flag on 2008-12-03
Hi, just tell us how far you are.
You do have an ISO image I guess ?
Make sure you have your wifi drivers ****.inf and ****.sys
Make sure your system boots from the ISO disc, I had to run it as " live " first and then on the desktop click install.
First thing to do after installation is enable wifi, go to system->admin->software sources, make sure your ISO disc is inserted and click to enable, then go to system--> admin synaptic install ndiswrapper / ndisgtk. Once done go to system--> admin you'll find at the bottom windows wireless drivers, click, install, update system.

---

### Post by Swanbot on 2008-12-03
Hey I am going to bed but I will follow advice and report back tomorrow. While I sleep I am trying a live install instead of the inside windows I did before.

---

### Post by Swanbot on 2008-12-03
Edit: Status Update...

Playing around got fwcutter open in Terminal, now the Broadcom B43 wireless driver is under Hardware Drivers, but when I click Activate it goes to 50% and then nothing happens.

---

