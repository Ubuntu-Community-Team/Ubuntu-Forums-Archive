---
title: "Wifi, graphics gone missing"
date: 2015-05-15
forum: Hardware
---

### Post by colonelmandrake on 2015-05-15
I'm running Ubuntu 14.04.2 on a Thinkpad 440s and I recently upgraded to Linux 3.13.0-52-generic. My /boot was full and I merrily mashed away at the keyboard until the upgrade succeeded. I also run grub-update.

After a reboot, I've found

(a) xrandr won't detect external monitors any more and describes the laptop monitor as "default". Previously this worked seamlessly.
(b) wifi is missing completely. Previously this worked seamlessly.

Here's debug info for the wifi: [http://piratepad.net/QpPDwfrdBv](http://piratepad.net/QpPDwfrdBv)

I'd be very grateful for any help. Thanks!

---

### Post by colonelmandrake on 2015-05-15
**SOLVED**

Given that no wireless card was showing from lspci, I reinstalled my kernel:

```

sudo apt-get install --reinstall linux-image-generic
sudo update-grub

```

---

### Post by RobGoss on 2015-05-15
Glad it's working for you

---

### Post by jeremy31 on 2015-05-15
So are using the 3.13.0-52 kernel or one of the 3.16 kernels that are part of 14.04.2?

---

