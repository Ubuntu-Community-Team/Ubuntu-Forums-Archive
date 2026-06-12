---
title: "Dell Inspiron 1420: Live CD wont load!"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by theratster on 2007-08-19
I've never had an issue like this before: I have a new Dell inspiron 1420 (with Vista FYI), and I tried to run the LiveCD for Ubuntu 7.04, but after a short run through the boot screen with the throbber, it immediately jumps to command line with this message:

[INDENT][B]BusyBox v1.1.3 (Debian 1:1.1-3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)[/B][/INDENT]


I've used this CD before on other systems and it works fine, and I even tried to redownload and reburn it, but still no luck. I have also tried running on safe graphics mode liveCD with no luck.

Any advice?

---

### Post by nosrednaekim on 2007-08-19
1) make sure the SATA controller is in compatibility mode.

2) its the video card, you need to use the alternate installer,or a gutsy tribe(which is still very unstable)

---

