---
title: "optimize Xubuntu 7.04 performance"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by beep1314 on 2007-08-07
I have a Toshiba Satellite 2595 CDT laptop w/ 64mb ram.  What steps can I take to make clean install of Xubuntu 7.04 faster on this old laptop?  I also tried DSL and Puppy, but could not get them to install.

---

### Post by merlinus on 2007-08-07
[B]Minimum system requirements for xubuntu
[/B]

 To run the Desktop CD (LiveCD + Install CD), you need 128 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run or 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to install. The Alternate Install CD only required you to have 64 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM").
 To install Xubuntu, you need 1.5 [GB]("http://en.wikipedia.org/wiki/Gigabyte") of free space on your hard disk.
 Once installed, Xubuntu can run with 64 MB RAM, but it is strongly recommended to use at least 128 MB RAM.
 **[B][SIZE=3]-merlin[/SIZE]**
[/B]

---

### Post by kerry_s on 2007-08-07
switch to a lighter wm. you should be using a custom install with such low ram. your boot must take forever with xubuntu.
suggest you get more ram, the max is 192 for that laptop.
give a good size swap, 1gig if you can(1024mb)

net installer> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso)

install the base,when it comes to package selection, uncheck everything but the laptop
after install & reboot
log in as root
apt-get install xorg gdm synaptic jwm menu mc dillo
reboot(ctrl+alt+delete)
select jwm in the session menu and login
open synaptic and get what ever else you want.

mines a 450mhz, 256ram, i'm using that exact setup. you can also go icewm or fluxbox or any other light WM. jwm is really small 213kb not very featured but very simple & fast.

try different setups, see if you can find your laptops sweet spot. good luck.

---

### Post by beep1314 on 2007-08-07
Boot takes about 4 mins.  Loading programs takes a long time too.  And I have still not been able to set up dial-up.

---

### Post by kerry_s on 2007-08-07
> **beep1314 said:**
> Boot takes about 4 mins.  Loading programs takes a long time too.  And I have still not been able to set up dial-up.

4mins! the last time i boot charted mine it only took 37secs.
you really need to try a custom install where you just add what you need it really does help.

forgot to give you a pic, so you kinda can see what you get with that command above.

---

