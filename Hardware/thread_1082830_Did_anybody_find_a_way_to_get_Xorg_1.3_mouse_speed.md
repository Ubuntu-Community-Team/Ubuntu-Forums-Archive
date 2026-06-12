---
title: "Did anybody find a way to get Xorg 1.3 mouse speed back in Xorg 1.4+?"
date: 2009-02-28
forum: Hardware
---

### Post by Cracauer on 2009-02-28
One after another all my machines get upgraded to Xorg 1.4, and apart from all the other breakage the thing that drives me most mad is the change in mouse acceleration.

Settings with `xset m`, or equivalent GUI equivalents via GNOME/KDE are definitely not sufficient to get the old behavior back.  Xorg must have changed something about the fundamental algorithm.

As a reminder, the normal parameters are
[list]
[*]A speed value
[*]A threshold value, that, when crossed, activates acceleration
[/list]

I am positive that no combination of these values gives me the Xorg 1.3 behavior in 1.4. I have tried for months. The mouse behavior when slowing down to aim at a certain point (such as a link) is just not the same, and I can't get used to it.

So, the question is: do I overlook some tuning parameters here?

---

