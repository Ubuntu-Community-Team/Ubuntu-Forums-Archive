---
title: "NVIDIA laptop monitor drivers killed twice now by updates"
date: 2013-09-07
forum: Hardware
---

### Post by Halfling Rogue on 2013-09-07
I have Ubuntu 12.04 installed on an ASUS K70IC with an NVIDIA G96M (GeForce 9600M GT) graphics card. I originally had a 1600x900 resolution with a custom Xconfig set up to enable my Wacom tablet and native webcam to work properly.

One of my automatic updates a few weeks ago (I was away for a couple of weeks, so the update could have been pushed any time after August 9th) caused the NVIDIA driver I had to collapse and screw up my resolution. I downloaded the driver [directly from NVIDIA]("http://www.nvidia.com/Download/index.aspx?lang=en-us"), killed my X session and existing Xconf to install it, and after a reboot and a bit of prayer got everything working again as it had been.

Then I just installed some more automatic updates last night and now it seems that the driver is completely canned somehow. I only get the command line at boot and running xinit gives the error "no screen found" with several warnings reading "Module off not found", as well as "vesa: Ignoring device with a bound kernel driver.".

My first instinct was to try reinstalling the driver again, but I'm having trouble getting both my wireless to behave and my external drives to mount from the command line (tbh, most likely because I'm out of practice with the CL, or so I'm hoping). Is there anything else I can try in the meantime? Should I *not* try reinstalling the driver?

And more importantly, how can I prevent this from happening again? Twice in one month is already getting really old.

---

### Post by Halfling Rogue on 2013-09-07
Got the driver downloaded and reinstalled, no change. Also tried running the following:

```
sudo apt-get --reinstall install fglrx
sudo dpkg-reconfigure xserver-xorg
install fglrx-updates fglrx-amdcccle-updates
dpkg-reconfigure fglrx-updates
```

No change there either. No idea what I can do to fix this. I can provide the Xorg log file if anyone thinks it would help them puzzle it out.

---

