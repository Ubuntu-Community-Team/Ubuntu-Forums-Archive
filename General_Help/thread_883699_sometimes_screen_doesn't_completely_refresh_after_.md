---
title: "sometimes screen doesn't completely refresh after asking for sudo password."
date: 2008-08-08
forum: General Help
---

### Post by miatawnt2b on 2008-08-08
I have a new install of Hardy with the latest Nvidia drivers 93.46.07 and am running the stock Hardy compiz packages (desktop effects).

I am having an issue when the machine asks me for gksudo password and the screen grey's out, after the password is typed, the screen doesn't completely refresh itself and there are still blotches of grey around.  I can fix it by switching to another desktop and back again.

I have not played at all with any xorg.conf settings other than to add AddARGBGLXVisuals True to fix the titlebar and white window bug.

I have not had any issues with black windows that I had in the past, so we are making progress, but this screen refresh issue is driving me crazy.

Any ideas on how to fix this?

THanks,

-J

---

### Post by flytripper on 2008-08-08
+! me too

---

### Post by Mgiacchetti on 2008-08-08
im thinking this is a distro wide thing, cuz i notice it too...

Just filed a [bug report.]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/256047")

---

### Post by Mgiacchetti on 2008-08-08
Allright guys its a [known bug since 7.10 ]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/198370")and [has a fix,]("http://gitweb.compiz-fusion.org/?p=fusion/plugins-main;a=commit;h=a5c49962c89e93d64769afb1cfe92bd8bfa27797")

---

