---
title: "Several problems with Ubuntu"
date: 2008-11-08
forum: General Help
---

### Post by Tribulation on 2008-11-08
Ubuntu has been, for the most part, great. However, last night several lines of black dots appeared on my screen for some reason, and the only way I could get them to go away was to restart. It's happened a few times. Today Ubuntu has been freezing a few times, and most of the time when it freezes, my screen goes blank and I can't get a picture back, even though the computer is still running. I need to restart to get it to work again.

---

### Post by Tribulation on 2008-11-08
Bump

---

### Post by Shazaam on 2008-11-08
Laptop? Desktop?
Sounds like a heat problem. Video card most likely. My old one used to artifact like that when it got hot.

---

### Post by Tribulation on 2008-11-09
I'm using 8.04 on a desktop. There does seem to be a decent amount of head coming out of my computer, that's why I'm leaving the panel off, but it's not affecting Windows. Why would that be? If it's any help, my video card is a 1650 Pro. Not sure if there are any known heating problems with those or not.

---

### Post by hi_raju5517 on 2008-11-09
Gnome starts, metacity works (I can launch windowed apps) - but nautilus does run at all.

It passes it's self check mode from the command line - but I have no desktop background, no icons, and cannot browse files/folders using nautilus.

How do I start tracing the cause of the problem?
__________________

---

### Post by sirebral on 2008-11-09
> **Tribulation said:**
> I'm using 8.04 on a desktop. There does seem to be a decent amount of head coming out of my computer, that's why I'm leaving the panel off, but it's not affecting Windows. Why would that be? If it's any help, my video card is a 1650 Pro. Not sure if there are any known heating problems with those or not.

Staying on topic.

I wouldn't remove the panel.  The panel needs to be there to create a certain amount of vacuum so the fan can frequent air in and out.

You should get lsensors and see what the output is.  If it is a heat problem you might be able to change the frequency of your Fans.  If not heat then it is a video problem most likely.

---

### Post by Tribulation on 2008-11-09
I don't even know what lsensors is. I googled it but came up with a bunch of random crap.

---

### Post by dburnett77 on 2008-11-09
> **Tribulation said:**
> I don't even know what lsensors is. I googled it but came up with a bunch of random crap.

I think the meant lmsensors:

[http://www.lm-sensors.org/](http://www.lm-sensors.org/)

It's available via Synaptic.  If it IDs your chips, then it'll give you info on whether it's heat related.

---

