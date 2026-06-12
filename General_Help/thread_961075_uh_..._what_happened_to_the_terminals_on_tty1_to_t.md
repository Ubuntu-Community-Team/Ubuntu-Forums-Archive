---
title: "uh ... what happened to the terminals on tty1 to tty6?"
date: 2008-10-28
forum: General Help
---

### Post by galoisien on 2008-10-28
Okay, I just switched from Slack to Ubuntu.

I don't have any terminals on tty1 to tty6? Is this intentional? Is it me? Who thought of this configuration?

And I don't have an /etc/inittab either to create any sort of getty/runlevel script.

I've searched on this subject for hours and I can't decipher the solution.

---

### Post by kavon89 on 2008-10-28
Ctrl+Alt+F1 through F6 don't take you to the tty? What version of Ubuntu are you using? Is this a fresh install?

---

### Post by galoisien on 2008-10-28
> **kavon89 said:**
> Ctrl+Alt+F1 through F6 don't take you to the tty? What version of Ubuntu are you using? Is this a fresh install?

Yeah it's a fresh install. Maybe it's a problem with the drivers for my ATI card ... which is another issue -- I'm trying to decipher the xorg setup on ubuntu.

My screen flickers between grey and total blackness on anything but tty7.

---

### Post by Ptero-4 on 2008-10-28
galoisien. the /etc/inittab file (which is part of the old sysvinit startup system) isn't used anyomre since the change from sysvinit to upstart. But the tty's show up by default.

---

### Post by galoisien on 2008-10-28
Hmm, it turned out to be an issue with fglrx, which I think I fixed.

Why am I playing with Linux 6 hours before a midterm?

---

### Post by bapoumba on 2008-10-28
> **galoisien said:**
> Hmm, it turned out to be an issue with fglrx, which I think I fixed.

Why am I playing with Linux 6 hours before a midterm?

denial ? ;)

---

### Post by Nameless_one on 2008-10-28
Please post the way you solved this. I also have fglrx, don't have tty's, although I'd looked into it some time ago and found that the problem was the keyboard shortcuts for the tty's weren't correctly configured (however I couldn't solve it). Did you have the same problem?

---

