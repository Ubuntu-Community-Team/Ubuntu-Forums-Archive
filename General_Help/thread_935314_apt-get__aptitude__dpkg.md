---
title: "apt-get / aptitude / dpkg"
date: 2008-10-01
forum: General Help
---

### Post by hostile on 2008-10-01
I was just wondering which of these is the more "correct" to use.

Personally, I like using apt-get, but I was having discussions at work with one of the other admins, and he said that aptitude is the more correct one to use as it keeps track of dependencies more accurately than apt-get.

Can anyone shed some light on this?

Thanks!

---

### Post by briandu on 2008-10-01
I always use apt-get and I believe it is the original father of the rest. It is good to use  and dependencies are managed ok.

Any of these tools can become confused if you install xxxx.deb files from anywhere - then you may experience dependency probs otherwise it will always work.

---

### Post by Aero-Z on 2008-10-01
dpkg should be for installing local deb packages only. So it's more like apt-get or aptitude. I prefer apt-get

---

### Post by hostile on 2008-10-01
> **briandu said:**
> I always use apt-get and I believe it is the original father of the rest. It is good to use  and dependencies are managed ok.

Any of these tools can become confused if you install xxxx.deb files from anywhere - then you may experience dependency probs otherwise it will always work.


For deb files, I usually use dpkg.

I was under the impression too that apt-get was the father, but this other admin was saying that aptitude is more correct now and that apt-get's dependency tracking is now "hacked" so that it acts more like aptitude... :confused:

---

### Post by briandu on 2008-10-01
Sounds like your admin friend likes a good tool -  there are many similar and they all work but some folks like a tool.

I would not get worked up about this - the dependency story is frankly nonsense. I have used it for 5 years now and no prob in Debian and now Ubuntu.

Ignore FUD

---

### Post by hostile on 2008-10-01
Ya... that's what I was thinking.

Until I see concrete evidence to the contrary, I'll just continue on my merry little apt-get way...

:D

Thanks!

---

