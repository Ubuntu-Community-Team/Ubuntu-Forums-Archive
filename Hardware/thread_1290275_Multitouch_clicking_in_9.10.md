---
title: "Multitouch clicking in 9.10"
date: 2009-10-13
forum: Hardware
---

### Post by VitaminG on 2009-10-13
I've noticed that with the release of 9.10 beta, the multitouch features of the synaptics touchpad in my Acer Extensa 5620 still work, but the click settings have changed. Instead of two finger tap for middle click and three fingers for right click, it's inverted. I've looked around for ways to change this, but have yet to find a config file to change this. Any ideas on where to change this back?

---

### Post by Ayuthia on 2009-10-13
> **VitaminG said:**
> I've noticed that with the release of 9.10 beta, the multitouch features of the synaptics touchpad in my Acer Extensa 5620 still work, but the click settings have changed. Instead of two finger tap for middle click and three fingers for right click, it's inverted. I've looked around for ways to change this, but have yet to find a config file to change this. Any ideas on where to change this back?

The original file is located at /usr/share/hal/fdi/policy/10osvendor/11-x11-synaptics.fdi.  What I generally do is copy that file to /etc/hal/fdi/policy/10osvendor/11-x11-synaptics.fdi to make my modifications.  Most likely there will not be a /etc/hal/fdi/policy/10osvendor folder so you will need to create it.  

I recommend doing it this way so that if there are any updates done, your configurations do not disappear.  If you just modify the /usr/share version any Synaptics updates will overwrite that file.

---

### Post by azanutta on 2009-10-13
i've got no such file... they're all empty...
in jaunty i'm used to modify the /etc/hal/fdi/policy/11-x11-synaptics.fdi file
so i did it for karmic too but the 3 with the 2 does work for only few seconds after the boot of the machine... then the swap of these 2 buttons comes back again =((

---

### Post by VitaminG on 2009-10-25
Sorry to be so long to reply... This is a fix I've used in the past (I'd forgotten about it), but it didn't work this time. I'm thinking it has to do with the fact that Ubuntu has moved from hal for most hardware abstraction to udev, and the fix presented here modifies hal config files. I think I'll start looking through udev documentation for information on this...

---

### Post by chezzo on 2009-10-29
> **VitaminG said:**
> Sorry to be so long to reply... This is a fix I've used in the past (I'd forgotten about it), but it didn't work this time. I'm thinking it has to do with the fact that Ubuntu has moved from hal for most hardware abstraction to udev, and the fix presented here modifies hal config files. I think I'll start looking through udev documentation for information on this...

Any luck? I have exactly the same problem :s

---

### Post by rx8saxman on 2009-10-30
The fix is quite simple, just enter this into the terminal:

```
synclient TapButton2=2 TapButton3=3
```

---

### Post by chezzo on 2009-10-30
> **rx8saxman said:**
> The fix is quite simple, just enter this into the terminal:

```
synclient TapButton2=2 TapButton3=3
```

Thank you! That's brilliant.

EDIT: Or not... Seems to revert whenever I reboot. Any way of making it stick?

---

### Post by rx8saxman on 2009-10-31
lol yeah I just realized that myself.  I'm still trying to figure out how to make the settings hold.  I made another thread about it but got no replies.

---

### Post by cmavr8 on 2009-11-01
> **rx8saxman said:**
> lol yeah I just realized that myself.  I'm still trying to figure out how to make the settings hold.  I made another thread about it but got no replies.

Lol, just go to System>preferences>mouse and select the third tab (touchpad). There is a two-finger scrolling option there!

Works fine..

---

### Post by bl4k3r on 2009-11-01
Thanks, I've been searching for this since thursday! :)

---

### Post by chezzo on 2009-11-02
> **cmavr8 said:**
> Lol, just go to System>preferences>mouse and select the third tab (touchpad). There is a two-finger scrolling option there!

Works fine..

That would be great... if that was what we were looking for. If you actually read the thread, you'll find that what we're discussing is the fact that it's possible to use a two-fingered tap as a middle-click and a three-fingered tap as a right-click, and the fact that Karmic seems to have swapped them around.

---

### Post by cmavr8 on 2009-11-02
Ouch.. sorry, I was too excited when I found out...

Anyway, it helped at least one person :)

---

### Post by chezzo on 2009-11-09
> **cmavr8 said:**
> Ouch.. sorry, I was too excited when I found out...

Anyway, it helped at least one person :)

Haha true...

Still, would appreciate some help with the original problem! Anyone?!

---

### Post by chezzo on 2009-11-16
bump

---

### Post by chezzo on 2009-12-07
bump?

---

