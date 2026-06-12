---
title: "msi wind eth0 *AND* wireless dead after kernel update"
date: 2009-02-18
forum: Hardware
---

### Post by hashbrowns on 2009-02-18
All of this work is for a friend's MSI wind, who has no idea about anything about computers and so I just hoped that the Wind and Linux would be the simplest thing for him.

Anyway, already with the previous kernel version of 2.6.27-7, I couldn't get connections with WPA/WPA2 wifi networks, and could only say to him to use WEP. He was okay with that.

Now though, after updating to 2.6.27-11, he has neither ethernet nor wireless at all, on any kind of network. The eth0 is a Realtek, and the wireless is the ralink 2700E I believe.

At the very least, is there any way I can revert or switch back to an older version of the kernel to make sure that's the problem? I thought I read somewhere that was possible during bootup, but I can't find any information on that right now...

This is kind of depressing. :( I use Ubuntu server and it's quite nice for work, but for "my" first real experience with it as a regular laptop OS, it's been quite disappointing. However, I do recall hearing horror stories from friends, years ago, using Warty and not having any wireless at all. Has linux always been a wireless nightmare?

---

### Post by panmoto on 2009-02-18
Hi there, sorry I can't help you with your wireless problem.

But I can help you to choose older kernel:

1. Just press Esc key during reboot. You'll see a list of available kernel to choose from (if you haven't delete them of course).

or:

2. Use startupmanager to choose default kernel to use on next boot.

or:

3. edit /boot/grub/menu.lst

---

### Post by 5BallJuggler on 2009-02-18
open a terminal and type

**lspci**

this will list your hardware for wireless, post the output on here

---

