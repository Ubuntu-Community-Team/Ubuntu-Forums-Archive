---
title: "No sound in headphones on Dell Latitude E6410"
date: 2011-03-18
forum: Hardware
---

### Post by wvandael on 2011-03-18
Hi,

I know others have reported this before, but I've tried everything I found on this forum and nothing seems to help. Can someone please explain how to get the headphones to work on this laptop using Ubuntu 10.10?

Here's the alsa-info output I got so far:

[http://www.alsa-project.org/db/?f=0060fc975b252ba5899beb06834fbbf2b742d2e4]("http://www.alsa-project.org/db/?f=0060fc975b252ba5899beb06834fbbf2b742d2e4")

I also tried with setting the model to dell-s14 in alsa-base.conf, but that doesn't work either.

---

### Post by arkangelboss on 2011-04-27
Same problem here.

My Latitude e6410 headphones jack worked fine since last week, while now I have no sound from it.

Any suggestion on how to fix this?

My alsa-base.conf is attached. Mic and regular speakers work good.

---

### Post by lidex on 2011-04-27
> **wvandael said:**
> Hi,

I know others have reported this before, but I've tried everything I found on this forum and nothing seems to help. Can someone please explain how to get the headphones to work on this laptop using Ubuntu 10.10?

Here's the alsa-info output I got so far:

[http://www.alsa-project.org/db/?f=0060fc975b252ba5899beb06834fbbf2b742d2e4]("http://www.alsa-project.org/db/?f=0060fc975b252ba5899beb06834fbbf2b742d2e4")

I also tried with setting the model to dell-s14 in alsa-base.conf, but that doesn't work either.

It does work but you need to remove the other config changes you made. What are these outputs:
```
cat /etc/modprobe.d/alsa-base.conf
```
```
ls /etc/modprobe.d/
```

---

