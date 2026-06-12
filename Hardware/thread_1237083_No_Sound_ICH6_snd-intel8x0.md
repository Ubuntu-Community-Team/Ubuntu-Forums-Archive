---
title: "No Sound ICH6 snd-intel8x0"
date: 2009-08-11
forum: Hardware
---

### Post by sovy on 2009-08-11
I did a recent default install of Jaunty and was thrilled to find that everything worked but the sound - I haven't gotten a peep from headphones or laptop speakers.  It's not muted.  I tried to follow [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) but ran into trouble on step 4.  Step 2 gave me:

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
    Subsystem: Gateway 2000 Device 0215
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 1c00 [size=256]
    I/O ports at 18c0 [size=64]
    Memory at b0040800 (32-bit, non-prefetchable) [size=512]
    Memory at b0040400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

I also found that the codec is conextant id 30, but I'm a little clueless as to what that means.  I'm a moderately noobie Ubuntu user - trying to switch from Windows.  Any help out there?

When I tried step #4 from the Sound Problem Guide, I got the following:

sov@sov-laptop:~$ sudo modprobe snd-intel8x0
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save.1, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save.2, it will be ignored in a future release.

Do I need to download a config file?  I don't know what to do here.

Another part of the Sound Problem Guide in Miscellaneous Tips and Tricks recommends that for intel8x0 you run
sudo nano /etc/modprobe.d/alsa-base
then add
"options snd-intel8x0 ac97_quirk=3"
to the last line.
I am very confused about GNU nano 2.0.9.  Can you explain what the instructions mean?
_**[SIZE=3][/SIZE]**_

---

### Post by Nonsteeler on 2009-09-01
Hmm, okay I have the same problem here, made the same searchs, tried the same things. What 'solved' the problem for me for a while was to install oss. But I'd would appriciate any help on this problem, too.

---

