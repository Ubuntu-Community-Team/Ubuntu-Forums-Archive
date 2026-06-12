---
title: "T60p with Ubuntu Edgy freezes during boot when connected to docking station"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by giorgione on 2006-11-06
Hi every one,

I have a "small" problem with my new T60p and its docking station. When the thinkpad is not connected to the station it boots (usually) without problems. But when is it connected, it just freezes and the only thing I can do is switch it of.

Because I am a newbie, I have no clue how I could approach this problem, so I could really use some help. Is this problem known, if yes, is there a solution?

Thank you very much!

---

### Post by giorgione on 2006-11-07
Hi, just updating the post.

I know now the error that is shown just before it freezes:

udevd-evet[3262] : wait_for_sysfs : '/sys/devices/platform/i8042/serio0/serio2/bus' failed
 * Loading manual drivers...
[17179601.084000] BUG: soft lockup detected on CPU#0!

After that there are sill coming some lines without errors and than it freezes.

What I know is that '/platform/i8042/serio0/serio2/' refers to the Tracking Point, but I don't know that I should do this that information and how to solve my problem.

THX

---

