---
title: "gutsy power management"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by appye on 2007-11-01
I have gutsy on a compaq c571nr (with the intel 3945abg wireless card instead of the broadcom/dell 1390.

Everything works fine except for power management.  Power management mostly works (hibernates when I close the lid, when the battery gets critically low, resumes just fine), what does not work is the idle timeouts.  Meaning, I have the machine set to hibernate after the machine has been sitting idle for the smallest amount of time possible (slider slid all the way to the left when going to SYSTEM>PREFERENCES>POWER MANAGEMENT>ON BATTERY POWER>PUT COMPUTER TO SLEEP...) which at the time I type this is 16 minutes.  Curiously, I am pretty sure that lowest value was a bit lower before, either at 8 or 11 minutes.  Another curiosity I notice is that when I look at the corresponding values in GCONF-EDITOR, /apps/gnome-power-manager/timeout, they do not match what I see in the power management control panel.  16 minutes in the control panel is equal to 60 seconds in gconf-editor.  17 minutes is equal to 120 seconds, etc.  Interestingly, on a different laptop I have (dell inspiron 5000e), 60 seconds equals 11 minutes on the slider, 120 seconds equals 12 minutes, etc.

Suffice it to say, the timeouts do not work regardless of what I have them set to.  Where do I start with the diagnosis of this?  I am assuming I should look in my system logs, but what do I look for?  What section even?

---

