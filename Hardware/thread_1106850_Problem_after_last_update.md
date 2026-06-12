---
title: "Problem after last update"
date: 2009-03-26
forum: Hardware
---

### Post by Hate on 2009-03-26
I was about to go to sleep when I noticed that there were some updates so I did they and I shut down the system.
when I've turned on the pc I've noticed that the visual effects were off (quite usual since I often disable them to play games with wine) so from the tab in the preferences I've tried to put it in the "normal" configuration the window looking for drivers shown but suddendly it said "Desktop effects could not be enabled" and obviously I can't play any game...

```
compiz
```

gives as output

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

```

trying to run amdcccle (ati catalyst control panel) from terminal gives as output

```
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode: 1 (X_CreateWindow)
  Resource id:  0x58
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Extension:    144 (Uknown extension)
  Minor opcode: 7 (Unknown request)
  Resource id:  0x4400002
Segmentation fault

```

while this looks ok...
```
#hate ~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.8494 Release

```


I'm running Ubuntu 8.10 and I've an ATI Radeon 9600 SE and these are the updates

```
Commit Log for Thu Mar 26 00:48:20 2009


Upgraded the following packages:
cups (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
cups-bsd (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
cups-client (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
cups-common (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
gnome-user-guide (2.24.0+svn20080922ubuntu1) to 2.24.0+svn20080922ubuntu2
libcups2 (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
libcupsimage2 (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
xserver-common (2:1.5.2-2ubuntu3) to 2:1.5.2-2ubuntu3.1
xserver-xorg-core (2:1.5.2-2ubuntu3) to 2:1.5.2-2ubuntu3.1


```

:(

---

### Post by dogooder on 2009-03-26
I have the same problem, must have happened after the update yesterday. It says "Desktop effects could not be enabled" when I try to switch to Normal or Extra under Appearance Preferences. I usually have it on Extra (I think), although I switch to metacity when I play videos fullscreen (which I think I did yesterday).

I'm on Ubuntu 8.10 with NVidia GeForce 7600 GT. I imagine I installed the same updates as Hate (I don't know the command to list them), and "compiz" gives:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
```

[edit] Okay, here are the updates:

```
Commit Log for Wed Mar 25 10:17:19 2009


Upgraded the following packages:
cups (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
cups-bsd (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
cups-client (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
cups-common (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
gnome-user-guide (2.24.0+svn20080922ubuntu1) to 2.24.0+svn20080922ubuntu2
libcups2 (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
libcupsimage2 (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
xserver-common (2:1.5.2-2ubuntu3) to 2:1.5.2-2ubuntu3.1
xserver-xorg-core (2:1.5.2-2ubuntu3) to 2:1.5.2-2ubuntu3.1 
```

---

### Post by dogooder on 2009-03-26
I followed the advice [here]("http://ubuntuforums.org/showthread.php?t=1106769&highlight=compiz") and reinstalled the NVidia driver and now things work again. You may want to try reinstalling the ATI driver, Hate.

---

### Post by Hate on 2009-03-26
Yes, reinstalling drivers worked, I only hope not to have to reinstall them again with the next xserver update :lolflag:

---

