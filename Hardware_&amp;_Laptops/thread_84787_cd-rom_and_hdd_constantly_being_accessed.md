---
title: "cd-rom and hdd constantly being accessed"
date: 2005-10-31
forum: Hardware &amp; Laptops
---

### Post by demiurge on 2005-10-31
I just did a fresh install of breezy on my Fujitsu S6120 and for some
reason my removable cd is constantly being accessed (the cd-rom 
icon on the computer is constantly flashing but drive not actually 
spinning since it's empty), I removed the drive and this hard locks 
the computer. In fact my hdd is also being accessed every 5 second
so it couldn't spin down, but after I started laptop-mode it went back
to normal. Is there some new process that's doing this? Everything
was smooth under 5.04.

Also the battery meter doesn't work anymore and that's a bit annoying.
However suspend to ram finally works after years of waiting :D

---

### Post by demiurge on 2005-11-01
Oh well turns out that the process hald-addon-storage is the culprit. Stopping
it and cd is no longer being accessed. Doe anyone know what that process 
does? And any idea how to get battery meter going? Now it always says system
is running on battery with 100% remaining and unknown time even if I am on
AC. The battery meter works in 5.04 so I don't know what was changed.

---

### Post by RavenOfOdin on 2006-05-02
That happened to me too just a while ago, and I'm not running any removable device.

---

