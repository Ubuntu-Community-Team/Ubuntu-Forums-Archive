---
title: "mouse weirdness: kernel: [4376537.849000] psmouse.c: bad data from KBC - timeout"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by Velvet Elvis on 2005-10-30
OK since around the time I upgraded to breezy, my mouse has been spazzing out on me.  Sometimes it will go bonkes and dance all over the screen why I'm using it.  Sometimes it will stop if I leave it alone for a while and sometimes it freezes up.  When it freezes, restarting X fixes nothing.  It only comes back to life after a reboot.

It's the same m$ ps/2 mouse (no wheel) that I've been using for years, but I do have a relatively new kb.

At times corosponding to when it does this, there is this message is /var/log/messages.

```
Oct 30 20:02:28 localhost kernel: [4376537.849000] psmouse.c: bad data from KBC - timeout
Oct 30 20:02:28 localhost kernel: [4376537.872000] psmouse.c: bad data from KBC - timeout
Oct 30 20:02:28 localhost kernel: [4376537.876000] psmouse.c: bad data from KBC - timeout
```

Short of doing everything from within emacs, any idea what I should do?  I used slackware for years before switching to ubuntu, so I don't mind getting my hands dirty.

---

### Post by Velvet Elvis on 2005-10-31
Here are a couple other error messages from the time of the freakouts:

```
Oct 31 17:41:15 localhost kernel: [4366616.318000] psmouse.c: bad data from KBC - bad parity
Oct 31 17:41:39 localhost kernel: [4366640.383000] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
...
Oct 31 17:43:04 localhost kernel: [4366726.043000] psmouse.c: bad data from KBC - bad parity
Oct 31 17:43:09 localhost kernel: [4366731.184000] psmouse.c: Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
```


Any ideas?  My next step is going to be trying a USB mouse I guess.

---

### Post by maxol on 2005-11-12
I have the same problem.

The really odd thing is that everything works fine if I unplug the RJ45 cable from my network card.

If I plug it in again the mouse spazzes out and I get the "bad data from KBC" errors from dmesg.

Everything was working fine untill recently, I'm using Breezy Badger with the i386 kernal.

Has anybody found a fix or have a similar problem?

---

### Post by stuffa on 2005-12-12
I also have a similar problem

gdm starts OK,  keyboard works,  just dont touch the mouse,  if you do the keyboard locks up,  the mouse doesnt work and the syslog and kern.log fill up with the following:

Dec 12 23:02:40 localhost kernel: [906944.924978] psmouse.c: bad data from KBC - timeout

About 80 times a second.

hoping that someone comes up with fix

PS: Im running Breezy on a compaq 1600 proliant

---

### Post by sinnerman on 2007-03-15
I have some problem with crazy mouse and bad parity.

Does anybody resolve problem?

---

### Post by Reugen on 2007-06-11
I have teh same problem, i have reinstalled  hal and that seems so far to have worked.  (aptitude reinstall hal).
One link you may want to check out is [http://kerneltrap.org/?q=node/2199](http://kerneltrap.org/?q=node/2199) . (check mouse cable, disable acpi etc,)  psmouse.c: bad data from KBC - bad parity has been accompanied by psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away. on my system, the latter of which the link refers to.

---

### Post by Reugen on 2007-06-11
nm i was just lucky enough to have that problem not occur for about 2 hours (it normally happens every few minutes)  reinstalling hal didn't work.

---

### Post by Reugen on 2007-06-11
Tried mouse with gentoo, and liveCD, and they had the same problem!  Replaced the mouse and all the problems went away.

---

