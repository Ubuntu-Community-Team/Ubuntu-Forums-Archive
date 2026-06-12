---
title: "panels on dual monitors"
date: 2012-09-13
forum: Hardware
---

### Post by netopalis45 on 2012-09-13
I'm sure this has been asked before but I can't seem to find it; I use dual monitors with my laptop when I am at home and like having a panel on the second monitor. My problem is that when I disconnect the second monitor the panel goes back to the laptop monitor. Is there a way of only making this panel appear when the second monitor is attached? I am using Ubuntu 12.04.

---

### Post by cortman on 2012-09-13
You'll have to tweak it to fit your needs, but you can start from my [display switching script]("http://cortman.wordpress.com/2012/04/07/cortmans-display-switching-script/"), and fix it so that (pseudo-code)

```
if [[ any monitor is attached ]]
set-external-monitor as primary
```

---

### Post by netopalis45 on 2012-09-15
Thanks for the reply but I don't really want the external monitor to be the primary. Is there a way to use this script to recognize the secondary monitor and add a panel to it and then delete the panel when the monitor is disconnected?

---

### Post by cortman on 2012-09-15
Perhaps I've not understood; "primary" simply means that that is the monitor that hosts the panel, launcher, etc.- are you wanting the panel to stretch across both?

---

### Post by netopalis45 on 2012-09-15
Thanks for the clarification, that is exactly what I wanted

---

### Post by cortman on 2012-09-16
Have a look at [Disper]("http://willem.engen.nl/projects/disper/")?

I don't use Unity, so I'm pretty lost on this one.

---

### Post by netopalis45 on 2012-09-16
I tried that script and it moved both the panels to the secondary monitor. I think it could work if I had a command to simply add a panel to the monitor (and to remove it on shutdown), which I don't seem to be able to find. I also tried to use that Disperser thing but couldn't get it to install.

---

