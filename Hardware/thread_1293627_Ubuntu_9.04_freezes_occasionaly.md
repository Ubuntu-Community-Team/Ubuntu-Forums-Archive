---
title: "Ubuntu 9.04 freezes occasionaly"
date: 2009-10-17
forum: Hardware
---

### Post by rasup on 2009-10-17
On Ubuntu 9.04 my laptop freezes about one time per day. When the freeze occurs I can't do anything except move the mouse, the display is completely frozen. Caps Lock doesn't even work.

I've managed to login to my laptop using ssh during a freeze but i can't make gdm restart. gdm tells me that it is restarted but nothing happens on the display. Sometimes I can make the computer reboot (using ssh and 'shutdown -r now') but it takes a long time before anything happens. I mostly need to do a hard reboot.

My laptop seems to have this [bug]("https://bugs.launchpad.net/bugs/314928") (i915GM mtrr bug) so I've followed this [guide]("http://ubuntuforums.org/showthread.php?t=1130582") using the Optimal solution. I don't know if this has something to do whith the freeze?

I've attached a batchbuffer dump made during the last freeze. I got the dump using this [guide]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze#How%20to%20Get%20a%20Batchbuffer%20Dump%20(-intel%20only)").

```
uname -a
Linux baerbar 2.6.30-02063003-generic #02063003 SMP Sat Jul 25 10:57:13 UTC 2009 i686 GNU/Linux

lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
```

---

