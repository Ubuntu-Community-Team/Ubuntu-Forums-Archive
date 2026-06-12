---
title: "How to recover when NVidia driver fails?"
date: 2008-03-08
forum: Hardware &amp; Laptops
---

### Post by BenPadman on 2008-03-08
Hi,

I am new to Linux world. I tried to install NVidia and thats it , lost X, When restarted the computer. It is showing - Fail to load X.

I am using...

AMD Athlon X2 5200
M2N E Motherboard
NVidia GeForce 7200 GS
Viewsonic 19"
1 GB Ram

I tried to install...

nvidia-glx-new
nvidia-kernel-common
nvidia-settings

Synaptic installed nvidia-glx-new and nvidia-kernel-common and said nvidia-settings cannot be installed and it is included in nvidia-glx-new.

However I was not able to adjust screen resolution or adjust anything but the basic settings. So I thought to install nvidia-settings and it gave me fatal.

I uninstalled 3 of it and reinstalled nvidia-glx-new and nvidia-kernel-common but I could not get into X.

I reinstalled the operating system again and installed nvidia-glx-new and nvidia-kernel-common. But it is not a good solution to reinstall OS in situations like this since I started to learn Linux and expecting more crashes in future.

Please help to me to take steps in situation like these.

1.  How can I recover the basic settings when graphic driver fail? I mean how to roll back the driver?
2. How can I install nvidia-settings, so that I can get 1440x900 resolution?

Thanks a lot in advance for helping me.

---

### Post by taurus on 2008-03-08
If X fails and you need to reconfigure the X server again, just run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by BenPadman on 2008-03-08
Thank you very much.

And how can I get adjust screen resolution in NVidia Settings. I have attached a screenshot of NVidia settings window that now am getting.

The screen resolution utility gives only 1024x768
How can I change it to 1440x900 - Is this safe?

---

### Post by taurus on 2008-03-08
What if you edit /etc/X11/xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```
and add "1440x900" in front of other resolutions in there?  Would it give you the wide screen?

Don't forget to either reboot or restart X server again after you've made changes to /etc/X11/xorg.conf, <Ctrl><Alt>Backspace.

---

### Post by BenPadman on 2008-03-08
I added 1440x900 as shown below and restarted comp. But the resolution am getting is still the same.  1024x768
_______________________________________________
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
_________________________________________________________


When I gave command > gksudo gedit /etc/X11/xorg.conf
I got an info like this

(gedit:6033): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
______________________________________________________

I don't know what this indicates.

---

### Post by taurus on 2008-03-08
Try looking in System -> Preferences -> Screen Resolution and see if you can change it from there.

p.s.  That is just a warning message when you run gedit so don't worry about it.

---

### Post by BenPadman on 2008-03-08
Yes I am trying to change restn from there only -  System -> Preferences -> Screen Resolution

But it still shows only the 3 prev resltns. "1024x768" "800x600" "640x480"

---

### Post by taurus on 2008-03-08
And you did install the nvidia restricted driver for your graphic card?

---

### Post by BenPadman on 2008-03-08
I have installed the following, 

nvidia-glx-new
nvidia-kernel-common

I don't know whether this includes nvidia restricted driver


Synaptic shows an installed item - restricted manager - but it does not indicate whether it is part of NVidia

But the info given is

Restricted Manager provides a Gnome user interface for configuring non-free hardware drivers, such as the Nvidia and ATI fglrx X.org and various Wireless LAN kernel modules.

---

### Post by taurus on 2008-03-08
Which _Driver_ does your /etc/X11/xorg.conf use?

```
cat /etc/X11/xorg.conf
```

---

### Post by BenPadman on 2008-03-08
When I gave the command I got the following
>cat /etc/X11/xorg.conf

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:2:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection
____________________________________________

Is this shows NVidia is not installed? or not properly configured?
But Synaptic shows  - nvidia-glx-new and nvidia-kernel-common is installed.

Thank you very much for the continued support.

---

### Post by taurus on 2008-03-09
Look in System -> Administration -> Restricted Drivers Manager and see if it is really installed.  And if it is, blue icon, then edit /etc/X11/xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```
and change the Driver from vesa to nvidia.

```

Driver "nvidia"

```
Save it and close down gedit editing window.  Now, restart X server and see what happens with <Ctrl><Alt>Backspace.

---

### Post by EXCiD3 on 2008-03-09
If you have the nvidia driver installed correctly, you can run ```
sudo nvidia-xconfig
``` in terminal to have it automatically configure the xorg for you.

---

### Post by BenPadman on 2008-03-09
Ok I checked in the System -> Administration -> Restricted Drivers Manager and it showed a red indicator and I tried to enable it. It went to download and install. After installing the driver it asked to restart the machine.

Gone - Fail to load X.

and I reconfigured X by sudo dpkg-reconfigure -phigh xserver-xorg [ learning things :) ]
__________________________________

The error msg I got is 

Error : API mismatch : the NVIDIA Kernel module has the version 1.0-9755, but this X module has the version 1.0-9631. Please make sure that the Kernel module and all NVIDIA driver components have the same version.
__________________________________

Then I tried 
dpkg --list | grep -i 'nvidia'

It gave the info

ii  nvidia-glx  1.0.9631+2.6.20.6-16.30  NVIDIA binary XFree86 4.x/X.Org driver
rc  nvidia-glx-new 1.0.9755+2.6.20.6-16.30   NVIDIA binary XFree86 4.x/X.Org 'new' driver
ii  nvidia-kernel-common 20051028+1ubuntu7  NVIDIA binary kernel module common files
___________________________________________

