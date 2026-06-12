---
title: "Touchpad Ceases Functioning after 9.10 Upgrade"
date: 2009-11-04
forum: Hardware
---

### Post by Rudy246 on 2009-11-04
Hey Ubuntu Forums,

I haven't posted here in a long time since it's been a long time since my last problem with Ubuntu. I didn't see any threads detailing this specific issue, so I hope I'm not posting something that's already been brought to light.

I updated from 9.04 to 9.10 the other day, and after the machine rebooted, my touchpad no longer worked. I tried opening up the Hardware Drivers window (I can't remember what it's called, but it's under Administration; I'm not currently in Ubuntu so I can't look) but it found nothing.

I have a Synaptics PS/2 Port Touchpad on my HP laptop.

Any help would be greatly appreciated.

-Rudy

---

### Post by lightrush on 2009-11-05
Try a clean install on a new partition to test if the problem is caused by the upgrade or not.

---

### Post by Rudy246 on 2009-11-05
I'm afraid that would be a bit too much of a hassle to do right now. Any other thoughts?

---

### Post by finndude on 2009-11-05
I have the same problem after upgrading from 9.04 to 9.10 -> touchpad is totally dead. So any help getting it work again is appreciated.

---

### Post by 5BallJuggler on 2009-11-05
> **Rudy246 said:**
> Hey Ubuntu Forums,

I haven't posted here in a long time since it's been a long time since my last problem with Ubuntu. I didn't see any threads detailing this specific issue, so I hope I'm not posting something that's already been brought to light.

I updated from 9.04 to 9.10 the other day, and after the machine rebooted, my touchpad no longer worked. I tried opening up the Hardware Drivers window (I can't remember what it's called, but it's under Administration; I'm not currently in Ubuntu so I can't look) but it found nothing.

I have a Synaptics PS/2 Port Touchpad on my HP laptop.

Any help would be greatly appreciated.

-Rudy

Check this thread, I had the same problem, but managed to fix it with a kernel change.

[http://ubuntuforums.org/showthread.php?t=1306012](http://ubuntuforums.org/showthread.php?t=1306012)

Hope this helps.
Phil

---

### Post by Rudy246 on 2009-11-05
> **5BallJuggler said:**
> Check this thread, I had the same problem, but managed to fix it with a kernel change.

[http://ubuntuforums.org/showthread.php?t=1306012](http://ubuntuforums.org/showthread.php?t=1306012)

Hope this helps.
Phil

Hm, that seems to have me on the right track, but I ran into some trouble. Now my Ubuntu will only boot into a CLI. I tried editing the file back to the way it was before, but it still will only boot to a CLI. Not sure how to go about fixing it.

---

### Post by SingingBush on 2009-12-31
I had this same issue and sorted it using a terminal command that I found on someones blog.  You need to enter it as root user:

echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe

After that reboot the system:

reboot

---

