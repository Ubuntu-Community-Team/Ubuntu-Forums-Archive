---
title: "odd module question"
date: 2008-11-02
forum: General Help
---

### Post by Haluci on 2008-11-02
Is there any way to change the order in which modules are loaded at boot time?

My problem is that I have a wireless card that needs ndiswrapper to work.  At boot time, first b44 and ssb are loaded (these are needed to make my wired connection work) and then ndiswrapper.  The problem that I have is that ssb claims my wireless card when it claims my ethernet card, and ssb doesn't work with my wireless card.  I have to do this manually every time I turn on my computer:

```
rmmod b44
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe b44
```

so ndiswrapper can claim my wireless card.  If there isn't a way to reorder the way these modules are loaded, is there at least a way that I can run this at boot time so I don't have to go through this manually every time I start my computer?

Thanks!

---

### Post by Haluci on 2008-11-06
bumping after 4 days of inactivity.

I did a really ugly hack and put this script into /init.d/rc.local.  Is this not suggested for any reason?

---

### Post by Haluci on 2008-11-08
bumping, again, after 1 day of inactivity, but I'm already assuming I'm getting no help here.  Figures.

---

### Post by adult swim on 2008-11-08
this is what you are looking for [http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003)

---

