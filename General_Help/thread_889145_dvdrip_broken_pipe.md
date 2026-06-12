---
title: "dvdrip broken pipe"
date: 2008-08-13
forum: General Help
---

### Post by buchannon on 2008-08-13
I recently had to reinstall Ubuntu because my vista partition screwed some things up. Before I was running gutsy, now I'm running hardy. With Gusty, I had it all set up where I could rip a dvd with dvdrip. I try to do the exact same steps with my hardy installation and I always get the following error no matter what DVD it is - even if I've been able to rip it before.

> Command exits with failure code:
Output: te: Broken pipe
syncinfo write error (0)
write: Broken pipe

I get about 25 of these errors in a dialog box that pops up after I press the "transcode" button. Any idea?

---

### Post by xakira on 2009-01-27
Hi,

I had this problem with 8.10 and fixed it by loading "Ubuntu's restricted extras" using the System => Administration => Synaptic Package Manager.

I just searched for "restricted".

In DVD:RIP I transcoded with the Xvid4 and AC3 codecs

---

### Post by rvernica on 2009-03-11
> > sudo apt-get install libxvidcore

did the trick for me.

if you still have trouble, copy & paste the transcode command line from the dvd::rip log to the command line and maybe you get more info on what fails...

---

### Post by rmartinus on 2009-04-30
I'm having the same problem here..
I'll give this libxvidcore install a try tonight and see if it works

---

### Post by rmartinus on 2009-05-01
rvernica, installing libxvidcore fixed my problem. Thanks!

---

