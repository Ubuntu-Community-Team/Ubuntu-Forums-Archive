---
title: "External Monitor Help"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by juliflip on 2007-12-28
I am running Ubuntu 7.10 on a Thinkpad T41. I had it connected to a docking station with an external keyboard, mouse, and monitor. The keyboard and mouse work fine, but I can't get the monitor to work. The monitor is an Acer AL1916W. Whenever I dock my laptop, the monitor gives a signal error message. I've tried changing the resolution in the graphics settings, but nothing has worked. I'm fairly new to Ubuntu. Is there an easy-ish solution? Thanks!

---

### Post by taurus on 2007-12-28
Maybe you need to reconfigure your X server again for that external monitor.  Boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure -phigh xserver-xorg
```
Now, you can shut down and let it boot into normal mode to see if it works.

```
shutdown -r now
```

---

