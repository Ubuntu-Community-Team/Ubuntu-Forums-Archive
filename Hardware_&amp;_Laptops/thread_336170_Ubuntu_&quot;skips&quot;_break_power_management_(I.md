---
title: "Ubuntu &quot;skips&quot; break power management (Inspiron 6k)"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by antar on 2007-01-11
I posted this a while back as two separate problems--it's become apparent that they're actually one and the same.

I've been running Dapper since August on (1) my Inspiron 6000 laptop (first off an external drive, now off the internal) (2) an old Compaq Armada laptop.

Aside from problems with the LinkSys external wireless card, the Armada works with Ubuntu as if the two were designed for each other.

The Inspiron 6000... not so lucky.

For about half the time I've had Dapper installed, it's been displaying this strange problem where, not every session and NEVER more than once a session, the computer will "skip" for about a minute the way a scratched CD skips--it's as if something's taking up all the CPU for that brief time, but looking at the system monitor, I see squat.

This is annoying as HELL if I'm already in the process of doing something CPU-intensive, like ripping a DVD (it breaks mencoder, making it "uninterruptible"), but usually I'm just checking my mail or something like that.

Anyway, Ubuntu will eventually stop "skipping," and everything seems to return to normal... except when I try to standby, hibernate, restart or shutdown. With all these processes, it'll get to the point where the computer should be shutting off... and then nothing happens. In the case of standby/hibernate, HAL will report that standby/hibernate failed. In the case of shutdown/restart, the screen will just stay on "Will Now Reboot" or "Will Now Shut Down" at the very end of the shutdown process, forcing me to kill it manually.


Anyone have ANY idea what's going on or what might fix it? I'm considering wiping Ubuntu and reinstalling, maybe this time going with Edgy Eft.

Thanks for your time.

-A

---

### Post by antar on 2007-01-12
Help? Please?

---

### Post by antar on 2007-01-16
It's too early to declare victory, but my computer hasn't experienced this problem in two days... ever since I uninstalled wine (which never worked for me, anyway). Huh.

---

