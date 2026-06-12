---
title: "Nvidia Prime Intel mode screen tearing"
date: 2019-09-17
forum: Hardware
---

### Post by BatteryKing on 2019-09-17
I picked up a new Dell XPS 16 7590, which comes with an Nvidia RTX 1650 card and loaded Ubuntu 18.04 LTS MATE on it.  One problem I am having is in Intel mode screen tearing.  There seems to be a particular nuance here in that I have fixed screen tearing in with pure Intel, no Nvidia card in the system, and I have fixed screen tearing while in Nvidia mode both on Prime systems and completely discrete setups.  However put the two together and well Intel mode just won't work.  I tried making the X11 config file and adding the "tearfree" option and also tried the "triplebuffer" options in various combinations and the result is massive corruption and unusable X display.  No options, well screen tearing.  I have also tried getting the most recent Nvidia drivers on here I can.

The reason I am interested in getting this to work is most of the time I don't need the Nvidia card and it makes the laptop, especially under Linux, run a lot hotter and thermally throttle a lot and the battery life to drop off dramatically.  The interesting thing is on my old Lenovo T420, which also had a Prime setup, screen tearing was not an issue, and I would often be in Intel graphics mode on that.

---

