---
title: "Dual-Monitor Setup, AMD, Freezing, and Grub2 Issues"
date: 2017-03-03
forum: Hardware
---

### Post by Sith Lord Kyle on 2017-03-03
I just added a new monitor to my setup today and there are all kinds of weird things going on.  The video card is AMD R9 390.

First, my old setup had a monitor on DV-I with AMDGPU-PRO 16.60 installed and it worked fine... with the exception that the desktop froze up after about 30-60 minutes.  Only the mouse moved, nothing else worked.  Even the keyboard was locked up.  It also did this on the AMDGPU-PRO 16.50 drivers.

Now, I added a new monitor on the HDMI output.  Once I did this when Grub2 boots up the screen blanks out (no signal).  I can blindly pick my OS and Ubuntu 16.04 boots normally, the screen on the DV-I comes back to life.  The HDMI one is neither shown in displays or anywhere else.  The freezing issue still happens as well.

TL-DR: Second monitor on HDMI not recognized as existing, Grub2 screen blanks out (no signal) but still works blindly, desktop freezes after half an hour of use and need hard reboot.

Any ideas?

Update 1 - Grub2 Issue: Solved with this thread ([https://ubuntuforums.org/showthread.php?t=1798863&highlight=grub2%2C+display%2C+dual+monitor](https://ubuntuforums.org/showthread.php?t=1798863&highlight=grub2%2C+display%2C+dual+monitor)) and saved for posterity.

Update 2 - All other issues solved by removing the AMDGPU-PRO drivers and installing the ones here: [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa/](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa/).  It seems like the AMDGPU-PRO drivers are really problematic still.

---

### Post by opsusec on 2017-03-06
> **Sith Lord Kyle said:**
> Update 1 - Grub2 Issue: Solved with this thread ([https://ubuntuforums.org/showthread.php?t=1798863&highlight=grub2%2C+display%2C+dual+monitor](https://ubuntuforums.org/showthread.php?t=1798863&highlight=grub2%2C+display%2C+dual+monitor)) and saved for posterity.

Update 2 - All other issues solved by removing the AMDGPU-PRO drivers and installing the ones here: [https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa/](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa/).  It seems like the AMDGPU-PRO drivers are really problematic still.


Kudos, I ALWAYS roll these drivers back and then lock 'em down due to this issue.
If it ain't broke; don't fix it! :guitar:

---

