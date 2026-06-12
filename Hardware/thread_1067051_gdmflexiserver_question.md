---
title: "gdmflexiserver question"
date: 2009-02-11
forum: Hardware
---

### Post by Alberstt on 2009-02-11
Hola,

I have an interesting situation/configuration that has been solved but I don't understand why.

I have a Fujitsu laptop [T4215 docked w/ Intel 965 Express (known issues)] with two Dell Monitors [SP2008W].  One monitor is on a DVI and the other monitor is on VGA (dock configuration). 

After playing with the configuration, I was able to get the picture as clear as possible. The problem is the VGA monitor is fuzzy and near static with the desktop barely visible. (Screen shots do not help as they always come out perfect)

Then I read to start **gdmflexiserver** at the terminal.  The system does as expected and re-logs me into the desktop environment.  BUT BOTH MONITORS DISPLAY GREAT!  PROBLEM SOLVED (kind of).

So the question is WHY did gdmflexiserver fix the vga monitor?  Is there a way to permanently run in this mode? (And do I want to?)  Is there a hint in here as to why the orignal configuration doesnt work correctly?

It irks me to find a solution that I do not understand.

Anyone care to share your thoughts?

Thank you in advance!

:rolleyes:

---

### Post by cariboo on 2009-02-11
If you just login the normal way does the problem reappear? The problem may have disappeared because the X server was restarted.

Jim

---

### Post by Alberstt on 2009-02-11
Yes the problem is persistent and comes back every time I reboot the machine and log in.

Additionally, I run gdmflexiserver each time and it clears it right back up.

---

