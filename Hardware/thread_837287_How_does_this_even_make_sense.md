---
title: "How does this even make sense?"
date: 2008-06-22
forum: Hardware
---

### Post by Doopydoo22 on 2008-06-22
I don't know why this worked, but it did.

I've been having ongoing issues with getting my Plantronics USB Headset to work.  I could get the test sound to work under "System > Preferences > Sounds," but nowhere else.  Tried "asoundconf set-default-card," no luck.

I'd given up on it for some time and was recently getting my extra mouse buttons to work.  I had just finished fixing them and rebooted, then started up UT2004 to test out my mouse config.  Of course, had issues caused by the evdev driver, so went on the interwebs and found this ([https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/189958]("https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/189958")).

I added this to my xorg.conf:

```
Section "Module"
    SubSection "extmod"
        Option "omit xfree86-dga" # don't initialise the DGA extension
    EndSubSection
EndSection
```

When I added it and rebooted again not only did it fix my mouse issue, but my USB Headset miraculously worked as well.

Please, tell me I'm not crazy.

---

