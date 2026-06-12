---
title: "(Almost) compelte lockups"
date: 2008-07-31
forum: General Help
---

### Post by shufflemoomin on 2008-07-31
Hi everyone,

I'm new to Ubuntu and Linux in general, but I'm having a stability problem. I keep having system freezes where nothing responds and I have to reboot. The odd thing is that the cursor still moves but nothing else responds to anything. This seems to be random. I'm using the latest Gnome. Are there any logs that might be written that I can look at to help me work out what is causing this issue or any other work arounds anyone can suggest? I'm having to reboot many times a day and sadly my XP installation was more stable but I want to stick with Linux. 

Any suggestions?

---

### Post by tuxxy on 2008-07-31
Did you recently install any apps?

---

### Post by shufflemoomin on 2008-08-01
Thanks for the reply.

It's a new install of Ubuntu, only a couple of weeks old. I have been installing a few things here and there to try them, but nothing that I can pinpoint I installed since this started. The lockups started not long after the install, I'm just not having much luck dealing with them. Can you, or anyone, suggest a way to get the desktop running again without rebooting the machine or a way to find out what locked up exactly?

---

### Post by northern lights on 2008-08-01
> **shufflemoomin said:**
> a way to find out what locked up exactly?

Check '/var/log/kern.log' directly after a freeze and/or ```
dmesg
```either might give some clues

---

### Post by JangMunho on 2008-08-01
Try pressing Ctrl+Alt+Backspace instead of reboot next time, that keys will restart your Gnome...

---

### Post by shufflemoomin on 2008-08-01
> **northern lights said:**
> Check '/var/log/kern.log' directly after a freeze and/or ```
dmesg
```either might give some clues

Thank you, I'll try that after the next freeze.

JangMunho, thanks for the suggestion, but the keyboard also seems to stop responding. I have no clue why the cursor doesn't freeze, but whatever reacts to the key combination is also not reacting.

*Just a thought* I know Gnome and other desktop managers deal with what happens on screen, but what controls the cursor? Is that done by the kernel or the desktop manager? Is it possible that Gnome is not responding the system itself is still fine?

---

