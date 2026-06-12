---
title: "Desktop effects on UNR 10.04/Wind u120 deactivated?"
date: 2010-08-12
forum: Hardware
---

### Post by ElNerdoDeGeek on 2010-08-12
Hey all,

I've been using and experimenting with Ubuntu and Linux in general for a while now. Today I installed UNR 10.04 on my MSI Wind u120, (as I have done since 9.04 I believe) and it's been great, save for one thing: the content of the effects tab in Appearance is greyed out and unusable as long as I'm using Metacity. When I switch to compiz, I have no window decoration (It says it's using the only decorator shown in compiz-icon: the KDE4 decorator??) I can switch to Emerald, though then the decorations stick out like a sore thumb anyway. :/

No effects is fine, but I prefer to have some; just makes things a little more pleasant during daily use. If anybody knows what's going on and how to turn Metacity compositing on or get compiz running with the normal Ubuntu window decorations, I'd sure appreciate it. Thanks =)

---

### Post by ElNerdoDeGeek on 2010-08-12
Seem to have fixed it =P Entered in "gtk-window-decorator --replace" into the compiz window dec command box and it works fine now, for anyone who cares. Seems to have been an error in install.

---

