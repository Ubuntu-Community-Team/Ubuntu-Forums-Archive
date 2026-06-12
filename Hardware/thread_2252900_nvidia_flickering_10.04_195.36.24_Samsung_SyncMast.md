---
title: "nvidia flickering 10.04 195.36.24 Samsung SyncMaster E2220"
date: 2014-11-15
forum: Hardware
---

### Post by zamcan45 on 2014-11-15
My Samsung SyncMaster E2220 flickers all the time. I have installed nvidia drivers 195.36.24. My kernell is 2.6.32-33-generic I am running Ubuntu 10.04
The same monitor does not flicker under Windows. I have read many forums but it seems a compatibility issue.
Thanks in advance.

---

### Post by sammiev on 2014-11-15
10.04 is no longer supported, you need to move up to 12.04 or 14.04 for the LTS versions.

---

### Post by zamcan45 on 2014-11-16
Hello,
I have marked this thread as solved even when there is no solution given. I will try another Linux version. Ubuntu 12.04 also fiickers and 14.04 is too demanding for my hardware.

---

### Post by zamcan45 on 2014-11-27
I would like to add something more and share my experience. It is true that 10.04 are not longer supported, but there is a workarround.
Problem: A Samsung SyncMaster E2220 has a standard resolution of 1920x1080, but flickering is so intense that after 30 minutes of standing in front of the screen your eyes hurt.
Solution: Change the refresh rate
Root-problem: propietary drivers allow you to have maximum 50 Hz refresh rate
Solution: Elevate the refresh rate at least to 75 Hz

Solution step by step:
First deshabiitate the propietary drivers
10.04 offers you 4 propietary drivers: 96, 173, Recommended (304), and 304 updates. The four of them allow you to have maximum 50 Hz at 1920x1080
How: with the GUI, In System > Administration > Hardware drivers. Click on the driver. Green means it is installed. You have to uninstall all of them
Second: habilitate native driver that comes with ubuntu called nouveau.
Nouveau has a refresh rate at 1920x1080 of 60 Hz. It stills flicker.
Third: Set a different refresh rate, but you have to change also the resolution
How: with the CLI (Command Line) Open a terminal (ALT+F2 and type "gnome-terminal") and write the following at the prompt:
```
xrandr -s 1280x1024 -r 75
```
The resolution is worse but the flickering is gone.

---

