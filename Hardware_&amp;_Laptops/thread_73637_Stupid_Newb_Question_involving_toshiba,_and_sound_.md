---
title: "Stupid Newb Question involving toshiba, and sound help me please"
date: 2005-10-09
forum: Hardware &amp; Laptops
---

### Post by ImplicitProcrastination on 2005-10-09
So I have Toshiba Satellite A75-S226 with "hoary" on it and I'm very happy with it. It runs well except that I can't get the sound to work. I've tried many different tutorials altering settings and downloading drivers trying to figure out how to get it to work but I can't, because alas, I am dumb newb. So can someone help me?

It is a Pentium 4 with like 3.06 gigahertz and 512 megs of ram (I think). The soundcard is an IXP 150 AC'97 Audio Controller from ATI according to the device manager.

I've tried everything on ubuntu wiki and the documentation and the unofficial page regarding the subject but can't figure out the problem. It makes simple noises like when I confuse it. Please help me.

---

### Post by rquinn19 on 2005-10-09
I've got almost the same laptop and had the same problem.  From the terminal type alsamixer and go all the way to the right and unmute the last one which is something like external amp or something and it should work.  you might have to turn the volume up a lil bit too

---

### Post by ImplicitProcrastination on 2005-10-09
I've done that, I get this:

alsamixer: function snd_ctl_open failed for default: No such file or directory

---

