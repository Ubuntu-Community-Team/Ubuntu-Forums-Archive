---
title: "Log In -&gt; Black Screen"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by MrMMShue on 2008-12-13
I used Wubi, the Ubuntu installer for Windows to install Ubuntu. I meet the minimum system requierments. It went through its process and restarted then asked me to log on. I entered in my user name and password and hit enter and it acted like it was logging me on but the screen just turned black. 

Why did the screen turn black and how can I fix it.

---

### Post by gettinoriginal on 2008-12-14
It sounds like you may have an ATI video card, and they are know to cause problems.  Check for the correct drivers in Synaptic.  :p

In case you don't know what you have:

in terminal type lspci

---

### Post by Mark Phelps on 2008-12-15
Go into System --> Preferences --> Appearance --> Visual Effects and make sure you have it set to "none".  The "Normal" and higher settings turn on Compiz -- and this is know to cause problems with some ATI cards.

---

