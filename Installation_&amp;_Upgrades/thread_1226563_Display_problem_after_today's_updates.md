---
title: "Display problem after today's updates"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by vewert on 2009-07-29
I ran the recommended updates today (as I always do), and was prompted to restart my computer.   After restarting  everything seems to go well until the log in screen is supposed to be displayed.  At that point I get a blank screen with some coloured lines along the top.  I tried booting into older kernels but that didn't help.  Right now I seem totally stuck.  I'm guessing some video driver was updated which is causing the problem.

Has anyone else encountered this problem, and (more importantly) does anyone know how to fix this?

Details:

Ubuntu 9.04 (upgraded from 8.10)
Kernel: 2.6.28-14
CPU: AMD 64 X2 Dual Core Processor 4400+
RAM: 2 GB
Video: Built in ATI Radeon 2100

I'm a relative Linux newbie, and would appreciate any help!

---

### Post by vewert on 2009-07-30
OK, I have solved my issue.  It seems that since I upgraded from 8.10 to 9.04, I still had fglrx driver installed.  Up until now, however, this hadn't caused any problems.  It seems that the latest batch of 9.04 updates caused a problem.  My solution was to removed the fglrx drivers.

I booted into recovery mode, and at the command prompt used the following to remove the fglrx drivers:

```
sudo apt-get remove --purge xorg-driver-fglrx
```I rebooted and was able to see the Login screen again and all seems good.  I don't know what negative effects there are to removing fglrx, but right now I'm glad to have a UI again.

Note: I got the above information from the following article:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Hope this helps some other people.

---

