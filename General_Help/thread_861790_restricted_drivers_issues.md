---
title: "restricted drivers issues"
date: 2008-07-16
forum: General Help
---

### Post by Torsion on 2008-07-16
Hello, I'm having trouble enabling restricted drivers for my integrated GeForce 7050.  After the driver is enabled and when the computer is restarted, I can hear the login screen make the "clink" sound, but the monitor says it's out of range.  I think the problem is my monitor only supports up to 1280 x 1024 and perhaps the driver has set the resolution too high.

So being unable to see the GUI after reboot, maybe I need to edit the xorg.conf file from the command line.  Could someone guide me through the process of doing this?  Thanks.

---

### Post by overdrank on 2008-07-16
> **Torsion said:**
> Hello, I'm having trouble enabling restricted drivers for my integrated GeForce 7050.  After the driver is enabled and when the computer is restarted, I can hear the login screen make the "clink" sound, but the monitor says it's out of range.  I think the problem is my monitor only supports up to 1280 x 1024 and perhaps the driver has set the resolution too high.

So being unable to see the GUI after reboot, maybe I need to edit the xorg.conf file from the command line.  Could someone guide me through the process of doing this?  Thanks.

Hi and you can try and use the keys alt, ctrl, F1 and this should bring you to the command line. Then you can reconfigure your xorg with this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Or you can reboot the system in recovery mode and use the xfix option.

Edit I see you made a choice
[http://ubuntuforums.org/showthread.php?t=853660](http://ubuntuforums.org/showthread.php?t=853660)
:)

---

### Post by Torsion on 2008-07-16
> **overdrank said:**
> Hi and you can try and use the keys alt, ctrl, F1 and this should bring you to the command line. Then you can reconfigure your xorg with this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Or you can reboot the system in recovery mode and use the xfix option.


Yes thank you, that's what I did so the GUI now works.  However, I am only able to view an 800 x 600 screen.  The driver says it's in use but when I try to enable accelerated graphics it gives the monitor out of range error after rebooting.  Is there a way (instead of recovering the old xorg) to edit xorg.conf from the command line?  I was thinking that the resolution just needs to be set lower than what the driver may have set it to.

> **overdrank said:**
> Edit I see you made a choice
[http://ubuntuforums.org/showthread.php?t=853660](http://ubuntuforums.org/showthread.php?t=853660)
:)

I went with the Asrock (why I bought a new system) and still having video trouble. :(  But I assume it's good for learning Linux. :)

---

### Post by jonian_g on 2008-07-16
Open a terminal and type

sudo displayconfig-gtk

Click where it says "Model" and at the screen that comes up choose your monitor model. If not in the list click add and locate the *.inf file in the cd-rom that came with your monitor. Then select you monitor model and press ok. If you don't have the cd choose a general model with your highest resolution.

This will prevent the driver from using higher resolutions that the ones your monitor supports.

---

### Post by Torsion on 2008-07-17
Awesome, thank you!

---

