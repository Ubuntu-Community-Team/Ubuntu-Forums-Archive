---
title: "File system hangs in certain apps after upgrade to Jaunty"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by yoyodyne on 2009-06-07
Thinkpad T61p. Originally installed Hardy, was working pretty well.

Did the upgrade to Ibex, then Jaunty, using update-manager -d. 

Seemed to go pretty well, I didn't really mess with anything. Really like the suspend fixes in Jaunty, never had that working before.

The only issue I've really noticed is certain applications freeze when saving/opening a file from disk.
For example, I was taking notes at a conference using gedit. gedit would open fine, but as soon as I tried to save the file, it would hang...then go grey (I'm using compiz fusion), then eventually I'd get the 'Browse...' window.
It does this with Firefox as well. The odd thing is that Nautilus doesn't seem slow and I can browse the file system (ext3) using a terminal just fine.

I was probably just going to back everything up (most data is on a different partition) and reinstall Jaunty from scratch, but before I do that figured I'd ask for ideas.

I don't see anything extra ordinary in the logs and other than that, most things are fine. I have had X freeze a few times, but killing it/restarting gdm usually works.

---

### Post by cmonkey on 2009-06-09
It seems this is a known bug.  I've run into something similar.

[https://bugs.launchpad.net/ubuntu/+bug/371191](https://bugs.launchpad.net/ubuntu/+bug/371191)

---

### Post by yoyodyne on 2009-06-12
cmonkey, meant to say thanks for the link.

although, still not sure if my issue is the same (or what is causing it). nothing seems to crash (yet). i normally use a wireless mouse with the laptop and noticed just the other night that it wasn't gdm faulting, it was the mouse. 
when i use the touchpad everything works.

so the only real problem is when i hit 'Browse...' to navigate the file system, whether that is from a text editor or Firefox. synaptic and installing/upgrading is full speed, nothing else seems bothered. 

Is there some process that controls the 'Browse' functionality? It's a bother, but not a deal breaker...should probably just reinstall.

---

### Post by winecurmudgeon on 2009-10-21
I have the same problem. I installed 9.04 on a dual boot with Vista, and some apps (Firefox, Thunderbird among them, but not Open Office) hang when I try to save a file. I also get very slow load times when  the save dialogue box comes up. 

Any thoughts?

---

