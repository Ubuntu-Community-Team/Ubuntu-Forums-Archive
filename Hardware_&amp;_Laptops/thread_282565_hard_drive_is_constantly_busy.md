---
title: "hard drive is constantly busy"
date: 2006-10-22
forum: Hardware &amp; Laptops
---

### Post by dmizer on 2006-10-22
my hard drive is getting accessed constantly, and i'm not sure what's causing it.

this is a desktop system, and i'm worried about the life of the drive.  not too sure where to start troubleshooting this ... any ideas on tools or something to check?  dmesg isn't showing any errors.

---

### Post by dmizer on 2006-10-22
```
sudo killall hald
```
this stopped my hdd activity.

what does this do, how much do i need it, and how can i prevent it from thrashing my drive?

---

### Post by kent41 on 2006-10-23
> **dmizer said:**
> my hard drive is getting accessed constantly, and i'm not sure what's causing it.

this is a desktop system, and i'm worried about the life of the drive.  not too sure where to start troubleshooting this ... any ideas on tools or something to check?  dmesg isn't showing any errors.

I am sure you have looked at TOP and what are the busy tasks?

---

### Post by dmizer on 2006-10-23
yeah ... top doesn't show anything out of the ordinary.  top is not so great at showing hard drive activity.  i tried the system monitor applet, but that didn't produce anything either.

i just happened to remember that hald did the same thing on my server until i turned it off.  what's the thing do anyway?

---

