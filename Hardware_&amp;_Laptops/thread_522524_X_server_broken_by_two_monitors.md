---
title: "X server broken by two monitors"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by expertninja on 2007-08-10
I booted up ubuntu with a second monitor attached to the VGA out on my laptop (nvidia card). I had the second monitor off when I started it up, but the login screen was on the second monitor. I figured I would reboot without the monitor attached, but when I did X wouldn't start. 

What I have tried:
1. Starting X with the monitor attached
2. Using a backup xorg.conf that had previously worked
3. sudo dpkg-reconfigure -phigh xserver-xorg to go back to the original settings
None of these worked. Any ideas?

---

### Post by expertninja on 2007-08-10
A little bit more information that might help: X said it couldn't start because of some internal system error, and to check syslog for details. I guess I better figure out how to do that...

---

