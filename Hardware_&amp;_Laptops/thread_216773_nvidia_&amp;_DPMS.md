---
title: "nvidia &amp; DPMS"
date: 2006-07-16
forum: Hardware &amp; Laptops
---

### Post by Arnaud_B on 2006-07-16
Hi,
I saw a couple a threats relating a problem of freeze of screensavers with some laptops when using nvidia drivers and DPMS, however I did not find any satisfying solution so here we are again... :-)
When I use the nvidia drivers (and keep DPMS enabled), if I let the laptop idle for a while the screensaver starts (blank in my case) and then DPMS turns the monitor off... as long as the monitor is not off everything is fine, however when the monitor goes off no key can resume the session... the screen seems like freezed and stays black. In my case, my laptop (toshiba-satellite m35-something) has a video I/O switch that allows to resume the screen... don't ask me why it has an effect I have no idea ;-) but it is not an acceptable solution anyway ;-)
There is no problem if I use nv drivers or if I use nvidia drivers with DPMS disabled...
I tried several config in xorg.conf and reinstalled the nvidia drivers but the problem is still there... for info I use a custom kernel (relevant changes are: no agpgart, no riva) but the problem exists also with stock kernel... :-(
I have no error in the Xorg.0.log and besides this problem the nvidia drivers are working fine...
Any ideas? or even solution? :-)
Thanks in advance,
A.

---

