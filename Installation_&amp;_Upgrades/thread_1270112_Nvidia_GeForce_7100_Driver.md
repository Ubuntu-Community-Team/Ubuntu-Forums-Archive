---
title: "Nvidia GeForce 7100 Driver"
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by nexoncore on 2009-09-19
I have tried everything to get my graphics card working but I cant, I have tried the Hardware Drivers section in Admin, and theres no drivers there

The graphics card I have is an onboard graphics nvidia GeForece 7 series / nvidia nforce 6 series.

Any help would really be appreciated.

---

### Post by tommcd on 2009-09-19
> **nexoncore said:**
> 
The graphics card I have is an onboard graphics nvidia GeForece 7 series / nvidia nforce 6 series.

Your video card is supported by the nvidia-glx-180 driver:
[http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180)
(The GeForce 7100 / NVIDIA nForce 630i is listed about 2/3 down the page).
To install the driver open a terminal and run:
```
sudo apt-get install nvidia-glx-180
```
Then hit ctrl + alt + F2 to get to a virtual terminal. Then login and run:
```
sudo /etc/init.d/gdm stop
```
This will stop the X server. 
Then to configure the nvidia driver run:
```
sudo nvidia-xconfig
```
Then reboot with "sudo reboot" (without the quotes). When you reboot the driver should be enabled. You can then run nvidia-settings from the terminal to do any setup or to see what is going on with the driver.

It is not strictly necessary to stop the X server to configure the nvidia driver in Ubuntu, but it is always a good precaution.

EDIT: I am assuming you are running Ubuntu 9.04 "Jaunty Jackalope". Is that correct?

---

### Post by deanhanson on 2009-09-19
Hi...
 I have some information regarding that so that i want to share with you...Although the 7300 LE was originally intended to be the "lowest budget" GPU from the GeForce 7 lineup, the 7100 GS has now taken its place. As it is little more than a revamped version of the GeForce 6200TC, it is designed as a basic PCI-e solution for OEMs to use if the chipset does not have integrated video capabilities. It comes in a PCI Express Graphics Bus and 512MB DDR2 VRAM.  Performance specification      * Graphics Bus: PCI Express     * Memory Interface: 64-bit     * Memory Bandwidth: 5.3 GB/s     * Fill Rate: 1.4 billion pixel/s     * Vertex/s: 263 million     * Memory Type: DDR-II with TC... thanks for sharing the post...

---

### Post by Imaginatorium on 2009-09-25
I seem to have the same problem; I have a GeForce 7100 [no 'GS' in sight] "onboard graphics" motherboard, and I've now been through about four cycles of trying to install the nvidia drivers following various sets of instructions, finishing up with the one above.

I always end up with gnome attempting to start up, and get an

 " Input not supported "

panel floating around the screen. (But I tried switching monitors, and a different one gives "OUT OF RANGE". So presumably the driver is sending out some sort of garbage?)

I have no idea where to start finding a way out of this. If I completely remove the nvidia drivers I can get gnome in low resolution; otherwise nothing (even with the gnome "failsafe" start)

I'm not bothered about "high-performance" graphics at all, so any alternative that would provide a high-resolution gnome desktop would be fine. Any suggestions?

Thanks in advance.
Brian Chandler

---

### Post by tommcd on 2009-09-26
> **Imaginatorium said:**
> ...I've now been through about four cycles of trying to install the nvidia drivers following various sets of instructions, finishing up with the one above.
I always end up with gnome attempting to start up, and get an
 " Input not supported "
panel floating around the screen... 

So you installed nvidia-glx-180 from the terminal, and then stopped the X server and ran "sudo nvidia-xconfig"? Is that right? 
I assume you are using Ubuntu 9.04 installed to a hard drive partition and not in Windows through Wubi? Is that correct also?
If so, can you post your /etc/X11/xorg.conf file? 
Also, with the nvidia-glx-180 driver installed and configured, what is the output of:
```
glxinfo | grep -i direct
```
The xorg.conf file will tell us if you are using the nvidia driver, and the glxinfo command will tell us if the driver is enabled properly.
It sounds like your monitor is not being detected properly. You could try adding your monitor's horizontal and vertical refresh rates to xorg.conf like this:
First, backup the file for safety:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then open the xorg.conf file with any text editor. For example, to use gedit run:
```
gksudo gedit
```
from the terminal and add the refresh rates to the "Monitor" section of xorg.conf like this example:
```

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        **HorizSync    30-107**
        **VertRefresh  48-120**
EndSection

```
Just **add** *the proper resolutions for your monitor's specs* to the Monitor section like that. Then reboot.
If that does not work, then try using **xrandr** to get proper resolutions:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

