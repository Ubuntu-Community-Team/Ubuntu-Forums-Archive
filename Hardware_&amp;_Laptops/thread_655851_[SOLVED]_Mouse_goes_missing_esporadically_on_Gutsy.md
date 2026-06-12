---
title: "[SOLVED] Mouse goes missing esporadically on Gutsy"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by victorbrca on 2008-01-01
Having a little problem where my mouse disappears after my laptop has been idle for a while. 

  I can still open a terminal using a keyboard shortcut, minimize it, resize and close it (all with keyboard shortcuts).

  I'm also able to switch between ttys. Now, here's something wird... I can switch between workspaces by using a special keyboard shortcut (Ctrl+Alt+number), but I can not do it by using the default Ctrl+Alt+left or right.

Any ideas??


Vic.

---

### Post by kmfdmk on 2008-01-18
I'm having the exact same issue.  This occurs for me when I leave the laptop running overnight or idle for long periods of time.  I'm using Ubuntu to recover data from an external hard drive to  another good external drive and the copy process is very slow.  So I let it run overnight (been going at it for about a week now).  When I get up in the morning to continue the process the mouse is gone however keyboard controls still work.

HP DV2000US Laptop
AMD Turion64 1.8Ghz
1GB Ram
120GB HDD
Edimax EW7318USG wifi
Gutsy Gibbon 7.10

---

### Post by victorbrca on 2008-01-18
I've noticed that for me when this happens, if I leave it alone for a little bit, after the screen goes black again the mouse comes back. 

WEIRD!!!!  :-s

---

### Post by kmfdmk on 2008-01-19
I'm still running the default video drivers but I do have the GeForce Go 6150 chipset.  However my screen doesn't go black it stays up I can still navigate, just no mouse.  It fixes itself once I reboot, but that's obviously not the fix.

---

### Post by victorbrca on 2008-01-19
My screen on my laptop goes black automatically after a few minutes. The problem usually happens after that. 

I have intel 915, but I'm guessing it might be something to do with X.

If you restart X does it no resolve the problem?

---

### Post by kmfdmk on 2008-01-29
Well if you mean restarting X by doing a CTRL + ALT + BKSP,if I do that it doesn't fix the missing cursor problem.  However I don't find that acceptable.

---

### Post by victorbrca on 2008-01-29
> **kmfdmk said:**
> Well if you mean restarting X by doing a CTRL + ALT + BKSP,if I do that it doesn't fix the missing cursor problem.  However I don't find that acceptable.

Agree... but it's better than a reboot... In my case it does resolve the problem.

---

### Post by arvevans on 2008-02-06
Same problem here.  Visible cursor goes away, or doesn't come up after first boot (re-boot fixes it every time).  The cursor function is actually there, just the visible glyph is missing.  CTRL-ALT-Backspace does not fix it.

I was running the default drivers.  Just downloaded and installed NVIDIA, we'll see if that makes any difference.

Arv
_._
Ubuntu 7.10 (32-bit version), AMD 2X64-3800, 1 GB RAM, 160 GB HD, LCD, USB Logitec Trackball/Mouse, PS2 Kybd, Belkin WiFi,

---

### Post by arvevans on 2008-02-07
Installing Nvidia drivers seems to have fixed the problem, for me anyway.

Arv
_._

---

### Post by victorbrca on 2008-02-07
On my case I have ATI with restricted drivers....

Vic.

---

### Post by victorbrca on 2008-07-02
If anyone else comes trough this problem, it's related to xscreensaver. On some machines locking the screen solves it (Ctrl+Alt+l), mine did not, so I removed xscreensaver.

You might get messages similar to this on your logs:

```
xscreensaver: 22:20:41: couldn't grab keyboard!  (AlreadyGrabbed)
xscreensaver: 22:20:45: couldn't grab keyboard!  (AlreadyGrabbed)
xscreensaver: 22:20:49: couldn't grab pointer!  (AlreadyGrabbed)
xscreensaver: 22:20:49: unable to grab keyboard or mouse!  Blanking aborted.
xscreensaver: 22:21:02: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 22:21:02: 0: for window 0xa00027 (gnome-screensaver / Gnome-screensaver)
xscreensaver: 22:21:32: 0: unrecognised ClientMessage "_NET_ACTIVE_WINDOW" received
xscreensaver: 22:21:32: 0: for window 0xa00027 (gnome-screensaver / Gnome-screensaver)
```

---

