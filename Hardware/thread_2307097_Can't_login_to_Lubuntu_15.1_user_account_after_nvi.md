---
title: "Can't login to Lubuntu 15.1 user account after nvidia driver installation."
date: 2015-12-21
forum: Hardware
---

### Post by cobalt2 on 2015-12-21
[COLOR=#111111][FONT=Ubuntu]I installed Nvidia driver version 352.63 (tested), from Software & Updates, for a Nvidia Geforce GTX 750 graphics card. Now whenever I log into the desktop, the screen turns black and the login screen reappears. When logging in as root, the desktop environment loads normally.


[/FONT][/COLOR]

---

### Post by Bashing-om on 2015-12-22
cobalt2; Hello ;

Can you activate a console at the log in screen ( ctl+alt+F1) ?
Login to the system here at the console.
What results when removing the proprietary graphic's driver, reverting to nouveau :
```

sudo apt-get --purge remove nvidia*

```
Re-boot and advise on status, and we consider to now install the Nvidia proprietary driver. Like maybe the 346 version ?

[INDENT][INDENT]and the kernel says to the graphic's card
[INDENT][INDENT][INDENT]"what are you talking about" ?[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by cobalt2 on 2016-01-19
After removing Nvidia and reinstalling Nouveau, the system was working correctly. The Nvidia driver failed to install because there was inadequate space on root to complete the installation. 

So I resized the root lv, from 5 GB to 26 GB. Then I uninstalled nouveau, and tried installing Nvidia. Now when I start Lubuntu, F7 console is showing a blinking dash. When switching to F1 console, there is an Ubuntu 15.10 login prompt, where I'm able to login.

---

### Post by Bashing-om on 2016-01-19
cobalt2; Welp ....


Let's get some info so we know what we are working with.
In that console one does not have the amenities of a GUI terminal - copy and paste and so on - .
Let's install a tool to upload requested info to our pastebin site,
In that F1 console, execute terminal command:
```

sudo apt-get install pastebinit

```

Now we get access to some info from your system:
execute:
```

lspci -vnn | grep -i VGA | pasatebinit
sudo lshw -C display | pastebinit
dpkg -l | grep -i nvidia | pastebinit
pastebinit /var/log/Xorg.0.log

```
The result is a URL back in terminal, pass these links back here and we access the files .
That tells us the hardware, if a driver is loaded,  what nvidia drivers are installed, and what is going on in the X layer.

Maybe from this we get an idea of what is not going on and why.

[INDENT][INDENT]cause and effect
[/INDENT][/INDENT]

---

### Post by cobalt2 on 2016-01-19
This is an image of the terminal output, when starting Lubuntu verbosely:

[IMG]https://drive.google.com/open?id=0B2ApMAJaChR9WGpCcnBOc0lMRTg[/IMG]

---

### Post by Bashing-om on 2016-01-19
cobalt2; Hey;

Nope your image did not take .

pastebin will work for the benefit of all .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by cobalt2 on 2016-01-20
Hello bashing-om. Thank you for the quick response. 

Pastebin URLs:
[paste.ubuntu.com/14581068]("http://paste.ubuntu.com/14581068")
[paste.ubuntu.com/14581066]("http://paste.ubuntu.com/14581066")
[paste.ubuntu.com/14581060]("http://paste.ubuntu.com/14581060")

I await your reply.

---

### Post by Bashing-om on 2016-01-20
cobalt2; Hummmm ...

Things in the log report that I truly do not understand:
The Hardware is found and identified:
"(--) PCI:*(0:1:0:0) 10de:1381:19da:288b rev 162, "

The GPU is found and recognized:
" 27.303] (II) NVIDIA: Allocated GPU:0 (GPU-a337d40c-5921-6cb6-647d-f36d7574a7a8) @ >> 27.303] (II) NVIDIA:     PCI:0000:01:00.0  >>  27.312] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0"

System is happy to build the Nvidia driver:
"27.331] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116) >> 27.332] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 750 (GM107-A) at PCI:1:0:0 (GPU-0)
27.348] (**) NVIDIA(0):     device JRY DIGITAL (DFP-0) (Using EDID frequencies has been enabled on all display devices.)
 27.454] (II) NVIDIA(0): [DRI2] Setup complete
27.454] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia


Now here I do not understand - perhaps others can advise - what this means in respect to 'DFP-0' 
> 
27.966] (II) NVIDIA: Freed GPU:0 (GPU-a337d40c-5921-6cb6-647d-f36d7574a7a8) @
[    27.966] (II) NVIDIA:     PCI:0000:01:00.0
[    27.987] (II) NVIDIA(GPU-0): Deleting GPU-0
[    28.077] (II) Server terminated successfully (0). Closing log file.

