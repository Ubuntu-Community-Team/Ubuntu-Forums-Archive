---
title: "HP Pavilion dm1 rt5390 Wireless Driver issue (Ubuntu 11)"
date: 2011-05-26
forum: Hardware
---

### Post by fily on 2011-05-26
Hey guys, I've had this awesome little notbook for a good month now, and since day one it's been my no.1 priority to get Ubuntu on there. Let's start from the beginning...

It's been a HUGE pain to get this wireless card to work with ANY Linux Distro. I got it working on 10 at one point, and for a moment on 11 (I then had to reinstall everything and haven't had luck to get it working again). These are the tutorials I used previously;

[http://ubuntuforums.org/showthread.php?t=1743525](http://ubuntuforums.org/showthread.php?t=1743525)
and
[http://ubuntulinux.co.in/blog/ubuntu/wifi-card-ralink-5390-configuration-in-ubuntu-10-10-64-bit/](http://ubuntulinux.co.in/blog/ubuntu/wifi-card-ralink-5390-configuration-in-ubuntu-10-10-64-bit/)

Every time I get to the "make" area of things, I get an error 2 issue.

Any ideas what would cause that kind of error?

Thanks in advance.
Gilipe

---

### Post by mindstorms83 on 2011-05-26
the reason your card may not be working in the first place is because Ubuntu may not have a generic driver that will work well with it, so it may work for a small amount of time, but then will eventually stop. My advice would be to use a program called ndiswrapper, but to be sure it works well, run these commands in the terminal in Ubuntu:
[COLOR=Red]lspci
iwconfig
ip addr

[COLOR=Black]Please post back the results so I can help you get your card working!![/COLOR]
[/COLOR]

---

