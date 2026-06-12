---
title: "Unable to install Ubuntu 10.10 on i7 860 with Hyper Threading enabled"
date: 2010-10-13
forum: Hardware
---

### Post by damiandamian on 2010-10-13
I get kernel panic message when I try to start installation of Ubuntu 10.10 (2.6.35) on a PC with core i7 860 (desktop and server edition):
kernel panic not syncing vfs
comm swapper not tainted

When I disabled HT in bios I can install Ubuntu. Is this a known issue? Are there any patches planned in a near future? Windows seems to support HT with this processor. Should I install a different version of Ubuntu.

Cheers,
Damian

---

### Post by shukle on 2010-10-14
I am running 10.10 ubuntu with i7 870 hyper threading enabled.
Not sure that this is your issue.

---

### Post by damiandamian on 2010-10-15
After installation I can run Ubuntu enabling HT. However it seems unstable. It hangs from time to time. What is especially strange - with HT enabled (8 processors shown) it seems to work slower than without HT. Maven builds takes more time :) My motherboard is Asus P7P55D-E. Does anyone had similar issues with this hardware?

---

### Post by damiandamian on 2010-10-18
I have HT turned off now, but I still get strange errors: 
- VMPlayer crashes with Win7 working on it
- JVM crashes (netbeans):
#  SIGSEGV (0xb) at pc=0x00007fcf2d0e991a, pid=14051, tid=140526944741136
#
# JRE version: 6.0_21-b06
# Java VM: Java HotSpot(TM) 64-Bit Server VM (17.0-b16 mixed mode linux-amd64 )
# Problematic frame:
# V  [libjvm.so+0x3b491a]
- firefox crashes (unable to recover)

Does anybody had similar issues on this platform using Ubuntu 10.10?

---

### Post by Tech-Boy on 2010-10-20
Same problem here is i7 920 at 4.0ghz on rampage II extreme.

10.4 works perfectly but ht in ubuntu doesn't work at all. Taking ht off works but it is still unstable. And this a 100% stable oc I am running!

---

### Post by damiandamian on 2010-11-10
This was a problem with damaged RAM. After replacing it Ubuntu and windows works now well. I do not know about the installer error (kernel panic), I have to test it again. Now I have no problems with HT enabled. Sorry for my misleading posts - I tested RAM with memtest, which found no errors. I discovered this hardware issue when I replaced memory. What trip me up was Installer error, which I could overcome only by turning of the HT. I had those strange crashes every few days (first when I enabled HT again).
Sorry for blaming Ubuntu :-) it works now faster than Windows 7 ;)

---

### Post by kuric on 2010-12-12
Ubuntu 10.10 runs with Hyper Threading enabled, but it freezes completely after some minutes of usage.
When Hyper Threading is disabled, the system runs a bit slowly, but without crashes.
Never had this issue before, although this happens not only in Ubuntu but in other Linux ditros too, perhaps due to new kernels.

Test: Install and run lbreakout2 (the game). If HT is enabled, the system will crash after some seconds. No problem occur when HT is disabled.

Bug reported here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/687553]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/687553")

---

### Post by shendai on 2010-12-12
I'm running my primary desktop with an i7 860, HT enabled, no issues.  The issues related here do sound a lot like there might be a hardware problem, particularly if there's any overclock involved.  You may not want to assume that a stable OC in Windows will be stable under Linux as well.  It *should* be, but the first thing I'd do is run memtest for at least 3+ hrs to make sure there's no hardware defect there, then probably run Prime95 (exercising all cores) and/or OCCT or one of the other stability tools available.  For what its worth, I'm OC'd to 3.79 GHz, memory at 1700, but this is with a huge heatsink & multiple fans solution, and all automatic up/down clocking disabled in BIOS.  If I saw any odd behavior come up, the first thing I'd do after eliminating the obvious & rebooting would be to return to stock clocks.

---

