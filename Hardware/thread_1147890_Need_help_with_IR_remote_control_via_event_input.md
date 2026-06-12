---
title: "Need help with IR remote control via event input"
date: 2009-05-03
forum: Hardware
---

### Post by Mysphyt on 2009-05-03
Hey, folks-
     Here is my (somewhat exhausting) situation.  I'm setting up Boxee for the first time, using Ubuntu 9.04, on a machine that had previously been a file server (running 8.04). As a result, I'm trying to use an IR remote control for the first time.  The receiver goes through an AverMedia AverTV Studio PCI card.  The IR receiver shows up as /dev/input/event6, which is all well and good.  If I push 8 on my remote, X receives a corresponding keyboard command.  If I push "AutoScan" on my remote, a file search dialog comes up.  I recently discovered that there is a button that, without warning, shuts down my computer.  (I have since tried to avoid it.)  I want to make this remote work with Boxee.  From there, I am lost.  Here's what I've done so far.
     First, I tried LIRC.  This seemed the most obvious option.  When I install LIRC, the keyboard functions of my remote disappear.  The problem is, no matter how my lircd.conf and hardware.conf are set up, I can't make my remote input get into LIRC.  I still get input via `cat /dev/input/event6`, but `irw` receives no response.  I have tried and tried.  `irrecord -H devinput -d /dev/input/event6` will generate a config file, but beyond that, I can't get anything.  ([Here]("http://lirc.sourceforge.net/remotes/avermedia/lircd.conf.avermedia.98") is the lircd.conf file recommended for my remote by LIRC.)  Ultimately, to get any input back, I had to `apt-get remove lirc`.  It showed up in X again.
     Second, I thought it might be worth it to go another way: namely, by setting up /dev/input/event6 as a separate InputDevice in xorg.conf.  This seemed like a good plan up 'til I got to the keyboard layout, and realized I'd have to make a custom layout from scratch, which seemed a daunting task.
     In short, I'm stuck.  I have no idea how to approach this problem from here.  I hope it's clear that I've searched up and down these forums and others in pursuit of making this work, but with LIRC in particular, I feel like even when I'm doing things right, I'm doing things wrong.  Any help would be appreciated.  Thanks heaps.

---

