---
title: "how to change the default runlevel"
date: 2008-10-18
forum: General Help
---

### Post by mkrahmeh on 2008-10-18
as addressed in the title..i tried to find the inittab file, but it doesn't exist, so what's the alternative here ??

---

### Post by RealPSL on 2008-10-18
Great question. I had to look this up myself and the answer for the most part is [here]("http://www.linuxquestions.org/questions/ubuntu-63/since-we-have-no-etcinittab-506281/").

You want to review /etc/event.d/rc-default. Create your own inittab to set the run level you want. However before that you can also test it using ```
telinit runlevel
``` Where run level is the desired runlevel. Why are you trying to change the run level anyway?

---

