---
title: "Installing Ati Radeon X1600 Pro"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by fil333 on 2008-02-28
I've had Ubuntu 7.10 installed ever since it was released. I've still not managed to install my Ati Radeon X1600 Pro (512MB). Can somebody please explain step by step what I need to do to install it. Thanks for your help!

---

### Post by reyhan on 2008-03-01
maybe you must install driver just type this on terminal

[HTML]sudo apt-get install xserver-xorg-video-radeonhd
[/HTML]

i hope that's work

---

### Post by flying_surprise on 2008-03-01
I'm trying to get my Radon HD3850 to work with this driver, but it only result in the following kernel messages:

[   71.848353] printk: 69 messages suppressed.
[   71.848361] gnome-settings-[7266]: segfault at 18 rip 7fc5d33fa7c0 rsp 7fffe54aeb28 error 4
[   76.489006] gnome-settings-[7287]: segfault at 18 rip 7fb1d8e047c0 rsp 7fffeaeb7518 error 4
[   77.047945] gnome-settings-[7310]: segfault at 18 rip 7ff2cdb2c7c0 rsp 7fffdfbe1238 error 4
[   77.055437] eth0: no IPv6 routers present
[   78.970999] gnome-settings-[7319]: segfault at 18 rip 7f91098637c0 rsp 7fff1b917f78 error 4
[   80.829768] gnome-settings-[7354]: segfault at 18 rip 7fd521a827c0 rsp 7fff33b37188 error 4
[   81.527195] gnome-settings-[7366]: segfault at 18 rip 7f531bba77c0 rsp 7fff2dc5c2b8 error 4
[   82.627763] gnome-settings-[7382]: segfault at 18 rip 7f0656c627c0 rsp 7fff68d15368 error 4
[   84.123091] printk: 1 messages suppressed.
[   84.123098] gnome-settings-[7399]: segfault at 18 rip 7fd789d5b7c0 rsp 7fff9be10468 error 4

If i switch back to radeon driver, it doesn't crash. But I want at least 2D-acceleration to be able to watch movies and TV without lagging!

---

### Post by flying_surprise on 2008-03-01
Maybe, I should just add that when gnome-settings-manager crashes, gnome doesn't look very Ubuntish anymore... This happens at login.

---

### Post by fil333 on 2008-03-01
Is this driver only for a Radeon HD or will it work with a Sapphire Radeon X1600 too?

---

### Post by TTrussell on 2008-06-04
Not to be a pessimist, but getting your ATi Radeon x1600 PRO to work in Ubuntu (7.10 or 8.04) is... well... just have your cyanide pill ready for when you've given up.

---