HUH ??

NOR am I sure how this applies :
"26.827] (WW) Warning, couldn't open module nouveau"
As we are running on the Nvidia driver, do we even care about the state of nouveau drivers ??
-----------------------

The Nvidia module is loaded :
" configuration: driver=nvidia latency=0 "
And we have but only the Nvidia graphic's card to contend with:
"01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX 750] [10de:1381]"
_________________

I am unable at this time to put my finger on a problem.
Please restate the issue with the thought that we are looking at a config issue in the desktop ???
> 
Now when I start Lubuntu, F7 console is showing a blinking dash.

such that maybe the desktop is not even started ??? Not enough info at this time to make a determination on what is not taking place.
Or maybe something in nouveau needs to be enabled ????

Confirm that this is a standard install of (l)ubuntu and we start investigating the desktop . But, again, I could be out in left field as I do not know the relationships between the reported GPU:0 and device JRY DIGITAL (DFP-0) !

[INDENT][INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by blm-ubunet on 2016-01-20
AFAIK JRY are a flat panel display manufacturer..
They also make small LCD panels (flat cable LVDS) for Arm SBC etc

The nVidia driver uses DFP-x as the name/label for the digital ports (DVI-D, HDMI, DP).

The driver appears to setup video mode "1680 x 1050" on DFP-0 (JRY panel) & then receive a power off signal...

The TK820 is a HTPC wireless keyboard; mine has worked faultlessly with ubuntu 14.04.
<fn><del> keystroke on this keyboard is powerdown/suspend keycode..

HTH

---

### Post by cobalt2 on 2016-01-20
Link to the screenshot of the F1 console at startup:
[https://drive.google.com/open?id=0B2ApMAJaChR9WGpCcnBOc0lMRTg](https://drive.google.com/open?id=0B2ApMAJaChR9WGpCcnBOc0lMRTg)

bashing-om:

I used the alternative install, but it don't think that matters. I installed lxde, whereas the original window manager and desktop environment was lubuntu-desktop. Why would you say that Nouveau needs to be enabled, if I'm using Nvidia instead?

blm-ubunet:
JRY is the name assigned to the display by the kernel.

---

### Post by cobalt2 on 2016-01-20
Reinstalled Lubuntu desktop environ: ```
apt-get install lubuntu-desktop
```.

Nouveau was reinstalled as part of this package, so I typed ```
apt-get remove xserver-xorg-video-nouveau
``` to remove it. Terminal responds: 

```
The following packages will be removed:
lubuntu-desktop lubuntu-core xserver-xorg-video-all xserver-xorg-video-nouveau
```

Apparently Nouveau is intertwined with the Lubuntu desktop environ, so that removing Nouveau also removes the Lubuntu desktop environ as well.

Since it is impossible to remove Nouveau without removing the Lubuntu desktop environ, I blacklisted it in blacklist.conf.

```
sudo nano /etc/modprobe.d/blacklist.conf
```
Added entry for blacklisting Nouveau:
```
blacklist xserver-xorg-video-nouveau
```
Ctrl + O Enter to save.

```
Upon restarting, I encounter:
Starting Update UTMP about System Runlevel Changes...
[OK] Stated Update UTMP about System Runlevel Changes.
```

Followed by a continuously blinking dash.

---

### Post by Yellow Pasque on 2016-01-21
Personally, I would try a newer driver first. The 352.63 officially supports your card, but maybe a newer driver would help:
```
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-361
```

> Since it is impossible to remove Nouveau without removing the Lubuntu desktop environ, I blacklisted it in blacklist.conf.

The nvidia package will blacklist nouveau for you (look in /etc/modprobe.d to see the file it creates).

---

### Post by cobalt2 on 2016-01-28
Even removing Nvidia and going back to Nouveau didn't work. What worked for me: reinstalling the operating system and installing Nvidia version 358. I went with version 358, because of a notice on Launchpad for version 361 that reads, "Copied from Ubuntu Wily in     [Staging (DO NOT USE)]("https://launchpad.net/%7Emamarley/+archive/ubuntu/staging")." Now my graphics are working flawlessly. Reinstalling the OS also solved a problem I discussed in this thread: [Could not open X display" Error When Launching Sudo GUI Program From Terminal]("http://ubuntuforums.org/showthread.php?t=2303650").

Much thanks for everyone who offered their support.

---

