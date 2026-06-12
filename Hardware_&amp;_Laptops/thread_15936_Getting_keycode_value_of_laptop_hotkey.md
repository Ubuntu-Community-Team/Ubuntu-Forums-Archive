---
title: "Getting keycode value of laptop hotkey"
date: 2005-02-18
forum: Hardware &amp; Laptops
---

### Post by izmaelis on 2005-02-18
I have HP ze4900 laptop and I want to enable hotkeys.
I did
```
# apt-get install hotkeys
```
then
```
# hotkeys -t hp8531.def
```
and I got volume control working perfectly. Launching webbrowser works too, but only if terminal window is active.
Other hotkeys do not work at all.
I think that definition file is not suitable for my laptop model. So I should edit it (write real keycodes for non-active buttons).
How should I get those keycodes? xev does not return any values as I press hotkeys.

Or maybe it's not a problem of keycode values at all?
Thanks for your help.

---

### Post by Big Cheese on 2005-02-21
Can't you use Computer -> Desktop Preferences -> Keyboard Shortcuts? That at least gave me the value of my "Fn" (function) key on my Dell laptop.

---

### Post by piedamaro on 2005-02-21
I wrote a 'multimedia keys' howto, in the howto section.

---

### Post by Slalomsk8er on 2005-03-11
I have some problems too with my hp/compaq nx9010 (some hotkeys work some not).

The HowTo can be found under [http://ubuntuforums.org/showthread.php?p=90864#post90864](http://ubuntuforums.org/showthread.php?p=90864#post90864) with my post about omke (the one I think we need).

---

