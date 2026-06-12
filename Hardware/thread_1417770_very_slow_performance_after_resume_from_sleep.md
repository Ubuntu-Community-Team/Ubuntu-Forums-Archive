---
title: "very slow performance after resume from sleep"
date: 2010-02-27
forum: Hardware
---

### Post by meonkeys on 2010-02-27
My laptop performs very poorly after resuming from sleep. It appears to be a problem with the disk. Anyone have any idea on things to try to fix the issue?

What I'm seeing might be [bug #371212]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/371212") (I marked it as affecting me).

Before resuming:
```

$ sudo hdparm -Tt /dev/sda
/dev/sda:
 Timing cached reads: 3266 MB in 2.00 seconds = 1634.85 MB/sec
 Timing buffered disk reads: 168 MB in 3.02 seconds = 55.55 MB/sec

```

After resuming:
```

$ sudo hdparm -Tt /dev/sda
/dev/sda:
 Timing cached reads: 1968 MB in 2.00 seconds = 984.62 MB/sec
 Timing buffered disk reads: 8 MB in 3.20 seconds = 2.50 MB/sec

```

* Dell Latitude D630
* Ubuntu 9.10
* processor is pegged upon resume (looks like lots of CPU time is spent "waiting"--can't tell if that's disk wait or what)
* uname -a shows "Linux 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux"
* rebooting fixes the issue

Interesting... just as I was writing this, I tried adding "irqpoll" to my kernel command line (by editing GRUB_CMDLINE_LINUX in /etc/default/grub), and this seems to have fixed the performance issue. If this works for a while, I'll mark this thread "solved".

---

### Post by meonkeys on 2010-03-13
Also see [this thread about erratic/jumpy mouse behavior]("http://ubuntuforums.org/showthread.php?t=1429199").

I've noticed:

[LIST]
[*]when irqpoll is on the kernel command line, the performance on resume problem is fixed but the mouse is erratic/jumpy
[*]without irqpoll, the opposite is true
[/LIST]

---

### Post by meonkeys on 2010-04-10
I gave up with the Dell Latitude D630. I'm using a Latitude E6400 instead now. Sleep/hibernate/resume in Ubuntu 9.10 works perfectly.

(as does the built-in web cam and mic, compiz, wifi, and everything else!)

---

