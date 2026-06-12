---
title: "No wake from sleep."
date: 2008-08-24
forum: Hardware
---

### Post by wizardfait on 2008-08-24
I have an HP pavilion ZE4800 (ZE4805US) that will go to sleep with no problem, however, waking from a sleep is impossible. It will power on, however the mouse never gets re-initialized and maybe the keyboard doesn't, however, it doesn't respond to anything, and the screen remains black, however, powered on as far as teh backlight goes.

System specs:
AMD Athlon XP 2800+
512 MB RAM
60GB HDD
Broadcom 4306 
And... Most likely the culprit: ATI Radeon IGP 320M (U1)

Any solutions?

---

### Post by wizardfait on 2008-08-25
Bump

---

### Post by wizardfait on 2008-08-25
Bump

Anyone?

---

### Post by enos76 on 2008-09-20
Did you try switching back and forth to a console to re-initialize the video mode? (CTRL-ALT-F1 then CTRL-ALT-F7)

-- 
enos76

---

### Post by Kev0r on 2008-11-08
Hey, I've the same problem.
When the laptop (Acer Aspire 5100) is woken from sleep, the screen remains black. The HDD led is lighting up for a while then goes dead too...
Mouse is not initialized and switching workspaces (Ctrl-Alt-F1..12) doesn't work either.

This laptop had no problems with 8.04... not very happy with this upgrade :/

Ps. Did a clean install on 8.10.

---

### Post by MgFrobozz on 2010-06-09
I have an HP Pavilion ze4800 with this problem running ubuntu 9.10. When it's in this mode, the screen is black, it doesn't respond to keystroke sequences (including ctrl-alt-backspace, an attempt to kill the X server). It normally runs sshd, but it won't respond to ssh attempts when this occurs, so I'm guessing that services aren't running.

Is there a way to diagnose what's happening?
Is there a way to disable suspend/hibernate?

---

