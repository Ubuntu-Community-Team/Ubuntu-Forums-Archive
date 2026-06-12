---
title: "File copy slows mouse response"
date: 2008-09-07
forum: General Help
---

### Post by ewisnor on 2008-09-07
Hi,

I'm having a problem with my mouse slowing down and being relatively unresponsive while copying files. Basically, my mouse (Logitech VX) acts like it's on low battery when it is not. It takes a few swipes to get across the screen, and sometimes I have to click 6 times quickly on something just to get a menu or execution. After the copy is complete, everything is back to normal and running great.

I've got a 1.8ghz core duo, 3GB of RAM, so I know it's not a resource problem. Both cores are hovering around 15-30% while copying. This is a network transfer to a samba share on another pc on my LAN, 2.5-3Mb/s.

The slowness is reproducible using both Nautilus and the cp command. The cp command runs as an "uninterruptible" process around 1% CPU, using only kilobytes of ram.

Using Gnome 2.22.3 on Hardy.
```
# uname -a
Linux thedominator 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
```

So what is the deal here? Typing is fine, it just seems to affect my mouse performance. I decided to load Quake III while copying a file and it was running smoothly except for the fact that mouse events were intermittently registering.

Can anyone provide insight to this? Maybe it's a kernel problem? Can anyone else reproduce this?

Thanks,
Evan

---

### Post by ewisnor on 2008-09-07
I can reproduce this with NFS shares as well, but local copies don't have the same effect.

So in summation, network file transfers have a negative effect on mouse performance. I'm curious to find the link between file transfers and mouse events.


If at least one other person can reproduce this I will file a bug report.

---

### Post by bihe on 2008-10-26
Hi there,

In my case it is not related to smb/nfs file transfer but file transfer between different partitions and or usb-discs. System is completely unresponsive. No solution found - seems similar to:

[http://ubuntuforums.org/showthread.php?t=757135&highlight=hardy+copy+unresponsive]("http://ubuntuforums.org/showthread.php?t=757135&highlight=hardy+copy+unresponsive")

A possible explanation can be found here: [http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/115008902931]("http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/115008902931")

This helped: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094/comments/112]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094/comments/112")

---

