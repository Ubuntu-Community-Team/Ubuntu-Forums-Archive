---
title: "Synaptics Touchpad 'gltiches'"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by AdeptPaladin on 2006-02-03
Just migrated up from Hoary to Breezy with little issue.  I'm going to say that the update in how Wifi is handled in Breezy is nice; I prefer GUI! :p

The only issue I have at present is with the synaptics touchpad and it happened in Hoary too.  Basically, whenever I type, the cursour will 'jump' to wherever the mouse is pointing at.  I can't seem to find anything online that relates to this problem either.

Suggestions?

---

### Post by stangbang on 2006-02-04
disable tapping and see if it still does it. I have heard of some laptops where the touchpad will actualy pick up vibrations from some keys being pressed and notice them as taps, also there is the chance of the palm hitting the touchpad

---

### Post by AdeptPaladin on 2006-02-05
Uhm... ok.  Here's the million dollar question:  how?

---

### Post by UnrulyGrrl99 on 2006-02-06
try:
```
/usr/bin/tpconfig --tapmode=0
```

---

### Post by nanotube on 2006-02-07
hey
read this link for how to disable tapclick:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Synaptics_Touchpad](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Synaptics_Touchpad)

---

