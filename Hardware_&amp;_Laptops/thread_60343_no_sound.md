---
title: "no sound"
date: 2005-08-27
forum: Hardware &amp; Laptops
---

### Post by Ubuntu_User on 2005-08-27
i installed ubuntu and i have no sound at all. It seems to recognise my sound card. It's on-board. Any ideas?

---

### Post by gratefulfrog on 2005-08-27
try running 'alsamixer' from at erminal and playing with the controls
> alsamixer

Also, read the Ubuntu guide section on sound:
[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

good luck!
GF

---

### Post by Qylvaran on 2005-08-27
There's a little trick that works for me.  Double-click the speaker in the taskbar.  when volume control comes up, go to File > Change Device and make sure it's on ALSA.  Then, go to Edit > Preferences and check the box for 'External Amplifier'.  Go to the Switches tab and make sure External Amplifier is UNchecked.  It's on by default, and it makes my internal laptop speakers not work.

---

