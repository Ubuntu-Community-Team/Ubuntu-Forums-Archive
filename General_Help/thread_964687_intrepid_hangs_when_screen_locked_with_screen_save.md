---
title: "intrepid hangs when screen locked with screen saver"
date: 2008-10-31
forum: General Help
---

### Post by jithin1987 on 2008-10-31
With kubuntu 8.10 when screen saver is on it hangs when screen is locked for a long time. Also the unlock dialog which appears sometimes flickers during end of typing password. 

I use dell compaq 6910p laptop. Please help.

--Regards
Jithin Emmanuel

---

### Post by jthaeder on 2009-01-07
Hi,

I have the same issue,... did you find a solution? It worked perfect for hardy.
I also see some problems with other GL applications ( X crashes hard ). I guess there is a problem the the intel driver ??  my 6910 has an intel  GM965 graphics card

cheers 
  Jochen

---

### Post by thedarkwinter on 2009-01-07
hi

to both of you, can i suggest disabling compiz and see if the problem persists. I have found that compiz runs very well until you run other openGL apps. Perhaps if this is the case, there are fixes/workarounds you can find...

(System->preferences->appearance: visual effects=none)

Cheers,
Michael

---

### Post by jthaeder on 2009-01-07
Hi Michael,

Yes I tried this before,... no effect ...
Just reproduced it:

running a gl application :
 
kernel: [32911.816084] [drm:i915_wait_irq] *ERROR* EBUSY -- rec: 110860332 emitted: 110860335
( out of syslog ) 

I guess I found some hints 
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/248505](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/248505)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=467319](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=467319)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/48932](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/48932)

which should be fixed, I guess ... 

Do you have any hints for me?

cheers
  Jochen

--
Linux ethera 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux
xserver-xorg-video-intel --> 2:2.4.1-1ubuntu10
libgl1-mesa-dri --> 7.2-1ubuntu2
.

---

### Post by aya_pro on 2009-01-17
The same problem here with screensaver, but I have ATI Radeon on Compaq nx9420, so it is obviously not an Intel issue.
No solution found so far :(

---

