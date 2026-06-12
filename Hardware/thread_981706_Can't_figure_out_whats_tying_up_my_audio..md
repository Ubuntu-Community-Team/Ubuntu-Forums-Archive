---
title: "Can't figure out whats tying up my audio."
date: 2008-11-14
forum: Hardware
---

### Post by boazarad on 2008-11-14
I've just installed Ubuntu 8.10 (64bit), and occasionaly I will lose audio capability altogether.
I'm using an onoard audio card on an Intel motherboard.

```
lsof /dev/snd/*
```
only gives me
```
COMMAND    PID USER   FD   TYPE DEVICE SIZE  NODE NAME
mixer_app 6581 boaz   22r   CHR  116,7      14134 /dev/snd/controlC0
```

And terminating mixer_app obviously doesn't help...

I'm suspecting the flash-player plug-in as the main culprit, but cant seem to find the rouge process and terminate it - any ideas?

Thanks

---

