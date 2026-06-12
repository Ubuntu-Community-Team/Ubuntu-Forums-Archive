---
title: "Hibernate/suspend not working on Dell m1530"
date: 2009-04-20
forum: Hardware
---

### Post by colonelqubit on 2009-04-20
I got a Dell m1530 recently and wiped the stock Dell Ubuntu install, replacing it with a dual boot of WinXP & Ubuntu 8.10 (x86_64).

WinXP suspends/hibernates without problem, but I have had trouble getting suspend and hibernate working under Ubuntu.

When I hibernate the machine it powers down successfully. When I open the laptop lid to resume, the Ubuntu splash screen with progress bar appears (at least most of the time), but the machine just hangs on that screen and doesn't progress any further. Power-cycling the machine will result in a normal boot.

From what I've read, suspend and hibernate generally work on the m1530, so I'm wondering if either the 64-bit kernel or the fact that I've installed Ubuntu on top of LVM is causing this problem.

Thoughts?

(I'll post the output of kern.log as a followup -- please pardon me while I go hibernate/hang my system)

---

### Post by RedSingularity on 2009-04-20
I have the same problem.  Its not a rare case, many other people have it as well.

---

### Post by colonelqubit on 2009-04-20
Okay, while going into hibernation I saw "hci urb failed to resubmit", then the machine powered down.

The machine appeared to hibernate and power down. Then when I powered-on the machine, the ubuntu splash screen appeared and the progress bar was moving (small bar moving back and forth inside the progress bar), but then froze at some point. A few moments later the screen went to black for half a second, then back to the frozen splash screen + progress bar.

After giving it some time, I restarted the machine. Included is the relevant part of kern.log.

---

### Post by colonelqubit on 2009-04-20
> **Shadow121 said:**
> I have the same problem.  Its not a rare case, many other people have it as well.

Are there any other forum posts or bugs filed about this problem?

(And as an aside, when should something be a question on the forum and when should it be filed as a bug report?)

---

### Post by RedSingularity on 2009-04-20
You file bug reports at _[https://launchpad.net/](https://launchpad.net/)_

---

