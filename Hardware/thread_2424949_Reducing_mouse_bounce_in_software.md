---
title: "Reducing mouse bounce in software?"
date: 2019-08-17
forum: Hardware
---

### Post by Skaperen on 2019-08-17
i am having bounce troubles with my wireless mouse.  it affects the left button the most, the right button some, and the middle button hardly ever.  the bounces are very fast, faster than i can do the clicking, myself (i timed them with "xev").  so i think there is a possibility to work around this in software by having button press and release events discarded if they happen too soon after the previous button press/release event, without losing my actual clicking efforts.  i would tweak this timing until it is just right which should work OK unless the bounces become slower.  is there any known settings or software that can do this?

i am currently using Xubuntu 18.04 LTS and a Logitech "Anywhere MX" 3 button wireless USB mouse.

---

