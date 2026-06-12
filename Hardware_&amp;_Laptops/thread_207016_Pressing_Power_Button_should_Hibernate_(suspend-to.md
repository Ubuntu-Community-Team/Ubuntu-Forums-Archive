---
title: "Pressing Power Button should Hibernate (suspend-to-disk) system"
date: 2006-07-01
forum: Hardware &amp; Laptops
---

### Post by A.Skwar on 2006-07-01
Hallo.

I'd like to setup the system so, that when I press the power button for a *short* time, the system should "Hibernate", ie. suspend-to-disk.
It should do so, by executing /usr/sbin/hibernate. And when I keep the power button pushed for a *long* time, the system should shut down.

Right now, when I push the power button shortly, the system shuts down.

I'm using Ubuntu Dapper, ie. Gnome. I had a look at the "Energy" settings under System, but I didn't find how to configure what I want there.

How do I do that?

Thanks,

Alexander

---

### Post by A.Skwar on 2006-07-03
I'm still looking for a solution, and as it seems that nobody knows what's going on, I'm trying to debug that situation by myself. To do so, I added debug messages (using logger) at various places. I'm actually not at all successful in finding out what's going on  :( 

Right now I'm wondering, what's supposed to happen, when the "Hibernate" button is pressed on the Gnome Logout dialog, when that dialog is shown after the Log Out button is pressed.

What happens is, that the Log Out dialog is shown. There, I'd like to hibernate the system by pressing the Hibernate button. But when I do so, just nothing useful happens. The WLAN goes away for a short time, and that's it. :confused: 

Somewhere, I read, that **/usr/sbin/pmi** should be executed? Well, that doesn't happen here. To /usr/sbin/pmi, I added at the beginning of the file, after #! /bin/bash:

```
logger -t pmi "In $0 - pmi"
logger -t pmi "command = $1"
logger -t pmi "event = $2"
```

When I run pmi manually, those 3 entries show up in the syslog. But they do NOT show up, when I push the Hibernate button.

I'd really like to know, what's supposed to happen, when the Hibernate button is pressed and how I can configure this. I'd also be interested to know, to what package this log out dialog belongs. On Gentoo it looks **VERY** different than on Ubuntu. How comes?

Thanks,

Alexander

---

### Post by madrabbit on 2006-08-29
What you want can be done via gconf-editor. See this thread: [http://www.ubuntuforums.org/showthread.php?t=144626](http://www.ubuntuforums.org/showthread.php?t=144626) for details.

---

