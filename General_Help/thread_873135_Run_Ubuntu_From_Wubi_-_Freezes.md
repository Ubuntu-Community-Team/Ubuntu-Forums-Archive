---
title: "Run Ubuntu From Wubi - Freezes"
date: 2008-07-28
forum: General Help
---

### Post by Conorgs on 2008-07-28
I install Wubi on my windows vista laptop. I boot up into Ubuntu after installation, everything is running fine un till about five miniutes into running ubuntu everything freezes, the mouse, the keyboard everything I have to switch the laptop of and boot into Vista as I have that problem every time I boot into Ubuntu via Wubi

---

### Post by ago on 2008-07-29
Check that you are not out of disk space.
Keep the log windows up (tail -f /var/log/syslog) and see if there is any relevant message when it freezes.

---

