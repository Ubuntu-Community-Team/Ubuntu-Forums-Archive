---
title: "Switched to AMD proprietary driver, now fails to boot"
date: 2015-11-11
forum: Hardware
---

### Post by mjpatey on 2015-11-11
Hi, all-

I haven't had a problem like this in a while (probably since 6.06!) but here I am. I recently decided to try the proprietary AMD video driver for my Ubuntu 15.10 installation, and it worked well until I had to reboot. The initial boot sequence is fine, but it hangs during the "loading" splash screen, with the logo and animated dots.

In the past, I remember editing a file in /etc/X11/ which is no longer a thing, apparently! Anybody know which file I should edit to switch from the proprietary AMD video driver back to the Open Source one?

Thanks in advance!

-Mark

---

### Post by Bashing-om on 2015-11-11
mjpatey; Hello;

FGLRX in 15.10 is presently broke. We are awaiting a possible fix to make it downstream .
see:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888)
[http://ubuntuforums.org/showthread.php?t=2299981&page=2&p=13383588#post13383588](http://ubuntuforums.org/showthread.php?t=2299981&page=2&p=13383588#post13383588) <- work-a-round
[http://ubuntuforums.org/showthread.php?t=2299981](http://ubuntuforums.org/showthread.php?t=2299981)

[INDENT][INDENT]not hopeless,
[INDENT][INDENT][INDENT]just a bit of a pain
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

