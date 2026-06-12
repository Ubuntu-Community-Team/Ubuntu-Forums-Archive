---
title: "Excessive processor usage"
date: 2009-11-16
forum: Hardware
---

### Post by Chris H on 2009-11-16
Hi, just tried Ubuntu for the first time in ages and have a query about processor usage. First post in ages as well!

Ever since the kernel went from 2.4 to 2.6 I've noticed that all distro derivatives aside from Slackware and it's cousins have issues with processor usage on my laptop.

What happens is that certain tasks such as ripping a cd, watching flash videos or other processes such as updating repos cause my processor to hit 100% and likely as not stay that way until my laptop shuts down or the task finishes.

As I've said, it doesn't happen with Slackware or distros like Zenwalk.

Laptop is a rebadged Uniwill 258KA0 with an AMD 64-bit processor.

One thing I haven't tried is running 64-bit distros, least not since kernel 2.4, mainly because of issues with flash etc on 64-bit distros.

Think it's worth a try with Ubuntu 64-bit? Or anyone have any ideas why I have this problem?

Ta.

---

### Post by ajgreeny on 2009-11-16
I am surprised that slackware does not also have a peak in cpu usage when flash is being used, as that seems to be a well documented problem with the linux flashplugin, and nothing specifically to do with Ubuntu or any other particular distro, as far as I'm aware.

Is the version of slackware you speak of a recent one with an up-to-date kernel, or are you talking of an older version and an older kernel; it's a long time, I think since most distros had a 2.4 kernel, Ubuntu has never had one, it started with a 2.6.8, and in the several years since the 2.4 kernel, most distros are probably doing a lot more in the background than they used to do.

Bloat?  Perhaps, to some extent, but that's for another thread and discussion.

What is taking all your cpu usage in any case?  Show us the output of ```
top
```to show where it's all being used, and maybe someone can suggest a way to improve things.

---

### Post by Chris H on 2009-11-16
This has been a long running issue on my laptop and I can only link it with the 2.6 kernel, I can't see any other factor. Perhaps there is.

There are specific progs and scripts that send my processor high. Firefox is one, flash has been another but just checking on youtube now I see no sign of flash in top, just ff. The only time this laptop shut down with 9.10 was when ubuntu one was sending files. Processor use went to 100%, fan speed went bananas and it shut down after a minute or two.

When I've tried to install gOS I can get it to partially install but when it updates it shuts down, other distros downloading repositories do the same - mandriva for one.

One thing with flash is that if a video is sending the cpu mad then scrolling the vid out of the window sees an immediate drop. Also enabling things like compiz-fusion causes the issue. ATI chipset.

As an aside do you know of any compatability issues that exist with the current 64-bit distro? Might be worth a try.

---