And welcome to the Ubuntu forums!

---

### Post by zupal1461 on 2009-09-26
i need some help

are there any methods for installing the package for those (like me) without an internet connection?

---

### Post by tommcd on 2009-09-26
> **zupal1461 said:**
> 
are there any methods for installing the package for those (like me) without an internet connection?
Are you talking about the nvidia-glx-180 driver? If so you could download the driver from here:
[http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180)
Click the links at the bottom of the page for i386 for 32 bit Ubuntu or amd64 for 64 bit. This will take you to a list of mirrors. You can download the driver as a .deb file from the pool/restricted/n/nvidia-graphics-drivers-180/ section of any mirror. You will have to also satisfy all the dependencies listed on the page I linked to. Search for all the dependencies in synaptic to see if they are installed.

---

### Post by Imaginatorium on 2009-09-27
Many thanks for the response... Sorry this is not very well organised, but perhaps there is a clue somewhere to the next step.


>> So you installed nvidia-glx-180 from the terminal, and then stopped the X server and ran "sudo nvidia-xconfig"? Is that right?

Not exactly: I used the Ubuntu System / Administration menu -> "Hardware drivers", which seems to mean "Try to install proprietary drivers and announce success, but don't tell me anything specific".

I'm sorry: I'm confused by "install" here: if I use APT / synaptic to install the package, then it's "installed", right? As far as I can see, once I have it installed, I can't run the X server -- logging into the "failsafe Gnome" gives the blank screen -- I can only access the "failsafe terminal". I discovered I can extract myself from this point by running 

envyng --uninstall-all

Here's the xorg.conf file (retyped, less comments) -- almost entirely platitudes, except the 'nv' which I put in myself.

 =========================================
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nv"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
 =========================================

AIUI, since I'm not bothered about any fancy graphics acceleration (no games!), if I could use the default 'nv' driver (?) it might be fine. But I can't find any instructions or help on how to do this. I did once manage to get to a state where the System / Administration menu included something called "Display resolution" or similar, but I can't get back to it. I can get back to running X in low-resolution using envyng, but I notice that it leaves the xorg.conf file with the driver as "nvidia". I don't understand this:

