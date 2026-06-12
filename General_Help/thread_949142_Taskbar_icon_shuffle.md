---
title: "Taskbar icon shuffle"
date: 2008-10-15
forum: General Help
---

### Post by Mimsy on 2008-10-15
This is driving me nuts. Every time I boot into Ubuntu (wubi install on the nc4010 in signature) the icons in my taskbar have been shuffled around. From the clock to the battery meter to the system monitor, they are as jumbled as if they'd been picked up, put in a shaker and poured out onto the task bar.

The thing that puzzles me is that when I right-click on them they show as "locked to panel", and I have to unlock them before I can move them back to where I want them.

How can I stop this shuffling?

---

### Post by dwn99 on 2008-10-15
> **Mimsy said:**
> This is driving me nuts. Every time I boot into Ubuntu (wubi install on the nc4010 in signature) the icons in my taskbar have been shuffled around. From the clock to the battery meter to the system monitor, they are as jumbled as if they'd been picked up, put in a shaker and poured out onto the task bar.

The thing that puzzles me is that when I right-click on them they show as "locked to panel", and I have to unlock them before I can move them back to where I want them.

How can I stop this shuffling?

never mind, I just reread your post and realize you have tried what I suggest.  good luck.

---

### Post by trikster_x on 2008-10-16
I had this exact same problem.  It turns out that I was forgetting to lock the icons again after I moved them.

---

### Post by loomsen on 2008-10-16
You probably assigned the lock to panel option to some dynamically expanding icons, such as your systray. This will make the systray start up right, but all icons affected by the systray or whatever during your last session won't.

Unless you specify the lock to panel option for every icon next to any expanding/padding panel applet.

---

### Post by jerome1232 on 2008-10-16
I don't know if this is your issue but in the past I had this issue with some fullscreen wine apps, any wine app that ran fullscreen at a low resolution would 'cause my panel icons to rearrange themselves on the subsequent boot, locked or unlocked. I never did find a solution for it.

---

### Post by Mimsy on 2008-10-16
Thank you for the quick replies! :)

I always lock all icons to panel after I have moved them, systray or close to it, and I don't have Wine installed. Is there anything else I can do?

---

### Post by loomsen on 2008-10-16
Except of arranging them the way the systray won't affect them anyhow?

Dunno, guess not... Get rid of gnome-panel at all if you like, just penetrate my signature ^^

---

