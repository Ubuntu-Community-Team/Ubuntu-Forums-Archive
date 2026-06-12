---
title: "Hibernate/Suspend work, but (sort of) reboot"
date: 2009-03-29
forum: Hardware
---

### Post by TheJimtasticOne on 2009-03-29
OK, basically, I can hibernate or suspend (hibernate takes a little while, but I can handle that), except that just when it should power off or go to sleep, my machine powers up again. With hibernate, it's like it saves its state, then instead of powering down, the machine reboots and displays the grub prompt again. When ubuntu loads up again, everything is as if it had hibernated or suspended fine. So, does anyone know of any way to get it to power down properly?

---

### Post by chiselwright on 2009-03-29
When I moved to 8.10 on my laptop I started to experience something that sounds just like this; the laptop would go through all the motions for a suspend, then immediately wake-up again.

I resolved it back then by adding:
```
blacklist ath_pci
blacklist ath_hal
```

to /etc/modprobe.d/blacklist.conf

Unfortunately, I've upgraded to the 9.04 beta this weekend, and the old behaviour is back, even though I have the items blacklisted in the file still. :(

---

### Post by TheJimtasticOne on 2009-03-30
Thanks for your reply; that's exactly what my problem is (with hibernate as well as suspend), but that didn't work for me :\ Any ideas what's causing it? Maybe it's my hardware...

---

### Post by TheJimtasticOne on 2009-04-06
Bump.

---

### Post by TheJimtasticOne on 2009-04-10
No-one has any idea? I'll probably file a bug on launchpad then.

---

### Post by geology on 2009-04-12
This just started happening to me a few days ago.  The actual hibernate and restore work fine.  Until a couple days ago, after hibernating it would power down, now it reboots instead.  To the best of my recollection, it was still behaving properly for a couple days after the last time I installed anything new, leading me to suspect it may be one of the system updates that occurred last week.

I'm running Ubuntu 8.10 x64 with kernel 2.6.27-11-generic on a Pentium E5200 with NVidia GeForce 7100 (using the proprietary nvidia drivers).

@TheJimtasticOne:  If you wrote a bug, please post a link to it, since I'd like to follow any progress or comments on it.

---

### Post by vidak on 2009-04-12
I have the same problem, I installed hibernate package, and use sudo hibernate from console. This unfortunately won't work at automatic hibernating (like when running out of battery power)

---

### Post by geology on 2009-05-17
About a week after my posting above, the problem stopped occurring - i.e. hibernate now both saves the current state and makes the PC power down, as it should.  I wasn't really paying attention to what had changed, so I can't say what fixed it.  (System update perhaps.  It was not just giving the system a full shutdown, since I did that a few times before writing my prior post.)

---

