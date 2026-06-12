---
title: "What's wrong with my ATI Radeon HD 3470 driver on Lucid Lynx?"
date: 2010-05-04
forum: Hardware
---

### Post by lion9 on 2010-05-04
After first boot of Licud ```
glxinfo
``` shows me that the built-in Mesa driver is currently installed.

I install the ATI Catalyst&#8482; Display Driver 10.04 downloaded from the official site ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English")) (I use the automatic installation). Then I configure the newly installed driver ```
sudo aticonfig --initial -f
``` and reboot.

Installation of the driver - log file.

```
fglrx-install.log

Creating symlink /var/lib/dkms/fglrx/8.723/source ->
 * * * * * * * * /usr/src/fglrx-8.723

DKMS: add Completed.

Kernel preparation unnecessary for this kernel. *Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.723/build; sh make.sh --nohints --uname_r=2.6.32-21-generic --norootcheck........
cleaning build area....

DKMS: build Completed.

fglrx.ko:
Running module version sanity check.
 - Original module
 * - No original module exists within this kernel
 - Installation
 * - Installing to /lib/modules/2.6.32-21-generic/updates/dkms/

depmod.......

DKMS: install Completed.
```

After installation of the driver there is no reaction for
```
glxinfo | grep OpenGL
```

the operation in the terminal seems to be suspended

```
fgl_glxgears
Using GLX_SGIX_pbuffer
```

the same problem - operation is suspended  


```
LIBGL_DEBUG=verbose glxinfo | grep render

libGL: XF86DRIGetClientDriverName: 8.72.5 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/tls/fglrx_dri.so
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.72.5 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/tls/fglrx_dri.so
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 5, (OK)
ukiOpenByBusid: ukiOpenMinor returns 5
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
```

operation is suspended again



My Xorg:

```
cat /etc/X11/xorg.conf

[spoiler]Section "ServerLayout"
	Identifier * * "aticonfig Layout"
	Screen * * *0 *"aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier * "aticonfig-Monitor[0]-0"
	Option	 * *"VendorName" "ATI Proprietary Driver"
	Option	 * *"ModelName" "Generic Autodetecting Monitor"
	Option	 * *"DPMS" "true"
EndSection

Section "Device"
	Identifier *"aticonfig-Device[0]-0"
	Driver * * *"fglrx"
	BusID * * * "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device * * "aticonfig-Device[0]-0"
	Monitor * *"aticonfig-Monitor[0]-0"
	DefaultDepth * * 24
	SubSection "Display"
		Viewport * 0 0
		Depth * * 24
	EndSubSection
EndSection

```

What may be the problem? I am trying to launch Nexuiz to check up if the driver works properly. The game doesn't run neither with ATI Catalyst&#8482; Display Driver 10.04, nor with the driver installed from System/Administration/Hardware Drivers GUI.

---

### Post by villiansv on 2010-05-04
Same problem with an HD3450 card in an Asus laptop.

---

### Post by johntuxman on 2010-05-08
I have the ATI Radeon Mobility HD 3470 in the Toshiba A350 laptop, my graphics work apart from the Open GL drivers which is some what annoying...

Is there a fix for this???

---

### Post by jrichter on 2010-05-18
I had similar problems with my Radeon HD 3450.  I could not get the proprietary driver to load OpenGL at first.  I followed this guide, [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD) then reinstalled the proprietary driver and for some reason it found OpenGL.  My minimize and maximize was taking forever, so I found a thread that said to do this:
```
sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE
```

That fixed my minimize and maximize problems.  Now my only problem is with suspend/hibernate and resuming from either.  It looks like the computer wakes up, but the screen (even backlight) never comes on.  I cant even blind type to shut the system down.  Or use mapped keys to restart x.

Here is my xorg.conf file
```


Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	BusID       "PCI:1:0:0"
	Driver	"fglrx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection


```

---

### Post by crixdaz on 2010-08-06
I have the same video card (ATI HD 3470) and the first thing after i installed[COLOR=red][COLOR=Black]ubuntu[/COLOR][/COLOR] 10.04 it's to install the official [LEFT][COLOR=Black]ati[/COLOR] drivers [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&#9001;=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.32&lang=English"). I try some 3D applications (of[COLOR=Black] compiz[/COLOR] ) and it's all perfect. The problem it's when i suspend (i not try to hibernate yet), at the second or third time i suspend my laptop it don't "wake". I try to search some solution, but finally i abandon and i[COLOR=red] [COLOR=Black]uninstall[/COLOR][/COLOR] the drivers (i use suspend a lot), but for my surprise all the 3D applications still working!!!.
[/LEFT]
 
Firstly i installed the drivers because in older versions of[COLOR=red] [COLOR=Black]ubuntu[/COLOR][/COLOR], the 3D applications don't work fine. Now i can use them and there's no problem to suspend my laptop every time.  So I have an fully operative[COLOR=red] [COLOR=Black]ubuntu[/COLOR][/COLOR] without drivers, thanks to the improvement of the[COLOR=green] [COLOR=Black]standard[/COLOR][/COLOR] drivers of[COLOR=red][COLOR=Black] ubuntu[/COLOR][/COLOR]. 

You can prove to use your[COLOR=red] [COLOR=Black]ubuntu[/COLOR][/COLOR] without drivers and tell.

Luck!!

---

