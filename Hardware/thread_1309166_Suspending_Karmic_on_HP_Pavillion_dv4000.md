---
title: "Suspending Karmic on HP Pavillion dv4000"
date: 2009-11-01
forum: Hardware
---

### Post by shadysamir on 2009-11-01
I reported a bug [#467323]("http://bugs.launchpad.net/ubuntu/+source/linux/+bug/467323") and I wish to share this with you.

I upgraded from a working jaunty to karmic final release. Jaunty used to suspend and hibernate and there is no problem. During upgrade, microsoft corefonts package failed to upgrade and it kinda messed up the process, the upgrade never performed the clean-up step. I know the clean-up probably just removes old packages that are no longer supported or needed.

Anyway, since then, the laptop would randomly not suspend. Sometimes it suspends and wakes up normally, some other times it's just stuck at the black dimmed screen but hard disk is spinning and fan is working and all lights are up. I have to reset holding the power button.

When the system is restarted after this hard reset, X server (gnome) fails to show window borders and I get a crash warning. I have to Restart from the menu to get it working back normally.

---

### Post by shadysamir on 2009-11-02
It seems like the problem occurs in a session that's been woken up from suspend. Such a session hangs when I try to suspend it again

---

