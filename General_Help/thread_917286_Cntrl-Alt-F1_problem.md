---
title: "Cntrl-Alt-F1 problem"
date: 2008-09-11
forum: General Help
---

### Post by venik212 on 2008-09-11
When I type: cntrl-alt-F1
I expect to see a terminal session (no gui).  Instead, I see a black screen, and I cannot type anything anywhere.  Cntrl-alt-F7 restores the previous gui.

What is going on?

I am running Kubuntu 8.04 with kde4.1.1
Could it be my video driver?  It is the default VESA, for some reason.  I am using a Diamond Stealth video board with a Samsung LCD monitor.

---

### Post by Pro-reason on 2008-09-11
And you get the same for F2?

This could be a video driver issue.  I think I may have had something similar in the past, before I did a fresh installation of Hardy Heron.

Perhaps changing (or adding) the VGA setting in /boot/grub/menu.lst would help.

---

### Post by _Atreides_ on 2008-09-11
Maybe your monitor doesnt know how to diplay it. I know on my Acer monitor and i have to press this auto adjust button sometimes to get windows to show up properly.

---

### Post by venik212 on 2008-09-19
Auto-adjust does nothing on my Samsung 24 inch LCD flat monitor.
MANY things do not work (cntrl-f12, dashboard, etc.), and I suspect that the culprit is, indeed, the video driver (VESA).  Under KDE4, I am unable to change the video driver (it had been removed from the System Settings), even if I knew which video driver to use.  XP seems soooooooooooo appealing now-- it had no problems with the card... ;-)

---

