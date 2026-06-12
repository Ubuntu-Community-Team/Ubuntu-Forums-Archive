---
title: "How do I re-wake keyboard and trackpad on resume from suspend?"
date: 2009-04-16
forum: Hardware
---

### Post by scradock on 2009-04-16
The subject says it all, really..... I'm trying to get suspend/resume working on my HP zv600, both in Intrepid and in Jaunty. The video quirk setting model has apparently changed (again), but I'm getting there.

Now that my screen wakes up after resuming, with all the apps running as they were before suspending, it's become clear that the keyboard and trackpad are not coming back to life. A USB mouse is active, but not the other two. This limits the usefulness of the resume - apps respond as expected to mouse clicks, but I can't type anything, so no CL tricks will help. Even the desperation ones (CTL-ALT-F1, CTL-ALT-DEL, ALT-SYSRQ-REISUB) are completely ignored - the only escape is to restart.

In /proc/acpi the keyboard and trackpad are known as pnp:00:06 and :07. They don't appear to have distinct pci: addresses, or they are so far down a branch that I haven't identified them.

Any ideas about how to re-waken them, or why resume is leaving them inactive?

Any helpful ideas gratefully considered!

---

### Post by unutbu on 2009-04-16
Perhaps try drs305's advice:
[http://ubuntuforums.org/showpost.php?p=6503389&postcount=55](http://ubuntuforums.org/showpost.php?p=6503389&postcount=55)

---

### Post by scradock on 2009-04-16
> **unutbu said:**
> Perhaps try drs305's advice:
[http://ubuntuforums.org/showpost.php?p=6503389&postcount=55](http://ubuntuforums.org/showpost.php?p=6503389&postcount=55)
Well, adding i8042.reset certainly seems to help. Another small step forward, perhaps. Thanks for the pointer -

---

