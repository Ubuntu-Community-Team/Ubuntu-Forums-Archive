---
title: "Strange crashing in Rhythmbox: &quot;deadlocking&quot;?"
date: 2006-05-05
forum: Hardware &amp; Laptops
---

### Post by andrewski on 2006-05-05
Hello,
I've been having a recurring problem with Rhythmbox.  I am currently running Dapper, but I'm pretty sure the problem cropped up before that on Breezy, and the fellas in #rhythmbox and #gstreamer seemed to think that it was more of a driver issue.

Anyhoobie, one fella said that it is a deadlock, and that those are normally caused by kernel space drivers. :confused:  I vaguely understand what that means, but I have no idea how to debug it.  It's rather random when it happens, it doesn't officially crash so I can't backtrace it in gdb, and the only way to get rid of the process is to reboot (kill -9 doesn't work).

Anyone have any ideas as to which driver could be causing the problem and/or how I could fix it... or at least put a worthwhile bug in Launchpad? :-(

Since this seems to be a driver issue, I put this in Laptop Support, but if that doesn't seem right, by all means, move it! ;)

---

### Post by andrewski on 2006-05-31
Turns out this was a problem with my CD/DVD drive.  I just got it replaced and now things are working much better!  Yay for a quick response from Dell and yay for Rhythmbox!

---

