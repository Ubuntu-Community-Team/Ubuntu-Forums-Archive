---
title: "Presario V2405 doesn't work"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by lik3n on 2005-11-01
I've tried booting the LiveCD and that locks up as Gnome is starting.
And I've tried installing Ubuntu but the xserver doesn't run.

AMD Sempron processor
256 megs of ram

I probably could add more details to this, but I've been trying to get this to work all day and my head hurts.

---

### Post by lik3n on 2005-11-13
I fixed it.

---

### Post by lik3n on 2005-11-13
I could also use this to get my posts up, but I won't.

---

### Post by punkr0x on 2005-11-14
So what did you have to do?

I'm currently working on getting a Presario V2000 (with an AMD Sempron) set up with ubuntu, I've found I have to put the line
Option   "noaccel"
in my xorg.conf for the video card, and also have to boot the livecd with the "noapictimer" command in order to get the clock running at the proper speed.

---

### Post by lik3n on 2005-11-14
I actually wrote how I got mine to work on my blog. I can't promise that it'll work for everyone, but it's worth a shot.

[http://worldclock.blogspot.com/2005/11/not-witherspoon-but-silverstone.html](http://worldclock.blogspot.com/2005/11/not-witherspoon-but-silverstone.html)

Good luck. :)

---

### Post by punkr0x on 2005-11-14
Cool.  What version of Ubuntu are you running?

---

### Post by lik3n on 2005-11-14
5.10 Breezy.

---

