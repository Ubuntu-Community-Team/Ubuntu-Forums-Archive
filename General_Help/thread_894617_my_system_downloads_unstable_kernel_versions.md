---
title: "my system downloads unstable kernel versions"
date: 2008-08-19
forum: General Help
---

### Post by kman16 on 2008-08-19
My laptop (thinkped R50e with ubuntu 8.04.1) started to make a beep sound  just before the login screen appears. It turns out that the kernel i'm using (2.6.24-19) can't build a module. I understood that odd last number means unstable kernel. i don't wish to solve it, i rather use a stable version.

I can choose in the GRUB menu to boot XP, IBM recovery or Ubuntu 2.6.24-16 to 2.6.24-19 (normal or safemode) + memtest86. and booting to 18 works fine.

why do I get updates to unstable versions? how can I stop it? and how do I remove the unstable and old kernels?


p.s. i'm quite now to linux and ubuntu. never tried to mess around with the kernel (building, upgrading, etc.).

---

### Post by Ryadt on 2008-08-19
2.6.24.19 is stable.

---

### Post by sdennie on 2008-08-19
The -19 doesn't refer to an unstable version.  As long as you don't have the proposed repository enabled (you can check with System->Administration->Software Sources), you will always receive what is considered to be a stable kernel.  If it's not stable and previous versions were, then it's a regression and you may want to file a bug at [www.launchpad.net](www.launchpad.net) or at the very least see if it's a known bug with a workaround.

---

### Post by kman16 on 2008-08-19
I've been told that 19 is unstable version in other forum... Any way when booting to 18 the problem is gone (no beeping at startup).

I checked my softwere sources settings and hardy-proposed isn't marked, only hardy-security and hardy-updates are marked. cheacking interval is on two days and "only notify..." is selected.

---

### Post by Nepherte on 2008-08-19
Every kernel update release goes through a testing/unstable phase. They can often be found in the proposed repository. After bug fixes and when it has been found stable for the test users, it gets the stable status. Maybe it was in the unstable status back then, but it isn't now.

You could either try to fix the problem with -19, but if -18 still works for you, you can always go with that one.

---

### Post by kman16 on 2008-08-20
@Nepherte:
I never marked "proposed" so I shouldn't be getting unstable versions from the first place. I'm currently using 18 and its fine but I wish to set my system not to download unstable kernels from the first place. 
Actually I'd rather to be asked every time there is going to be a kernel update (even when its for a stable one), if i'd like the system to update with out telling me I would choose winXP.  

I'm also curious what are the benefits of having 4 kernel versions on my pc?

---

### Post by bingoUV on 2008-08-20
odd numbers no longer mean unstable: [http://en.wikipedia.org/wiki/Linux_kernel#Version_numbering](http://en.wikipedia.org/wiki/Linux_kernel#Version_numbering)

If you find .19 is doing you no good, search launchpad for bugs on it. If you don't find any, file a bug on it. Include as much information as possible from here: [http://www.kernel.org/pub/linux/docs/lkml/reporting-bugs.html](http://www.kernel.org/pub/linux/docs/lkml/reporting-bugs.html)

---

### Post by Nepherte on 2008-08-20
> **kman16 said:**
> @Nepherte:
I never marked "proposed" so I shouldn't be getting unstable versions from the first place. I'm currently using 18 and its fine but I wish to set my system not to download unstable kernels from the first place. 
Actually I'd rather to be asked every time there is going to be a kernel update (even when its for a stable one), if i'd like the system to update with out telling me I would choose winXP.  

I'm also curious what are the benefits of having 4 kernel versions on my pc?
As I was trying to tell you, -19 is a stable version, unfortunately not for you. Situations like these are the reason old kernels don't get removed when a new one is installed. If a newer one breaks your system, you can use a previous one. If -18 works for you, you can remove every < -18 version if you want.

---

