---
title: "Problems to install Flexcam 100"
date: 2009-09-28
forum: Hardware
---

### Post by jc-sama on 2009-09-28
Hello, im a new ubuntu user, practically, im still a windows slave =P. Well, i'm having problems now that i erased windows from my computer and installed Ubuntu 9.04. Im trying to use this webcam:

Sunplus Technology Co., Ltd Flexcam 100

but when i started the video on skype, it didnt work. On its preferences, i can make a test of it, but the webcam looks green, so i think that it is a drivers problem. I installed gnome-device-manager to see what it was installed and it says:

Model: Generic Digital Camera
Subsystem: video4linux

I want to give it a chance to Ubuntu, so, if somebody can tell me a way to test the webcam  and say that it is a skype thing, or a possible solution to my problem, ill appreciate, thanks, see ya :)

---

### Post by lufo4 on 2009-10-31
i have the same problem with skype i have a half solution, i created a script with the following

```

#!/bin/sh
eport LD_PRELOAD=/ur/lib/libv4l/v4l1compat.so
skype &
```

and named it launchskype and used that to open skype, now skype can see a clear test, however my problem is that i cannot call with skype because i do not have a mic, so i cannot test if you can call, is there a way to get around this?

---

