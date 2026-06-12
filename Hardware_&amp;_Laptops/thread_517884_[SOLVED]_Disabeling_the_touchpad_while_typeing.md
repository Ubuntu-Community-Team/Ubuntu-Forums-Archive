---
title: "[SOLVED] Disabeling the touchpad while typeing"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by Aleksandersen on 2007-08-05
Hi,

Is it possible to temporarily disable the tochpad when typing?

My computer is a *Lenovo N100 3000* running KUbuntu Linux 7.04.

**Solution:**
Install *KSynaptics*, and restart your computer. You will notice a new icon in the *system tray* that will allow you to configure your touchpad.

---

### Post by eggdeng on 2007-08-05
> sudo synclient TouchpadOff=1
and
> sudo synclient TouchpadOff=0
to enable it again.

---

### Post by Aleksandersen on 2007-08-05
I want it to be disabled automagically when I start typeing. Anyway to do that?

---

### Post by ugm6hr on 2007-08-05
My Acer came with a shortcut that works automatically in Xubuntu7.04 (can't understand how):
Fn+F7

This turns the touchpad on/off.

Yours might have something similar - have a look in the manual.

If not - you can do it from Terminal (or create a launcher / shortcut yourself):
```
synclient TouchpadOff=1 
```
And back on:
```
synclient TouchpadOff=0 
```

Otherwise - install GSynaptics (from Synaptic Package Manager) - it gives a GUI to edit settings.

---

### Post by Aleksandersen on 2007-08-05
No way to make this happen as I start typeing? I would never remember to turn off the touchpad everytime I use the keyboard.

I keep bumping onto the touchpad whit my wrist. So my cursor moves and I start typeing somewhere different. It is really annoying!

My iBook turns off the touchpad when I start typeing! Very helpful.

---

### Post by ugm6hr on 2007-08-05
> **Aleksandersen said:**
> No way to make this happen as I start typeing? I would never remember to turn off the touchpad everytime I use the keyboard.

I keep bumping onto the touchpad whit my wrist. So my cursor moves and I start typeing somewhere different. It is really annoying!

My iBook turns off the touchpad when I start typeing! Very helpful.

Some touchpad have a palm detect feature - it can be turned on by editing xorg.conf - it's the Option "PalmDetect" & "PalmMinWidth" you need to add (with appropriate settings).

Have a look at:
```
man synaptics
```

As for turning it off when you touch any key on the keyboard - I would find that annoying.  I use the keyboard for searching through File Manager etc.  

But I'm sure it would be possible to write something to do that - if someone hasn't already.  Maybe suggest it here: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by Lapino on 2007-08-05
syndaemon seems to enable you to do this. Haven't tried it myself though: [http://www.debuntu.org/2006/06/25/70-how-to-disabling-your-touchpad-while-typing]("http://www.debuntu.org/2006/06/25/70-how-to-disabling-your-touchpad-while-typing")

---

### Post by ugm6hr on 2007-08-05
> **Lapino said:**
> syndaemon seems to enable you to do this. Haven't tried it myself though: [http://www.debuntu.org/2006/06/25/70-how-to-disabling-your-touchpad-while-typing]("http://www.debuntu.org/2006/06/25/70-how-to-disabling-your-touchpad-while-typing")

Absolutely right.  It's true - someone has already had the idea, and solved the problem.
```
syndaemon -i 1 -d -t -K
```

Stops the tap-to-click and scrolling options for 1 second after any main key-press (ignoring Shift, Ctrl etc) but allows you to move the pointer and also click with the actual touchpad buttons in that time.  Everything comes live automatically if you don't press any keys for 1 second.

I think you could add it (as a command) to your autostarted list, so it's always active when you boot up.  It appears to use almost no processor at all (always 0% on my taskmanager in Xubuntu).

Perhaps I might grow to like this feature now that I've found it..... :popcorn:

---

### Post by Aleksandersen on 2007-08-05
KSynaptics is really handy too! ;)

Thanks for the help.

---

