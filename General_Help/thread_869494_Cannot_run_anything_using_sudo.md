---
title: "Cannot run anything using sudo"
date: 2008-07-24
forum: General Help
---

### Post by richard270384 on 2008-07-24
Gday all,

I'm almost certainly sure that I am the one who has stuffed something up here.
[B]
First some background:[/B]
I installed Ubuntu 8.04 (prev used WinXP) about 2 weeks ago, and it worked almost fine - I was quite happy with everything except that it was a bit sluggish. The only thing I had to do was approve the use of some proprietry drivers for my graphics and wireless - other than that things were easy.

My first instinct was to get everything on the system updated. So I added all 200 or so updates using the package manager. Then something went horribly wrong. My wireless card stopped working and NO programs would load in the GUI. Without the knowledge of Linux to fix the prob myself, and with out an internet connection, I figured the easiest thing to do was re-install Linux and start again.

**Here's my current problem:**
So I re-installed Ubuntu yesterday, but this time I haven't updated anything - I'll do some research first this time. My wireless is working again.
The problem I have now is that anything that requires me to enter a password (such as anything in the System -> Administration menu) won't load... I just see the "Starting XXXX" in the taskbar and then it disappears and I get nothing. When I run something in a terminal using sudo it appears to do nothing as well.

I've figured out that kacpid is what is making ubuntu sluggish, hammering my CPU - but I'm thinking this is something in my BIOS that is possibly the problem...

Any thoughts on what is going on (mainly with the sudo issue for now)?

Let me know any info you need.

---

### Post by drs305 on 2008-07-24
If you type the following do you see your username and "admin" somewhere in the generated list:
```
groups
```

If you don't, boot into recovery mode and in terminal:
```
adduser *username* *username*
adduser *username* admin
```

---

### Post by richard270384 on 2008-07-24
Yes both are listed..

```
richard adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin
```

---

### Post by richard270384 on 2008-07-27
Bump.. anymore ideas on this?

---

### Post by gjoellee on 2008-07-27
1. I am going to check further about this, never seen it before
2. Report this to [www.launchpad.net](www.launchpad.net)

---

