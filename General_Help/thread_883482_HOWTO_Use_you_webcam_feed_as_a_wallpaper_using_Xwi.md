---
title: "HOWTO: Use you webcam feed as a wallpaper using Xwinwrap."
date: 2008-08-08
forum: General Help
---

### Post by easybake on 2008-08-08
This tutorial will show you how you can use your webcam feed as your wallpaper (For people who constantly need to look at themselves). 
*This will NOT make you lose the functionality of icons, conkys, screenlets, or docks. *

**From this**[[IMG]http://img359.imageshack.us/img359/7707/screenshotia1.th.png[/IMG]](http://img359.imageshack.us/img359/7707/screenshotia1.png)_[[IMG]http://img210.imageshack.us/img210/5060/screenshotir7.th.png[/IMG]](http://img210.imageshack.us/img210/5060/screenshotir7.png)**To This!**

[COLOR="Red"]**[SIZE="3"]1. Check Requirements:[/SIZE]**[/COLOR]
> 
[SIZE="2"][COLOR="Red"]**This will only work with Compiz-Fusion enabled as your Window Manager.**[/COLOR][/SIZE] [_Click Here_]("http://ubuntuforums.org/showpost.php?p=5056867&postcount=1") for installation instructions.
*NOTE: This won't require any special settings in CompizConfig Settings Manager.*

[COLOR="Red"][SIZE="2"]**This will also require Mplayer being installed.** [/SIZE][/COLOR][_Click Here_]("http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-804-hardy-heron.html") for installation instructions.


[SIZE="2"]**[COLOR="Red"]This also requires an already working webcam.[/COLOR]**[/SIZE]


[SIZE="3"]**2. Download Xwinwrap**[/SIZE].

**[SIZE="3"]_Installation Option 1[/SIZE]_** 
> **Open Accessories>Terminal**
*Enter the following codes*:```
sudo apt-get install build-essential libx11-dev x11proto-xext-dev libxrender-dev libxext-dev cvs
```
```
cvs -d :pserver:anoncvs@cvs.freedesktop.org:/cvs/xapps co xwinwrap
```
```
cd xwinwrap
```
```
make
```
```
sudo cp xwinwrap /usr/bin
```


**[SIZE="3"]_Installation Option 2[/SIZE]_**
> Go to this URL. _[http://www.getdeb.net/app/xwinwrap]("http://www.getdeb.net/app/xwinwrap")_

Select the option that fits your system.

Click Download Xwinwrap

A download popup should appear.

Select the option **Open with GDebi Package Installer (default)**

**Click OK**

The rest of the installation is automated.[/quote]

*You have now successfully installed Xwinwrap*.

[SIZE="3"]**3. Test it out.**
[/SIZE]
**In Terminal** 
```
cd
```
```
xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- mplayer -wid  WID -quiet -fps 15 tv://
```
*If you want a Mirror effect add this to the end of the line above*```
 -vf mirror
```
*NOTICE: When you close the terminal window it will stop Xwinwrap.*
[SIZE="3"]


**4. Create an easy way to start/stop this effect**[/SIZE].

**[SIZE="2"]In Teminal[/SIZE]** ```
gedit toggle
```
**Paste this in your text editor**```
#!/bin/sh

# click to start, click to stop
if pidof xwinwrap ; then
 killall xwinwrap
 else
 exec xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- mplayer -wid  WID -quiet -fps 15 tv:// 
fi
```
*NOTE: If you want the Mirror effect, after "tv://" , _on the same line_ add:*```
 -vf mirror
```

**Save and close.**

You now need to make the script executable.

**In Terminal**
```
sudo chmod a+x toggle
```

**[SIZE="3"]5. Create A Launcher[/SIZE]**:

Right Click on either the desktop or on your panel.  
***For Desktop*** select (create Launcher)
***For Panel*** select (click Add To Panel)+(Custom Application Launcher)

For _Name_ input anything.
For _Command_ input ```
./toggle
```
You can leave the comment section blank.
**Click Ok**. 

**[SIZE="3"]You're done![/SIZE]**
-----------------------------------------------------

[COLOR="Navy"]_**Dissecting the Xwinwrap code.**_
```
xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- mplayer -wid  WID -quiet -fps 15 tv://
```
**-ni** means No Input
**-o 0.20** is the Opacity setting from 0 to 1
**-fs** means FullScreen
**-s** means Sticky(its on all workspaces)
**-sp** means Skip Pager (window won't appear in pager)
**-st** means Skip Taskbar (window won't appear in taskbar)
**-b** means Below
**-nf** means No Focus
**-wid** creates a window id
**--mplayer** means mplayer 
**-fps 15** means 15 Frames Per Second
**tv://** tells mplayer to use the default video input device.
**-vf mirror** means video filter Mirror.

Feel free to change any of these if you want it to act differently.
More filters and effects can be found by opening Terminal and typing ```
man mplayer
```[/COLOR]
-----------------------------------------------------

[COLOR="DarkRed"]**_[SIZE="2"]Problems you may run into.[/SIZE]_ **

_If you have a tv tuner hooked up to your computer._ The tv:// command may not work, and instead of getting a webcam feed you could potentially get tv channels as your wallpaper. But that might be cooler than a webcam feed.

_Other programs can't use the webcam simultaneously._ I suggest turning Off the program before you use other programs.

_Suspend-To-Ram won't work while your webcam is on._ I suggest turning Off the program when you don't want it in use. You could also add the line **killall xwinwrap** to **/etc/acpi/sleep.sh** Which would kill the process before suspending to ram. You can also add the line **killall xwinwrap** to **/etc/acip/hibernate.sh** if you have problems suspending to the hard drive.

_This apparently only works using the X11 driver in Mplayer._ Other drivers tend to not be capable for handling due to the lack of indirect rendering on some Intel cards.

*Got to give credit to* [***The Warlock***]("http://ubuntuforums.org/member.php?u=18829"), [***gaminggeek***]("http://ubuntuforums.org/member.php?u=105709"), ***[Valdi]("http://ubuntuforums.org/member.php?u=311216")***, and ***[cammin]("http://ubuntuforums.org/member.php?u=384472")*** for pointing out problems [/COLOR]

-----------------------------------------------------

(For more info on Xwinwrap click [_Here_]("http://www.fsckin.com/2008/04/14/fun-with-xwinwrap-in-compiz-fusion/") or [_Here_]("http://swik.net/xwinwrap"))

Credit for the original idea [_Here_]("http://ubuntuforums.org/showthread.php?t=879897") and [_Here_]("http://ubuntuforums.org/showthread.php?t=846743")

---

### Post by easybake on 2008-08-09
Let me know if you run into any problems or if you have any ideas on what to add.

---

### Post by cammin on 2008-08-09
If you add a line like
**killall xwinwrap**
to
**/etc/acpi/sleep.sh**
You won't have to remember to kill it before suspending to ram.

You may have to add it to
**/etc/acip/hibernate.sh**
if you have problems suspending to the hard drive.


[Here's a typical disclaimer about how you should be backing up files before you change them, and that you're doing what I mentioned at your own risk.]

---

### Post by Vadi on 2008-08-09
A tip, you can ease the xwrinwrap installation by recommending .debs: [http://www.getdeb.net/search.php?keywords=xwinwrap](http://www.getdeb.net/search.php?keywords=xwinwrap)

(and if you'd like to make it super nice, maybe a gnome-panel gadget to toggle this :))

---

### Post by easybake on 2008-08-09
> **Vadi said:**
> A tip, you can ease the xwrinwrap installation by recommending .debs: [http://www.getdeb.net/search.php?keywords=xwinwrap](http://www.getdeb.net/search.php?keywords=xwinwrap)

(and if you'd like to make it super nice, maybe a gnome-panel gadget to toggle this :))

You can use the launcher part I had in the installation no matter which way you install it.

---

