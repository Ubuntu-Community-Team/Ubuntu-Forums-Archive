---
title: "Troubles with zMate Usb pen and Gutsy"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by Giano89 on 2007-11-11
I have Ubuntu 7.10 on my desktop PC and every time I plug in my zMate USB pen by Dane Elec (quite an old model) I have some problems.
[LIST]
[*]First of all, most of the times Ubuntu doesn't mount automatically the device (althought I have set the automount option and my external usb HD is automatically mounted)
[*]Second, using dmesg I've discovered that the device is sdg1 so I set it in /etc/fstab. Mounting it manually, it works very well.
[*]Third, every time I have my pen mounted, it becomes VERY hot, much more than what it used to be in WinXP.
[/LIST]
Do you have any clues/advice? I'd like Ubuntu to mount the pen automatically EVERY TIME I plug it in and I fear that it could be destroyed by the high temperature.
Thank you!!

---

