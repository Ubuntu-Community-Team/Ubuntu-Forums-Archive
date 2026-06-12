---
title: "Trackpad Stopped Working (Acer Aspire One Netbook)"
date: 2012-08-02
forum: Hardware
---

### Post by ctownstud00 on 2012-08-02
I was working on fixing my wireless modules/drivers, and suddenly, after I have it working, my trackpad stopped working after login! It works before login, and if I logout, it works at the login screen, but not after I login. Maybe something weird got blacklisted or something, I can't think of anything else. I'm a beginner with Ubuntu, so I really need some help!

Thanks kindly,
Sean

---

### Post by ctownstud00 on 2012-08-06
After searching and attempting multiple solutions, nothing has worked. The mouse doesn't work even before login, now. Here is my blacklist.conf as it relates to mice. I believe it was set this way prior to the problem, but I don't know what other information to provide for assistance.

blacklist.conf
```
# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
```

This all came after I fixed my Wireless driver. It seems as though it must be related, since it started afterwards.

Also worth mentioning is that sometimes when I login, the wrong theme loads. What the heck is that about?? Highly annoying! When I log out and log back in, it usually loads the right theme, then, but why would it do that??

Please help!

---

### Post by ctownstud00 on 2012-08-08
OK, seriously?? Nothing??

Let's try some bumps, then...!

---

### Post by ctownstud00 on 2012-08-12
Bump.

---

### Post by kay65535 on 2012-08-12
> **ctownstud00 said:**
> Bump.


Hey, I started having that problem with an Aspire One, all of the sudden, the mouse would stop working.

The way I solved it was by restarting the driver:

```
sudo rmmod psmouse
sudo modprobe psmouse

```

It was very frustrating. I think it was happening because my RAM was getting low... (zramswap helped solve that issue :D )

Anyway, hope that helps!

---

