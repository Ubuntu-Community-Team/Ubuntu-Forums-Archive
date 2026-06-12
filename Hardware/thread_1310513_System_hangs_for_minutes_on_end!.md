---
title: "System hangs for minutes on end!"
date: 2009-11-01
forum: Hardware
---

### Post by QuintusFabius on 2009-11-01
My computer has started hanging more and more often recently (starting a few weeks back and quickly becoming more frequent). When it "hangs" the mouse and gnome still seem to work just fine, but individual programs (usually most or all of them at once) are grayed out by gnome for not responding and sit w/o responding for as much as 2-3 minutes or as little as 5-10 seconds.

My XP partition has also been freezing in odd ways recently so I'm sure it is some kind of hardware problem. Both freeze in a similar way where they become non-responsive starting with some event (mouse click, key press, song changes in banshee, incoming message on skype, etc) and, after a while without responding, all programs eventually resume with all changes and events being processed in a matter of seconds.

My naive guess would be that there is some resource these programs are waiting for that is becoming unreliable (maybe my internal harddrive? or a usb drive?). My computer is just under 4 years old now and I am able to replace it soon if that is necessary - I'd just really like to at least know what this is and find a way to diminish symptoms for the time being, if possible.

Any thoughts what this might be and what I can do to investigate? Thanks,

Stats:
- Dell inspiron 6400 with a broken screen being used as a desktop.
- Core Duo 1.83GHz
- 2 GB Memory (already ran memtest86)
- Ubuntu 9.04 / XP SP3 dual boot
- Has been happening for weeks, just this weekend started getting really bad
- Happens the most to firefox, but usually multiple programs at once

---

### Post by dearingj on 2009-11-02
Perhaps try running the "System Testing" app (System->Administration->System Testing) a few times. See if it freezes during those tests, hopefully at a consistent point.

---

### Post by QuintusFabius on 2009-11-02
I ran those tests, nothing unusual. Any other ideas!?

Thanks...

---

### Post by TheForumTroll on 2009-11-02
Well you might try to look for a tool to check your harddrive on the manufactures website and run memtest to check for memory corruption (faulty ram, voltage problems, motherboard errors, etc).

---

### Post by QuintusFabius on 2009-11-03
My computer ran an automatic disk check a few weeks ago and it showed some problems and refused to boot. I ran a manual diagnostic program ("e2fsck" i think) and set it to automatically repair. It eventually worked and booted. I haven't had any errors/serious-problems since then, but could this be causing all the intermittent freezing? 

If so I'll probably wait until I can build a new computer, but is there anything I can do (short of replacing the HD) to improve performance of the drive in the short-term?

---

### Post by TheForumTroll on 2009-11-03
You could try to run "palimpsest". I think it's installed by default in System->Administration->Disk utility or you could just start it from ALT+F2. Run it, chose your harddrive in the list, click on More information and then have a look for errors. S.M.A.R.T doesn't catch everything but you might find something in there if your drive is faulty.

---

### Post by QuintusFabius on 2009-11-03
> **TheForumTroll said:**
> You could try to run "palimpsest".

I don't seem to have this installed. Some light research seems to indicate that this is part of 9.10. The one article I've found for installing this in 9.04 has broken links.

---

### Post by TheForumTroll on 2009-11-03
Well then there's "gsmartcontrol" in the repo.


```
sudo aptitude install gsmartcontrol
```

---

### Post by andrewabc on 2009-11-03
Back up any important information on winxp/ubuntu.

If it affects winxp and ubuntu then most likely hardware problem.

---

### Post by QuintusFabius on 2009-11-03
Do I need to add any repos? It can't find gsmartcontrol...

---

### Post by TheForumTroll on 2009-11-04
It seems it is only in karmic then. Sorry I do not know what app you can use from Jaunty.

---

### Post by dearingj on 2009-11-05
Perhaps boot from a Karmic live CD/USB and run gsmartcontrol and palimpsest from that

---

### Post by lswb on 2009-11-05
Hard drive problems are often accompanied by disk error messages in /var/log/syslog or other sytem log files.

---

### Post by QuintusFabius on 2009-11-09
> **lswb said:**
> Hard drive problems are often accompanied by disk error messages in /var/log/syslog or other sytem log files.

Well. I see a huge number of "pulseaudio" errors saying "protocol-native.c: Failed to push data into queue" and "asyncq.c: q overrun, queuing". There are hundreds of these spanning a recent 8-second period. Could these be related to the strange pauses?

The problems have gotten slightly better in the last few days, but not significantly. My screen and usb is also intermittently bad on this 4-year old laptop, so I think I _am_ going to move my plans to build a new computer ahead a few months.

([http://ubuntuforums.org/showthread.php?p=8277775](http://ubuntuforums.org/showthread.php?p=8277775))

---

