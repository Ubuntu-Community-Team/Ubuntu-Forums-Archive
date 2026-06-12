---
title: "computer hibernates after wake up from auto suspend"
date: 2008-12-14
forum: Hardware
---

### Post by ethanay on 2008-12-14
hello folks,

dell xps m1330 running hardy w/latest (except kernel 2.6.24-19 kernel b/c the latest versions break suspend/hibernate completely and cause some other hardware issues)

here's the issue:  manually entering suspend is fine, works great.  however, when the computer automatically enters suspend after a pre-defined time (45 minutes when plugged in) for some reason, when i wake it up some hours later, it begins to hibernate!  the hibernation is successful, but it is a completely unnecessary step before i can begin using my computer again, eh? :)

so i figured it might be due to one of these two issues:
1. the computer is still counting something (a setting i can't find?) while suspended and it passes a "hibernation time" but can't initiate hibernate until wake up from suspend occurs.  apart from disabling hibernate completely, i don't see how it is possible to fix this if it is the case.
2. the computer resumes and can't ascertain power state, so initiates hibernate on a "critical power state" (which i have set <=2%).  i have increased the suspend policy on wakeup threshold in gconf-editor and will report if this fixes the issue.

---

