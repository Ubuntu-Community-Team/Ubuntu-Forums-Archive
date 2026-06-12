---
title: "Increasing resolution in Lucid"
date: 2010-05-30
forum: Hardware
---

### Post by crowderd on 2010-05-30
I am having the hardest time increasing my resolution. The option in the MONITOR menu only goes up to 1280x800. I would like to keep the 16:10 ratio but just increase a little maybe 1680x1050 or even 1440x900. I have played around with xrandr and haven't really gotten anywhere and found some articles on the xorg.config but apparently that went away with Karmic. Please help me... Thank you

---

### Post by josvanr on 2010-05-31
xrandr --output LVDS1 --mode 1280x800 --scale 1.5x1.5



I use this to increase my resolution with factor 1.5 . Dontknow if this is what you are looking for

josvanr

---

### Post by crowderd on 2010-06-01
YESSSS!!!!! That works amazing. 1.5 was a little much but 1.25 was perfect. The only problem is how do I make it permanent? This would be amazing if it is possible.

---

### Post by crowderd on 2010-06-01
Never mind. I figured it out i just added the Line to /etc/gdm/Init/Default under OLD_IFS=$IFS. Works like a charm for now. Any other ideas are greatly appreciated though. Thank you so much again.

---

### Post by josvanr on 2010-08-20
ok, I'll do that too!... 

Would be nice if it would work with kde, but the command messes up the desktop unfortunately...

---

