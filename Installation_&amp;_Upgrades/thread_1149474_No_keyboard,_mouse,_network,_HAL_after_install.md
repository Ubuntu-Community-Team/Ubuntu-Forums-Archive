---
title: "No keyboard, mouse, network, HAL after install"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by mobrien118 on 2009-05-05
Hello,

I had recently posted in [http://ubuntuforums.org/showthread.php?t=1145490](http://ubuntuforums.org/showthread.php?t=1145490) about a problem I had after upgrading my system.

I am starting a new thread because the old one doesn't really explain what is going on.

Quite simply, if I install Ubuntu off of the alternate CD, when I try to go into an X session, there is no mouse/keyboard/network.

When I install off of the regular LiveCD, I can get in fine UNTIL I run the Update Manager and reboot. Then when it loads (with autologin) the same thing happens.

I Just started getting the error "INTERNAL ERROR: failed to initialize HAL!"

I realize this is very bad and probably why I am having this problem.

The computer is an old Dell Dimension 8300.

Any ideas?

Thanks,

--mobrien118

---

### Post by mobrien118 on 2009-07-09
OK, This problem is back!

I fixed it last time by installing a "bugfix" new version of HAL from here: [https://bugs.launchpad.net/bugs/361689](https://bugs.launchpad.net/bugs/361689)

Well, that worked for some time, but now HAL is busted again!

I'm all getting the "Failed to initialize HAL" screen, and have no network, (and the system is remote,so I have to call someone and coach them through starting safe mode then i have to manually initialize X and use VNC).

Can anyone help me diagnose this issue?

Thanks!

--mobrien118

---

### Post by mobrien118 on 2009-07-27
Is anyone equipped and knowledgeable, and would really love to help me figure this out?

I have this message in my Xorg:

(EE) config/hal: couldn't initialise context: (null) ((null))

Can anyone help me diagnose HAL/DBUS problems? I have an unusual storage situation, that may be causing it.

Could I safely remove HAL? If not, should I try to remove/purge it, then re-install it?

I can't get into the GUI at all, now, but I can have someone (I'm remote to the machine) turn it on and start ssh. This should allow me enough control to try anything out. This is the level of access i have at this moment.

Please! I am getting desperate!

--mobrien118

---

