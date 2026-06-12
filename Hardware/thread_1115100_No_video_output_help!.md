---
title: "No video output help!"
date: 2009-04-03
forum: Hardware
---

### Post by maxclimber1w on 2009-04-03
Hi! I am running Ubuntu 8.10 on my computer. Its a Q6600 proccessor, 4gb ram, and an ATI Radeon 2400 HD PRO video card.

About a week ago, out of nowhere, the video output started having problems. Compiz stopped working, scrolling in firefox became extremely slow and jumpy, and the same things happened when I tried to move windows around the workspace.

I was using the ATI driver installed by envyNG, and assumed that something to do with this was the problem. Following directions from this thread:
[http://ubuntuforums.org/showthread.php?t=799070&page=53](http://ubuntuforums.org/showthread.php?t=799070&page=53)

I tried to restart compiz, then ran compiz-check and this was the output:
```
max@dell-desktop:~$ compiz --replace &  
[1] 7951
max@dell-desktop:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

max@dell-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect fglrx driver version in use.
```

According to some instructions on that thread, I deactivated my driver via restricted drivers manager, then restarted the computer.

The comp went through the bootloader, but right before the login screen popped up (as gnome took control of video ouput) the screen went blank and my monitor switched to power-save mode.

I quickly realized that I had forgotten to input the command
```
sudo dpkg-reconfigure xserver-xorg
```
after uninstalling the driver, as I had been instructed on the compiz-check forum.
I booted into a terminal and ran the command, then restarted the machine.

This is where I am now. The display still is not detected, and goes to power save after the bootloader. I can log in in text mode but I don't really know much about bash commands.

Is there anyway I can install the driver via text mode or fix this otherwise? I am desperate for help! Thank you so much if you got this far!

---

### Post by maxclimber1w on 2009-04-03
SOLVED:

```
 sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo dpkg-reconfigure xserver-xorg

sudo aticonfig --initial -f
sudo reboot


```

---

### Post by shnurui on 2009-04-06
This also got my video to work, now it freezes every time I try and open the resolution center.

HD 2600 pro, 764ram p4

---

