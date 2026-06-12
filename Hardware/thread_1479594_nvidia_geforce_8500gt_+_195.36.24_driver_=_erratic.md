---
title: "nvidia geforce 8500gt + 195.36.24 driver = erratic freezing"
date: 2010-05-10
forum: Hardware
---

### Post by /bee/ on 2010-05-10
Problems I have encountered:
1. No warning, the system becomes unresponsive.
2. Screen pixelates and then becomes unresponsive.
3. Screen pixelates, mouse movement is still responsive (but very sluggish) and then becomes unresponsive.
4. Screen pixelates and shortly thereafter goes black, logs me out and kicks me back to the gnome login (currently set to skip during bootup)
5. While playing FLAC and MP3 files in Rhythmbox it'll stutter and sound like a broken record playing the same 3 or 4 seconds over and over and over.

Sometimes it will work fine for 24-36 hours and then become unresponsive.  Other times it will only work for a minute after logging in.

When it becomes unresponsive, my only option is to turn it off via the power button on the tower.
Occasionally, after turning it off and letting the drives spin down it won't get past the ubuntu welcome screen with the 5 white/red dots.  Instead it will just cycle through red and then white until I turn it off and back on again.

There doesn't seem to be anything in particular that triggers it.  It doesn't happen in conjunction with anything I can pinpoint.  I've had it freeze when I was simply using gedit, but then I've had it freeze with Google Earth, Rhythmbox, Chrome, Brasero, Deluge, jDownloader, Empathy IM, CheckGmail, and GIMP open.

Specs:
GIGABYTE GA-MA770T-UD3P AM3 AMD 770 ATX AMD motherboard
AMD Phenom II X2 550 Black Edition (unlocked 3rd and 4th cores, now recognized as a Phenom II X4 B50)
4 GB G.Skill DDR3 1333MHz ram
NVIDIA GeForce 8500GT

I used ubuntu in the early hardy heron days and thought I could figure this out on my own this time around.  Boy was I wrong.


I burned the alternate iso of 10.04 and installed.  Afterwards, I went into System>Admin>Hardware Drivers and selected the recommended current driver for my ancient gfx card.

Then the problems started.

Tried using an older driver listed in Hardware Drivers.  No luck.

Then I found a suggested driver (185.18.31) for someone having similar problems.  Not quite the same, but I figured I would give it a shot.  No dice.

Then went and checked NVIDIA's site and found that they have listed 195.36.24, which hardware drivers didn't find.

CTRL+ALT+F1, gdm stop, installed 195.

However, now when I open the Hardware Drivers dialog it tells me that 173 is currently in use.

I've read through numerous articles dealing with nvidia driver issues.  I'm in well over my head and any help would be greatly appreciated.

-bee

---

