---
title: "Hotkey bindings? Is this possible, or not yet?"
date: 2008-08-24
forum: General Help
---

### Post by Miyavix3 on 2008-08-24
I have a Thinkpad and it has forward and back buttons. I was wondering if there was a way to set keys to go forward and back in file browsers and web browsers. Is it possible?

---

### Post by mssever on 2008-08-24
> **Miyavix3 said:**
> I have a Thinkpad and it has forward and back buttons. I was wondering if there was a way to set keys to go forward and back in file browsers and web browsers. Is it possible?
I run the following script as part of the login process:```
! Enable the ThinkPad buttons
keycode 234 = XF86Back
keycode 233 = XF86Forward
```It works in Firefox, Epiphany, and Galeon, but not Opera.

---

### Post by Miyavix3 on 2008-08-24
> **mssever said:**
> I run the following script as part of the login process:```
! Enable the ThinkPad buttons
keycode 234 = XF86Back
keycode 233 = XF86Forward
```It works in Firefox, Epiphany, and Galeon, but not Opera.

How do I do that, and does it work for file browsers? 'Cause it did in Windows.

---

### Post by kspncr on 2008-08-24
Hmm... For me, alt+<-(left arrow) is to go back and alt+->(right arrow) is to go forward. These were there by default. I thought it was always like that, at least for Firefox...

---

### Post by Miyavix3 on 2008-08-24
> **kspncr said:**
> Hmm... For me, alt+<-(left arrow) is to go back and alt+->(right arrow) is to go forward. These were there by default. I thought it was always like that, at least for Firefox...

There are literal back and forward buttons on my keyboard. I just want to use them.

---

### Post by mssever on 2008-08-24
> **Miyavix3 said:**
> How do I do that, and does it work for file browsers? 'Cause it did in Windows.I forgot to give you the other half of this: ```
#!/bin/bash
# Enables ThinkPad buttons
xmodmap /etc/X11/Xmodmap
```Set this file to executable, and adjust the path /etc/X11/Xmodmap to reflect where you saved the other script. Then, go to System > Preferences > Session Preferences and add the above script as a startup item. You can run the script directly from the command line to test it.

It works in Nautilus as well (I just tested it). I don't use Nautilus's back/forward controls, though.
> **kspncr said:**
> Hmm... For me, alt+<-(left arrow) is to go back and alt+->(right arrow) is to go forward. These were there by default. I thought it was always like that, at least for Firefox...
ThinkPads have dedicated back and forward buttons, in addition to the keyboard shortcuts.

---

### Post by kspncr on 2008-08-24
> **Miyavix3 said:**
> There are literal back and forward buttons on my keyboard. I just want to use them.

Ah sorry, misunderstood.

---

### Post by Miyavix3 on 2008-08-24
erm... 
```
xmodmap:  unable to open file '/etc/X11/Xmodmap' for reading
xmodmap:  1 error encountered, aborting.

```

---

### Post by mssever on 2008-08-25
> **Miyavix3 said:**
> erm... 
```
xmodmap:  unable to open file '/etc/X11/Xmodmap' for reading
xmodmap:  1 error encountered, aborting.

```
Did you adjust the path? My xmodmap script (in my first post above) is /etc/X11/Xmodmap. If you saved yours somewhere else, you need to adjust the bash script that calls it (see my other post).

---

### Post by TinkerJ on 2008-08-30
I think that Hardy does not use Xmodmap as part of the init process for X11, so creating a ~/.Xmodmap will do nothing.

I'm running Xubuntu 8.04 and
```
~$ locate xmodmap
~$ locate Xmodmap
```

returns nothing except the xmodmap binary.

I recently switched from ALSA to OSS4 because of numerous sound problems, and my volume keys have stopped working (for obvious reasons). I'm having a hard time tacking down the tree that these keypresses traverse.

I've tried messing with the shortcuts in the Keyboard control panel in the XFCE Settings manager. At one point something started working, but only when I left the Keyboard CP open, as another forum poster complained, which is pretty useless.

---

### Post by mssever on 2008-08-31
> **TinkerJ said:**
> I think that Hardy does not use Xmodmap as part of the init process for X11, so creating a ~/.Xmodmap will do nothing.I wrote a simple script to call xmodmap, which I run as one of my startup programs. So it works for me.

> I recently switched from ALSA to OSS4 because of numerous sound problems, and my volume keys have stopped working (for obvious reasons). I'm having a hard time tacking down the tree that these keypresses traverse.
xev is the program I used to find the keycodes for the other keys, but I can't make sense of its output for my volume buttons. I wish I knew more about that.

---

