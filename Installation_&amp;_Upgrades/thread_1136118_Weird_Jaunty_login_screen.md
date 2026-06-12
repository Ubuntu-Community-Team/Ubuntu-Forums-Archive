---
title: "Weird: Jaunty login screen"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by LeBurt on 2009-04-24
I've got me the weirdest problem after upgrading to Jaunty.

The system boots ok and gets me to the login screen. I was using the username/password style with Hardy (as opposed to the click-on-user/password style) so I'm prompted with the username box as usual. However, I can't enter text in the username box at all. It's like my keyboard is not connected or simply not working. 

However, and here the weird part, I can CTRL-ALT-Fx to a terminal and from there and log in normally. I can also CTRL-ALT-DEL out of there to reboot the system, so my keyboard IS connected and working.

I don't get it.

How do I even begin troubleshooting this?

---

### Post by LeBurt on 2009-04-24
Well, the problem appears much worse than what I first described.

For a terminal, I tried apt-get update just for the sake of it and got a slew of warnings: could not resolve this and that host, mostly archive.ubuntu.com. A quick ifconfig revealed that I'm not even connected to the network, all I have is the loopback (lo) interface.

Something went awfully wrong in the upgrade process. I'm stuck. Where do I go from here?

---

