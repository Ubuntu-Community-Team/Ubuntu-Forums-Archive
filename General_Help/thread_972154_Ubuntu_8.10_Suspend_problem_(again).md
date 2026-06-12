---
title: "Ubuntu 8.10 Suspend problem (again)"
date: 2008-11-05
forum: General Help
---

### Post by canadeza on 2008-11-05
Ok since ver 6 of Ubuntu I am experiencing the same and the same problem - my Sony Vaio VGN-S460P with Nvidia 6200 wakes up with white screen and colorfull vertical lines on it... beauty

But.. I've read about the solution of the problem and was able to apply it successfully on 8.04 (the moethod with adding options NvAGP 1 in xorg, post-video FALSE and others in acpi-support)

Ok now Im in 8.10 and I enjoy it but it seems that this method doesnt work for this version of ubuntu.
When i oopen acpi-support file I see it has changed but I skip this and change the values as in the manual. Then I set the sleep method (new option) to "acpi-support" - the original option was dbus pm-utils...

and it doesnt work... I can suspend but when i hit the power button again, a white screen with vertical lines pops up.

Any help would be appreciated.

---

### Post by canadeza on 2008-11-05
bump

---

### Post by Jorge_C on 2008-11-05
Hi, I'm sorry I don't know how to solve your problem, but I also experience [this problem]("http://ubuntuforums.org/showthread.php?t=913868") (with hardy right now).

Could you please link the thread(s) which solved your suspend problems in hardy?
Any way, I will be updating to Intrepid very soon and I'm afraid I will get the same problem as you, so I will keep an eye on this thread.

---

### Post by canadeza on 2008-11-05
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

---

### Post by canadeza on 2008-11-05
bump

---

