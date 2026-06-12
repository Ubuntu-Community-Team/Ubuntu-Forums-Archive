---
title: "Asus X50Z no sound.."
date: 2008-11-16
forum: Hardware
---

### Post by kafkaesk on 2008-11-16
Hey Guys, 

My notebook Asus X50Z has no sound, alsamixer is 100%, sound tests failed!

Here outputs: 

```
marcel@marcel-laptop:~$ head -n 1 /proc/asound/card0/codec* ==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC662 rev1

==> /proc/asound/card0/codec#1 <==
Codec: Motorola Si3054
marcel@marcel-laptop:~$ 

```

and the second:

```
marcel@marcel-laptop:~$ cat /proc/asound/cards 
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfdbf4000 irq 16

```

And  zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz says to ALC662:

```
        ALC662/663
          3stack-dig    3-stack (2-channel) with SPDIF
          3stack-6ch     3-stack (6-channel)
          3stack-6ch-dig 3-stack (6-channel) with SPDIF
          6stack-dig     6-stack with SPDIF
          lenovo-101e    Lenovo laptop
          eeepc-p701    ASUS Eeepc P701
          eeepc-ep20    ASUS Eeepc EP20
          m51va         ASUS M51VA
          g71v          ASUS G71V
          h13           ASUS H13
          g50v          ASUS G50V
          auto          auto-config reading BIOS (default)

```

Wich of this i have to add to /etc/modprobe.d/alsa-base? Ive tested auto, g50v, m51va, lenovo, 3stack-6ch i dont now more?

---

### Post by louisJ on 2010-07-17
With Ubuntu 10.04 and Asus x50z, I have the sound but no mic.
[http://ubuntuforums.org/showthread.php?p=9600582](http://ubuntuforums.org/showthread.php?p=9600582)
Did you find anything?

---

