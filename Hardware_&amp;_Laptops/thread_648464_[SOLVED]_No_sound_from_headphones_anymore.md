---
title: "[SOLVED] No sound from headphones *anymore*"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by lian1238 on 2007-12-23
Hi.

I used to be able to get sound from the headphones jack on my laptop, but now it's gone! I don't know what I did. Was it the recent update? I don't remember what was updated, either. Did my messing with the module-assistant mess it up? I didn't install anything, though. I didn't know how to work it. After I got this problem, I opened up module-assistant again and checked alsa, and I did "get", "build", and "install".

Any ideas?

note: my (Acer Aspire 5580) laptop has the common problem where there's no sound from headphones jack until after a suspend (even in Windows). But now, still no sound after suspend. If you need more info, please ask. And also tell me how to get the info, please, I'm still quite new to Ubuntu.

---

### Post by lian1238 on 2008-01-10
Solution found:
```

cd /usr/src
sudo module-assistant update
sudo module-assistant prepare
sudo module-assistant auto-install alsa
sudo shutdown -r now

```
Although I still have to suspend to ram.

---

