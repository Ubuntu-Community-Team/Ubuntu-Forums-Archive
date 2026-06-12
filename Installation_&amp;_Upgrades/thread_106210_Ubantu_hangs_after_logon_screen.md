---
title: "Ubantu hangs after logon screen"
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by voiceofxile on 2005-12-20
I cannot get ubantu to load past the logon screen after the installation of either cd (5.10 or the 64 bit ver.). The live cd's do not work as well. Where it freezes I have a mouse cursur that works, untill the freeze happens. Each version hangs at the same place, so I assume it is a problem with my hardware. I have an ATI AIW 600 pro graphics card. Is there a remedy? thanks.

---

### Post by bonjun on 2005-12-20
[QUOTE=voiceofxile]I cannot get ubantu to load past the logon screen after the installation of either cd (5.10 or the 64 bit ver.). The live cd's do not work as well. Where it freezes I have a mouse cursur that works, untill the freeze happens. Each version hangs at the same place, so I assume it is a problem with my hardware. I have an ATI AIW 600 pro graphics card. Is there a remedy? thanks.[/QUOTE]


it's **Ubuntu** my friend.

---

### Post by Juippisi on 2005-12-20
[QUOTE=bonjun]it's **Ubuntu** my friend.[/QUOTE]

Well well, aren't you helpful there?


Ok, seems like a hardware-problem. "After logon screen" as a GDM? If so, it sounds like a Gnome-problem.

Ok, next time when you're on the logon screen, hit the Ctrl+Alt+F1 and log in. Try installing something like fluxbox (sudo apt-get install fluxbox) and when you're done, type startx /usr/bin/fluxbox . What happens now? Does fluxbox start or do you get any error-messages?

Maybe your new Ati is causing problems for the Xorg or Gnome.

---

