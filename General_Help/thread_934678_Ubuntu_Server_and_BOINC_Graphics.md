---
title: "Ubuntu Server and BOINC Graphics"
date: 2008-09-30
forum: General Help
---

### Post by bserra17 on 2008-09-30
So I installed Ubuntu Server on an old PC I have mostly so I could run boinc. I installed xorg, openbox as my GUI, then BOINC. I started up BOINC and it works fine, but I'd like to get the graphics to work if possible. I know about xhost +local: but that didn't work. I'm guessing I need some other packages installed for it to work. Anyone know what else I need?

---

### Post by dcstar on 2008-09-30
> **bserra17 said:**
> So I installed Ubuntu Server on an old PC I have mostly so I could run boinc. I installed xorg, openbox as my GUI, then BOINC. I started up BOINC and it works fine, but I'd like to get the graphics to work if possible. I know about xhost +local: but that didn't work. I'm guessing I need some other packages installed for it to work. Anyone know what else I need?

Some work, some don't. SETI graphics work on mine, Einstein ones don't.

---

### Post by bserra17 on 2008-09-30
That's what I'm running, SETI. I have to apply xhost +local: before I start BOINC right? Or is it after?

---

### Post by dcstar on 2008-09-30
> **bserra17 said:**
> That's what I'm running, SETI. I have to apply xhost +local: before I start BOINC right? Or is it after?

I have that command in my System-Preferences-Sessions as a start up when I log in.

---

