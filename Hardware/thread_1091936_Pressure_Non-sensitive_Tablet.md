---
title: "Pressure Non-sensitive Tablet"
date: 2009-03-09
forum: Hardware
---

### Post by ltHank on 2009-03-09
I'm using a WACOM ET-0405-U Graphire tablet and I have installed the files available through synaptic and then over wrote those with the files I found here in the forum.  My question is, should I be expecting pressure sensitivity?  Is this known not to work in Ubuntu?

This tablet works fine with my old Mac tower; never had any issues getting the pressure sensitivity to work.

I think the problem may be (though it seems odd) that my tablet is too old... any ideas?

---

### Post by Favux on 2009-03-09
Hi ltHank,

Yes you should have pressure sensitivity.  What program are you lacking it in?  If you're configured through your xorg.conf and have used wacomcpl then you should have a pressure curve in your /home/username/.xinitrc.  Have you enabled it in sessions so it runs when you reboot or restart X.  In .xinitrc it should look something like:
```
xsetwacom set stylus PressCurve "0 10 90 100"
```
which you could change to something like:
```
xsetwacom set stylus PressCurve "5 15 85 95"
```
where the two inner and two outer numbers add up to 100.  See:
[https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom")
for information on how to set-up in Gimp or Inkscape etc.

---

### Post by ltHank on 2009-03-10
Ach, thanks Favux!  I thought that the xorg.conf stuff was just if you wanted to change settings, not doing the actual set up.  I realized this was wrong only after I looked for the .xinitrc file that you pointed me towards (which wasn't there).

Much gratitude for the quick reply!

---

### Post by Favux on 2009-03-10
Hi ltHank,

You're welcome.

---

