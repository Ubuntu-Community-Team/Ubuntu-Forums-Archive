---
title: "Application Installed does not show"
date: 2006-01-24
forum: Installation &amp; Upgrades
---

### Post by wizzkid on 2006-01-24
Hi, I installed my kubuntu from scratch. then I updated my kde to kde 3.5 and installed the Kubuntu-Desktop.

Now, I installed Noatun, but it didnt show on the menu of multimedia. I tried to look my Kmenuedit and it was not there, then I tried to check the Menu Editor (Smeg) and IT WAS THERE. How come? any clue on this? how can I fix this issue?

Thanks.. Hope to receive feedback.

---

### Post by borisattva on 2006-01-24
might or might not work but when i experienced this relogging on refreshed it.

might be worth a shot?

---

### Post by wizzkid on 2006-01-24
I un-install re-install refresh, but still it didnt show up.. any suggestion on this? :D

---

### Post by Jucato on 2006-01-24
- Have you tried to logging out and logging in again? Usually it solves that problem.
- Does your program run? (Alt+F2,  noatun)? If it runs, then your installation 
is ok.
- Try to run KAppFinder (Alt+F2, kappfinder) then click on "Scan", see if Noatun is there. If it is, put a check mark beside it and click apply. 
- If Noatun is not there, you can always manually edit the K Menu.

---

### Post by wizzkid on 2006-01-25
again i installed another application called firestarter.  it didnt show up on Kmenu > System, but it does on Smeg. I tried to restart my copmuter 2 times, but still it didnt show up... why this happened? think this is a bug, is there any fix for this issue?  I am using Kubuntu 5.10 breezy with KDE 3.5.. i need feedback here.  I can do manual edit the kmenuedit, but thought if this is always happens , this is so annoying.

Any input would be highly appreciated. Thanks

---

### Post by tokyovigilante on 2006-01-25
Firestarter is a GTK (Gnome) application, but I can't explain why noatun isn't in the K menu. I guess editing manually is your only option, assuming a locate firestarter/locate noatun turns up the binaries.

---

### Post by Jucato on 2006-01-25
I'll try to install noatun on my KDE, to see if this is really an issue. I'll get back to you in a few minutes after I've installed it.

P.S. I'm not sure why you have Smeg installed, since it's GNOME's own Menu Editor. So naturally, GNOME apps like firestarter would show in Smeg, and not in K Menu.


EDIT: Just installed Noatun. It was immediately added to my K Menu, without even restarting anything. Maybe it's my installation or something. Maybe somebody else could try to test this out.

---

