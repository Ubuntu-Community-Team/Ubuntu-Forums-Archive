---
title: "Freezes while away or I plug in speakers"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by oiper on 2007-01-08
Hey all, I've run into a freezing problem. Yesterday, I powered down, removed one of my 2 sound cards, and booted up. A simply procedure, right? After booting up, when I plugged up my speakers to the remaining sound card, Ubuntu froze. I rebooted, tried again out of curiosity, and everything but my ability to move the mouse cursor around froze. So I decided to leave everything plugged in to avoid the problem.

When I came back hours later, my screen had gone into power saving mode, per my power management settings, and would not come back on. Keyboard num lock, etc..., all frozen. This has happened repeatedly.

I suspect an upgrade from yesterday could have introduced a new bug or perhaps it's related to the sound card removal. Any ideas on what to poke at? :-k

---

### Post by lhtown on 2007-01-09
Maybe you should open the case back up and double check for loose connections?

Maybe there was a reason why you had a second sound card that had to do with the other one having a problem?

You can check your memory from the Ubuntu install disk running as a live CD.

You might be able to disable your sound card in the BIOS to see if the problem goes away.

You could try running your computer from the live CD to see what works and if it crashes.

---

### Post by oiper on 2007-01-17
I've narrowed the problem down to my graphics card. I'll post again when I get this figured out.

From my syslog just before freeze up:
```
kernel: [17254823.368000] NVRM: Xid (0002:00):
```

---

### Post by oiper on 2007-01-18
I seemed to have solved the issue by turning off both "AGP Fast Write" and set AGP from 8x to 4x in my bios. Not sure which did it, but no freezes for a day or 2 now.

EDIT: Nevermind, it's still locking up. This is really fun.

---

### Post by oiper on 2007-01-24
Unresolved. Saying goodbye to Eft. :-|

---

