---
title: "Possible X problem in Gnome"
date: 2008-08-13
forum: Hardware
---

### Post by deamon_knight on 2008-08-13
I've installed Hardy on several computer systems without problems, but I'm having some odd problems on a third. Ubuntu will not run, it crashes after a few minutes from an ALT install or Live CD, can't even change to a different TTY. Xubuntu live CD works normally, so I installed that and have been working without trouble for weeks. However, I was looking at other CD/DVD programs and installed gnomebaker yesterday. Today I started having the same problems with I had before with Ubuntu, even in other burning software (I was using Brasero when the recent problem occured). Its like I'm playing a game and my FPS drops suddenly, moving the mouse over windows sometimes gets them to refresh somewhat but the whole system becomes unstable. Uninstalling Gnomebaker seems to have fixed it, it seems like some Gnome service is causing instability in X, but has anyone heard of a problem like this?

-Thanks

---

### Post by phidia on 2008-08-13
Have you searched the errors that "dmesg" or /var/log/xorg.0.log and/or messages contains? 

There are many reports of crashes and freezes with hardy. 
Checking for and submitting a bug report at [launchpad]("https://launchpad.net/ubuntu") would probably be a good thing.

There are a [few hits there]("https://launchpad.net/+search?field.text=gnome+crashes") for "gnome crashes".

---

### Post by deamon_knight on 2008-08-13
Thanks Phidia, but I'm not sure what I'm looking for.

Should I post the output of

/var/log/xorg.0.log
 
and Dmesg?

---

### Post by phidia on 2008-08-13
Yes, maybe attaching is better since they're bound to be large files.

---

