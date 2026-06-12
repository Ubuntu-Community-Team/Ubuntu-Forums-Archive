---
title: "Speed up Thinkpad pointing stick"
date: 2009-10-01
forum: Hardware
---

### Post by legendbb on 2009-10-01
X61 Tablet, although it's only 12' LCD.

Don't know if there is a way to speed up the pointing stick. I always use maximum under windows. uBuntu's default maximum is less than half of the maximum in Windows.

Thanks,:KS

---

### Post by oceanside on 2010-03-18
[QUOTE=legendbb]Don't know if there is a way to speed up the pointing stick. I always use maximum under windows. uBuntu's default maximum is less than half of the maximum in Windows.[/QUOTE]

Did you ever figure this out? I'm experiencing the same thing with my T61. It's a minor annoyance but would be great if I could make it faster.

---

### Post by tgalati4 on 2010-03-18
Look for a debian package called configure-trackpoint.

It's a small dialog box that controls sensitivity, upper speed limit, and negative inertia.  It also has several settings for vertical force and tap-to-select.

apt-cache search trackpoint

I can't remember if I needed a special PPA repository for it.

---

### Post by oceanside on 2010-03-18
Found it:

[HTML]http://tpctl.sourceforge.net/configure-trackpoint.html[/HTML]

Thanks!

---

### Post by edonia on 2010-05-02
Detailed explanation:
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

---

