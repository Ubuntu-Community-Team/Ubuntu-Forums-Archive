---
title: "Jaunty can't get to login prompt after upgrade"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by wordsmythe on 2009-05-20
I'm on a Dimension 5150 (desktop) with what I believe to be the onboard Intel Graphics Media Accelerator 950. Jaunty seems to hang between the bootup progress bar and the login screen.

After upgrading, it prompted a reboot. On reboot, the screen gets to the progress bar loading screen, and (like it used to) quarters the screen for a couple seconds (used to be four identical, off-color progress bar screens, now it's two like that on top and static on the bottom). This used to be normal and quickly move on to the login screen, but seems to freeze there now (requires hard reboot). I can get into recovery mode, at least. I've tried editing xorg.conf to add the Driver "vesa" line, but to no avail. 

I was a little rash and thought that it had been long enough since Jaunty dropped that I could upgrade without checking ahead for problems.

---

### Post by DLG102282 on 2009-05-20
> **wordsmythe said:**
> I'm on a Dimension 5150 (desktop) with what I believe to be the onboard Intel Graphics Media Accelerator 950. Jaunty seems to hang between the bootup progress bar and the login screen.

After upgrading, it prompted a reboot. On reboot, the screen gets to the progress bar loading screen, and (like it used to) quarters the screen for a couple seconds (used to be four identical, off-color progress bar screens, now it's two like that on top and static on the bottom). This used to be normal and quickly move on to the login screen, but seems to freeze there now. I can get into recovery mode, at least.

I was a little rash and thought that it had been long enough since Jaunty dropped that I could upgrade without checking ahead for problems.
The video driver was configured properly what you need to do is start Ubuntu in recovery mode and in a terminal type ```
 sudo nano /etc/X11/xorg.conf
``` and change your Video Card driver to Vesa all you have to do is add the line Driver: vesa under the video card. Then once you restart into Ubuntu either install the proprietary driver for your video card or use the correct open source driver.

---

### Post by wordsmythe on 2009-05-20
> **DLG102282 said:**
> The video driver was configured properly what you need to do is start Ubuntu in recovery mode and in a terminal type [CODE} sudo nano /etc/X11/xorg.conf[/CODE] and change your Video Card driver to Vesa all you have to do is add the line Driver: vesa under the video card. Then once you restart into Ubuntu either install the proprietary driver for your video card or use the correct open source driver.

Should have mentioned: Adding "Driver: 'vesa'" is the one thing I have tried. I'll double check my work before adding that to the OP. Thanks.

ETA: Yeah, it's ```
Section "Device"
Identifier     "Configured Video Device"
Driver         "vesa"
EndSection
```

---

### Post by wordsmythe on 2009-05-21
From what I can tell, some folks were having problems with Intel hardware. I only see laptop hardware mentioned in that, though. Is that worth looking at?

---

