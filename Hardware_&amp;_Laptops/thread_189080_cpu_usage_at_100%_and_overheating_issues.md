---
title: "cpu usage at 100% and overheating issues"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by r.bulboaca on 2006-06-04
Hi,

I've just installed Ubuntu 6.06 on a HP nx6125 laptop (1.8 GHz AMD Turion 64, 512 RAM) and I quickly ran into some problems.

The 'System Monitor' and /proc/loadavg constantly report near 100% CPU usage. This hapens even while the computer is supposed to be idle. I've had this problem ever since i installed Ubuntu (it was a default install) and since I get a delay even when I move the mouse cursor, I haven't been able to use it much. 

It seems that the 'gnome-system-monitor' and 'gnome-panel' processes use up most of my processor time, but I can't figure out why this hapens. I didn't run any processor-intensive applications or install any daemons, so I don't  figure out what might be wrong.

The computer has shut down a couple of times due to processor overheating, and I'd like to find a solution before it gets any permanent damage.

Thank you for your time,
Radu Bulboaca

---

### Post by rrstiff on 2006-06-06
[QUOTE=r.bulboaca]Hi,

I've just installed Ubuntu 6.06 on a HP nx6125 laptop (1.8 GHz AMD Turion 64, 512 RAM) and I quickly ran into some problems.

The 'System Monitor' and /proc/loadavg constantly report near 100% CPU usage. This hapens even while the computer is supposed to be idle. I've had this problem ever since i installed Ubuntu (it was a default install) and since I get a delay even when I move the mouse cursor, I haven't been able to use it much. 

It seems that the 'gnome-system-monitor' and 'gnome-panel' processes use up most of my processor time, but I can't figure out why this hapens. I didn't run any processor-intensive applications or install any daemons, so I don't  figure out what might be wrong.

The computer has shut down a couple of times due to processor overheating, and I'd like to find a solution before it gets any permanent damage.

Thank you for your time,
Radu Bulboaca[/QUOTE]
I have the same computer with an AMD Turion 64 ML-40 processor, 1 gigabyte of memory, and same overall configuration- just got it home today, loaded LTS on it, same issues as you, and exceedingly slow performance!  This is a critically important issue- please help us.  Thank you!

---

### Post by Patsoe on 2006-06-06
Hi rrstif, the answer is in this other topic: [http://ubuntuforums.org/showthread.php?t=189337](http://ubuntuforums.org/showthread.php?t=189337) (see post #4)

Perhaps we should try to turn that topic into "the grand nx6125 topic" :)

---

### Post by rrstiff on 2006-06-06
[QUOTE=Patsoe]Hi rrstif, the answer is in this other topic: [http://ubuntuforums.org/showthread.php?t=189337](http://ubuntuforums.org/showthread.php?t=189337) (see post #4)

Perhaps we should try to turn that topic into "the grand nx6125 topic" :)[/QUOTE]

Thank you so much for leading me to the right fix (suggestion # 4 at the above-mentioned thread.  Can you tell me how to add that line of text to the Boot Options?  I would appreciate your help.

---

### Post by Patsoe on 2006-06-06
No problem! I hope you won't mind if I put it in the other thread, to keep the information together. So you'll see a post appearing there soon :)

---

### Post by rrstiff on 2006-06-06
Wow- it works terrific now!  Thank you, and especially, thank you for how quickly you responded to my need for information, and for how clear and concise it was- you obviously know what you are doing.  Microsoft certainly has never come close to how quickly and effectively issues are dealt with!

---

### Post by polo_step on 2006-06-07
[FONT="Courier New"]This is very interesting.

I have had no such problems playing around with Ubuntu in live mode on my notebook, but one of the other live Linux distributions I tried recently nearly burned it down with 100% CPU usage lockup!

Scary.  

This stuff isn't 100% foolproof nor risk-free yet.[/FONT]

---

