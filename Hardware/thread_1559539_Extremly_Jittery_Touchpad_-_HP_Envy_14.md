---
title: "Extremly Jittery Touchpad - HP Envy 14"
date: 2010-08-23
forum: Hardware
---

### Post by ShakataGaNai on 2010-08-23
I recently got my hands on a brand new HP Envy 14 to play with.  First thing I did was kill 7 and install 10.04 Desktop x64.  Everything works out of the box (Sound, video, wifi, ethernet, buttons, etc)... except for the touchpad.

The touchpad "works", but is nearly useless to me due to how sensitive and jittery it is.  For Example: the click buttons are also touchpad, and when I try to click with the side of my thumb (What I normally use), it ends up pushing my cursor around instead of clicking.  The rest of the time I just find the cursor jumping about (probably because I looked at the pad wrong) randomly.

I went into System > Preference > Mouse and turned the sensitivity down all the way to low, disabled the touchpad while typing (Which didn't seem to disable), disabled mouse clicks with touchpad and disable scrolling.  That prevents me from getting random "clicks" and the scroll bar going crazy... but otherwise this is still useless.

Anyone have any way to turn this down to a more tolerable level?

lsinput:
/dev/input/event7
   bustype : BUS_I8042
   vendor  : 0x2
   product : 0x7
   version : 433
   name    : "SynPS/2 Synaptics TouchPad"
   phys    : "isa0060/serio4/input0"
   bits ev : EV_SYN EV_KEY EV_ABS

---

### Post by frank_costanza on 2010-09-09
Not sure about your trackpad issues. But I would like to know your thoughts about the Envy 14 in general and Ubuntu on the Envy 14.

---

### Post by ShakataGaNai on 2010-09-10
> **frank_costanza said:**
> Not sure about your trackpad issues. But I would like to know your thoughts about the Envy 14 in general and Ubuntu on the Envy 14.

The only Ubuntu issues I had were the touchpad and an intermittently crashing wifi driver.  The wifi drive probably could be fixed... but I never got to it.  The touchpad issue is so bad under Ubuntu that we sent back both the machines we bought.

---

### Post by ShakataGaNai on 2010-09-10
> **frank_costanza said:**
> Not sure about your trackpad issues. But I would like to know your thoughts about the Envy 14 in general and Ubuntu on the Envy 14.

Got a little trigger happy on the "post reply" button.  Sorry.  As for the machines themselves? They feel very Mac-ish.  Everything is Mac-ish about them, all the way from the hardware to the boxes they come in.  They even come with microfiber sleeves (which are quite nice).

All in all, they look like nice machines, they don't seem too bad... but I honestly didn't get much use out of them.  Most of my time spent with the machine was cursing it's infernal trackpad (never ran Windows).  A friend of mine has an Envy 15 and really loves it.  They seem like quite nice hardware for the price (one of the best graphics cards I've seen in a non-gaming centric machine).

---

### Post by Marc128000 on 2011-01-14
I'd imagine you already found a fix for this or are working around it. However for those that navigate here looking for a fix, I've written out the instructions in my blog.
[http://linuxenvy.blogspot.com/2011/01/touchpad-fixed.html]("http://linuxenvy.blogspot.com/2011/01/touchpad-fixed.html")
I'll also be covering other Linux-Hp Envy issues there. Mod you might mark this as solved.

---

### Post by Marc128000 on 2011-01-14
I'd imagine you already found a fix for this or are working around it. However for those that navigate here looking for a fix, I've written out the instructions in my blog.
[http://linuxenvy.blogspot.com/2011/01/touchpad-fixed.html]("http://linuxenvy.blogspot.com/2011/01/touchpad-fixed.html")
I'll also be covering other Linux-Hp Envy issues there. Mod you might mark this as solved.

---

### Post by Marc128000 on 2011-01-14
Delete

---

