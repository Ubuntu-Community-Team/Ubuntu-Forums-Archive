---
title: "View Current Network Adapter(s)?"
date: 2009-06-02
forum: Hardware
---

### Post by AtomFury on 2009-06-02
I'm booting Ubuntu 8.10 on a Windows 7 machine in the hope that I can find out what network adapter is in it. However, I was unable to find it through Windows and was hoping I might be able to find out what its name is so I can download the appropriate drivers. Does anyone know how I might do this with Ubuntu?

Thanks in advance!

---

### Post by doas777 on 2009-06-02
> **AtomFury said:**
> I'm booting Ubuntu 8.10 on a Windows 7 machine in the hope that I can find out what network adapter is in it. However, I was unable to find it through Windows and was hoping I might be able to find out what its name is so I can download the appropriate drivers. Does anyone know how I might do this with Ubuntu?

Thanks in advance!

well there are a few ways to look at hardware information, the easiest is to hit alt+F2, and enter 
```
gksu lshw-gtk
```. then double click your host in the left column. and keep drilling down until you get to your nics.

if you recieve an error that the command cannot be found, use synaptic to install lshw-gtk, and try again. 

ps, lshw-gtk appear in my preferences menu, but the command does not use gksu (?!?), so it causes an error message that it may give bunk output. you could edit the launcher to start with gksu though.

have fun

---

### Post by AtomFury on 2009-06-02
Right.... Well I'll try this out and tell you how it works in a few minutes. Thanks!

---

### Post by AtomFury on 2009-06-02
Hmmm... All that happens is I get a flashing white Terminal window with a blinking prompt.... BUT I reinstalled lshw in Synaptics and then entered 'lshw' in a regular Terminal window after getting superuser rights and then it showed me all my hardware information. Very useful, I should be able to find my wireless adapter with this information. Thanks a bunch!

---

