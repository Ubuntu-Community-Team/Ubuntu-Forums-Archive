---
title: "NVIDIA messed up after kernel update"
date: 2009-10-27
forum: Hardware
---

### Post by LeeU on 2009-10-27
I am running Ubuntu 8.04 (Hardy), with an NVIDIA GeForce 8300 GS video card. The system worked fine until I recently did an update, using the update manager. When I restarted the system, it went into low graphic mode and I could not re-establish the NVIDIA card. I booted up in 640x480 mode (which I am still in) and have attempted to fix the situation but to no avail. I have listed below what I have done, along with a few notes.

[LIST]
[*] There is nothing in System -> Administration -> Restricted Drivers screen, either before or after doing any of the steps below, so [this step won't work]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Ubuntu%208.04%20and%20Ubuntu%208.10").

[*] I tried installing EnvyNG, but it didn't install/configure the driver properly. When the system rebooted, there were green bars running across the top of the screen, with 2 bold white lines, then a multicolored line, then another bold white line. The actual screen was displayed "reversed" at the bottom, with the left side on the right, and the right side on the left. Only the top half of the screen was displayed. I rebooted into recovery mode and ran the XFIX utility.

[*] I have tried installing the NVIDIA drivers manually using the instructions [here]("https://help.ubuntu.com/community/NvidiaManual"), which helped before. However, the install failed. I have the errors in the "nvidia-installer.log", if it's necessary. If needed, I can post it here. (It's a bit long and I wasn't sure if there was any security info in there.)
[/LIST]

As it is, according to the Synaptic Pack Manager, I only have the following packages installed for NVIDIA:

[LIST]
[*]nvidia-kernel-2.6.22-15-rt
[*]nvidia-kernel-2.6.22-16-rt
[*]nvidia-kernel-common
[/LIST]

Anyone have any ideas how to fix this?

---

### Post by wojox on 2009-10-27
This always works for me: [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

I use the NVIDIA 173.xx

---

### Post by LeeU on 2009-10-29
Thanks! I'll check it out.

---

