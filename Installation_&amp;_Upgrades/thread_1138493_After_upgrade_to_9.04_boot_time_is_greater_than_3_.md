---
title: "After upgrade to 9.04 boot time is greater than 3 minutes..."
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by ducheus on 2009-04-26
I upgraded my Ubuntu 8.10 in a Dell Latitude D830 to 9.04 and the boot process is really slow. More than 3 minutes...
After some research, it appears that parport module is the problem, below is a copy of dmesg. I tried to blacklist the parport but the command in blacklist.conf file is ignored.

...
[ 14.850398] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[ 14.851094] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[ 14.851751] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[ 193.832869] lp0: using parport0 (interrupt-driven).
[ 193.974241] Adding 3373640k swap on /dev/sda4. Priority:-1 extents:1 across:3373640k
[ 194.501485] EXT3 FS on sda3, internal journal
[ 196.070317] type=1505 audit(1240675112.792:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2627
...

Any suggestion will be welcome!

---

