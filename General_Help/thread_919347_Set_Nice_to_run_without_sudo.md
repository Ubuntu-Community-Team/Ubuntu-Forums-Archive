---
title: "Set Nice to run without sudo?"
date: 2008-09-13
forum: General Help
---

### Post by Gannon8 on 2008-09-13
Is there any way to make it so the command "nice," when set to a negative value, not require root permissions? I would like to bring up the System Monitor in high priority when I press Control+Alt+Delete, like in Windows, so I can kill a misbehaving process.

Thank you ahead of time.

---

### Post by Pro-reason on 2008-09-13
If it were possible to set a negative nice value without root permissions, then any user on a system could make the system unusable.  It would be a big security issue.

If you are having trouble bringing up the graphical System Monitor because the graphical interface has slowed down so much, then hit Ctrl-Alt-F1 to log into the text terminal.  Then use “killall” to kill any misbehaving processes.

---

### Post by Gannon8 on 2008-09-14
> **Pro-reason said:**
> If it were possible to set a negative nice value without root permissions, then any user on a system could make the system unusable.  It would be a big security issue.

Except I am the only one who uses my computer. :)

Anyway, what if it could be only assigned for a specific process or value? Or am I asking someone to write a brand new program? :)

---

