---
title: "ATI/AMD FGLRX drivers do nothing on Dell Studio XPS 1640"
date: 2010-05-15
forum: Hardware
---

### Post by potiphera on 2010-05-15
I just installed 10.04 on a Dell Studio XPS 1640.  It prompted me to install hardware drivers, one of which was the proprietary driver for ATI cards.  I installed/activated it and restarted, but there's no change in the graphics: images still have blocky colors, etc.  The card on this computer is an ATI Mobility Radeon HD 3670.  How do I fix this?

---

### Post by dino99 on 2010-05-15
install: xserver-xorg-video-radeon

---

### Post by potiphera on 2010-05-15
Hmmm, I see that that is installed already.  Should I remove one of them?

---

### Post by khelben1979 on 2010-05-15
Download the driver yourself instead of letting Ubuntu handle it might solve it: [Graphics Drivers & Software - AMD]("http://support.amd.com/us/gpudownload/Pages/index.aspx").

---

### Post by mellowtothemax on 2010-05-18
If for some reason you mess up the proprietary ATI 3D display driver then just remove the fglrx package and delete '/etc/X11/xorg.conf'. (Lucid radeon driver does not use this file only the proprietary does)

Make sure that the radeon driver is always installed.

Then run the command 'sudo dpkg-reconfigure xserver-xorg'.

When you restart, the system will reconfigure using the radeon driver that was installed originally.

Then try installing the proprietary again if you like.

There are more detailed instructions on the ATI website regarding what files and directories to delete when you want to completely remove all related files for the proprietary driver.

On my laptop the proprietary driver causes screen tearing but has better 3D performance and power management.  The radeon driver works flawlessly but fans run more often and slower 3D.

Studio XPS 16 ATI 4670

---

### Post by potiphera on 2010-05-19
Thanks for the advice, everyone! After having switched between the two drivers a few times, I decided to try viewing the same stuff on an XPS with an Nvidia card, and came to the realization that what I'm seeing is a normal amount of banding, but it's just more noticeable on this screen because the contrast is higher.

---

### Post by Yellow Pasque on 2010-05-20
Please mark solved.

---

