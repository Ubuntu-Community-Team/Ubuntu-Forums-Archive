---
title: "Radeon X1650 and Video Tearing"
date: 2013-07-17
forum: Hardware
---

### Post by Repetestrois on 2013-07-17
Hello - I'm seeing problems with video tearing in both Youtube and VLC playback on my computer. It's an old machine, Pentium 4 and 1.5GB of RAM, with a Radeon X1650 Pro card. I'm assuming it's the card/driver combo that's causing the problem?


I understand that this card is no longer supported by ATI/AMD and that I'll have to make do with the open-source, built-in driver, but is there anything that I can configure that is likely to improve the video performance? I've read the 'man radeon' page but might be even more confused now.


Screen resolution is an issue too - I'm currently limited to 1024x768 but am reasonably confident that I can find my way about xorg.conf to fix this - could this be contributing to the problem too?


Essentially, I'm trying to understand whether I'm going to be wasting my time in trying to get such an old, underpowered computer and unsupported gfx card to work competently. I really like the learning and fun of checking out new distros and seeing what's possible, but it needs to work for me at least as well as XP did. I'm loathe to go back and hope this video problem isn't a deal breaker.


Apologies if I've left out too many details, do let me know if there's any other info I can provide that might help. Any advice gratefully received!


Sarah

---

### Post by Repetestrois on 2013-07-19
Sorry to bump this, but I'm still at a loss here :sad:

---

### Post by Yellow Pasque on 2013-07-19
What desktop environment are you using?

---

### Post by Repetestrois on 2013-07-20
Xfce

---

### Post by gvorik on 2013-07-20
OS and Kernel version would be helpful also. I read that kernel support for my ati 1650 pro stopped with kernel 3.2 which will keep me locked into 12.04 for the duration.

---

### Post by Yellow Pasque on 2013-07-20
> **gvorik said:**
> I read that kernel support for my ati 1650 pro stopped with kernel 3.2 which will keep me locked into 12.04 for the duration.

No, you're referring to AMD dropping support for RadeonHD 2000-4000 cards in the proprietary driver, which doesn't affect your card. Proprietary support for the X1650 was dropped in Ubuntu 9.04...

---

### Post by QIII on 2013-07-20
The open source community hasn't given up of users of older ATI hardware!

:D

---

### Post by Yellow Pasque on 2013-07-20
> **Repetestrois said:**
> Xfce
Yes, I use xfce and have the same issue (it's called "video tearing"). 
The first thing to try is disabling compositing (Settings -> Window Manager Tweaks -> Compositor). If it doesn't help, you can easily re-enable it.

If that doesn't help, there are more experimental things to try, but I can't vouch for their effectiveness, and I wouldn't recommend using them on a system that you really depend on in case something goes wrong:
[http://ubuntuforums.org/showthread.php?t=2144468](http://ubuntuforums.org/showthread.php?t=2144468)
[http://www.webupd8.org/2012/10/xfce-sync-to-vblank-support-for-xfwm.html](http://www.webupd8.org/2012/10/xfce-sync-to-vblank-support-for-xfwm.html)

---