### Post by 23dornot23d on 2010-05-10
You could try this out ,,, [http://ubuntuforums.org/showthread.php?t=990978&page=129](http://ubuntuforums.org/showthread.php?t=990978&page=129)

Check the first page out ....... thats if you haven't seen it already ......

I left my response there too and got mine running .....

I also tend to remove GDM and use KDM to start up ...... it gives me less problems ........

and boots fast too ....

---

### Post by /bee/ on 2010-05-10
Thanks, I'll try that out.

Doesn't work for me.  Same problems.

---

### Post by 23dornot23d on 2010-05-10
Ok sorry it did not help .....

Do you get any clues from the log files ...... xorg.0.log

Menu - Administration - Logfile viewer

Mine is in my footer ...... if you want to check against it for any peculiarities .....

---

### Post by /bee/ on 2010-05-10
The very end is perplexing...  it isn't loading glx or the nvidia driver?

(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
dlopen: /usr/lib/xorg/modules/extensions/libglx.so: file too short
(EE) Failed to load /usr/lib/xorg/modules/extensions/libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)


&&&&


(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
dlopen: /usr/lib/xorg/modules/drivers/nvidia_drv.so: file too short
(EE) Failed to load /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.




Xorg.0.log
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux bee-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=a39b7aa3-a9e0-45fe-9479-24e744de6ce4 ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 10 22:35:22 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0421:3842:c740 nVidia Corporation G86 [GeForce 8500 GT] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
dlopen: /usr/lib/xorg/modules/extensions/libglx.so: file too short
(EE) Failed to load /usr/lib/xorg/modules/extensions/libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
dlopen: /usr/lib/xorg/modules/drivers/nvidia_drv.so: file too short
(EE) Failed to load /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

---

### Post by 23dornot23d on 2010-05-11
So the Nvidia-glx .....file is it loaded in Synaptic ......

Mine looks like this as an example although the 185.18.36 is there I am running the 185.18.15 ........ not sure if it makes a difference or not .......
as soon as I got mine to work ....... I stuck there .....


[IMG]http://i42.tinypic.com/20fb2tj.jpg[/IMG]

Yours is the **195.36.24** ....... check and see if all the files have loaded .....

You are using a later kernel  than me too ... the 22 ..... I am still on the 21 .... don't know how much difference this will make ...  

Also try a search like this in google there are a few results one may help  .... [nvidia geforce 8500gt lucid EnvyNG solved]("http://www.google.com/search?hl=en&q=nvidia+geforce+8500gt+lucid+EnvyNG+solved&aq=f&aqi=&aql=&oq=&gs_rfai=")

---

### Post by /bee/ on 2010-05-11
Thank you very much for your help so far.  After reading through a bunch of those links my computer appears much more stable.

What's the terminal command(s) to see what is currently being used?


My new Xorg.0.log looks like this...  There's a LOT in there now:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux bee-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=a39b7aa3-a9e0-45fe-9479-24e744de6ce4 ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 11 12:03:46 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0421:3842:c740 nVidia Corporation G86 [GeForce 8500 GT] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
dlopen: /usr/lib/xorg/modules/extensions/libglx.so: file too short
(EE) Failed to load /usr/lib/xorg/modules/extensions/libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched nouveau as autoconfigured driver 0
(==) Matched nv as autoconfigured driver 1
(==) Matched vesa as autoconfigured driver 2
(==) Matched fbdev as autoconfigured driver 3
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nouveau"
(WW) Warning, couldn't open module nouveau
(II) UnloadModule: "nouveau"
(EE) Failed to load module "nouveau" (module does not exist, 0)
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.7.3.901, module version = 2.1.15
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
(II) NV: driver for NVIDIA chipsets:  RIVA 128,  RIVA TNT,  RIVA TNT2,
	 RIVA TNT2 Ultra,  Unknown TNT2,  Vanta,  RIVA TNT2 Model 64,
	 GeForce 6800 Ultra,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 XE,  GeForce 6800 XT,  GeForce 6800 GT,
	 GeForce 6800 GT,  GeForce 6800 GS,  GeForce 6800 XT,
	 Quadro FX 4000,  GeForce 7800 GTX,  GeForce 7800 GTX,
	 GeForce 7800 GT,  GeForce 7800 GS,  GeForce 7800 SLI,
	 GeForce Go 7800,  GeForce Go 7800 GTX,  Quadro FX 4500,
	 Aladdin TNT2,  GeForce 6800 GS,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 XT,  GeForce Go 6800,  GeForce Go 6800 Ultra,
	 Quadro FX Go1400,  Quadro FX 3450/4000 SDI,  Quadro FX 1400,
	 GeForce 256,  GeForce DDR,  Quadro,  GeForce2 MX/MX 400,
	 GeForce2 MX 100/200,  GeForce2 Go,  Quadro2 MXR/EX/Go,
	 GeForce 6600 GT,  GeForce 6600,  GeForce 6600 LE,  GeForce 6600 VE,
	 GeForce Go 6600,  GeForce 6610 XL,  GeForce Go 6600 TE/6200 TE,
	 GeForce 6700 XL,  GeForce Go 6600,  GeForce Go 6600 GT,
	 Quadro NVS 440,  Quadro FX 550,  Quadro FX 550,  Quadro FX 540,
	 GeForce 6200,  GeForce2 GTS,  GeForce2 Ti,  GeForce2 Ultra,
	 Quadro2 Pro,  GeForce 6500,  GeForce 6200 TurboCache(TM),
	 GeForce 6200SE TurboCache(TM),  GeForce 6200 LE,  GeForce Go 6200,
	 Quadro NVS 285,  GeForce Go 6400,  GeForce Go 6200,
	 GeForce Go 6400,  GeForce 6250,  GeForce 7100 GS,  GeForce4 MX 460,
	 GeForce4 MX 440,  GeForce4 MX 420,  GeForce4 MX 440-SE,
	 GeForce4 440 Go,  GeForce4 420 Go,  GeForce4 420 Go 32M,
	 GeForce4 460 Go,  Quadro4 550 XGL,  GeForce4 440 Go 64M,
	 Quadro NVS,  Quadro4 500 GoGL,  GeForce4 410 Go 16M,
	 GeForce4 MX 440 with AGP8X,  GeForce4 MX 440SE with AGP8X,
	 GeForce4 MX 420 with AGP8X,  GeForce4 MX 4000,  GeForce4 448 Go,
	 GeForce4 488 Go,  Quadro4 580 XGL,  Quadro4 NVS 280 SD,
	 Quadro4 380 XGL,  Quadro NVS 50 PCI,  GeForce4 448 Go,
	 GeForce 8800 GTX,  GeForce 8800 GTS,  GeForce 8800 Ultra,
	 Quadro FX 5600,  Quadro FX 4600,  GeForce2 Integrated GPU,
	 GeForce 7350 LE,  GeForce 7300 LE,  GeForce 7300 SE,
	 GeForce Go 7200,  GeForce Go 7300,  GeForce Go 7400,
	 GeForce Go 7400 GS,  Quadro NVS 110M,  Quadro NVS 120M,
	 Quadro FX 350M,  GeForce 7500 LE,  Quadro FX 350,  GeForce 7300 GS,
	 GeForce4 MX Integrated GPU,  GeForce3,  GeForce3 Ti 200,
	 GeForce3 Ti 500,  Quadro DCC,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 GT,  GeForce 6800 XT,  GeForce 6200,
	 GeForce 6200 A-LE,  GeForce 6150,  GeForce 6150 LE,  GeForce 6100,
	 GeForce Go 6150,  Quadro NVS 210S / NVIDIA GeForce 6150LE,
	 GeForce Go 6100,  GeForce4 Ti 4600,  GeForce4 Ti 4400,
	 GeForce4 Ti 4200,  Quadro4 900 XGL,  Quadro4 750 XGL,
	 Quadro4 700 XGL,  GeForce4 Ti 4800,  GeForce4 Ti 4200 with AGP8X,
	 GeForce4 Ti 4800 SE,  GeForce4 4200 Go,  Quadro4 980 XGL,
	 Quadro4 780 XGL,  Quadro4 700 GoGL,  GeForce 7900 GTX,
	 GeForce 7900 GT,  GeForce 7900 GS,  GeForce 7950 GX2,
	 GeForce 7950 GX2,  GeForce 7950 GT},  GeForce Go 7950 GTX,
	 GeForce Go 7900 GS,  GeForce Go 7900 GTX,  Quadro FX 2500M,
	 Quadro FX 1500M,  Quadro FX 5500,  Quadro FX 3500,  Quadro FX 1500,
	 Quadro FX 4500 X2,  GeForce FX 5800 Ultra,  GeForce FX 5800,
	 Quadro FX 2000,  Quadro FX 1000,  GeForce FX 5600 Ultra,
	 GeForce FX 5600,  GeForce FX 560T,  GeForce FX Go5600,
	 GeForce FX Go5650,  Quadro FX Go700,  GeForce FX 5200,
	 GeForce FX 5200 Ultra,  GeForce FX 5200,  GeForce FX 5200LE,
	 GeForce FX Go5200,  GeForce FX Go5250,  GeForce FX 5500,
	 GeForce FX 5100,  GeForce FX Go5200 32M/64M,  Quadro NVS 55/280 PCI,
	 Quadro FX 500/600 PCI,  GeForce FX Go53xx Series,
	 GeForce FX Go5100,  GeForce FX 5900 Ultra,  GeForce FX 5900,
	 GeForce FX 590T,  GeForce FX 5950 Ultra,  GeForce FX 5900ZT,
	 Quadro FX 3000,  Quadro FX 700,  GeForce FX 5700 Ultra,
	 GeForce FX 5700,  GeForce FX 5700LE,  GeForce FX 5700VE,
	 GeForce FX Go5700,  GeForce FX Go5700,  Quadro FX Go1000,
	 Quadro FX 1100,  GeForce 7650 GS,  GeForce 7600 GT,
	 GeForce 7600 GS,  GeForce 7300 GT,  GeForce 7600 LE,
	 GeForce 7300 GT,  GeForce Go 7700,  GeForce Go 7600,
	 GeForce Go 7600 GT},  Quadro NVS 300M,  GeForce Go 7900 SE,
	 Quadro FX 550M,  Quadro FX 560,  GeForce 6150SE,
	 GeForce 6100 nForce 405,  GeForce 6100 nForce 400,
	 GeForce 6100 nForce 420,  GeForce 8600 GTS,  GeForce 8600 GT,
	 GeForce 8600 GT,  GeForce 8600 GS,  GeForce 8400 GS,
	 GeForce 9500M GS,  GeForce 8600M GT,  GeForce 9650M GS,
	 GeForce 8700M GT,  Quadro FX 370,  Quadro NVS 320M,  Quadro FX 570M,
	 Quadro FX 1600M,  Quadro FX 570,  Quadro FX 1700,  GeForce 8400 SE,
	 GeForce 8500 GT,  GeForce 8400 GS,  GeForce 8300 GS,
	 GeForce 8400 GS,  GeForce 8600M GS,  GeForce 8400M GT,
	 GeForce 8400M GS,  GeForce 8400M G,  Quadro NVS 140M,
	 Quadro NVS 130M,  Quadro NVS 135M,  GeForce 9400 GT,
	 Quadro FX 360M,  GeForce 9300M G,  Quadro NVS 290,  GeForce GTX 295,
	 GeForce GTX 280,  GeForce GTX 260,  GeForce GTX 285,  GeForce 7050,
	 GeForce 7025,  Quadro CX,  Quadro FX 5800,  Quadro FX 4800,
	 Quadro FX 3800,  GeForce 8800 GTS 512,  GeForce 9800 GT,
	 GeForce 8800 GT,  GeForce 9800 GX2,  GeForce 9800 GT,
	 GeForce 8800 GS,  GeForce 9800M GTX,  GeForce 8800M GTS,
	 GeForce 9800M GT,  GeForce 8800M GTX,  GeForce 8800 GS,
	 GeForce 9600 GSO,  GeForce 8800 GT,  GeForce 9800 GTX,
	 GeForce 9800 GTX+,  GeForce 9800 GT,  GeForce GTS 250,
	 GeForce 9800M GTX,  Quadro FX 3700,  Quadro FX 3600M,
	 Quadro FX 3700M,  GeForce 9600 GT,  GeForce 9600 GS,
	 GeForce 9600 GSO 512,  GeForce GT 130,  GeForce GT 140,
	 GeForce 9800M GTS,  GeForce 9700M GTS,  GeForce 9800M GS,
	 GeForce 9800M GTS,  Quadro FX 1800,  Quadro FX 2700M,
	 GeForce 9500 GT,  GeForce 9400 GT,  GeForce 9500 GT,
	 GeForce GT 120,  GeForce 9600M GT,  GeForce 9600M GS,
	 GeForce 9600M GT,  GeForce 9700M GT,  GeForce 9500M G,
	 GeForce 9650M GT,  GeForce 9500 GT,  Quadro FX 380,  Quadro FX 580,
	 Quadro FX 770M,  GeForce 9300 GE,  GeForce 9300 GS,
	 GeForce 8400 GS,  GeForce 9300M GS,  GeForce G100,
	 GeForce 9200M GS,  GeForce 9300M GS,  Quadro NVS 150M,
	 Quadro NVS 160M,  Quadro NVS 420,  Quadro FX 370 LP,
	 Quadro NVS 450,  Quadro NVS 295
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA  GeForce 8500 GT at 01@00:00:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(EE) open /dev/fb0: No such file or directory
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Console is VGA mode 0x3
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(==) NV(0): Using hardware cursor
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): MMIO registers mapped at 0x7f19bd46e000
(--) NV(0): Total video RAM: 256.0 MB
(--) NV(0):       BAR1 size: 256.0 MB
(--) NV(0):   Mapped memory: 255.0 MB
(II) NV(0): Linear framebuffer mapped at 0x7f19ad56e000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) NV(0): Connector map:
(--) NV(0):   Bus 0 -> DAC1
(--) NV(0):   Bus 0 -> SOR0
(--) NV(0):   Bus 1 -> DAC2
(--) NV(0): Load detection: 340
(II) NV(0): I2C bus "I2C0" initialized.
(II) NV(0): Output VGA1 has no monitor section
(II) NV(0): Output DVI0 has no monitor section
(II) NV(0): I2C bus "I2C1" initialized.
(II) NV(0): Output VGA2 has no monitor section
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0): I2C device "I2C0:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: GWY  Model: 6dd  Serial#: 9802
(II) NV(0): Year: 2005  Week: 25
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.638 redY: 0.353   greenX: 0.279 greenY: 0.604
(II) NV(0): blueX: 0.142 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 108.0 MHz   Image Size:  337 x 270 mm
(II) NV(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) NV(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) NV(0): Monitor name: FPD1765
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 80 kHz, PixClock max 140 MHz
(II) NV(0): Serial No: B56 50H 09802
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff001ef9dd064a260000
(II) NV(0): 	190f010368221b78ea5a65a35a479a24
(II) NV(0): 	115054afcf0081800101010101010101
(II) NV(0): 	010101010101302a009851002a403070
(II) NV(0): 	1300510e1100001e000000fc00465044
(II) NV(0): 	313736350a2020202020000000fd0038
(II) NV(0): 	4c1e500e000a202020202020000000ff
(II) NV(0): 	004235362035304820303938303200c2
(--) NV(0): Trying load detection on VGA1 ... found one!
(II) NV(0): EDID for output VGA1
(II) NV(0): Manufacturer: GWY  Model: 6dd  Serial#: 9802
(II) NV(0): Year: 2005  Week: 25
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.638 redY: 0.353   greenX: 0.279 greenY: 0.604
(II) NV(0): blueX: 0.142 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 108.0 MHz   Image Size:  337 x 270 mm
(II) NV(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) NV(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) NV(0): Monitor name: FPD1765
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 80 kHz, PixClock max 140 MHz
(II) NV(0): Serial No: B56 50H 09802
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff001ef9dd064a260000
(II) NV(0): 	190f010368221b78ea5a65a35a479a24
(II) NV(0): 	115054afcf0081800101010101010101
(II) NV(0): 	010101010101302a009851002a403070
(II) NV(0): 	1300510e1100001e000000fc00465044
(II) NV(0): 	313736350a2020202020000000fd0038
(II) NV(0): 	4c1e500e000a202020202020000000ff
(II) NV(0): 	004235362035304820303938303200c2
(II) NV(0): EDID vendor "GWY", prod id 1757
(II) NV(0): Using EDID range info for horizontal sync
(II) NV(0): Using EDID range info for vertical refresh
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): EDID vendor "GWY", prod id 1757
(II) NV(0): Printing probed modes for output VGA1
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): EDID for output DVI0
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0): I2C device "I2C1:ddc2" registered at address 0xA0.
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): EDID for output VGA2
(II) NV(0): Output VGA1 connected
(II) NV(0): Output DVI0 disconnected
(II) NV(0): Output VGA2 disconnected
(II) NV(0): Using exact sizes for initial modes
(II) NV(0): Output VGA1 using initial mode 1280x1024
(--) NV(0): Virtual size is 1280x1280 (pitch 1280)
(**) NV(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) NV(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NV(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NV(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NV(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NV(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) NV(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NV(0): Display dimensions: (340, 270) mm
(**) NV(0): DPI set to (95, 120)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.1
	ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(--) NV(0): 153.75 MB available for offscreen pixmaps
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(==) NV(0): DPMS enabled
(II) NV(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) NV(0): Setting screen physical size to 338 x 270
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) XKB: reuse xkmfile /var/lib/xkb/server-0C76CA335E924C2441A31FBFED02D59A89874CA6.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device HP HP Wireless Keyboard Kit (/dev/input/event3)
(**) HP HP Wireless Keyboard Kit: Applying InputClass "evdev keyboard catchall"
(**) HP HP Wireless Keyboard Kit: always reports core events
(**) HP HP Wireless Keyboard Kit: Device: "/dev/input/event3"
(II) HP HP Wireless Keyboard Kit: Found keys
(II) HP HP Wireless Keyboard Kit: Configuring as keyboard
(II) XINPUT: Adding extended input device "HP HP Wireless Keyboard Kit" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device HP HP Wireless Keyboard Kit (/dev/input/event4)
(**) HP HP Wireless Keyboard Kit: Applying InputClass "evdev pointer catchall"
(**) HP HP Wireless Keyboard Kit: Applying InputClass "evdev keyboard catchall"
(**) HP HP Wireless Keyboard Kit: always reports core events
(**) HP HP Wireless Keyboard Kit: Device: "/dev/input/event4"
(II) HP HP Wireless Keyboard Kit: Found 8 mouse buttons
(II) HP HP Wireless Keyboard Kit: Found scroll wheel(s)
(II) HP HP Wireless Keyboard Kit: Found relative axes
(II) HP HP Wireless Keyboard Kit: Found x and y relative axes
(II) HP HP Wireless Keyboard Kit: Found absolute axes
(II) HP HP Wireless Keyboard Kit: Found keys
(II) HP HP Wireless Keyboard Kit: Configuring as mouse
(II) HP HP Wireless Keyboard Kit: Configuring as keyboard
(**) HP HP Wireless Keyboard Kit: YAxisMapping: buttons 4 and 5
(**) HP HP Wireless Keyboard Kit: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "HP HP Wireless Keyboard Kit" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) HP HP Wireless Keyboard Kit: initialized for relative axes.
(WW) HP HP Wireless Keyboard Kit: ignoring absolute axes.
(II) config/udev: Adding input device HP HP Wireless Keyboard Kit (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device UVC Camera (046d:0990) (/dev/input/event5)
(**) UVC Camera (046d:0990): Applying InputClass "evdev keyboard catchall"
(**) UVC Camera (046d:0990): always reports core events
(**) UVC Camera (046d:0990): Device: "/dev/input/event5"
(II) UVC Camera (046d:0990): Found keys
(II) UVC Camera (046d:0990): Configuring as keyboard
(II) XINPUT: Adding extended input device "UVC Camera (046d:0990)" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: GWY  Model: 6dd  Serial#: 9802
(II) NV(0): Year: 2005  Week: 25
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.638 redY: 0.353   greenX: 0.279 greenY: 0.604
(II) NV(0): blueX: 0.142 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 108.0 MHz   Image Size:  337 x 270 mm
(II) NV(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) NV(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) NV(0): Monitor name: FPD1765
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 80 kHz, PixClock max 140 MHz
(II) NV(0): Serial No: B56 50H 09802
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff001ef9dd064a260000
(II) NV(0): 	190f010368221b78ea5a65a35a479a24
(II) NV(0): 	115054afcf0081800101010101010101
(II) NV(0): 	010101010101302a009851002a403070
(II) NV(0): 	1300510e1100001e000000fc00465044
(II) NV(0): 	313736350a2020202020000000fd0038
(II) NV(0): 	4c1e500e000a202020202020000000ff
(II) NV(0): 	004235362035304820303938303200c2
(--) NV(0): Trying load detection on VGA1 ... found one!
(II) NV(0): EDID vendor "GWY", prod id 1757
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): EDID vendor "GWY", prod id 1757
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: GWY  Model: 6dd  Serial#: 9802
(II) NV(0): Year: 2005  Week: 25
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.638 redY: 0.353   greenX: 0.279 greenY: 0.604
(II) NV(0): blueX: 0.142 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 108.0 MHz   Image Size:  337 x 270 mm
(II) NV(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) NV(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) NV(0): Monitor name: FPD1765
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 80 kHz, PixClock max 140 MHz
(II) NV(0): Serial No: B56 50H 09802
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff001ef9dd064a260000
(II) NV(0): 	190f010368221b78ea5a65a35a479a24
(II) NV(0): 	115054afcf0081800101010101010101
(II) NV(0): 	010101010101302a009851002a403070
(II) NV(0): 	1300510e1100001e000000fc00465044
(II) NV(0): 	313736350a2020202020000000fd0038
(II) NV(0): 	4c1e500e000a202020202020000000ff
(II) NV(0): 	004235362035304820303938303200c2
(--) NV(0): Trying load detection on VGA1 ... found one!
(II) NV(0): EDID vendor "GWY", prod id 1757
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): EDID vendor "GWY", prod id 1757
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: GWY  Model: 6dd  Serial#: 9802
(II) NV(0): Year: 2005  Week: 25
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.638 redY: 0.353   greenX: 0.279 greenY: 0.604
(II) NV(0): blueX: 0.142 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 108.0 MHz   Image Size:  337 x 270 mm
(II) NV(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) NV(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) NV(0): Monitor name: FPD1765
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 80 kHz, PixClock max 140 MHz
(II) NV(0): Serial No: B56 50H 09802
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff001ef9dd064a260000
(II) NV(0): 	190f010368221b78ea5a65a35a479a24
(II) NV(0): 	115054afcf0081800101010101010101
(II) NV(0): 	010101010101302a009851002a403070
(II) NV(0): 	1300510e1100001e000000fc00465044
(II) NV(0): 	313736350a2020202020000000fd0038
(II) NV(0): 	4c1e500e000a202020202020000000ff
(II) NV(0): 	004235362035304820303938303200c2
(--) NV(0): Trying load detection on VGA1 ... found one!
(II) NV(0): EDID vendor "GWY", prod id 1757
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): EDID vendor "GWY", prod id 1757
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: GWY  Model: 6dd  Serial#: 9802
(II) NV(0): Year: 2005  Week: 25
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max Image Size [cm]: horiz.: 34  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.638 redY: 0.353   greenX: 0.279 greenY: 0.604
(II) NV(0): blueX: 0.142 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 108.0 MHz   Image Size:  337 x 270 mm
(II) NV(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) NV(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) NV(0): Monitor name: FPD1765
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 80 kHz, PixClock max 140 MHz
(II) NV(0): Serial No: B56 50H 09802
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff001ef9dd064a260000
(II) NV(0): 	190f010368221b78ea5a65a35a479a24
(II) NV(0): 	115054afcf0081800101010101010101
(II) NV(0): 	010101010101302a009851002a403070
(II) NV(0): 	1300510e1100001e000000fc00465044
(II) NV(0): 	313736350a2020202020000000fd0038
(II) NV(0): 	4c1e500e000a202020202020000000ff
(II) NV(0): 	004235362035304820303938303200c2
(--) NV(0): Trying load detection on VGA1 ... found one!
(II) NV(0): EDID vendor "GWY", prod id 1757
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): EDID vendor "GWY", prod id 1757
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.

