---
title: "Netbook Edition + Pentium M = Fail?"
date: 2010-06-16
forum: Hardware
---

### Post by mjkerpan on 2010-06-16
I was recently given an old mini-notebook with a first generation Pentium M CPU and after seeing that the CPU is rouigly equal to a present-day "Atom" CPU in various benchmarks, I thought that it would be cool to run Ubuntu Netbook Edition on the thing. Sadly, UNE doesn't seem to want to boot on the laptop: it starts out fine but then when it looks like X11 is about to start, things go dead. Does UNE lack the graphics drivers needed to make the old Intel 855/865 graphics chips work? Is there any way to get the netbook interface going on top of a vanilla install? Help on resurrecting an old but still solid laptop is needed.

---

### Post by bobnutfield on 2010-06-16
> **mjkerpan said:**
> I was recently given an old mini-notebook with a first generation Pentium M CPU and after seeing that the CPU is rouigly equal to a present-day "Atom" CPU in various benchmarks, I thought that it would be cool to run Ubuntu Netbook Edition on the thing. Sadly, UNE doesn't seem to want to boot on the laptop: it starts out fine but then when it looks like X11 is about to start, things go dead. Does UNE lack the graphics drivers needed to make the old Intel 855/865 graphics chips work? Is there any way to get the netbook interface going on top of a vanilla install? Help on resurrecting an old but still solid laptop is needed.

There are numerous posts about this issue.  There is a regression in the intel driver (i915 is usually loaded by default with that chip).  I don't totally understand it, but for many appending the kernel line in grub with:

```
i915.modeset=1
```

works.  This is done in /etc/default/grub.  Sorry, I am not on my Ubuntu laptop right now, but it is in the same line as "quiet splash".  You would add to this line INSIDE THE SAME QUOTES.  Save it then run sudo update-grub.  No quarantees, but it has worked for some with this issue.

---

### Post by kerry_s on 2010-06-16
is your installer good, did you check it?
your cpu has nothing to do with it working or not.
remix has 2 versions theres 3d & 2d, which are installed, if your system can not handle the 3d, try the 2d made for even lower spec netbooks.

> Is there any way to get the netbook interface going on top of a vanilla install?

install ubuntu-netbook-remix
log out
select it in the session menu
log in

if you still need lighter, i suggest you try lubuntu. it also has a netbook setup at the menu. but i would switch the lxlauncher for netbook-launcher-efl from the ubuntu-remix setup.

---

### Post by mjkerpan on 2010-06-16
Adding that line fixed things. I'd just realized that the same problem existed with the "normal" release too, but it's all good now.

---

