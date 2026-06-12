---
title: "Screen Freezing on Eee PC 1000 with ubuntu 8.10"
date: 2009-01-23
forum: Hardware
---

### Post by jolarson on 2009-01-23
I installed ubuntu 8.10 on my Eee PC 1000 and it worked well, however after upgrading the RAM to 2GB the screen will sometimes lockup and force me to cold reboot the computer.  Most of the time this only happens when I am on battery power, but it has happened a few times when I was plugged in.  Everything else seems to be working fine.  I ordered the RAM from crucial following their recommendation for the model, and it seemed to checkout with the other things I read.  I ran a memtest an it found no errors.  As well I have tried reinstalling ubuntu to make sure I hadn't broke something else,  but it will still sometimes crash on me.  The 2GB is recognized by the computer and in ubuntu.  So I was wondering if anyone has advice or similar problems.

---

### Post by burlyman on 2009-02-28
I have a similar problem, though I did not upgrade the RAM. The Eee PC 1000 freezes frequently with ubuntu 8.10. I use it on the train every day, for about one hour sessions. It usually freezes after 3-5 sessions, at random times. I do web development on it, using lighttpd, mysql, firefox, vim, gnome-terminal, that's pretty much it. I'm not doing anything special when it happens. However, the freeze has a peculiar pattern. First the computer becomes slow, then within a few minutes it comes to a crawl, until finally it completely freezes, the mouse stops moving, and I cannot switch to VT either. 

During the meltdown, there is nothing suspicious in /var/log/messages. Memtest passes without errors. I originally installed everything on the second disk, but later I moved it to the first. Now the OS and swap partition are on the first disk, only the /home partition is on the second disk. This helped overall performance, but did not help with the freezing, at all. I also tried to completely avoid hibernating and clean-boot every time instead, but it still freezes all the same. 

Any ideas what more I can try? I suspect faulty hardware, but I don't have a clue which part it could be. (Battery?) If the problem is ubuntu 8.10 that would be easy to fix, I'll be very happy with 8.04 or even older. But migrating my files is a pain, so I will only do it if somebody can say there is a chance that can fix it. 

Let me know!

---

### Post by pitris on 2009-03-06
Hello,
my gf has the same problem. Most probably it's a bug in xserver intel video driver.
[http://forum.eeeuser.com/viewtopic.php?id=54055](http://forum.eeeuser.com/viewtopic.php?id=54055)

The bug report is here:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/337116](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/337116)

---

