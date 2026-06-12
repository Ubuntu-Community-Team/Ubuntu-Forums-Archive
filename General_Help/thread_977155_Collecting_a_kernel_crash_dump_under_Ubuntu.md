---
title: "Collecting a kernel crash dump under *Ubuntu"
date: 2008-11-09
forum: General Help
---

### Post by siquad on 2008-11-09
I'm not sure if this is the best forum to post this question...

I've been seeing random kernel panics with caps-scroll blinking along with frequent freezes for the last week or so and I've been trying to collect a crash dump for a few days now to no avail.

I cannot find a complete how-to on this topic specific to *Ubuntu. I found a few general articles, most of them are for previous kernels and focus on recompiling with the correct paramaters...etc.

I've checked the kernel shipped with 8.10 and it's configured to enable crash dumps, I have crash, kexec-tools and makedumpfile packages and their dependencies.

I'm able to use kexec to load a crash kernel and set it to boot in the case of a panic, but if I try to do "kexec -e", I see my eth connection go down, followed by a kernel panic.

I've tried various settings and kexec paramaters from different articles, I've recompiled my kernel with different tweaks, changed all kinds of boot settings but I cannot get a dump file under /var/crash/ no matter what I do, and my /proc/vmcore is always empty.

I don't see any issues in the various system logs other than benign warnings.

Can someone _please_ post a complete procedure for capturing a kernel dump under *Ubuntu starting with a fresh 8.10 installation?

---

### Post by siquad on 2008-11-12
I guess I'm not posting to the right audiance.

Can someone at least point me to the right forum for this question?

---

### Post by prshah on 2008-11-12
> **siquad said:**
> 
I've been seeing random kernel panics with caps-scroll blinking along with frequent freezes for the last week or so and I've been trying to collect a crash dump for a few days now to no avail.

Can someone _please_ post a complete procedure for capturing a kernel dump under *Ubuntu starting with a fresh 8.10 installation?

[http://ubuntuforums.org/showpost.php?p=5475062&postcount=71](http://ubuntuforums.org/showpost.php?p=5475062&postcount=71) may be of some help in this regard.

And, if you continue further down in [the thread (Posts 71~74)]("http://ubuntuforums.org/showthread.php?t=832383&page=8"), it's been done successfully, and more details are given, including where to get the cable required.

---

