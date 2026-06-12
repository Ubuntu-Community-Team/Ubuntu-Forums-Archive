---
title: "Xsession: warning: unable to write to /tmp"
date: 2005-11-03
forum: General Help
---

### Post by {{corona}} on 2005-11-03
Hi
.
I run,

kubuntu-5.10-breezy- kde 3.4
Installed nvidia drivers successfully


..and I extended(sources.list) to fetch applications(using adept) from the extended set of deb repositories(which i read were in a way unsafe and unsupported!)

Now probably the blunder i made was to updated a set of applications like konqueror, kcontrol, konsole etc that were (i think,) meant for KDE3.5 using adept. I did this without considering that the KDE installed on my system was 3.4. Also, adept showed them as upgradeable and so i marked them to upgrade.

After these updates i restarted the system and tried to login and received this error:
---

Xsession: Warning" Unable to write to /tmp; X session may exist with an error

---
At this error dialogue is an ok button. Pressing this button takes me back to login prompt (after a few screen flickers)

Trying to login with fluxbox and blackbox both gave me this same error. Though i am able to login into console mode.

---
I have tried recovery mode. but it still fails.
I am a newbie
please help

thank you

---

### Post by {{corona}} on 2005-11-04
It's working now after i did

sudo apt-get clean

from console

---

### Post by evilhomer on 2006-10-27
good stuff!  but why did it work?

---

### Post by Marsolin on 2006-12-23
This worked for me as well running Kubuntu Edgy.  I believe it was because the disk ran out of space and apt-get clean freed a lot of space up.

---

