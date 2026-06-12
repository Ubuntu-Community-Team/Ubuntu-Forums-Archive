---
title: "old satellite, no sound, stop beeping"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by vector on 2005-06-12
HOW do i just remove or tell ubuntu to not look for sound cards on boot and on shutdown.

i have other posts here which have gone unanswerd so have given up on trying to get sound.. however now on boot I get losts of beeps and yamaha not found errors..
I just want to clean it up and stop it even looking..its driving me mad and slowing down the turn on turn off process. ](*,)

---

### Post by felipe on 2005-06-12
```

sudo chmod a-x /etc/init.d/alsa

```

maybe this?

---

