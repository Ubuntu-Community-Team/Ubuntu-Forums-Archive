---
title: "HP dv9000 ubuntu user's guide: Ironing out the kinks."
date: 2012-06-07
forum: Hardware
---

### Post by ntzrmtthihu777 on 2012-06-07
Hello all!

Super-noob once again, here to serve all HP dv9000 w/Ubuntu users. I myself have ran into a few issues with setting up Ubuntu (12.04 at this moment) to get all functionality out of my dv9000. I've scoured the wired world searching for solutions, and I'm posting them here for the benefit of all. These solutions are not all my own, and to be frank I can't for the life of me remember each source for each fix. So if these solutions are yours, please pm me and I will give credit where credit is due. My goal is not plagiarism, but to collect all info related to this particular OS/hardware combination. These solutions may work on other combos, but the focus is Ubuntu (12.04 in particular) on the HP dv9000.

---

### Post by ntzrmtthihu777 on 2012-06-07
First off, one thing I noticed when I installed Ubuntu 10.04 on my laptop is the screen looked 'fuzzy'. I posted to the forums here
[http://ubuntuforums.org/showthread.php?t=1989670](http://ubuntuforums.org/showthread.php?t=1989670)
 asking for a solution, but I figured it out before anyone replied. The solution is easy, one a veteran user would of immediately known, but we were all noobz at one time, so I repost it here:

Open System>Administration>Hardware Drivers  and install NVIDIA accelerated graphics driver (version current)  [Recommended]

Nearly identical problem (and solution) with 12.04, but with different symptoms: Unity 3D displays a black screen with mouse. Originally I posted here
[http://ubuntuforums.org/showthread.php?t=1990517](http://ubuntuforums.org/showthread.php?t=1990517)
Log in with Unity 2d, click the dash and type 'system settings', open it, click on additional drivers, and install NVIDIA accelerated graphics driver (version current) [Recommended]

I personally use the GNOME shell with the Unity task-bar.

---

### Post by ntzrmtthihu777 on 2012-06-07
Multi-touch does not work right out of install. It is easily enabled with the script below.
1. Copy the following into a blank gedit document and save it as multitouchenable.sh
2. Right click on it, choose properties, choose the permissions tab, and check the allow it to execute box.
3. Double-click the icon choose run, and viola! Multi-touch!
4. Add this file to the startup programs, and you won't have to do this again.

[FONT=Courier New]#!/bin/bash
sleep 5
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Circular Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Palm Detection" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Scrolling Distance" 32 200 200
xinput set-prop --type=float "SynPS/2 Synaptics TouchPad" "Synaptics Circular Scrolling Distance" 0.4
#xinput list-props 'SynPS/2 Synaptics TouchPad'[/FONT]

---

### Post by ntzrmtthihu777 on 2012-06-07
**Do not use just yet! On reboot mouse disables after a bit**

Pressing the touchpad disable hardware button will do just that, but will not enable it upon the second press. Worse yet, it disables clicking and the keyboard. Also an easy fix.

1. Copy the following into a blank gedit document and save it as touchpaddisable.sh
2. Right click on it, choose properties, choose the permissions tab, and check the allow it to execute box.
3. Double-click the icon choose run, and viola! You can both enable and disable with the hardware button!
4. Add this file to the startup programs, and you won't have to do this again.

#!/bin/bash
if [ `xinput list-props 'SynPS/2 Synaptics TouchPad' | grep 'Synaptics Off' | cut -c23-23` -eq 0 ]
then
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Off" 8 1
else
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Off" 8 0
fi

---

### Post by ntzrmtthihu777 on 2012-06-07
The webcam starts when it feels like it. Part of the problem is that after a few successful runs, /dev/video0 gets renamed to /dev/video1. The fix is pretty simple for this part, just run

sudo rename s/1/0/g /dev/video1

and at least one problem will be fixed. This is only treating one symptom and not the core issue, will post full solution when found.

---

### Post by ntzrmtthihu777 on 2012-06-07
to automate the process, you can create this launcher

1. Create a blank document named video1_fixer.sh (you  can name it something else, but make sure the change is consistent) and  paste this into it:

[FONT=Courier New]#!/bin/bash

echo `sudo rename s/1/0/g /dev/video1`
echo `guvcview`[/FONT] 

2. Save it and make it executable. (you can use cheese or whatever too, I just use guvcview because it works better on my machine)

3. Create a file named Guvcview_fixed.desktop in /usr/share/applications  and paste this into it (again, rename as you please, just be  consistent):

[FONT=Courier New][Desktop Entry]
Type=Application
Terminal=true
Icon=/usr/share/pixmaps/guvcview/camera.png
Name=Guvcview_Fixed
Exec=/path/to/this/video1_fixer.sh
Name=Guvcview_Fixed
Name[en_US]=Guvcview_Fixed

[/FONT] (You can use a different icon too, this is just my setup)

4. Drag the resulting Launcher to the task-bar for quick access. This  renames /dev/video1 to /dev/video0 and then launches guvcview, but you  need to give it your password in terminal.

There is some other problem too, as even when the file is named video0 sometimes the webcam fails to launch.

---

### Post by ntzrmtthihu777 on 2012-06-07
When I figure out the core issue I'll post it here. It seems to be an issue with the uvcvideo driver, as the problem is not localized to one webcam program.

---

### Post by ntzrmtthihu777 on 2012-06-07
There are some sound issues too, which I accidentally fixed and don't know how, uh-heh. Might re-install and systematically search for solution. Man that'll suck, but anything for the good of the community.

---

### Post by ntzrmtthihu777 on 2012-06-07
to every one I know of right now. sorry I had to hog the first posts.

---

### Post by sdowney717 on 2013-04-16
I just installed raring on a dv9000.
I have no sound.

---

