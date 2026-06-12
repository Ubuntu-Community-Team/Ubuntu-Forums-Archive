---
title: "Screen Resolution: X11, matrox, and a KVM switch"
date: 2009-05-11
forum: Hardware
---

### Post by BrewBelly on 2009-05-11
Hello,

I have 9.04 installed on a PC containing an on-board Matrox video device. My monitor can run with 1024x768 and 75 Hz refresh.

When Ubuntu was installed, the installer recognized the video/monitor correctly and I had 1024x768 available.  Then, I installed a KVM switch and Ubuntu no longer detects the monitor type during boot, and the X11.conf file has no matrox-specific information.  I reasoned I could install the matrox driver following:

[https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia](https://help.ubuntu.com/community/BinaryDriverHowto/MatroxParhelia)

when I run the installer, the compiler spits back errors and nothing is created (yes, I updated the headers first). the log file has many warnings, then "error 1" and "error 2"... very detailed.

If this Ubuntu install recognized the video fine prior to the KVM switch install, then there must be a driver and config file that works, somewhere on the computer.

If I remove the KVM switch, boot ubuntu, then pull the cords and insert the KVM, the computer keeps the monitor resolution for that session.  Copying the existing X11.conf file and putting it in place when I boot with the KVM switch in place gives an error during boot saying the monitor can't be detected and the system reverts to 600x800.

I tried to just enter setting in the X11.conf, such as resolution and refresh, but errors occur during boot, and we're back at 600x800.

Is there a way to save the config file that is running in the absence of the KVM switch, and have Ubuntu ignore the fact it can't detect the monitor type during boot in the future?

-BB

---

