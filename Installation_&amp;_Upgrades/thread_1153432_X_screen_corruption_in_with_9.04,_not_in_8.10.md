---
title: "X screen corruption in with 9.04, not in 8.10"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by mkngl84 on 2009-05-08
The system uses the on-board Intel 945G chipset and recently was upgraded to ubuntu 9.04 32-bit jaunty. The upgrade worked flawlessly (except the loss of DRI in the Intel driver due to issues somewhat unrelated to the upgrade).

After reinstalling almost every package in the system to fix a separate issue, this issue cropped up.

When I boot into recovery mode, everything works perfect. When X is started using Intel or VESA: the screen goes blank, flashes three times with lines on the screen and then ends with a static image of various colors at the top with the rest being grey-scale noise.

Starting in recovery mode, doing netroot and starting sshd allows for login after X is started so the system is still up. The computer becomes totally unusable unless you use a means other than keyboard, mouse and monitor. However, the safe keyboard reboot via Alt-SysReq+RESIUB works so it is X only that may be effected.

Here's the kicker, Xorg runs normally when running the 8.10 live CD. Jaunty has worked before, so it should not be the real issue here.

The Xorg logs don't show any new warnings or errors on installed OS.

Any ideas? There shouldn't be a need to reinstall everything, I think, since everything works except X.

Thanks a bunch.

---

