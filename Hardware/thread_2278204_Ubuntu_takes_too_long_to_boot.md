---
title: "Ubuntu takes too long to boot"
date: 2015-05-14
forum: Hardware
---

### Post by erik23 on 2015-05-14
Hi guys, since i had extend my ubuntu partition, (  i've ha system with WIndows & Ubuntu )the latter takes like 2 minutes to start... ( against the maximum 15 seconds  at the beginning!!) moreover,   during the ubuntu's installation, i had encrypted the disk, but by many time, ubuntu doesn't requires me the password during the ubuntu boot What can i do? Ah, another thing, when i turn off the pc, and appears the "ubuntu" words on the pink background, the screen begins to warp and flash... nothing really bad but it annoying me... Someone know what to do? Cheers

---

### Post by iojedaperez on 2015-05-14
To check/test problems at the startup you should use the followin commands depending on init daemon you are using upstart or systemd

for Upstart
bootchart

for Systemd
systemd-analyze blame

---

### Post by erik23 on 2015-05-16
> **iojedaperez said:**
> To check/test problems at the startup you should use the followin commands depending on init daemon you are using upstart or systemd

for Upstart
bootchart

for Systemd
systemd-analyze blame

Could you be more specific? What can i do with these commands?? thank u

---

### Post by ian-weisser on 2015-05-16
> **erik23 said:**
> Could you be more specific? What can i do with these commands?? thank u

You can learn why your system takes like two minutes to start.
No real mystery to it. Install the bootchart package and read 'man bootchart' ... or run the systemd command.

---

### Post by erik23 on 2015-05-17
> **ian-weisser said:**
> You can learn why your system takes like two minutes to start.
No real mystery to it. Install the bootchart package and read 'man bootchart' ... or run the systemd command.

No man for bootchart :mad:

---

### Post by ian-weisser on 2015-05-17
> **erik23 said:**
> No man for bootchart

You are correct (there should be...might file a bug on that). Instead of man, see [https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

---

### Post by erik23 on 2015-05-17
> **ian-weisser said:**
> You are correct (there should be...might file a bug on that). Instead of man, see [https://wiki.ubuntu.com/BootCharting](https://wiki.ubuntu.com/BootCharting)

i have already installed bootchart, but it seems that the bootchart folder in var/log is empty...

---

