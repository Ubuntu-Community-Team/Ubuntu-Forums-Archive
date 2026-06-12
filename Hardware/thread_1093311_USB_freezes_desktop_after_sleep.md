---
title: "USB freezes desktop after sleep"
date: 2009-03-11
forum: Hardware
---

### Post by MorayJ on 2009-03-11
Hi,

I'm wondering how best to explore this problem.

After I put my machine to sleep and wake it up again, running a script with the command 'scanimage -L' freezes up the desktop. I have a USB scanner.

I have edited /usr/lib/pm-utils/defaults to include the line:

```
SUSPEND_MODULES="ohci_hcd ehci_hcd"
```

This was to make sure that my Wacom tablet would be connected after waking.

I do not know how to diagnose what is going on as everything has stopped - is there some way to log what has happened so I can check on reboot. I am loathe to experiment too much, as I'm worried about corrupting the hard drive as I'm needing to just switch off the machine after this happens.

Any tips?

Thanks
MorayJ

---

### Post by MorayJ on 2009-07-14
Does anyone at all have any problems with their AMD64 machine freezing up altogether and requiring a reboot, sometime after the computer has been woken from sleep, or am I the only one?

---

