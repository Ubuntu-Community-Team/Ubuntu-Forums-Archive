---
title: "Ubuntu 8.10 network and battery management suite problem"
date: 2009-07-07
forum: Hardware
---

### Post by bastienauneau on 2009-07-07
Hi everyone

I have a friend who's computer run under Ubuntu 8.10 (Yes I'm proud that I after few month of preaching, almost non of my friends have windows anymore !). She has now troubles with the network manager and cannot access the wireless network available. Here are the steps (I suppose she went through)
1. Ubuntu 8.10 is working perfectly fine
2. by mistake someone remove from the up panel the network manager
3. she tried to fix it herself (very good so far), so she decided to go to "add/remove application" and to uncheck then check again the network management. Doing that she got internet back at home with the wire
4. but now it's hard to get the wireless to work. left click on the network management gives the network properties instead of wired and wireless network prperties. Right click does not show anymore the "Enable network" and "Enable wireless". Also it seams to be some old network management, without support for browsing available wireless networks. I think that by uninstalling/installing back the network management she removed some extra layer working on the network manager. This must include some icon suite because the power supply icon is different from what I can see usually, and it does not offer all the feature of the usual one. Also the notification for new update available does not appear anymore.

Any suggestion ? What if I upgrade to 9.04, will it put this back ? Or Am I doomed to re-install ubuntu from scratch to her laptop ?

Thanks
Bastien

---

### Post by bastienauneau on 2009-07-07
anyone ?

---

### Post by d_liebscher on 2009-07-07
Hi,

what desktop environment does she use? KDE 3.x, KDE 4.x, Gnome, ...?

Daniel

---

### Post by bastienauneau on 2009-07-08
It's the default install of Ubuntu 8.10, so Gnome

---

### Post by bastienauneau on 2009-07-09
any idea ?

---

### Post by gradinaruvasile on 2009-07-09
> **bastienauneau said:**
> Hi everyone

I have a friend who's computer run under Ubuntu 8.10 (Yes I'm proud that I after few month of preaching, almost non of my friends have windows anymore !). She has now troubles with the network manager and cannot access the wireless network available. Here are the steps (I suppose she went through)
1. Ubuntu 8.10 is working perfectly fine
2. by mistake someone remove from the up panel the network manager
3. she tried to fix it herself (very good so far), so she decided to go to "add/remove application" and to uncheck then check again the network management. Doing that she got internet back at home with the wire
4. but now it's hard to get the wireless to work. left click on the network management gives the network properties instead of wired and wireless network prperties. Right click does not show anymore the "Enable network" and "Enable wireless". Also it seams to be some old network management, without support for browsing available wireless networks. I think that by uninstalling/installing back the network management she removed some extra layer working on the network manager. This must include some icon suite because the power supply icon is different from what I can see usually, and it does not offer all the feature of the usual one. Also the notification for new update available does not appear anymore.

Any suggestion ? What if I upgrade to 9.04, will it put this back ? Or Am I doomed to re-install ubuntu from scratch to her laptop ?

Thanks
Bastien
What happens if u launch nm-applet from a terminal? 

Is there a notification area in the upper right corner? 
If u launch pidgin or whatever it has tray icons do they show up?

---

### Post by bastienauneau on 2009-07-09
Hi couldn't reach her, but I think the answers are :
What happens if u launch nm-applet from a terminal? it works, but I dont see the panel opening and showing all network available on wired and wireless

Is there a notification area in the upper right corner? Yes

If u launch pidgin or whatever it has tray icons do they show up? Yes

I think that when she uninstalled and reinstalled the network manager, software dependent on this network manager where uninstalled as well, but not re-installed. These uninstalled software are working on top of network manager and provide the wireless and wpa supplicant features etc... And I think it is linked to some management suite of Gnome because the battery manager is also different and dont include the usual features like hibernate, suspend etc... when left click on it.

---

### Post by bastienauneau on 2009-07-09
So I guess I need the name of the packages to re-install.

---

### Post by d_liebscher on 2009-07-09
Sorry, I'm not enough familiar with Gnome to help you.

---

### Post by bastienauneau on 2009-07-09
thanks anyway !
I hope someone will come up with some idea

---

