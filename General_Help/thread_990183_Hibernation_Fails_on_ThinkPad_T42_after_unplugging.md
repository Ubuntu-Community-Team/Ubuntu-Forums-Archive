---
title: "Hibernation Fails on ThinkPad T42 after unplugging and plugging again power cord"
date: 2008-11-22
forum: General Help
---

### Post by coolnba on 2008-11-22
I got problem with hibernation on my ThinkPad T42

When i upgraded ubuntu to 8.10 i noticed that my ubuntu don't resume from hibernation when i unplug power cord after my laptop is hibernated and then plug in it back my laptop freezes with kernel panic ( blinking caps lock ). When i hibernate and resume with power cord plugged it resume without problem.

Anybody have this problem because I'm searching google and forums for days and didn't find answer?

---

### Post by danielfarley on 2008-11-24
I am having the same kind of isuew, i changed my wifi driver from support for atheros 802.11 to the suport for 4xxx series of atheros 802.11 wirless lan cards.. i think it was the ath5k driver i changed to.  And things start to work a bit better.. some times i come out of hybernation ok some times the capslock flash.... i will try and take note how it behaves pluged in and not pluged in.  

Im also haveing sound not come back on resume.  (when it does resume)

Suspend works fine, but is not go into a very low power suspend.. i think.. the computer feels warm when you open it up.. (and with 8.04 it never lasted as well in suspend as it did in windows)

i posted this after i did the upgrade but got no replys.  [http://ph.ubuntuforums.com/showthread.php?t=966208](http://ph.ubuntuforums.com/showthread.php?t=966208)

I will try and take note on how it behaves in difrent power modes..  and come back with another post.. if you sort it out let me know :-)

Daniel

---

### Post by coolnba on 2008-11-24
I downagraded kernel to 2.6.24-19-generic and works fine , when i boot from and try to wake up from hibernation after unplugging / pluging power cord 2.6.27-7 it crashes with kernel panic so i asume that is kernel based problem

---

