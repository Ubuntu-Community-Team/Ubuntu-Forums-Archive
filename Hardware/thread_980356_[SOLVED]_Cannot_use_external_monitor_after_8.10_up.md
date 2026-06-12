---
title: "[SOLVED] Cannot use external monitor after 8.10 upgrade"
date: 2008-11-12
forum: Hardware
---

### Post by ARam1024 on 2008-11-12
**Background**
I recently upgraded a Dell laptop (Latitude D600) from Kubuntu 8.04 (Remix) to Kubuntu 8.10.  When I rebooted, I was greeted by a host of problems, the first of which was that I couldn't log in.  I looked for the KDE option in x-session-manager as instructed in the Kubuntu release announcement, but I only had KDE4.  I found that I still had .kde and .kde4 folders in my home directory.  I moved the contents of .kde4 to .kde.  That almost worked, but I had to delete the .kde folder and let Kubuntu recreate it to log in.

After I did that, things were almost back to normal, except that I couldn't use an external monitor. Kubuntu detected it and poped up a message, but after I selected the correct resolution and clicked apply, the monitor was still blank.  After all the updates, it still didn't work.

**Current State**
I thought it was likely that some part of the botched upgrade process messed with x.org or the video card settings, so I did a clean install, but I'm still having the same problem with all external display sources I've tried (monitors and projectors).

**Useful Info**
Video Card: Mobility Radeon 9000 (no restricted drivers available)

Specs List: [drivers]("http://support.dell.com/support/downloads/driverslist.aspx?c=us&cs=04&l=en&s=bsd&ServiceTag=&SystemID=LAT_PNT_PM_D600&os=WW1&osl=en&catid=&impid=")

Any help getting external monitors to work would be helpful.

---

### Post by ARam1024 on 2008-11-13
**Other helpful info**

/etc/X11/xorg.conf

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

---

### Post by ARam1024 on 2008-11-20
From advice in another post, I used Envy to get the newest ATI driver.  After a restart, I could not start x. The screen was refreshing about every 20 to 30 seconds.  After waiting about 10 minutes, I restarted into recovery mode and had Envy uninstall the ATI drivers.  I still couldn't get to the login screen.  Since there wasn't much on the computer, I simply reinstalled Kubuntu.  Does anyone have some advice in case something like this happens again?  Also, a reinstall is not going to resolve my first problem, so any help there would still be appreciated.

---

### Post by ARam1024 on 2008-12-08
The issue is resolved.  After a fresh installation, I was able to reboot with an external monitor attached.  Can't get an external monitor to work if I attach it after I boot up though.  Small problem.

---

