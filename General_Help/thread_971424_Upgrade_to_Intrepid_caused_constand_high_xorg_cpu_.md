---
title: "Upgrade to Intrepid caused constand high xorg cpu usage"
date: 2008-11-05
forum: General Help
---

### Post by freedomorfire on 2008-11-05
It was not an issue with hardy.. i upgraded using "update-manger -d" and now xorg lags my whole pc with its 20% cpu usage.. causing compiz to stutter.. flash to stutter.. and various other programs to work inefficiently.

I have an Intel x3100 integrated gfx card in an HP pavillion dx6665ca laptop

anyone have any insight?

---

### Post by waydownsouth on 2008-11-06
I too am experiencing the same xorg cpu usage after the upgrade, I initially thought it was just me and I'd broken something.
Glad I'm not alone...

I've got a P4 3.4Ghz, Nvidia 8400GS & 1Gig RAM

Hopefully someone can give us an idea.

---

### Post by waydownsouth on 2008-11-06
[http://ubuntuforums.org/showthread.php?t=965897]("http://ubuntuforums.org/showthread.php?t=965897") 
may be related?

---

### Post by phidia on 2008-11-06
Both of you should look at your System > Admin System Logs or /var/log/xorg.log
and file bug reports. The X3100 gpu should be auto detected and set up. The nvidia card is enabled from System > Admin > Hardware drivers.

Bug reporting [guidelines]("http://www.ubuntu.com/community/reportproblem").

---

### Post by waydownsouth on 2008-11-06
xorg.log looked pretty much normal except for this right at the end:

```
AUDIT: Fri Nov  7 07:10:04 2008: 5985 X: client 4 rejected from local host ( uid=0 gid=0 pid=6591 )
AUDIT: Fri Nov  7 07:10:04 2008: 5985 X: client 4 rejected from local host ( uid=0 gid=0 pid=6591 )
AUDIT: Fri Nov  7 07:10:11 2008: 5985 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6625 )
AUDIT: Fri Nov  7 07:10:11 2008: 5985 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6626 )
AUDIT: Fri Nov  7 07:10:11 2008: 5985 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6627 )
```

haven't got a clue what it means though?

---

### Post by meastp on 2008-11-08
I'm also experiencing this, and I'm not sure what's causing it. Xorg suddenly starts using up to ~90% of my cpu, and my desktop becomes very unresponsive.

I'm using a nvidia graphics card, Quattro 140M. However, I did experience this with the open source *nv driver as well*, and have tried to change between compiz and metacity on the nvidia (binary) driver.

I am not sure where to look next, as I did not find anything interesting in the logs.

Tip: Use htop instead of the System Monitor. The cpu usage of xorg made System Monitor unusable at times. htop is ncurses.

---

### Post by waydownsouth on 2008-11-08
I filed a bug:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/294972")

not sure if this will amount to anything, will wait and see...

---

