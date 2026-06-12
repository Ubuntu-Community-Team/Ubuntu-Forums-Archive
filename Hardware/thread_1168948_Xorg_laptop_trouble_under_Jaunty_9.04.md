---
title: "Xorg laptop trouble under Jaunty 9.04"
date: 2009-05-24
forum: Hardware
---

### Post by VogonZarniwoop on 2009-05-24
I have an old Acer 2010 laptop, with ATI Mobility 9700 gfx and 1.25 GB RAM.

I've run a number of different distros on it, including Fedora and Mandriva.  Most recently I was on Intrepid, and it's been rock solid.  It just ran - never had a hang or reboot even with many months of uptime.

Recently I upgraded to Jaunty, and suddenly I'm having all kinds of random Xorg hangs.  My average uptime is probably about 20 or 30 minutes.

$ uname -a
Linux flizbit 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

I was using compiz when I first saw the hangs, and moved to kwin to see if that changed anything, but I still see them.  There's no obvious trigger - the machine is lightly loaded, and I'm not doing anything unusual at the time.  I'll just randomly go to move the mouse or type something, and find the machine is not responding.

However, I have just noticed that when they happen (at least under kwin), I can ssh into the machine from another box and look around.  The first time I tried that, everything looked fine.  Nothing was taking CPU time, etc.  However, trying to kill -9 Xorg didn't work.  The second time, it seemed like Xorg was taking 100% of the CPU, and it also wouldn't die even with a kill -9.  I'll attach Xorg.0.log.

If I go back to boot off the 8.10 live CD, the crashes stop and all is well again.  I'd rather not have to downgrade if I can help it though :-/

Any ideas or tips?  Are there any known problems with 9.04 in this area?  Should I just give up and reinstall 8.10?  Unfortunately the machine is not very usable the way it is now :-/  I have a desktop machine with NV graphics running Jaunty and it seems quite fine.

---

### Post by VogonZarniwoop on 2009-05-26
Ah well - back to Intrepid I go.  Nearest I can figure is that it must be a defect in the radeon driver, since Jaunty works fine on my desktop machine.

---

