---
title: "password in live/expert install doesn't work"
date: 2006-02-12
forum: Installation &amp; Upgrades
---

### Post by per engberg on 2006-02-12
In my first attempt at loading Ubuntu 5.10 Live i386 I've run in to a problem. In order to get my video to load I use live-expert vga=771 although I'm certainly no expert. I then follow the instructions. When asked for a root password I enter <whatever>, then I'm asked if I want to create another user. Wheater I select YES or NO to this, I'm not prompted for any username or password for this second account. The install continues, Ubuntu starts OK but I'm prevented from any installations, adding users etc. I seem to be logged on as <Ubuntu>. If I try using sudo I'm promted for a password. The only password I've entered during install (supposedly root-password) doesn't work. Can't edit etc/sudoers, stuck.
Any ideas would be of great help.

Per

System> HP Pavilion DV5055, AMD Turion 64, 1GB ram, ATI Radeon Xpress 200M

---

### Post by Ocxic on 2006-02-12
try it wothout the live-expert option and just use vga=771

---

### Post by per engberg on 2006-02-12
OK, finally got it. Just leave root password blank, and I got sudo working without any need for password (booting just with vga=771 didn't work, video problem).
Per

---

