---
title: "Optimizing boot times jaunty"
date: 2009-05-05
forum: Hardware
---

### Post by hesjnet on 2009-05-05
Hi Guys

Since installing jaunty with ext4 and noticing the big difference in boot times from 8.04 to 9.04 (1:20 -> 0:42) I took on me a mission to reduce the boot time even more.

So far I have done this:
[LIST]
[*]Removed unecessary startup programs and services
[*]Changed init.d/RC concurrency=shell
[*]auto login
[*]removed grub waiting(3 sek)
[*]grub profiling
[*]enabed speedstep
[/LIST]

So far I'm down to about 0:32, but I want more. I'm hoping to get down to 0:25.
[IMG]http://img147.imageshack.us/img147/7611/pallaptopjaunty20090505.png[/IMG]

Any ideas?

---

