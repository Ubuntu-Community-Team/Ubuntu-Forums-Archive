---
title: "Display resolution limitation problems with Ubuntu 10.04 on Eee Pc 1005PX netbook"
date: 2011-01-14
forum: Hardware
---

### Post by jal741 on 2011-01-14
Problem situation:
[INDENT]I am unable to select a display resolution of 1024x768 when I connect an LCD projector to this computer's VGA port, and choose to display the same content on both the internal and external display.  The maximum display resolution Linux will show is 800x600.  Windows does not have this problem, and can show 1024x768 on both the Netbook's LCD display and the external projector without any problem, on this same computer hardware.
[/INDENT]

Background information: 
[INDENT]I installed Ubuntu 10.04 LTS on an Eee PC 1005PX netbook computer.  I installed it as a dual-boot, retaining the pre-existing Windows 7 operating system that came with this computer.
[/INDENT]

Technical details:
[INDENT]Windows 7's display manager reports a list of supported display resolutions for this Netbook as follows:
[LIST]
[*]800x600
[*]1024x600
[*]1024x768
[*]1152x864
[/LIST]
Ubuntu 10.04's 'Preferences --> Monitors' reports a different list of supported display resolutions for this Netbook as follows:
[LIST]
[*]640x480
[*]800x600
[*]1024x600
[/LIST]
The video card in this NetBook is reported by Windows 7 to be an Intel 3150.

In Ubuntu, 'System --> Administration --> Hardware Drivers' has an empty list, and indicates that 'no proprietary drivers are in use on this system'.  Does this mean that the display drivers are not properly installed?
[/INDENT]


So, how can I quickly and easily get Ubuntu Linux to support the same display resolutions that Windows 7 supports (or at least 1024x768)?  What menu items or settings options do I need to click on?

P.S.  Please try to avoid telling me to run any command-line gibberish, or manually edit any configuration files.  If GUI instructions can not be provided, then any command-line instructions will need to be VERY specific and step-by-step.  That is, instructions need to be so easy that my grandmother's grandmother should be able to follow them.

---