My Linux version is 2.6.20.15 generic.

Please help to install NVidia driver properly.

Thanks a lot

---

### Post by taurus on 2008-03-09
Sounds like you have two different versions of nvidia driver on your machine.  I would edit /etc/X11/xorg.conf and change the Driver back to vesa again.  Then, go into synaptic and remove all the nvidia packages.  Then, check with System -> Administration -> Restricted Drivers Manager and make sure to uninstall nvidia from there too.  Then, reboot your machine.

Now, install nvidia driver for your graphic card from System -> Administration -> Restricted Drivers Manager.

---

### Post by BenPadman on 2008-03-09
Oh this time I messed up everything I uninstalled Nvidia drivers and now I am not getting desktop.

I am getting login screen and can type usr name and passwd and getting only blank golden screen nothing after that.

This is from Fedora desktop.

I ddnt noted down which all things I uninstalled, I think I uninstalled restricted drivers too..

I am trying to reinstall it....

---

### Post by fisfia on 2008-03-09
> **taurus said:**
> Look in System -> Administration -> Restricted Drivers Manager and see if it is really installed.  And if it is, blue icon, then edit /etc/X11/xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```
and change the Driver from vesa to nvidia.

```

Driver "nvidia"

```
Save it and close down gedit editing window.  Now, restart X server and see what happens with <Ctrl><Alt>Backspace.

I have the same problem as in this thread. But when I look to replace vesa to nvidia there is no such thing as "Driver" in my /etc/X11/xorg.conf should I simply add it as a row? Or what to do?

---

### Post by BenPadman on 2008-03-09
Its not recovering...... Still desktop is not loading..

I tried installing Nautilus, Gnome but it feel am doing things with wild guesses.....

I thought to update by 

>sudo  apt-get update

But I don't want to miss the big opportunity to locate root cause of the problem.

Please help what are the things that needed to load desktop?
What all things I need to reinstall?

Thanks for your patience and valuable support.

---

### Post by BenPadman on 2008-03-11
I did it...

I got back my desktop after trying many things...

I reinstalled..

1. xorg-driver-fglrx         -   sudo apt-get install xorg-driver-fglrx
2. restricted-manager    -   sudo apt-get install restricted-manager

 but i couldn't get back desktop.

Then I installed GNome - sudo apt-get install gnome

This time I got back Desktop :)
________________________________________________________

Then I installed packages using Synaptic

linux-restricted-modules-2.6.20-16-generic (2.6.20.6-16.30)
xserver-xorg-video-nv (1:2.0.0-0ubuntu3)
________________________________________________________

After that I installed nvidia driver using restricted manager

But this time again X crashed and I reconfigured using sudo dpkg-reconfigure -phigh xserver-xorg

In the Synaptic it was listed - [COLOR="Blue"]nvidia-glx[/COLOR] which I uninstalled and installed 

nvidia-glx-new
nvidia-kernel-common

This time I gave  -  [COLOR="Blue"]sudo nvidia-glx-config enable[/COLOR]  - to  enable the driver.

and I got the info - 
----------------------------------------------------------------------
Error: your X configuration has been altered. This script cannot proceed automatically. If you believe that thisnot correct, you can update the md5sum entry executing the following command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
-----------------------------------------------------------------------
I gave > md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum

and I got nvidia configured 

But I got only "1024x768" "800x600" "640x480"

and I added "1440x900" using

> gksudo gedit /etc/X11/xorg.conf

[COLOR="Blue"]and at last I got  "1440x900" resolution.[/COLOR]
_______________________________________

Though I got "1440x900" the refresh rate I am getting is only 50. 55. and 56

But the manufacturer recommends 60 Hz

[COLOR="Blue"]Please help to get the refresh rate of 60Hz.[/COLOR]

**[COLOR="Blue"]Thanks a lot Taurus, You helped much to resolve this issue. I appreciate your help.[/COLOR]** :)

---

### Post by Zorael on 2008-03-11
The kernel/driver mismatch can be fixed by **purging**/**completely removing** the driver package. The error (to my knowledge) occurs when you've installed a new driver, and then you revert to an older one.

It doesn't remove the nvidia kernel, and the older driver doesn't overwrite it as it's of a higher version.

The solution is to pick **completely remove** in Synaptic, or **purge** in Adept Manager. Or, for those console-inclined:
```
$ sudo apt-get remove --purge nvidia-glx*
```

**Then** reinstall.

---

### Post by BenPadman on 2008-03-14
At last I got 1440x900 resolution with 60Hz refresh rate. I reinstalled Nvidia driver using Envy.

But it still shows some problem. (I am not sure whether its really a problem)

1. See the attachments - I am getting 1440x900 with 60Hz using Nvidia X Server settings, whereas Ubuntu screen resolution utility gives only 50, 55, 56Hzs. Why refresh rate is not changing in Ubuntu screen resolution utility?

2. Monitor is detecting as ViewSonic VA1912w-4 (CRT-1) but it is LCD. Is (CRT-1) just a code or it detecting only as CRT monitor?
   
3. After maximizing windows it is not possible to close (using X button), minimize or maximize it. It can be done only by right clicking on task bar area. Prev I have changed desktop effects, but I reverted back the changes.
________________________________________________

---

