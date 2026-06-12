---
title: "Getting ATI Radeon driver  working on Compaq Evo N610C"
date: 2008-08-31
forum: Hardware
---

### Post by pmulgaonkar on 2008-08-31
Folks, I would appreciate some help here. I have gone through all the forum threads on getting the ATI Radeon M7 LW (Radeon Mobility 7500) enabled to do hardware acceleration. Particularly, I have tried updating the xorg.conf as suggested in [http://ubuntuforums.org/showthread.php?p=4790762](http://ubuntuforums.org/showthread.php?p=4790762) and all the tips in [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI). But to no avail. I see several threads on the forum suggesting that people have gotten compiz working on the N610C. But when I try the command:  glxinfo | grep "direct rendering" as suggested in [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver), the result is "No Direct Rendering", and LIBGL_DEBUG=verbose glxinfo results in a "segmentation fault". All suggestions welcome.

Thanks in advance.

--prasanna

---

### Post by milasch on 2008-11-13
I'm sharing the same results here... As a result, the performance is being very very poor and the CPU is busy all the time when doing the most simple things.

Did you manage to find anything?

Thanks

---

### Post by practic on 2009-05-06
This is a very late reply, but perhaps others are having the same problems. 

I have a Compaq Evo N610c that works fine with Ubuntu 8.10 and Compiz, I can "spin the cube" and so forth. In fact, I am really pleased with the performance. It used to have Windows XP, and videos were stuttering after about 5 minutes, but everything works very nicely now.

I don't remember doing anything special to make it work...maybe the open source drivers were updated since the original posts? It seems to be using the open source "radeon" driver.

If anyone else still has problems and want to know more about how my system is configured, feel free to ask (maybe send me a personal email as well, since I'm not always hanging around the forums: support "at" practicatechnical.com).

---

