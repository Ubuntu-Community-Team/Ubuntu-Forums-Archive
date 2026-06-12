---
title: "Ubuntu 9.10 Webcam Upside Down"
date: 2010-02-09
forum: Hardware
---

### Post by drummwill on 2010-02-09
okay i am new to Ubuntu so hello everyone :D

i have the Asus K50IN
the webcam is:

```
Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC WebCam / CNF7129
```

webcam is upside down
i've tried google and nothing seemed to help, i think im doing something wrong

someone please guide me :) okay thank you everyone :D

---

### Post by retimer on 2010-03-20
The problem is usual for asus. To flip your camera you are to run the program using the following code (example for Skype)
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by iliantiliev on 2010-03-26
> **retimer said:**
> The problem is usual for asus. To flip your camera you are to run the program using the following code (example for Skype)
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

This does not work for me:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

I run Ubuntu 9.10 on Asus U6V bamboo.

Any ideas? 

If I do: export LIBV4LCONTROL_FLAGS=3 (found somewhere else) this corrects the problem for some software (e.g. cheese), but not for Skype or VLC.

Ilian Iliev

---

### Post by hunternet93 on 2010-06-02
I have the same problem. The LD_PRELOAD works on everything except skype for me. I believe the problem is in skype needing the 32-bit version of the driver as it is a 32-bit program, and the LD_PRELOAD trick leads it to the 64-bit lib, which cannot be used. I've been trying to see if I can find the 32-bit lib on my computer, I'll post any successes I have.

---

### Post by RKimber on 2010-06-15
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

seems to work for me.

---

