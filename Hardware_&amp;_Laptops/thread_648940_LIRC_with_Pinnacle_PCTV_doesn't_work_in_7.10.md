---
title: "LIRC with Pinnacle PCTV doesn't work in 7.10"
date: 2007-12-24
forum: Hardware &amp; Laptops
---

### Post by cyrus_the_virus on 2007-12-24
Hi everybody,

This is my first message on this forum and I'm quite new to ubuntu. I must say I'm very impressed. I've used openSUSE before but I'm staying with ubuntu for now because it's much faster and more stable.

Anyway, I've a got a problem with Pinnacle PCTV remote control. I can't get it to work in LIRC. It use to work in suse, though I remember it was a bit of a hassle to get it to work.
I used this [http://ubuntuforums.org/showthread.php?t=221299]("http://ubuntuforums.org/showthread.php?t=221299") tutorial for ubuntu.
I carefully followed every step in that tut and it all went well until I got to the final step which is testing the remote control with *irw*

I run the lircd daemon in one shell like this:
*sudo /usr/sbin/lircd -H pinsys -d /dev/ttyS1 --nodaemon*
and run *irw* into another shell
I then push some buttons on my remote but nothing happens at all! No errors, nothing. I also tried to run the daemon on the other port (/dev/ttyS0) but it doesn't work :( I also did some reboots but that didn't help either.

Any ideas how to solve this?

Thanks,
Marty

---

