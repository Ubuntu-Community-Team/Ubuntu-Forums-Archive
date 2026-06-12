---
title: "Use 'kbd' instead of 'evdev' for keyboard input device in xorg?"
date: 2009-10-24
forum: Hardware
---

### Post by dwhsix on 2009-10-24
(posting this in laptops/hardware since I'm trying to resolve a laptop issue)

Can someone advise how to switch 9.04 xorg.conf keyboard device from evdev to the old 'kbd' (e.g. what's the whole xorg.conf stanza I have to put in)?

I've had progressively more and more problems with my Dell Studio 15 keyboard; both the repeating-characters bug (which is known an outstanding) but also now I get extremely frequent dropped keystrokes.

I know it's not the hardware, because I dual-boot to Vista and it doesn't happen *at all*.

Some googling has led me to think there may be issues with the new evdev xorg device, so I'd like to try the old 'kbd' configuration and see if that makes any difference.

Thanks,

dwh

---

### Post by rimunroe on 2009-10-24
I am experiencing both dropped keystrokes and keystroke doubling in 9.04 on a Lenovo SL500.  The problem seems to increase as the computer is on for a longer time, or as the load on it increases (such as by playing Dwarf Fortress).  The rate of occurrences of keystroke doubling is much lower than the rate at which keystrokes don't seem to register.

---

### Post by dwhsix on 2009-10-25
Over in the Dell forums there has been some discussion of this being due to static buildup, but I'm very dubious...

I would absolutely agree that it tends to be worse when the system is under load.  Which points to a software issue, not hardware.

dwh

---

