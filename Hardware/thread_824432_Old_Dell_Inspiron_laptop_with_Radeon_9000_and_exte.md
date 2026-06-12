---
title: "Old Dell Inspiron laptop with Radeon 9000 and external monitor"
date: 2008-06-10
forum: Hardware
---

### Post by kapatp on 2008-06-10
I was trying to setup an external monitor on a relatively old Dell Inspiron laptop running Kubuntu 8.04.

Graphics card: ATI Mobility Radeon 9000.

Resolutions: Laptop LCD is 1024x768 and that for the external monitor (Acer AL2216W) is 1680x1050 (22in W).

What I can get:
Acer monitor at 1680x1050 of which the top-left corner of 1024x768 is a clone of the laptop LCD - sort of weired - the KDE panel, which sits on the bottom edge of the laptop screen is, right in the middle of the Acer screen. I have tried with "ati" as well as "radeon" drivers in xorg.conf.

OTOH What I am looking for:
The acer screen to work separately from laptop screen - like two distinct monitors: laptop screen: "1024x768+0+0" disjoint from the acer screen: "1680x1050+1024+0" (right of laptop screen). So that the total virtual screen has "2704x1050" resolution.

I use such a setup for my desktop machine (Kubuntu 8.04) with the proprietary nvidia drivers and twinview (my nvidia card on the desktop has two outputs - VGA and DVI)

Is such a thing possible? If so, how? Help is always appreciated! I can provide more information, let me know.

PK

---

### Post by kapatp on 2008-06-12
Hmm, no one has any clues? Is it not possible to have an external monitor like this?

---

