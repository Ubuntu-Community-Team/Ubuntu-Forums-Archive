---
title: "not able to log into ubuntu.."
date: 2008-10-01
forum: General Help
---

### Post by Julius1988 on 2008-10-01
some part of boot sequence fails because of which i am not able 
to log into ubuntu, how to identify the failure?

---

### Post by Sycron on 2008-10-01
Well, I don't understand. When you start your computer it gets stuck ? or what ? Can you login in cosole ?

---

### Post by Julius1988 on 2008-10-01
no i cant log in........

---

### Post by Sycron on 2008-10-01
Can you give a screenshot ?

---

### Post by Julius1988 on 2008-10-01
how if i cant even reach the login screen?

---

### Post by Sycron on 2008-10-01
With a camera.

---

### Post by bobbob1016 on 2008-10-01
Julius1988 You need to be more specific.  At what point does it fail to startup?  Try pressing Escape when you boot (if you aren't dual booting), and selecting Recovery Mode, if you are dual-booting just select Ubuntu Recovery Mode.  Recovery Mode shows you the commands that are being run at startup.  Whichever line gets stuck, is probably the problem.

> **Sycron said:**
> Well, I don't understand. When you start your computer it get stucked ? or what ? Can you login in cosole ?

Your sig says to correct you if it sounds bad to tell you "gets stuck" not "get stucked".

---

### Post by Sycron on 2008-10-01
> Your sig says to correct you if it sounds bad to tell you "gets stuck" not "get stucked".

Well, thanks.

---

### Post by Julius1988 on 2008-10-01
here goes the whole scenario
i updated my system today, after which i was not able to log 
into my system...after the boot splash screen progress reaches to the end i get a black screen(strangled not able to do anything).
Actions  taken:
Removed the packages which i suspected where the reason for cause
from recovery mode.
(firefox-gnome-support,
firefox,
rdesktop)

---

### Post by Sycron on 2008-10-01
When you get that blank screen use the Ctrl+Alt+F1 combination. If it works login and type sudo gdm.

---

### Post by Julius1988 on 2008-10-01
i'l try and report to u.

---

### Post by Aero-Z on 2008-10-01
[Just a sidenote]There's two things: booting and logging in. Logging in means that you enter your username and password. Booting is the process until your reach for the screen where you can enter your username and password. You need to be more specific where the problem starts, what does it say, what happens and so on.
We can't help you if you don't give any usable information.[/Just a sidenote]

---

### Post by Julius1988 on 2008-10-01
> **Sycron said:**
> When you get that blank screen use the Ctrl+Alt+F1 combination. If it works login and type sudo gdm.

tried ctrl+alt+f1 but nothing happend.

---

### Post by Sycron on 2008-10-01
Well, I can't help you. What you said is not enough to understand your problem.

If you really messed somthing try the LiveCD and recover your data.

---

### Post by bobbob1016 on 2008-10-01
So you were able to get in in recovery mode?  Removing those things probably wasn't needed.  It seems like the login screen might be having issues, not the actual startup.

---

### Post by Julius1988 on 2008-10-01
any other alternatives.

---

