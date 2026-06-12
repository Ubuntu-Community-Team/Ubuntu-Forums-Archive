---
title: "ASUS X71SL - Installer doesn't progress beyond partition manager"
date: 2010-11-30
forum: Hardware
---

### Post by RRockon on 2010-11-30
I've had this issue with all the debian based linux distros I tried recently. All seem to share this problem.

When I attempt to install a 'recent' ubuntu/debian variant (ubuntu 10.04 or later as well as the new Debian Squeeze Beta) the installer does not progress beyond the partition manager. There it just hangs the installer. If I do this from a live disk the distro itself keeps on running fine, it's just that part of the installer that it doesn't seem to be able to progress beyond.

If I go to the console output for the debian installer, the last few things I see there are repeats of the following line, maybe it helps.
```
(EE) FBDEV(0) FBIOBLANK: Invalid Argument
```A friend of mine told me this is a somewhat rare bug but it's not completely unheard of, and I was curious if there are any fixes/workarounds for it, or if I can help in any way to find out the cause of this problem.

---

