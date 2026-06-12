---
title: "stop cd drive from closing automatically"
date: 2018-11-24
forum: Hardware
---

### Post by paulweinrich on 2018-11-24
I have a Ubuntu box setup for ripping cd's using the Automatic Ripping Machine software. Once I insert a cd, it rips it then ejects the cd drive. I'm having a problem where the cd drives will not stay open indefinitely. After 10 minutes, they close again. Unfortunately this causes the ripping process to start over. Is there a way to disable this automatic closing timeout? I want the drive to stay open until I close it again.

Any help is appreciated!

---

### Post by TheFu on 2018-11-24
It is only a guess, but perhaps udev is the problem?

---

### Post by paulweinrich on 2018-11-24
That's a good thought. I'm monitoring the drive now with udevadm monitor to see if I can find anything that may be causing it. I know that it's possible to write udev rules. Do you know of a good place to find documentation on the different settings you can modify with udev?

---

