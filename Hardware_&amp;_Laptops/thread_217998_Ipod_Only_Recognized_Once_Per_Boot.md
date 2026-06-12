---
title: "Ipod Only Recognized Once Per Boot"
date: 2006-07-17
forum: Hardware &amp; Laptops
---

### Post by ldrhcp on 2006-07-17
I just switched to Ubuntu from WinXP in the last week and it's been going pretty smoothly, but this iPod problem is a show-stopper. I saw some similar threads, but I couldn't find a solution.

I have a 3rd-gen iPod that I connect to my laptop via Firewire (1394). When I boot and connect the iPod, /dev/sda2 is mounted to /media/ipod. Here's the line from /etc/mtab:

```
/dev/sda2 /media/ipod vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
```

If I eject the iPod and reconnect it, nothing happens. The iPod does not show the "do not disconnect" screen, and there is no /dev/sda2.

Thanks in advance,
-Lenny

---

### Post by mgmiller on 2006-07-30
I have the exact same problem.  3rd gen ipod with firewire connection.  Only mounts once per boot.  Logoff and back on doesn't fix it.  Must do a complete restart.  I heard a rumor there is a fix for this in the 2.6.16 kernel.  Edgy will be released with 2.6.17, so theoretically, it should be fixed by that point.  A real PITA till then, though.

---

### Post by mgmiller on 2006-07-30
sorry, double post, can't figure out how to delete this.

---

