---
title: "sound card + headphones"
date: 2008-09-20
forum: Hardware
---

### Post by mut80r on 2008-09-20
On Ubuntu 7.10 with Linux kernel 2.6.24-16-generic.

============================================

Alienware m5500-R3i series
Volume Control: Realtek ALC885 (OSS Mixer)

```

aaron@ubox1:~$ sudo lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

============================================
I only get sound through the headphone port.
If I unplug the headphones, I get nothing.

Anyone know why?

EDIT: I must add.. this problem existed on 2.6.22-15-generic too.

---

### Post by mut80r on 2008-09-21
ok, after reading [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and using alsamixer, I found I only need channels PCM, Center and LFE enabled for sound.

Now I have the reverse problem however-- I've managed to get sound through the speakers, but when I plug headphones in, sound comes through both.

I've tried muting the Headphone channel and not, using the volume control "Headphones" switch and not, etc, nothing is changing.

I also tried the 8.04 livecd and followed the alsamixer instructions, same result.

---

### Post by markbuntu on 2008-09-21
You should look here for help with that:


[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

This one is more specific to headphone /speaker issues:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

