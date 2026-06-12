---
title: "NVIDIA Driver Upgrade"
date: 2013-01-06
forum: Hardware
---

### Post by DoingMyHeadIn on 2013-01-06
Greetings (again) All

My issue is that the latest update caused my nvidia card to stop working and to use the VESA - GF100 board.  After some frustration and assistance from the forum I am able to get back into the GUI.  And when I look at the startx output it shows that the kernel is using the nvidia 304.48 version while the nvidia driver is 304.64 - obvious conflict.

Have tried updating (and removing and re-updating) the system and using various nvidia drivers (apt-get) this has not worked. Since the last time I can no longer log-in using my administrator account :( - but for some reason can log in using the guest account!

Did find the following two errors:
[LIST]sudo dpkg-reconfigure nvidia-current generates message -> /usr/sbin/dpkg-reconfigure: nvidia-current is broken or not fully installed[/LIST]
[LIST]sudo dpkg-reconfigure nvidia-current-updates generates message -> ERROR: modinfo: could not open /lib/modules/3.2.0-35-generic/updates/dkms/nvidia_current_updates.ko: Invalid argument[/LIST]

I need some assistance in fixing this and perhaps updating the kernel to 304.64, or revising the nvidia driver back to 304.48.

Help please (I am starting to panic) I have lost two days to this and need to progress with uni work urgently.

I am running:
Ubuntu 12.04.1
64 bit
Nvidia Quadro 4000

J

---

