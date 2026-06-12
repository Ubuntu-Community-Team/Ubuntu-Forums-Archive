---
title: "egalax touchscreen Samsung n145/150"
date: 2012-03-19
forum: Hardware
---

### Post by rocketscove on 2012-03-19
Long story(short?):>>>Old n145 w/pixel qi screen/egalax touchscreen/ubuntu 11.10/kernel 3.0.0-16-generic. (and oh yes...64gig ssd)

I want to rotate screen 90 degrees and retain touchscreen use.

I calibrated touch with xinput-calibrator, but this only gives 4 point cal. Therefore I tried to install EETI's egalix driver. I suceeded and got 9 and 25 point calibration. Several attempts at screen rotation (xrandr, touchrotate, etc) failed to provide touch grid rotation.

The egalax driver instructions state:>>Patch kernel modules..EVDEV, UINPUT, HIDRAW.

and check to see if installed using "make menuconfig".  I have headers installed for -15 and -16 in usr/src but do not have a "make" file, so cannot check or update (patch kernel). I tried "modprobe evdev" then lsmod and could not find the evdev module.

Question:>>>do I have to compile kernel?

Question:>>>how to compile?

Question:>>Is there an easier way to get screen rotate?

I have spent almost a week googling and forum swimming, and have tried many suggestions. Hope someone can cut thru this info and point me to an easy solution.

---

### Post by rocketscove on 2012-03-20
Update:>>>
As usual, I plowed ahead. Installed the egalax driver without patching the kernel. Followed the EETI instructions. Everything except rotate works great....
```

Sec 3: Install Driver Package
This section describes how to install eGTouch into OS. Before following this, please make
sure referring to “Section 2 Patch Kernel” to rebuild kernel for supporting necessary features.
3-1 Install Process
Please execute script file setup.sh to automatically decompress and install driver. It will
help you accomplish below efforts.
You could also complete these steps manually.
.
Decompress eGTouch package which contains:
a) eGTouchD: a daemon service driver for EETI touch controller.
b) eGTouchL.ini: a parameter list could be loaded by driver
c) GetEvent.c: a sample code describes how to read EETI input event.
d) eGTouchU: an utility tool of eGTouch ( Only x86 CPU would contain this)4. After launching eGTouchD, check /proc/bus/input/devices file and we will find two
virtual devices called “eGalaxTouch Virtual Device for Multi” and “eGalaxTouch
Virtual Device for Single”. Information like below figure:
9

e) eCalib: a command line calibration tool.
2. Place “eGTouchL.ini” into Linux system directory “/etc/eGTouchL.ini” where driver
would load it. We can change driver behavior by modifying this file. The detail
descriptions of parameters are described in Section 5. ( You can see brief
definitions in eGTouchL.ini )
3. Place eGTouchD & eGTouchU & eCalib under /usr/bin. Write in execution
/usr/bin/eGTouchD in /etc/rc.local to make eGTouchD executing at system start.


5-2 DetectRotation Note
As DetectRotation is enabled, eGTouch driver have to be executed after X-server is
ready.( We use Xlib to do detection ). You have to remove the eGTouch execution in rc.local
because it would not work out. Please manually put eGTouch execution in the sequence after
OS’s X server is ready.
We provides gdm solution since it’s a general startup.
1. Modify the file ”Default” under /etc/gdm/Init
2. Add eGTouch execution /usr/bin/eGTouchD at the end of file but before ”exit 0”
3. Reboot system.
Since the ready time sequence of Xlib is different among diverse startup. We’re sorry that we
couldn’t provide solution correspond to all startup. If there’s any further problem as setting up
please contact us for technical support.
```After edit eGTouchL.ini to detect rotation, remove eGTouchD from rc.local, add eGTouchD to /etc/gdm/init/default...:>>>>the daemon fails to load. If loaded manually the xrandr does not tranlate touch screen data.

Some one please advise where to put the "start daemon" or do I really have to compile kernel????

---