### Post by Halfling Rogue on 2013-09-07
No takers? I'd prefer not to have to resort to a complete reinstall, but that's starting to look like the only option. :(

---

### Post by Halfling Rogue on 2013-09-07
Egh, here's Xorg logs anyway for my own personal reference and in case someone else runs into this problem later.

```
[   674.633] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[   674.633] X Protocol Version 11, Revision 0
[   674.633] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[   674.634] Current Operating System: Linux upstairs-laptop 3.2.0-53-generic-pae #81-Ubuntu SMP Thu Aug 22 21:23:47 UTC 2013 i686
[   674.634] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-53-generic-pae root=UUID=cd792e0b-b391-4649-a10a-d93afc18a5cc ro quiet splash
[   674.634] Build Date: 11 April 2013  01:04:30PM
[   674.634] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 
[   674.634] Current version of pixman: 0.24.4
[   674.635] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   674.635] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   674.636] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep  7 17:52:50 2013
[   674.636] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   674.637] (==) No Layout section.  Using the first Screen section.
[   674.637] (==) No screen section available. Using defaults.
[   674.637] (**) |-->Screen "Default Screen Section" (0)
[   674.637] (**) |   |-->Monitor "<default monitor>"
[   674.637] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   674.637] (==) Automatically adding devices
[   674.637] (==) Automatically enabling devices
[   674.637] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   674.637] 	Entry deleted from font path.
[   674.637] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   674.637] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   674.637] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   674.637] (II) Loader magic: 0xb77575a0
[   674.637] (II) Module ABI versions:
[   674.637] 	X.Org ANSI C Emulation: 0.4
[   674.637] 	X.Org Video Driver: 11.0
[   674.637] 	X.Org XInput driver : 16.0
[   674.637] 	X.Org Server Extension : 6.0
[   674.638] (--) PCI:*(0:2:0:0) 10de:0649:1043:202d rev 161, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[   674.638] (II) Open ACPI successful (/var/run/acpid.socket)
[   674.638] (II) LoadModule: "extmod"
[   674.639] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   674.639] (II) Module extmod: vendor="X.Org Foundation"
[   674.639] 	compiled for 1.11.3, module version = 1.0.0
[   674.639] 	Module class: X.Org Server Extension
[   674.639] 	ABI class: X.Org Server Extension, version 6.0
[   674.639] (II) Loading extension MIT-SCREEN-SAVER
[   674.639] (II) Loading extension XFree86-VidModeExtension
[   674.639] (II) Loading extension XFree86-DGA
[   674.639] (II) Loading extension DPMS
[   674.639] (II) Loading extension XVideo
[   674.639] (II) Loading extension XVideo-MotionCompensation
[   674.639] (II) Loading extension X-Resource
[   674.639] (II) LoadModule: "dbe"
[   674.639] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   674.639] (II) Module dbe: vendor="X.Org Foundation"
[   674.639] 	compiled for 1.11.3, module version = 1.0.0
[   674.639] 	Module class: X.Org Server Extension
[   674.639] 	ABI class: X.Org Server Extension, version 6.0
[   674.639] (II) Loading extension DOUBLE-BUFFER
[   674.639] (II) LoadModule: "glx"
[   674.639] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   674.675] (II) Module glx: vendor="NVIDIA Corporation"
[   674.675] 	compiled for 4.0.2, module version = 1.0.0
[   674.675] 	Module class: X.Org Server Extension
[   674.675] (II) NVIDIA GLX Module  319.49  Tue Aug 13 19:48:35 PDT 2013
[   674.675] (II) Loading extension GLX
[   674.675] (II) LoadModule: "record"
[   674.675] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   674.675] (II) Module record: vendor="X.Org Foundation"
[   674.675] 	compiled for 1.11.3, module version = 1.13.0
[   674.675] 	Module class: X.Org Server Extension
[   674.675] 	ABI class: X.Org Server Extension, version 6.0
[   674.675] (II) Loading extension RECORD
[   674.675] (II) LoadModule: "dri"
[   674.676] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   674.676] (II) Module dri: vendor="X.Org Foundation"
[   674.676] 	compiled for 1.11.3, module version = 1.0.0
[   674.676] 	ABI class: X.Org Server Extension, version 6.0
[   674.676] (II) Loading extension XFree86-DRI
[   674.676] (II) LoadModule: "dri2"
[   674.676] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   674.676] (II) Module dri2: vendor="X.Org Foundation"
[   674.676] 	compiled for 1.11.3, module version = 1.2.0
[   674.676] 	ABI class: X.Org Server Extension, version 6.0
[   674.676] (II) Loading extension DRI2
[   674.676] (==) Matched nvidia as autoconfigured driver 0
[   674.676] (==) Matched nouveau as autoconfigured driver 1
[   674.676] (==) Matched nv as autoconfigured driver 2
[   674.676] (==) Matched vesa as autoconfigured driver 3
[   674.676] (==) Matched fbdev as autoconfigured driver 4
[   674.676] (==) Assigned the driver to the xf86ConfigLayout
[   674.676] (II) LoadModule: "nvidia"
[   674.677] (WW) Warning, couldn't open module nvidia
[   674.677] (II) UnloadModule: "nvidia"
[   674.677] (II) Unloading nvidia
[   674.677] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   674.677] (II) LoadModule: "nouveau"
[   674.677] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   674.677] (II) Module nouveau: vendor="X.Org Foundation"
[   674.677] 	compiled for 1.11.3, module version = 0.0.16
[   674.677] 	Module class: X.Org Video Driver
[   674.677] 	ABI class: X.Org Video Driver, version 11.0
[   674.677] (II) LoadModule: "nv"
[   674.678] (WW) Warning, couldn't open module nv
[   674.678] (II) UnloadModule: "nv"
[   674.678] (II) Unloading nv
[   674.678] (EE) Failed to load module "nv" (module does not exist, 0)
[   674.678] (II) LoadModule: "vesa"
[   674.678] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   674.678] (II) Module vesa: vendor="X.Org Foundation"
[   674.678] 	compiled for 1.11.3, module version = 2.3.0
[   674.678] 	Module class: X.Org Video Driver
[   674.678] 	ABI class: X.Org Video Driver, version 11.0
[   674.678] (II) LoadModule: "fbdev"
[   674.679] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   674.679] (II) Module fbdev: vendor="X.Org Foundation"
[   674.679] 	compiled for 1.11.3, module version = 0.4.2
[   674.679] 	ABI class: X.Org Video Driver, version 11.0
[   674.679] (==) Matched nvidia as autoconfigured driver 0
[   674.679] (==) Matched nouveau as autoconfigured driver 1
[   674.679] (==) Matched nv as autoconfigured driver 2
[   674.679] (==) Matched vesa as autoconfigured driver 3
[   674.679] (==) Matched fbdev as autoconfigured driver 4
[   674.679] (==) Assigned the driver to the xf86ConfigLayout
[   674.679] (II) LoadModule: "nvidia"
[   674.679] (WW) Warning, couldn't open module nvidia
[   674.679] (II) UnloadModule: "nvidia"
[   674.679] (II) Unloading nvidia
[   674.679] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   674.679] (II) LoadModule: "nouveau"
[   674.680] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   674.680] (II) Module nouveau: vendor="X.Org Foundation"
[   674.680] 	compiled for 1.11.3, module version = 0.0.16
[   674.680] 	Module class: X.Org Video Driver
[   674.680] 	ABI class: X.Org Video Driver, version 11.0
[   674.680] (II) UnloadModule: "nouveau"
[   674.680] (II) Unloading nouveau
[   674.680] (II) Failed to load module "nouveau" (already loaded, 0)
[   674.680] (II) LoadModule: "nv"
[   674.680] (WW) Warning, couldn't open module nv
[   674.680] (II) UnloadModule: "nv"
[   674.680] (II) Unloading nv
[   674.680] (EE) Failed to load module "nv" (module does not exist, 0)
[   674.680] (II) LoadModule: "vesa"
[   674.681] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   674.681] (II) Module vesa: vendor="X.Org Foundation"
[   674.681] 	compiled for 1.11.3, module version = 2.3.0
[   674.681] 	Module class: X.Org Video Driver
[   674.681] 	ABI class: X.Org Video Driver, version 11.0
[   674.681] (II) UnloadModule: "vesa"
[   674.681] (II) Unloading vesa
[   674.681] (II) Failed to load module "vesa" (already loaded, 0)
[   674.681] (II) LoadModule: "fbdev"
[   674.681] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   674.681] (II) Module fbdev: vendor="X.Org Foundation"
[   674.681] 	compiled for 1.11.3, module version = 0.4.2
[   674.681] 	ABI class: X.Org Video Driver, version 11.0
[   674.681] (II) UnloadModule: "fbdev"
[   674.681] (II) Unloading fbdev
[   674.681] (II) Failed to load module "fbdev" (already loaded, 0)
[   674.681] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[   674.681] (II) NOUVEAU driver for NVIDIA chipset families :
[   674.681] 	RIVA TNT        (NV04)
[   674.681] 	RIVA TNT2       (NV05)
[   674.681] 	GeForce 256     (NV10)
[   674.681] 	GeForce 2       (NV11, NV15)
[   674.681] 	GeForce 4MX     (NV17, NV18)
[   674.681] 	GeForce 3       (NV20)
[   674.681] 	GeForce 4Ti     (NV25, NV28)
[   674.681] 	GeForce FX      (NV3x)
[   674.681] 	GeForce 6       (NV4x)
[   674.681] 	GeForce 7       (G7x)
[   674.681] 	GeForce 8       (G8x)
[   674.681] 	GeForce GTX 200 (NVA0)
[   674.681] 	GeForce GTX 400 (NVC0)
[   674.681] (II) VESA: driver for VESA chipsets: vesa
[   674.681] (II) FBDEV: driver for framebuffer: fbdev
[   674.681] (--) using VT number 7

[   674.686] drmOpenDevice: node name is /dev/dri/card0
[   674.694] [drm] failed to load kernel module "nouveau"
[   674.694] (EE) [drm] failed to open device
[   674.694] drmOpenDevice: node name is /dev/dri/card0
[   674.701] [drm] failed to load kernel module "nouveau"
[   674.701] (EE) [drm] failed to open device
[   674.701] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   674.701] vesa: Ignoring device with a bound kernel driver
[   674.701] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   674.701] vesa: Ignoring device with a bound kernel driver
[   674.701] (WW) Falling back to old probe method for vesa
[   674.701] (II) Loading sub module "fbdevhw"
[   674.701] (II) LoadModule: "fbdevhw"
[   674.701] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   674.701] (II) Module fbdevhw: vendor="X.Org Foundation"
[   674.701] 	compiled for 1.11.3, module version = 0.0.2
[   674.701] 	ABI class: X.Org Video Driver, version 11.0
[   674.701] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   674.701] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   674.701] (EE) open /dev/fb0: No such file or directory
[   674.701] (WW) Falling back to old probe method for fbdev
[   674.701] (II) UnloadModule: "vesa"
[   674.701] (II) Unloading vesa
[   674.701] (II) UnloadModule: "vesa"
[   674.701] (II) Unloading vesa
[   674.701] (II) UnloadModule: "fbdev"
[   674.701] (II) Unloading fbdev
[   674.701] (II) UnloadModule: "fbdevhw"
[   674.701] (II) Unloading fbdevhw
[   674.701] (EE) Screen(s) found, but none have a usable configuration.
[   674.702] 
Fatal server error:
[   674.702] no screens found
[   674.702] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   674.702] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   674.702] 
[   674.705]  ddxSigGiveUp: Closing log
[   674.705] Server terminated with error (1). Closing log file.
```

---

### Post by Halfling Rogue on 2013-09-07
Tried "jockey-text -l" for a driver list ([as per this post]("http://askubuntu.com/questions/17892/failed-to-load-module-nvidia")) and found all of the following for nvidia:

nvidia_173, nvidia_173_updates (proprietary, disabled)
nvidia_304, nvidia_304_updates (proprietary, enabled)
nvidia_319, nvidia_319_updates (proprietary, disabled)

As nvidia-319 is the native driver for my card, I suspected a conflict and tried purging nvidia-304 using apt-get (this removed nvidia-current as well). I then ran jockey-text -e xorg:nvidia_319, though it hung and I wound up cancelling the process.

Running into some troubles with apt-get (locked archive) preventing me from trying [this fix]("http://askubuntu.com/questions/113993/ubuntu-11-10-nvidia-module-failed-to-load-no-module-exists"), so I rebooted the computer to clear things. The graphics card wouldn't show the Ubuntu 12.04 splash/startup page, but after a few moments my login page loaded just fine with the proper 1600x900 resolution. Logging in presented no problems and everything seems to be working as it should. Checking the Synaptic Package Manager shows that nvidia-current is still uninstalled (and nvidia-304, nvidida-173, and nvidia-319 are all showing as uninstalled. The only one present is nvidia-common).

My guess is that the default packages were interfering with the driver I downloaded and installed directly from Nvidia. Just glad that everything's working now!

---

### Post by buzzingrobot on 2013-09-08
Just a guess, but I suspect that first update, while you were away, overwrote your custom X config.  A correct Nvidia install, whether via Ubuntu's packages or using Nvidia's, backs up any existing xorg,conf and creates a new one. (That's what nvidia-xconfig does.)

In my experience, mixing Nvidia install methods doesn't work well.  It's best to stay with the approach  you start with.

Also curious about the reference to "fglrx", since that's the AMD driver.

---

