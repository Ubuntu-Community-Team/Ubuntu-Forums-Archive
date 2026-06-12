---
title: "Boot/Shutdown errors - serious?"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by RanDinCarolina on 2005-12-07
i was just wondering if these errors are serious and if so, what I should do to fix them. 
the 1st errors are at boot:

```
insmod: can't read ` /libmodules/2.6.12-10-686-smp/initrd/vesafb.ko: No such file or directory
```

then:

```
0[4294676.369000] usb 1-1: device not accepting address 2, error -71
```

At shutdown, I get:

```
/etc/dbus-1/event.d/20hal: line 49: /var/run/hal/hald.pid: No such file or directory
```

a little bit further on, I get:

```
/lib/lsb/init-functions: Line 236: /usr/bin/tput: no such file or directory
```

At the end, I get:

```
[4295498.797000] power down.
```

At this point, the machine hangs and I have to smack the large round shiny thingy to turn it off. I don't post a lot because I usually either google or search, but either I'm not using the right terms or these errors are not in here.

What should I do to rid myself of these errors? Should I create the requested files or directories in those locations?

My main worry is that the reiserFS will become corrupted since I get a lot of journal replays.

This particular machine is a MSI 865PE Neo2-P w/P4 3.0HT, 2G 400mhz, 2 160 SATA WD and a nVidia 5200 w/256m video running a basic Gnome w/nvidia drivers (7667). It also dual boots XP (for the wife and kids).

---

### Post by Arktis on 2005-12-08
Just to point something out:  This is the wrong area for this topic.  You may have better luck posting in the proper forum section.

---

