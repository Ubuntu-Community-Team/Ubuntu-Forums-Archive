---
title: "nvidia kernel and component dont match"
date: 2009-04-28
forum: Hardware
---

### Post by sweet_mackerel on 2009-04-28
[original problem]
hi i was wondering how to fix my nvidia kernel so that it matchs the compenent

i seem to have the 96.43.5 kernel and the 96.43.10 component

[solution]
not too certain of the how and why of the fix (mostly because i didn't really understand the problem)

i "fixed it" by

1 > running a livecd, grabbing the xorg.conf from etc/X11
2 > restarting into my normal system, and replacing only the sections from the livecds xorg.conf that existed in my systems xorg.conf ( screen monitor and device)
3 > restarting x (by logging out and then back in again) and then running NVIDIA X SERVER SETTINGS (i found this under system>administration but i'm fairly certain i had to install this from the repos at some earlier point)
4 > resarting x again ( same way as before)

---

