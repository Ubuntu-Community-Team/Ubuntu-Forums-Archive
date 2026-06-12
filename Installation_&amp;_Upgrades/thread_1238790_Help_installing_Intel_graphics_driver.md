---
title: "Help installing Intel graphics driver?"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by wurlyfan on 2009-08-12
[SIZE=2]Can anyone tell me (or point towards help with) installing the Intel 2009Q2 graphics package for my [/SIZE][SIZE=2]laptop? I have downloaded the tar, but I don't know how to install it (or even if I should try).

The Hardware Devices screen shows no installed drivers and I can't increase the resolution beyond 800x600.

This is a new installation of Jaunty 9.04 on my [/SIZE][SIZE=2]ASUS M6A laptop (1.8 GHz Centrino, 2 GB RAM), which uses the Intel 915GM/GMS Express Chipset.

I'm a relative noobie, although I'm successfully 9.04 on my desktop (go Linux!) [/SIZE]

---

### Post by overdrank on 2009-08-12
Hi and welcome, You may look at the link in my signature on Intel graphics in Jaunty. Good luck.

---

### Post by wurlyfan on 2009-08-12
Thanks overdrank. Actually I had already found that post and followed its "safe" procedure, but it didn 't make any difference, so I reverted it.  However it might bear another look, so thanks for the suggestion.

---

### Post by wurlyfan on 2009-08-14
Hello to all and please try to help me!

I have now carefully followed [psyke83]("http://ubuntuforums.org/member.php?u=50843")'s instructions on installing new Intel graphics drivers and although the procedure seemed to work, I am still in trouble.

After I rebooted into the new kernel, the startup falters after the setting APM step, and I get the following error messages:

(EE) intel(0): Output LVDS enabled but has no modes
(EE) intel(0): No valid modes.
(EE) Screen(s) found, but none have a usable configuration

From there, several options relating to the x config file are presented, but all lead eventually to a blue screen telling me that there appears to be an X server already running and asking whether to start another.

By selecting the appropriate options I can get to a point where Ubuntu starts, but in low resolution mode, and I can't increase the resolution or get rid of an annoying screen flicker.

By the way, all this also happened when I first installed 9.04 on this laptop, so I don't think it is a result of [psyke83]("http://ubuntuforums.org/member.php?u=50843")'s procedure, but rather a more basic problem.

However, I am now stumped and really need a kind expert to help me!

---

### Post by wurlyfan on 2009-08-14
[quote=wurlyfan;7783918]Hello to all and please try to help me!

I have now carefully followed [psyke83]("http://ubuntuforums.org/member.php?u=50843")'s instructions on installing new Intel graphics drivers and although the procedure seemed to work, I am still in trouble.

After I rebooted into the new kernel, the startup falters after the setting APM step, and I get the following error messages:

(EE) intel(0): Output LVDS enabled but has no modes
(EE) intel(0): No valid modes.
(EE) Screen(s) found, but none have a usable configuration

From there, several options relating to the x config file are presented, but all lead eventually to a blue screen telling me that there appears to be an X server already running and asking whether to start another.

By selecting the appropriate options I can get to a point where Ubuntu starts, but in low resolution mode, and I can't increase the resolution or get rid of an annoying screen flicker.

By the way, all this also happened when I first installed 9.04 on this laptop, so I don't think it is a result of [psyke83]("http://ubuntuforums.org/member.php?u=50843")'s procedure, but rather a more basic problem.

Please help if you have some expertise in this area!

---