```




Edit: Now i can't run nvidia-xconfig from terminal.

and ldconfig reports this:
```
bee-desktop:~$ ldconfig
/sbin/ldconfig.real: File /usr/lib/libXvMCNVIDIA_dynamic.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libcuda.so is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libnvidia-tls.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libXvMCNVIDIA.so.195.36.24 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libOpenCL.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libnvidia-cfg.so is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libnvidia-cfg.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libOpenCL.so.1.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libGLcore.so.195.36.24 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libGL.so.195.36.24 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libnvidia-compiler.so.195.36.24 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libnvidia-compiler.so is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libGL.so is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libcuda.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libGLcore.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libvdpau.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libXvMCNVIDIA_dynamic.so is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libvdpau.so is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libnvidia-cfg.so.195.36.24 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libcuda.so.195.36.24 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libnvidia-tls.so.195.36.24 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libvdpau.so.195.36.24 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libnvidia-compiler.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libGL.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libvdpau_trace.so is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libOpenCL.so.1.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/tls/libnvidia-tls.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/tls/libnvidia-tls.so.195.36.24 is empty, not checked.
/sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied

```


This is the most troublesome.


```
glxinfo: error while loading shared libraries: /usr/lib/libGL.so.1: file too short
```

I browsed to the dir/file and it appears to be empty.

Edit 2:

```
bee-desktop:~$ grep -n "^(EE)" /var/log/Xorg*log
/var/log/Xorg.0.log:73:(EE) Failed to load /usr/lib/xorg/modules/extensions/libglx.so
/var/log/Xorg.0.log:75:(EE) Failed to load module "glx" (loader failed, 7)
/var/log/Xorg.0.log:103:(EE) Failed to load module "nouveau" (module does not exist, 0)
/var/log/Xorg.0.log:234:(EE) open /dev/fb0: No such file or directory
```

---

### Post by 23dornot23d on 2010-05-11
Administration - X server settings 

- shows whats currently running .......

[IMG]http://i43.tinypic.com/2r2tdth.jpg[/IMG]


root@keith-laptop:/home/keith# uname --all
Linux keith-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

There is nothing else to add ....... no more files for me to upgrade

What I can show is my History of how I got mine to work if this helps - have removed lines not needed .....

  183  apt-get purge nvidia*
  184  blacklist nouveau
  185  apt-get install nvidia-current
  186  modprobe nvidia
  
189  aptitude install nvidia    

|     I use aptitude just to list the names .... 
  
  191  apt-get install nvidia-185-libvdpau nvidia-185-kernel-source
193  apt-get install nvidia-glx-185 nvidia-kernel-common 
    
  196  apt-get install nvidia-current
  
  198  lsmod | grep -i nvidia
  
199  nvidia-xconfig
  
202  apt-get clean
  203  apt-get autoclean
  204  df
  205  startx
  206  exit
  207  reboot
  


I have read some reports that things have gone unstable for some Nvidia cards .... using this though  ... 
[http://ubuntuforums.org/showthread.php?t=1480600](http://ubuntuforums.org/showthread.php?t=1480600)
at the end here it seems like its the 64 bit again and Kernel  2.6.32-22-generic 
[http://ubuntuforums.org/showthread.php?t=990978&page=129http://ubuntuforums.org/showthread.php?t=990978&page=129]("http://ubuntuforums.org/showthread.php?t=990978&page=129")
or
[http://ubuntuforums.org/showthread.php?t=1478439](http://ubuntuforums.org/showthread.php?t=1478439)
or
[http://ubuntuforums.org/showthread.php?t=1480140](http://ubuntuforums.org/showthread.php?t=1480140)


Also found Bug Reports ......... both still appear valid ..... the first 2 users affected and the second has 15 users affected

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/554439](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/554439)

[https://bugs.launchpad.net/ubuntu/lucid/+source/nvidia-graphics-drivers/+bug/573557](https://bugs.launchpad.net/ubuntu/lucid/+source/nvidia-graphics-drivers/+bug/573557)

I was going to try it out and then we are both using the same Kernel 22 ...... (gets rid of one more variable)
but yours is later and is 64 bit ..... 

I think if someone is running a similar setup here .... they could help you more than me ..... 
I too am out of my depth on this one ( The new kernel and 64 bit are not what I am using )


( I don't think I can check this from the normal repositories as I am running 32 bit and it appears the 2.6.32-21-generic kernel is the latest for me !!! )
___________________________________________________________________


Yours is this from the LOG ...... which is 64 bit ...... and  2.6.32-22-generic 
Current Operating System: Linux bee-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64


[COLOR=Red]IF YOU STILL HAVE THE PREVIOUS KERNEL  2.6.32-21-generic ..... I would advise trying booting from it - if worked ok ......
I hope once that the Bugs are sorted there will be an update for the drivers .........
[/COLOR]

---

### Post by /bee/ on 2010-05-12
Thanks very much for helping me out.  I will cross my fingers and hope there is an update to fix this problem.  (Or if it doesn't get better, maybe I'll just buy a new video card... smh)

edit: I *still* can't download glx...

```
bee@snicklefritz:~$ sudo apt-get install nvidia-glx
sudo: unable to resolve host snicklefritz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx has no installation candidate

