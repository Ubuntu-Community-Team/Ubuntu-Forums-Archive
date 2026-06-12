---
title: "beginner cannot use GUI"
date: 2020-06-25
forum: Hardware
---

### Post by Emos on 2020-06-25
Dear all, I'm a linux newbie and just installed Ubuntu 16.04 on an elderly machine (Shuttle XS350VA).
The computer has an Integrated Intel GMA3150 Graphics card.
I can use the system from the commandline, but have trouble loading the GUI. It will sometimes allow me to log into the GUI, but never load the desktop and present me with a puzzle of different colours.
I have tried several things, including:
- installing mesa-utils to correct the drivers
- running xrandr to understand a bit more, however xrandr says "Can't open display" and won't help me.
I have an Acer screen (V243H)

Please help!

---

### Post by Yellow Pasque on 2020-06-25
Why such an old version for a new install? How does a LiveUSB of Ubuntu 20.04 work?

---

### Post by Emos on 2020-06-25
Would you suggest to upgrade to 18? would my old hardware including 2gm ram be ok?

---

### Post by Perfect Storm on 2020-06-25
Lubuntu will be more appropriated in your case.

---

### Post by Bashing-om on 2020-06-25
Emos - hello

For a good experience "Ubuntu" requires 4 Gigs of ram as a minimum:
[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)

Where as lubuntu and xubuntu are designed to operate on lower spec hardware.

Try each and see for yourself which spin that you prefer.

[INDENT][INDENT]one size does not fit all
[/INDENT][/INDENT]

---

### Post by Emos on 2020-06-26
Hi. My system currently works OK, can I just swap the GUI for a lighter one on ubuntu 16?

---

### Post by guiverc on 2020-06-26
Ubuntu releases for servers and desktops are *yy.mm* in format, with *yy *used by specialist releases such as Ubuntu Core 16 (which is intended for IoT appliances/devices and has no desktop/GUI).

Yes you could add a lighter desktop to Ubuntu 16.04 LTS (sorry I don't know about Ubuntu Core 16 which is snap based), however if you're currently using Ubuntu 16.04 LTS (and not Ubuntu Core 16) the desktops of Lubuntu (LXDE) and Xubuntu (XFCE) are no longer supported as being flavors, they only came with 3 years of supported life (16.04 = 2016.April = 3 years so EOL was 2019.April)

If you *release-upgraded* to 18.04 you'd still be supported with a lighter desktop, however you'd only get less than a years support left anyway (18.04 + 3 years = 2021.April EOL for flavors) which is when Ubuntu 16.04 LTS reaches EOL anyway. To me a lighter flavor even with a shorter life span is worth it, as you'll always be running newer software because of the more frequent *release-upgrades*, but like which flavor best suits you, it's your decision.

Also note: Lubuntu 18.04 LTS was the last Lubuntu using LXDE, and upgrades after that require a re-install (*modern Lubuntu uses the LXQt desktop*).  Yes Lubuntu is lighter than XFCE/Xubuntu (esp. more modern Xubuntu's which uses heavier GTK3), but the change of desktop is a *minor* hurdle when compared to Xubuntu GTK2 to GTK3 transition which is invisible to users..  (Lubuntu's re-install doesn't mean you need to restore all your data, it's actually fast, but it's still a step & change..)

---

