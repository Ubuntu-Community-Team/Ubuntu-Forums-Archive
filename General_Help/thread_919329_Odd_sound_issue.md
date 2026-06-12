---
title: "Odd sound issue"
date: 2008-09-13
forum: General Help
---

### Post by UltraCheese on 2008-09-13
Sound works for the start up noises, but after that, nothing.  Swfdec will play sound, but it's unrecognizable and clearly not how it's supposed to be.  When I try to play videos in totem, the video moves really slow and there's no sound.  If I go into System -> Preferences -> Sound and hit test, the sound plays, but when I try to exit, it freezes and I have to force quit.
This was all working about a week ago, and still works on the live cd.  I was having a problem where acpi was using 70% of my CPU so I had to use the option acpi=off.  Really can't think of anything else that would have effected it.
Any ideas on how to fix this?

---

### Post by phidia on 2008-09-13
What are your system specs? It's very likely that setting acpi=off is the problem but to prove that edit that setting and see how sound works then.
You need to find out why acpi is using so much of your cpu cycles.
Check System > Admin > log files and/or /var/log/messages (dmesg plus other files in /var/log too).

---

