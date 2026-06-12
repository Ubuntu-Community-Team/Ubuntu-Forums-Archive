---
title: "upsd problems"
date: 2006-03-05
forum: Hardware &amp; Laptops
---

### Post by xmastree on 2006-03-05
I've swapped my motherboard, and upgraded to breezy at the same time.
Previously I had upsd running and working fine with my home made cable.

Now it doesn't. :( 

First thing I did was to check the serial port, so I used a serial mouse and booted from a breezy live disc. As expected, no mouse so I edited xorg.conf a couple of times and determined that on this system the port is /dev/ttyS1 (previously it was S0).

So, I edited my /etc/init.d/upsd to reflect this change, and edited /etc/inittab to be the same as on my previous installation.

It still doesn't work.

I made the cable according to the diagram in the readme.
DSR DTR tied together, which provide the pull-up voltage for DCD and CTS (prw fail and low bat). However, it isn't pulling up, it's still -9V. :-k

So, it seems that it's not initialising the port...

Any ideas whythis could be?

---

### Post by xmastree on 2006-03-06
bump...

---

### Post by xmastree on 2006-03-09
:( 

Is this the wrong forum? :confused:

---

### Post by xmastree on 2006-03-11
\\:D/  [SIZE="4"]I fixed it![/SIZE]  \\:D/ 

So, for the benefit of anyone with a similar problem who stumbles across this lonely thread (or for me again, when I install dapper :rolleyes: ), here's what I had to do:

**/etc/init.d/upsd** has the following lines:
```
PORT=**/dev/ttyS1**
[ -r /etc/default/upsd ] && . /etc/default/upsd
```Originally that was **/dev/ttyS0**, but I had changed it.

However, in the file that line points to, **/etc/default/upsd** was the same line:
```
PORT=/dev/ttyS0
```
I changed *that* to **/dev/ttyS1** and it worked, once i restarted upsd.
:mrgreen:

---