```

---

### Post by 23dornot23d on 2010-05-13
Sorry ...... after glx there wiil be a number relating to your driver .....

In Menu ......

System-Administration-Synaptic Package manager

To try to find the drivers for your card on your system ..... (mine is different here) ,,,

go into the Synaptic Package Manager and search for .....

Nvidia-glx or Nvidia-19

Then select the one you think might work .... maybe based on the success's of others .....

or do

replace *** for the number that you have possibly either 185 or 195 if the one that applies to your system appears in your list ....

sudo apt-get install Nvidia-glx-***

I will say again though ..... 
I have searched on the success of this card being installed properly on any of the later Linux Systems
and it seems to be negative ..... 
( I have found in the past that sometimes graphics cards will work in one version of Linux but not necessarily in another )

I really do hope that you find a solution for this ..... but I have done a lot of searches on this card and find very little to
give me confidence of its success ..... if you have different links to information showing that it works ok in Lucid
post one and we can work through it ......

after looking through this the last comment does say a fix was released for this particular bug ....... but not sure how
you implement it ..... if you did a fresh install of Lucid
or even doing all the upgrades on your system - should have included it ..... one would think ....

I would have expected it would have been included ... check through the comments under the bug reports
sometimes you can pick out useful information ..... on what others have tried to resolve their particular problems
( there seems plenty of bugs and problems but I have not seen a success yet ! for your card using 64 bit on Lucid )

[https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/494166](https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/494166)


The picture I had here is shown previously in no ... #6


Interesting link ..... 
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-xorg-proprietary-drivers](https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-xorg-proprietary-drivers)

Gives the reasons behind what is happening ..... and what it is they are trying to achieve .......

I will continue searching ......

I found this thread today and wondered if this may be part of the problem for it freezing ...

[Random Freeze]("http://ubuntuforums.org/showthread.php?t=1478787")

---

### Post by Ric95 on 2010-05-18
The odds are slim but your bios may not be set for your card.
Eg. if your NV 8500 is a PCI-E , make sure your bios is pointing at the PCI-E slot.

---

### Post by /bee/ on 2010-05-21
Yea, it's pointed at the right location.

---

### Post by /bee/ on 2010-05-29
Fixed many of my nagging (smaller) issues.  Still can't figure out why nvidia's drivers foul everything up...  I am in the market for a new graphics card though.

---

### Post by gnopak on 2011-01-17
I have been experiencing exactly the same kind of freezing with Ubuntu (Linux Mint actually) 10.04 with nVidia proprietary driver 195.x and now with nVidia proprietary driver 260.x. The problem disappeared after switching to Nouveau. I cannot afford to use Nouveau, though. It lacks the features I need.

I have GeForce 6200 LE. A year ago the support for GeForce 6 was in a "legacy driver". All cards are now supported with the same proprietary driver, but could it be that the part responsible for support of legacy hardware such as GeForce 6/7/8 is no longer developed by nVidia? Should I buy a GTX 260 or similar, considering that the newest GTX 4xx is said to have serious speed issues with OpenGL?

---

