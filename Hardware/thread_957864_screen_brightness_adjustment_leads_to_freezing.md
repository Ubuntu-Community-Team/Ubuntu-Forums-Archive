---
title: "screen brightness adjustment leads to freezing"
date: 2008-10-24
forum: Hardware
---

### Post by polychroa on 2008-10-24
hi all,

to start off, i am new to ubuntu.
i have a couple of laptops on which i am running intrepid (2.6.27-7).
on my older dell 600m, i encounter a strange problem when i try to adjust the screen brightness.
first of all, the brightness applet does not work.
when i adjust with Fn+, it changes the brightness correctly, but does some very strange things that i don't understand how to fix:
1) the keyboard no longer works. ubuntu doesn't recognize it either, because if i start the update manager while this issue is live, it says the keyboard is disconnected or taken over (?!).
2) right clicking on items in the panels works as far as starting a new program, bringing a window to the front, selecting items within programs (particular pages of a pdf) but not for dropping down menus or dropping in a cursor. for example, the user/power button will highlight green, but no menu will appear, but if i set up a log out button in the panel, i can click to start that new window, and can then wait to log out. i do that because...
3) logging out and logging back in fixes the problem
4) and i can adjust brightness while in the log window without problems

any ideas?
need more information?

thanks for any and all help!

cheers,
pc

---

### Post by toadliy on 2008-10-31
Just installed Intrepid today. I seem to be having precisely the same problem. Everything works fine until I try to hit Fn+up/down to adjust my screen's brightness, when all of the issues polychroa described pop up. I'm using a Dell Inspiron E1505; could this be a hardware-specific issue?

Sorry about the unhelpful reply.

---

### Post by ut40755 on 2008-11-01
same here.  i have a dell inspiron 6000, and whenever I change the brightness, my keyboard and menus do not work.  this is a big problem because by default, when on batt power, the brightness is set to half way instead of all the way dim, limiting my batt time to about 45 minutes when it should be around 100.  someone help!

edit: however, i didnt know that if you do it at the login screen, its ok.  i will have to remember that, thanks.

---

### Post by wgrant on 2008-11-01
We know about it. For now you can work around it by switching to a VT and back (Ctrl+Alt+F1, Ctrl+Alt+F7).

---

### Post by estanton on 2008-11-08
good to hear this is known about already, a just upgraded today on my laptop and this came as an unhappy surprise. Do you have a feeling for when this issue will be resolved roughly?

---

### Post by Flynsarmy on 2008-11-13
I have the same problem on a Dell Inspiron 1520, however the cause of the problem for me is having 'blacklist video' in modprobe.d blacklist file.

In Hardy, if i didn't have that line in the blacklist file the screen brightness would move twice as far as it should each time you press Fn+up/Fun+down. It still does in Intrepid, however in Intrepid adding the line to the blacklist file fixes the error but causes the issues described in this thread.

Just thought i'd add a little more information about the problem.

---

### Post by nanotube on 2009-01-10
same problem here
using ubuntu intrepid, 32bit, on dell inpiron 5150

switching to a vty and back fixes it.

---

### Post by Flynsarmy on 2009-01-10
> **nanotube said:**
> switching to a vty and back fixes it.
Newbie here, could you please post instructions on how to do that?

---

### Post by nanotube on 2009-01-11
> **Flynsarmy said:**
> Newbie here, could you please post instructions on how to do that?

hi
press ctl-alt-f2, (to switch to VTY 2), then ctl-alt-f7 (to switch to vty7, where X lives).

---

