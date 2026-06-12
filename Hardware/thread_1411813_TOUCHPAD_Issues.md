---
title: "TOUCHPAD Issues"
date: 2010-02-20
forum: Hardware
---

### Post by Sugz on 2010-02-20
Okay sorry for the Capitalised title, but this has been going on for far too long. 

Basically, I Dont know where my system is getting and setting my touchpad settings. 

From startup, it seems to be fine, but From Waking up from Hibernate, the settings are completely different, and I therefore need to run Gsynaptics to re-correct them every time. 

I am next to clueless as to why this is hapenning, and would greatly appreciate any assistance. 

Regards

---

### Post by alexbardasu on 2010-02-20
It may sound dumb, but have you checked in System->Preferences->Mouse ?
Alternately do a
```
sudo apt-get install synaptic
```
and play with the settings.

---

### Post by Sugz on 2010-02-21
Thanks for your reply, 
Yes i have installed everything you and suggested. 
One thing however I forgot to mention, is that I'm sure I have SHM Config enabled, but Programs such as Ksynaptics, thing that I dont..

---

### Post by pi/roman on 2010-02-21
I have a guide for the touchpad here:
[[COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1401645[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1401645")

The settings descussed in this guide would probably be what is conflicting with gsynaptics.  You may be able use both but gsynaptics does not give you as much control as you can have so I would recommend following the guide and uninstalling gsynaptics.

Let me know if you have any problems.

---

