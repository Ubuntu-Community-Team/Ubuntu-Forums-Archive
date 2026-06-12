---
title: "Video Issue - Dell laptop, Gutsy, my mistake"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by guitodd on 2008-02-13
Have a Dell Laptop with Intel graphics.

Was trying to set up a second monitor and chose a bad refresh rate. Causes monitor two to give me an error and keeps my main laptop monitor from showing anything.  Reboot... same thing... failsafe... same thing.

I'm kind of a newby.. is there a way to get back to where I was with just my main laptop screen working??

---

### Post by taurus on 2008-02-13
Boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by guitodd on 2008-02-13
Wow!  That worked. I can't tell you how much I appreciate you right now!

I was digging for re-install disks!   This happens to be my work machine I screwed up.

Thanks again!

---