If xorg.conf determines what driver is used, and I have just removed the nvidia driver, what does it mean? (Otherwise, I don't understand the function of xorg.conf.)

-------

Anyway, I just installed nvidia-glx-180 from synaptic, forgot to stop the X server, and ran sudo nvidia-xconfig. This complained about having to generate various bits automatically: it has put the line

	Driver 	"nvidia"

in the xorf.conf file.

------

I now tried:

glxinfo | grep -i direct

Gives a lot of lines, each

Xlib: extension "GLX" missing on display ":0.0".

-------

And xrandr gives "Can't open display"

-------

Incidentally, when the system starts up I get a message:

Ubuntu is running in low-graphics mode ...
(EE) No devices detected.

Perhaps this confirms that the monitor resolution (etc) isn't being read. The current monitor has no identifiable maker name, just the model number MT7CNA (which gives around 30 google hits, almost all in Japanese, and no spec whatsoever). But I had the same problem with an Acer monitor before I swapped them.

Thanks again

---

### Post by tommcd on 2009-09-29
> **Imaginatorium said:**
> 
I used the Ubuntu System / Administration menu -> "Hardware drivers", which seems to mean "Try to install proprietary drivers and announce success, but don't tell me anything specific"....

envyng --uninstall-all

Did you install the nvidia driver from: system > administration > hardware drivers *and also* install the nvidia driver with envyng? If so, you should not do this. Having the nvidia driver from the ubuntu repos and the driver from nvidia.com is not good since they will likely conflict. Remove all nvidia drivers you may have installed (use apt-get remove --purge) and try again with only 1 method (envyng or the ubuntu repos driver). I would use envyng at this point since there are reports of success with envyng with the nvidia 7100:
[http://ubuntuforums.org/showthread.php?p=4124204](http://ubuntuforums.org/showthread.php?p=4124204)
[http://www.linuxquestions.org/questions/linux-hardware-18/nvidia-7100-unknown-chipset-613160/](http://www.linuxquestions.org/questions/linux-hardware-18/nvidia-7100-unknown-chipset-613160/)
[http://lukasz.dk/2008/02/09/ubuntu-710-and-nvidia-nforce-630i/](http://lukasz.dk/2008/02/09/ubuntu-710-and-nvidia-nforce-630i/)
> **Imaginatorium said:**
> 
I'm sorry: I'm confused by "install" here: if I use APT / synaptic to install the package, then it's "installed", right? 
Yes that is correct. You can check this by searching for the package in synaptic, or by running:
```
aptitude search nvidia
```
A "p" before a package means it is purged (i.e., not installed). A "i" before a package means it is installed. Or you can show detail about any package with:
```
aptitude show nvidia-glx-180
```
The beginning of the output will say if the package is installed or not.
> **Imaginatorium said:**
> 
AIUI, since I'm not bothered about any fancy graphics acceleration (no games!), if I could use the default 'nv' driver (?) it might be fine. But I can't find any instructions or help on how to do this. I did once manage to get to a state where the System / Administration menu included something called "Display resolution" or similar, but I can't get back to it. I can get back to running X in low-resolution using envyng, but I notice that it leaves the xorg.conf file with the driver as "nvidia". I don't understand this:

If xorg.conf determines what driver is used, and I have just removed the nvidia driver, what does it mean? (Otherwise, I don't understand the function of xorg.conf.)

If you want to use the "nv" driver just uninstall the nvidia driver(s) you installed and use "nv" in the driver line of the device section of xorg.conf. Or you can try booting to recovery mode and choose the option: **xfix fix video**. And then reboot.
> **Imaginatorium said:**
> 
Anyway, I just installed nvidia-glx-180 from synaptic, forgot to stop the X server, and ran sudo nvidia-xconfig. This complained about having to generate various bits automatically: it has put the line

	Driver 	"nvidia"

in the xorf.conf file.

------

I now tried:

glxinfo | grep -i direct

Gives a lot of lines, each

Xlib: extension "GLX" missing on display ":0.0".

Make sure there is a line: Load  "glx" in the Module section of xorg.conf like this:
```

Section "Module"
    Load           "glx"
    Load           "dri2"
    Load           "extmod"
    Load           "dbe"
EndSection

``` 
> **Imaginatorium said:**
> 
Incidentally, when the system starts up I get a message:
Ubuntu is running in low-graphics mode ...
(EE) No devices detected.

This is referring to your graphics card, not the monitor, although if ubuntu can't detect your monitor's specs that would likely give you the wrong resolution.
To see what driver is being loaded check your Xorg.0.log:
```
cat /var/log/Xorg.0.log | grep -i loadmodule

```
It will report either nv or nvidia.
Try installing the driver with envyng (after removing the driver from the Ubuntu repos). If it still fails, post the output of:
```
cat /var/log/Xorg.0.log | grep EE
```
If you still can't get the nvidia driver to work, edit the /etc/default/linux-restricted-modules-common file and change the last line from:
```
DISABLED_MODULES=""
``` 
to:
```
DISABLED_MODULES="nv"
```
and reboot. You could also try adding:
```
DISABLED_MODULES="nv nvidia_new"
```
Reboot after each of these changes.
Note that you will have to remove those blacklisted modules from that file and return the line to: DISABLED_MODULES="" if you plan to use the nv driver.

---

### Post by Imaginatorium on 2009-10-02
Thanks for the help. There are a lot of clues in there...

I tried first to install the nv driver, and was able (eventually) to find the problem now I know how to find the X error log -- nv doesn't support my onboard graphics, which is GeForce 7100/nForce 630i.

So I tried the nvidia driver again, using envyng. Again, at least I could find a problem in the x log file:

```
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv000046gl
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
```

I googled around on libglx, and could see hints that it might be some sort of version problem, but I don't understand how to update (or "roll back") the version. I've attached the complete log file in the hope this helps. Grateful for more clues...

---

### Post by tommcd on 2009-10-03
Farther down in you Xorg.0.log it says this:
```

(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled

```
This would seem to indicate that the driver is loaded. Are you able to get a graphical desktop at all? If so, try using xrandr to set the proper resolutions since it says RandR enabled.

---

