---
title: "remapping the &quot;house&quot; key on a dell laptop"
date: 2008-08-09
forum: Hardware
---

### Post by wayneandleanne on 2008-08-09
anybody advise on how i would remap the "house" key on dell laptop, if i remeber correctly when this laptop used to run vista pressing the button used to start windows media centre, and i would like to keep the function and start mythtv, anybody got any ideas?

wayne
:lolflag:

---

### Post by sergiom99 on 2008-08-09
I set my left win key as a "compose key" for my spanish characters by adding this to the xorg.conf file.
```


 Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
# agregado para tratar de usar LWIN como Compose Key -- 08/06/08
        Option         "XkbOptions" "compose:lwin"
EndSection
```

Maybe you can explore along this line.
There's also something called keytouch that lets you create your own keyboard layout.
Search the forum for it, i dont know how to use it but know its there.
Good luck!

---

### Post by sdennie on 2008-08-09
If it's the same key as on my laptop (Dell XPS m1330), it just appears to Ubuntu as a regular key.  You can go to System->Preferences->Keyboard Shortcuts and map it to the media player just by clicking that option and then pressing the key.

---

### Post by wayneandleanne on 2008-08-09
yes it's the same key (next to power button), i already have it mapped to open rhythembox, but i want to map it to open mythtv, any ideas on how

:guitar:

---

### Post by jocko on 2008-08-09
> **wayneandleanne said:**
> yes it's the same key (next to power button), i already have it mapped to open rhythembox, but i want to map it to open mythtv, any ideas on how

:guitar:

Try this:
Go to System --> Settings --> Preferred applications. In the multimedia tab select "custom", and in the command box that appears, type the command to start mythtv.

---

### Post by sdennie on 2008-08-09
One thing you could try would be to go System->Preferences->Preferred Applications and see if you can make the mythtv the preferred multimedia application.  That should make mythtv appear when you click the button instead of rhythmbox.

---

### Post by wayneandleanne on 2008-08-09
err thats a good idea, i'll try that

---

