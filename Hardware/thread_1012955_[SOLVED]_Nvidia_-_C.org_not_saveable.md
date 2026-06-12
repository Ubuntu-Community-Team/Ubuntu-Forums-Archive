---
title: "[SOLVED] Nvidia - C.org not saveable"
date: 2008-12-16
forum: Hardware
---

### Post by benste on 2008-12-16
hy guys, 
seems to be that launchpad' user reaction is a bit like slow isn't it?

Would you like to take a look into:
[https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/305700]("https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/305700")

my laptop isn't uasable for me without the ability to connect to a presenter in a xinerama dual x-server mode.

---

### Post by jocko on 2008-12-16
In a terminal:
```
gksudo nvidia-settings
```

That will allow you to save the settings...

---

### Post by benste on 2008-12-16
rofl,
if you read my bug report you would see that nvidia-settings isn't able to save the x.org config file since 8.10 !!

---

### Post by jocko on 2008-12-16
I did read the bug report, which is why I gave that advice. Have you tried what I told you?
That error in the picture in the bug report looks exactly like when you run nvidia-settings as a regular user. Run it with gksudo and you will be fine...

---

### Post by benste on 2008-12-16
It works without an error (didn't try a presenter yet)

thanks,
but why did they change the launcher from 8.04 to 8.10?

---

### Post by benste on 2008-12-16
+ where to report this litle mistake?

---

### Post by jocko on 2008-12-17
> **benste said:**
> + where to report this litle mistake?
You could perhaps add to the bug report that you've found what the problem was.

---

### Post by benste on 2008-12-17
possible midea,
I'll do so

---

