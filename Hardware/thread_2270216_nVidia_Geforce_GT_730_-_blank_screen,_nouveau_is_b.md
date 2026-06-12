---
title: "nVidia Geforce GT 730 - blank screen, nouveau is bad"
date: 2015-03-21
forum: Hardware
---

### Post by mastablasta on 2015-03-21
So many users here say use nVidia for linux. Mights as well i think since i don't care what brand the card is al long as it works.

it's been 4 hours now since i've added the card to the PC and i have yet to start using it. the nvidia linux support is really bad. or is this maybe just in ubuntu?


the computer an only boot to desktop with nomodeset parameter and igve resolution 1024 x768 on a 1650 x 1050 monitor. Ubuntu then proposes proprietary drivers. none of those drivers actually support this card. so blank screen. i check the web and apparently the needed driver is 340 at least. ok xorg edgers installs it via their PPA. so i follow that advice

i get blank screen!
using nomodeset parameter i get a cursor and can move to TTY1 to remove the driver. 

i tried several other version notihng seems to be working. always blank screen
nvidia settings is empty there is no card inside there. only setup for various applications.

xrandr is not helpful as i can not set any resolution.

all in all this is not working. why not? official documents says it should work just fine. driver supposedly has support fo rthis card. so i am not sure but it looks to me like something is wrong with ubuntu setup.

and the windows way (or why linux desktop is where it is) ? well insert the CD and run the file, profit.

by the way the informaiton on official wiki pages is outdated. some programs are mentioned there that do not even seem to exists. and the instructions are missing or should i say incomplete.

---

### Post by ulgor on 2015-03-21
Hi mastablasta,
For my GeForce GTX 750 Ti, I recently installed the most recent proprietary drivers from the nVidia homepage, and it worked without many additional programs or steps (some issues after kernel updates remain, which still need to be fixed - see below). 

The basic steps were:
[LIST=1]
[*] find and download most recent driver
[*] press Ctrl+Alt+F1 to drop from graphical desktop to terminal
[*] stop graphics via ```
sudo lightdm stop
```
[*] enter download directory, then run nvidia install script via ```
 sudo sh NVIDIA..something
```
[*] answer all with "Yes"
[*] reboot
[/LIST]


The installer script seems to take care of most of the settings. I am not sure if blacklisting the nouveau drivers is still needed (as suggested in some other threads).

Now the only problem I have is that some updates (probably the ones updating kernel/graphics driver settings) lead to a black screen on startup. This is fixed by simply re-installing the driver using the steps above... That's ugly, but restores the system to a usable state immediately. Trying to find a solution for that at the moment...

---

### Post by mastablasta on 2015-03-21
the only thing i haven't tried yet is manual install and that is the reason why i try to avoid it since PC is used by others mostly.

i wonder if the card should be recognised even with opensource drivers. mine is not. it is just nvidia corporation device (no chip or whatsoever not even with driver installed). i went through checks found here toward the end: [http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/)
obviously i can't make the opengl one in CLI, but the rest seem kidn of Ok except for the chip - still only a device 

the issue is that the card can not be initialised it seems. however why this happens remains a mistery to me. could it be that something is wrong with the card?

oh and the drivers via PPA should work and update along with kernel. basically they patch the kernel and use the dkms to update upon kernel update.

xorg logs say that the nvidia GPU can not be initialised and that there is no screens available (and this is displayed on the screen). various errors i found - i tried to google them but most advice is purge and reinstall. not helping at all.

i spent 9 hours on this and i think i will just return the card. it shouldn't be so hard to do install a GPU... and the most it upsets me because there is no information of why it doesn't work or what is wrong. i mean saying you can't initialise the GPU means nothing to me. i can already see it is not working. i would need to know why not. somethign in driver? something wrong with the GPU?

edit: somthing frtm syslog - not sure if it's normal or not.:
```
Mar 21 09:54:02 tatie-desktop kernel: [   18.615933] nvidia: module license 'NVIDIA' taints kernel.
Mar 21 09:54:02 tatie-desktop kernel: [   18.615938] Disabling lock debugging due to kernel taint
Mar 21 09:54:02 tatie-desktop kernel: [   18.631035] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
Mar 21 09:54:02 tatie-desktop ModemManager[727]: <info>  ModemManager (version 1.0.0) starting...
Mar 21 09:54:03 tatie-desktop kernel: [   19.296016] hda-intel 0000:02:00.1: Codec #1 probe error; disabling it...
Mar 21 09:54:03 tatie-desktop nvidia-persistenced: Started (797)
Mar 21 09:54:03 tatie-desktop nvidia-persistenced: Failed to query NVIDIA devices. Please ensure that the NVIDIA device files (/dev/nvidia*) exist, and that user 121 has read and write permissions for those files.
Mar 21 09:54:03 tatie-desktop nvidia-persistenced: The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced
Mar 21 09:54:03 tatie-desktop nvidia-persistenced: Shutdown (797)
```


found another interesting log thing:
```
Mar 21 14:24:29 tatie-desktop kernel: [ 1494.815570] NVRM: API mismatch: the client has the version 340.76, but
Mar 21 14:24:29 tatie-desktop kernel: [ 1494.815570] NVRM: this kernel module has the version 331.113.  Please
Mar 21 14:24:29 tatie-desktop kernel: [ 1494.815570] NVRM: make sure that this kernel module and all NVIDIA driver
Mar 21 14:24:29 tatie-desktop kernel: [ 1494.815570] NVRM: components have the same version.
Mar 21 14:24:29 tatie-desktop kernel: [ 1494.815579] NVRM: nvidia_frontend_ioctl: minor 255, module->ioctl failed, error -22
Mar 21 14:24:29 tatie-desktop kernel: [ 1494.825490] NVRM: API mismatch: the client has the version 340.76, but
Mar 21 14:24:29 tatie-desktop kernel: [ 1494.825490] NVRM: this kernel module has the version 331.113.  Please
Mar 21 14:24:29 tatie-desktop kernel: [ 1494.825490] NVRM: make sure that this kernel module and all NVIDIA driver
Mar 21 14:24:29 tatie-desktop kernel: [ 1494.825490] NVRM: components have the same version.
Mar 21 14:24:29 tatie-desktop kernel: [ 1494.825499] NVRM: nvidia_frontend_ioctl: minor 255, module->ioctl failed, error -22
```

alos why do i have jockey log (from last year when it was still active). i did  not have nvidia card back then. interesting.

---

### Post by mastablasta on 2015-03-23
BUMP! serioulsy? no one knows why the blank screen?? or how to propperly troubleshoot this?

---

### Post by Keith_Helms on 2015-03-23
Those log messages sure look like you've got both the 331 and 340 drivers installed, or at least pieces of both.  Why don't you try deleting all nvidia drivers with "sudo apt-get purge nvidia*" and then try to reinstall either 331 from the repository or 340 from xorg-edgers.

What gpu were you using before installing the Nvidia card?  Onboard graphics?  If so, did you disable it in the BIOS after putting in the new card? 

What does "sudo lshw -C video" show?

---

### Post by tokyobadger on 2015-03-23
```
Mar 21 09:54:03 tatie-desktop nvidia-persistenced: The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced
```
You've been hit by the persistenced issue - in the older driver versions (at least on Ubuntu and up to the 343 series if I remember correctly) updating the drivers did not handle the stopping and updating of nvidia-persistenced properly.

That's why you're getting the following error about API mismatch:
```
Mar 21 14:24:29 tatie-desktop kernel: [ 1494.815570] NVRM: API mismatch: the client has the version 340.76, but
Mar 21 14:24:29 tatie-desktop kernel: [ 1494.815570] NVRM: this kernel module has the version 331.113.  Please
Mar 21 14:24:29 tatie-desktop kernel: [ 1494.815570] NVRM: make sure that this kernel module and all NVIDIA driver
Mar 21 14:24:29 tatie-desktop kernel: [ 1494.815570] NVRM: components have the same version.
```

Try the following:
```
ps ax | grep persistenced
sudo kill <persistenced process number goes here>
sudo apt-get purge nvidia* && sudo apt-get install nvidia-340
```
Why not try nvidia-346 instead of 340?
[more detailed steps in this thread](http://ubuntuforums.org/showthread.php?t=2258309&highlight=persistenced) plus a compiz workaround if you need it

---

### Post by mastablasta on 2015-03-23
@[**[COLOR=#000000]tokyobadger[/COLOR]**]("http://ubuntuforums.org/member.php?u=1047324")
does "perstistenced issue" mean part of drivers remain while the yhsould have been purged?

ok now you made me want to have another try. my biggest problem is finding what error messages exactly mean. I tried so many options so I might try another one. yes I agree 346 would maybe be better. or in fact I see there is newer driver on their website. I downloaded manual install version to maybe have a go.

> **Keith_Helms said:**
> Those log messages sure look like you've got both the 331 and 340 drivers installed, or at least pieces of both.  Why don't you try deleting all nvidia drivers with "sudo apt-get purge nvidia*" and then try to reinstall either 331 from the repository or 340 from xorg-edgers.

I ran sudo apt-get remove --purge nvidia-*
then 
sudo apt get autoremove
> 
What gpu were you using before installing the Nvidia card?  Onboard graphics?  If so, did you disable it in the BIOS after putting in the new card? 

Board has two slots AGP and PCIe. I was using AGP ATI Radeon 9600 XT 256 MB. I then set PCIe as primary GPU device and took out the AGP card before inserting the NVidia.
> 
 What does "sudo lshw -C video" show?
this is now from my memory since I placed the AGP card back in so we can get at least some work done on that PC. 
but it was saying NVidia corporation device, driver in use was NVidia.  as I recall it did not recognise the chip. now if there really is residual trace from NVidia 331 that would make sense since 331 does not yet support this card. 

so I am giving this another try it seems. if not I might need help getting the Radeon HD 3650 to work nicely in Linux, cause as I remember, I had to use nomodeset to boot into live session on 14.04, but I donwloaded (14.04.4 [is it .4?!] 14.10 and 15.04beta to see if newer kernels correct this issue). I love kubuntu, the desktop and the apps, but these hardware issues are so exhausting.

otherwise what I use now the 10+ year old radeon 9600 works great for youtube and such desktop stuff, but as soon as you throw an OpenGL game at it, it crashes the whole system. and it appears it is not CPU overheating because immediate reboot after crash showed a higher but still cosy temp of 43C. easiest way to crash is Wolfenstein: Enemy territory - select flamethrower, let is rip. it crashes after about 20-30 seconds. :-) jDoom take s a bit longer but crashes nonethe less. in supertux cart it takes about 1/4 -1/2 of the track before it all freezes...

---

### Post by tokyobadger on 2015-03-23
[quote="mastablasta"]@[**[COLOR=#000000]tokyobadger[/COLOR]**]("http://ubuntuforums.org/member.php?u=1047324")
does "perstistenced issue" mean part of drivers remain while the yhsould have been purged?[/quote]
yes - previous versions of nvidia-persistence would not get removed during an upgrade because the daemon persistenced was not getting stopped - to successfully fix your situation you need to stop the persistenced process (autostarts at boot) which is part of nvidia-331 package, before you can install any other nvidia driver version - apt-get purge nvidia* will not do it, you must identify the process ID (number) and kill it as sudo

---

### Post by oldfred on 2015-03-23
Besides purging all traces of any older nVidia driver before installing a new one, you may need to create a new xorg file which the install will do, but it may not overwrite the old one.

 sudo mv /etc/X11/xorg.conf /etc/X11/xorg/conf.old

The main disadvantage of installing directly from nVidia is that every new kernel update requires manual update to use the nVidia driver. IF from Ubuntu repository or even ppa then dpkg includes that update in the kernel update.


 Lists installed version, in/with your kernel:
dkms status

---

### Post by mastablasta on 2015-03-23
yeah.... it didn't work at all. blank screen. had to battle over one hour just to get to the command line. i tried to attach the TV - also got a blank screen.

i only got line with this no nvidia in the line: 
0:00 grep --color=auto persistenced

some highlights
```
Mar 23 17:41:21 tatie-desktop kernel: [   31.005799] NVRM: RmInitAdapter failed! (0x26:0x65:1292)
Mar 23 17:41:21 tatie-desktop kernel: [   31.005814] NVRM: rm_init_adapter failed for device bearing minor number 0
Mar 23 17:41:21 tatie-desktop kernel: [   31.005847] NVRM: nvidia_frontend_open: minor 0, module->open() failed, error -5



Mar 23 17:41:21 tatie-desktop kernel: [   31.005814] NVRM: rm_init_adapter failed for device bearing minor number 0
Mar 23 17:41:21 tatie-desktop kernel: [   31.005847] NVRM: nvidia_frontend_open: minor 0, module->open() failed, error -5
Mar 23 17:41:22 tatie-desktop kernel: [   31.846175] init: plymouth-upstart-bridge main process ended, respawning
Mar 23 17:41:22 tatie-desktop nvidia-persistenced: Failed to unlink socket: No such file or directory
Mar 23 17:41:22 tatie-desktop nvidia-persistenced: Failed to unlink PID file: No such file or directory
Mar 23 17:41:22 tatie-desktop nvidia-persistenced: Shutdown (1407)
Mar 23 17:41:22 tatie-desktop kernel: [   31.991914] nvidia 0000:02:00.0: irq 65 for MSI/MSI-X
Mar 23 17:41:22 tatie-desktop nvidia-persistenced: Started (1715)
Mar 23 17:41:30 tatie-desktop NetworkManager[830]: <info> (eth0): IP6 addrconf timed out or failed.
Mar 23 17:41:30 tatie-desktop NetworkManager[830]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 23 17:41:30 tatie-desktop NetworkManager[830]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 23 17:41:30 tatie-desktop NetworkManager[830]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete. 

```

Xorg
```
[    31.941] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    31.941] X Protocol Version 11, Revision 0
[    31.941] Build Operating System: Linux 3.2.0-75-generic i686 Ubuntu
[    31.941] Current Operating System: Linux tatie-desktop 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:08:14 UTC 2015 i686
[    31.941] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-46-generic root=UUID=3f43c7a8-003b-4564-9f0d-a7a4c0393e06 ro quiet splash xforcevesa
[    31.941] Build Date: 12 February 2015  02:49:46PM
[    31.941] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[    31.941] Current version of pixman: 0.30.2
[    31.941]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    31.941] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    31.941] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 23 17:41:22 2015
[    31.941] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    31.942] (==) No Layout section.  Using the first Screen section.
[    31.942] (==) No screen section available. Using defaults.
[    31.942] (**) |-->Screen "Default Screen Section" (0)
[    31.942] (**) |   |-->Monitor "<default monitor>"
[    31.942] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    31.942] (==) Automatically adding devices
[    31.942] (==) Automatically enabling devices
[    31.942] (==) Automatically adding GPU devices
[    31.942] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    31.942]     Entry deleted from font path.
[    31.942] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    31.942]     Entry deleted from font path.
[    31.942] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    31.942]     Entry deleted from font path.
[    31.942] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    31.942]     Entry deleted from font path.
[    31.942] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    31.942]     Entry deleted from font path.
[    31.942] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    31.942] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    31.942] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    31.942] (II) Loader magic: 0xb779a6c0
[    31.942] (II) Module ABI versions:
[    31.942]     X.Org ANSI C Emulation: 0.4
[    31.942]     X.Org Video Driver: 15.0
[    31.942]     X.Org XInput driver : 20.0
[    31.942]     X.Org Server Extension : 8.0
[    31.942] (II) xfree86: Adding drm device (/dev/dri/card0)
[    31.944] (--) PCI:*(0:2:0:0) 10de:0f02:1462:8a9f rev 161, Mem @ 0xfd000000/16777216, 0xf0000000/134217728, 0xfa000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/524288
[    31.944] Initializing built-in extension Generic Event Extension
[    31.944] Initializing built-in extension SHAPE
[    31.944] Initializing built-in extension MIT-SHM
[    31.944] Initializing built-in extension XInputExtension
[    31.944] Initializing built-in extension XTEST
[    31.944] Initializing built-in extension BIG-REQUESTS
[    31.944] Initializing built-in extension SYNC
[    31.944] Initializing built-in extension XKEYBOARD
[    31.944] Initializing built-in extension XC-MISC
[    31.944] Initializing built-in extension SECURITY
[    31.944] Initializing built-in extension XINERAMA
[    31.944] Initializing built-in extension XFIXES
[    31.944] Initializing built-in extension RENDER
[    31.944] Initializing built-in extension RANDR
[    31.944] Initializing built-in extension COMPOSITE
[    31.944] Initializing built-in extension DAMAGE
[    31.944] Initializing built-in extension MIT-SCREEN-SAVER
[    31.944] Initializing built-in extension DOUBLE-BUFFER
[    31.944] Initializing built-in extension RECORD
[    31.944] Initializing built-in extension DPMS
[    31.944] Initializing built-in extension Present
[    31.944] Initializing built-in extension DRI3
[    31.944] Initializing built-in extension X-Resource
[    31.944] Initializing built-in extension XVideo
[    31.944] Initializing built-in extension XVideo-MotionCompensation
[    31.944] Initializing built-in extension SELinux
[    31.944] Initializing built-in extension XFree86-VidModeExtension
[    31.944] Initializing built-in extension XFree86-DGA
[    31.944] Initializing built-in extension XFree86-DRI
[    31.944] Initializing built-in extension DRI2
[    31.944] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    31.944] (II) "glx" will be loaded by default.
[    31.944] (WW) "xmir" is not to be loaded by default. Skipping.
[    31.944] (II) LoadModule: "glx"
[    31.944] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    31.982] (II) Module glx: vendor="NVIDIA Corporation"
[    31.983]     compiled for 4.0.2, module version = 1.0.0
[    31.983]     Module class: X.Org Server Extension
[    31.983] (II) NVIDIA GLX Module  346.47  Thu Feb 19 18:14:56 PST 2015
[    31.983] Loading extension GLX
[    31.983] (==) Matched nvidia as autoconfigured driver 0
[    31.983] (==) Matched nouveau as autoconfigured driver 1
[    31.983] (==) Matched nvidia as autoconfigured driver 2
[    31.983] (==) Matched nouveau as autoconfigured driver 3
[    31.983] (==) Matched modesetting as autoconfigured driver 4
[    31.983] (==) Matched fbdev as autoconfigured driver 5
[    31.983] (==) Matched vesa as autoconfigured driver 6
[    31.983] (==) Assigned the driver to the xf86ConfigLayout
[    31.983] (II) LoadModule: "nvidia"
[    31.983] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    31.983] (II) Module nvidia: vendor="NVIDIA Corporation"
[    31.983]     compiled for 4.0.2, module version = 1.0.0
[    31.983]     Module class: X.Org Video Driver
[    31.983] (II) LoadModule: "nouveau"
[    31.984] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    31.984] (II) Module nouveau: vendor="X.Org Foundation"
[    31.984]     compiled for 1.15.0, module version = 1.0.10
[    31.984]     Module class: X.Org Video Driver
[    31.984]     ABI class: X.Org Video Driver, version 15.0
[    31.984] (II) LoadModule: "modesetting"
[    31.984] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    31.984] (II) Module modesetting: vendor="X.Org Foundation"
[    31.984]     compiled for 1.15.0, module version = 0.8.1
[    31.984]     Module class: X.Org Video Driver
[    31.984]     ABI class: X.Org Video Driver, version 15.0
[    31.984] (II) LoadModule: "fbdev"
[    31.984] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    31.985] (II) Module fbdev: vendor="X.Org Foundation"
[    31.985]     compiled for 1.15.0, module version = 0.4.4
[    31.985]     Module class: X.Org Video Driver
[    31.985]     ABI class: X.Org Video Driver, version 15.0
[    31.985] (II) LoadModule: "vesa"
[    31.985] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    31.985] (II) Module vesa: vendor="X.Org Foundation"
[    31.985]     compiled for 1.15.0, module version = 2.3.3
[    31.985]     Module class: X.Org Video Driver
[    31.985]     ABI class: X.Org Video Driver, version 15.0
[    31.985] (II) NVIDIA dlloader X Driver  346.47  Thu Feb 19 17:51:09 PST 2015
[    31.985] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    31.985] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    31.985] (II) NOUVEAU driver for NVIDIA chipset families :
[    31.985]     RIVA TNT        (NV04)
[    31.985]     RIVA TNT2       (NV05)
[    31.985]     GeForce 256     (NV10)
[    31.985]     GeForce 2       (NV11, NV15)
[    31.985]     GeForce 4MX     (NV17, NV18)
[    31.985]     GeForce 3       (NV20)
[    31.985]     GeForce 4Ti     (NV25, NV28)
[    31.985]     GeForce FX      (NV3x)
[    31.985]     GeForce 6       (NV4x)
[    31.985]     GeForce 7       (G7x)
[    31.985]     GeForce 8       (G8x)
[    31.985]     GeForce GTX 200 (NVA0)
[    31.985]     GeForce GTX 400 (NVC0)
[    31.985] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    31.985] (II) FBDEV: driver for framebuffer: fbdev
[    31.985] (II) VESA: driver for VESA chipsets: vesa
[    31.985] (++) using VT number 7

[    31.989] (II) Loading sub module "fb"
[    31.989] (II) LoadModule: "fb"
[    31.989] (II) Loading /usr/lib/xorg/modules/libfb.so
[    31.989] (II) Module fb: vendor="X.Org Foundation"
[    31.989]     compiled for 1.15.1, module version = 1.0.0
[    31.989]     ABI class: X.Org ANSI C Emulation, version 0.4
[    31.989] (II) Loading sub module "wfb"
[    31.989] (II) LoadModule: "wfb"
[    31.989] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    31.990] (II) Module wfb: vendor="X.Org Foundation"
[    31.990]     compiled for 1.15.1, module version = 1.0.0
[    31.990]     ABI class: X.Org ANSI C Emulation, version 0.4
[    31.990] (II) Loading sub module "ramdac"
[    31.990] (II) LoadModule: "ramdac"
[    31.990] (II) Module "ramdac" already built-in
[    31.990] (WW) Falling back to old probe method for modesetting
[    31.990] (WW) Falling back to old probe method for fbdev
[    31.990] (II) Loading sub module "fbdevhw"
[    31.990] (II) LoadModule: "fbdevhw"
[    31.991] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    31.991] (II) Module fbdevhw: vendor="X.Org Foundation"
[    31.991]     compiled for 1.15.1, module version = 0.0.2
[    31.991]     ABI class: X.Org Video Driver, version 15.0
[    31.991] (EE) open /dev/fb0: No such file or directory
[    31.991] (WW) Falling back to old probe method for vesa
[    31.991] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    31.991] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    31.991] (==) NVIDIA(0): RGB weight 888
[    31.991] (==) NVIDIA(0): Default visual is TrueColor
[    31.991] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    31.991] (**) NVIDIA(0): Enabling 2D acceleration
[    44.090] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA GPU at PCI:2:0:0.  Please
[    44.091] (EE) NVIDIA(GPU-0):     check your system's kernel log for additional error
[    44.091] (EE) NVIDIA(GPU-0):     messages and refer to Chapter 8: Common Problems in the
[    44.091] (EE) NVIDIA(GPU-0):     README for additional information.
[    44.091] (EE) NVIDIA(GPU-0): Failed to initialize the NVIDIA graphics device!
[    44.091] (EE) NVIDIA(0): Failing initialization of X screen 0
[    44.091] (II) UnloadModule: "nvidia"
[    44.091] (II) UnloadSubModule: "wfb"
[    44.091] (II) UnloadSubModule: "fb"
[    44.091] (EE) Screen(s) found, but none have a usable configuration.
[    44.091] (EE) 
Fatal server error:
[    44.091] (EE) no screens found(EE) 
[    44.091] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    44.091] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    44.091] (EE) 
[    44.092] (EE) Server terminated with error (1). Closing log file. 



```

dmesg:
```
[   17.202354] nvidia: module license 'NVIDIA' taints kernel.
[   17.202360] Disabling lock debugging due to kernel taint
[   17.202563] type=1400 audit(1427128356.681:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=545 comm="apparmor_parser"
[   17.202573] type=1400 audit(1427128356.681:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=545 comm="apparmor_parser"
[   17.202578] type=1400 audit(1427128356.681:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=545 comm="apparmor_parser"
[   17.203129] type=1400 audit(1427128356.681:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=545 comm="apparmor_parser"
[   17.203140] type=1400 audit(1427128356.681:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=545 comm="apparmor_parser"
[   17.203395] type=1400 audit(1427128356.681:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=545 comm="apparmor_parser"
[   17.260930] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   17.322014] init: cups main process (522) killed by HUP signal
[   17.322031] init: cups main process ended, respawning
[   18.032363] init: failsafe main process (602) killed by TERM signal
[   18.176030] hda-intel 0000:02:00.1: Codec #0 probe error; disabling it...
[   18.390524] type=1400 audit(1427128357.869:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=771 comm="apparmor_parser"
[   19.188032] hda-intel 0000:02:00.1: Codec #1 probe error; disabling it... 


```

following the advice and going to nvidia chapter 8: common problems i found this:
[TABLE]
[TR="class: question"]
[TD="align: left"][/TD]
[/TR]
[TR="class: answer"]
[TD="align: left"]**My X server fails to start, and my X log file contains the error:**
 (EE) NVIDIA(0): The NVIDIA kernel module does not appear to
(EE) NVIDIA(0):      be receiving interrupts generated by the NVIDIA graphics
(EE) NVIDIA(0):      device PCI:mad::mad::mad:. Please see the COMMON PROBLEMS
(EE) NVIDIA(0):      section in the README for additional information.[/TD]
[TD="align: left"] This can be caused by a variety of problems, such as PCI IRQ routing errors, I/O APIC problems or conflicts with other devices sharing the IRQ (or their drivers).

 If possible, configure your system such that your graphics card does not share its IRQ with other devices (try moving the graphics card to another slot if applicable, unload/disable the driver(s) for the device(s) sharing the card's IRQ, or remove/disable the device(s)).

 Depending on the nature of the problem, one of (or a combination of) these kernel parameters might also help:

  [TABLE]
[TR]
[TH]Parameter[/TH]
[TH]Behavior[/TH]
[/TR]
[TR]
[TD]pci=noacpi[/TD]
[TD]don't use ACPI for PCI IRQ routing[/TD]
[/TR]
[TR]
[TD]pci=biosirq[/TD]
[TD]use PCI BIOS calls to retrieve the IRQ routing table[/TD]
[/TR]
[TR]
[TD]noapic[/TD]
[TD]don't use I/O APICs present in the system[/TD]
[/TR]
[TR]
[TD]acpi=off[/TD]
[TD]disable ACPI[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

however i am terrified of using this now as it is difficult to get back to CLI (obviously i can get to recovery mode but there i am root and disk is not mounted). thee ris no guarantee any of these will work. Also i am not sure why it would suddenly be an IRQ issue as it doesn't say this in any messgae. it could be just another false lead.

"Depending on the nature of the problem" and what is the nature of the problem? where is it defined?

edit: **how do i remove nvidia drivers from recovery console?**

---

### Post by mastablasta on 2015-03-23
as an interesting informaiton - i tried to run 14.04.2 and 15.04beta

i could not launch any of them - i tall froze after this (tried with and without nomodeset): ASPM could not configure common clock

to make sure DVD is good i booted on the other PC. sure enough both work well. which means if i use this nvidia card in the WindowsPC and then need to for some reason boot into linux - i will probably fail.

---

### Post by tokyobadger on 2015-03-24
let's see if you got rid of all nvidia files with the apt-get purge nvidia*
```
dpkg -l | grep nvidia
```

---

### Post by mastablasta on 2015-03-24
the problem is once I install NVidia drivers it all goes dark. I can't reach CLI to even generate some debug information that NVidia provides via some script (not sure if script is included or not). so I can't really troubleshoot well after I install the drivers. 

out of curiousity and to see if console is working I hit alt+ctrl+f2 after blank screen, then tpyed in blindly my username and password. and then sudo reboot and password. nothing happened. so it looks like nothing is really working when screen goes blank.

and even if I didn't remove all pieces of NVidia I can not help but wonder why new Kubuntu live distros can not even launch.

---

### Post by tokyobadger on 2015-03-24
try [this temporary Grub](http://ask.xmodulo.com/boot-into-command-line-ubuntu-debian.html) workaround to boot into text mode

---

### Post by mastablasta on 2015-03-24
ok I will do later when I get home. I have "remote assistant" helping me now. oh and by the way your command gave out nothing, so looks like it was all cleaned.

```

[FONT=Times New Roman][COLOR=#000000]:~$dpkg -l | grep nvidia
:~$ 
[/COLOR][/FONT]
```

I am really out of ideas. my bro said reformat & reinstall. but I can't get this NVidia card on Linux to boot with live CD (ok maybe I could install via minimal iso but then what. and I am not even sure reinstall would help.

thanks for the text command btw. this could come in handy.

I was thinking the only thing left to do is to stick this card into a windows PC  and see what happens there. and move the one from there into Linux PC. wont' be ideal. it's a radeon and they also get crashes (something I am trying to solve in Linux by replacing ATI/AMD with Nvidia). But at least we would know if card is working or not. perhaps it's again just too new model. I actually wanted to get Palit's with 64bit memory width. but they ran out. or maybe I should try to get GT 630 only it seems ridiculous since price range is the same for half the power.

I've checked the official readme files and the message in kernel log could point to something wrong in BIOS, however mine does not refer to BIOS. it's just the most similar.

my log:
```
Mar 23 17:41:21 tatie-desktop kernel: [   31.005799] NVRM: RmInitAdapter failed! (0x26:0x65:1292)
Mar 23 17:41:21 tatie-desktop kernel: [   31.005814] NVRM: rm_init_adapter failed for device bearing minor number 0
Mar 23 17:41:21 tatie-desktop kernel: [   31.005847] NVRM: nvidia_frontend_open: minor 0, module->open() failed, error -5
```

NVidia messages : [http://us.download.nvidia.com/XFree86/Linux-x86/346.47/README/commonproblems.html](http://us.download.nvidia.com/XFree86/Linux-x86/346.47/README/commonproblems.html) :
[TABLE]
[TR="class: question"]
[TD="align: left"]**[B]Why does the VBIOS fail to load on my Optimus system?**
 
[/B] 
[/TD]
[/TR]
[TR="class: answer"]
[TD="align: left"][/TD]
[TD="align: left"]On some notebooks with Optimus graphics, the NVIDIA driver may not be able to retrieve the Video BIOS due to interactions between the System BIOS and the Linux kernel's ACPI subsystem. On affected notebooks, applications that require the GPU will fail, and messages like the following may appear in the system log:
NVRM: failed to copy vbios to system memory.
NVRM: RmInitAdapter failed! (0x30:0xffffffff:858)
NVRM: rm_init_adapter(0) failed
Such problems are typically beyond the control of the NVIDIA driver, which relies on proper cooperation of ACPI and the System BIOS to retrieve important information about the GPU, including the Video BIOS.
[/TD]
[/TR]
[/TABLE]

why is it behaving like I have optimus and furthermore I do not get the vbios line in my errors?

found another one in chapter 9 known issues (could this be the one?!):

> [Driver fails to initialize when MSI interrupts are enabledThe Linux NVIDIA driver uses Message Signaled Interrupts (MSI) by default. This provides compatibility and scalability benefits, mainly due to the avoidance of IRQ sharing.
Some systems have been seen to have problems supporting MSI, while working fine with virtual wire interrupts. These problems manifest as an inability to start X with the NVIDIA driver, or CUDA initialization failures. The NVIDIA driver will then report an error indicating that the NVIDIA kernel module does not appear to be receiving interrupts generated by the GPU.
Problems have also been seen with suspend/resume while MSI is enabled. All known problems have been fixed, but if you observe problems with suspend/resume that you did not see with previous drivers, disabling MSI may help you.
NVIDIA is working on a long-term solution to improve the driver's out of the box compatibility with system configurations that do not fully support MSI.
MSI interrupts can be disabled via the NVIDIA kernel module parameter "NVreg_EnableMSI=0". This can be set on the command line when loading the module, or more appropriately via your distribution's kernel module configuration files (such as those under /etc/modprobe.d/).


---

### Post by tokyobadger on 2015-03-24
Since it's a newer card I'd try the nvidia-346 drivers.

It may help others to help you by listing the hardware set-up. As frustrating as the process is, when something doesn't work you have to go through a process of elimination to pinpoint you're underlying issue.

---

### Post by mastablasta on 2015-03-24
I did try those.

I also found a similar issue here: [https://devtalk.nvidia.com/default/topic/776693/nvrm-rminitadapter-failed-with-gigabyte-gtx-750-on-kubuntu-and-arch/](https://devtalk.nvidia.com/default/topic/776693/nvrm-rminitadapter-failed-with-gigabyte-gtx-750-on-kubuntu-and-arch/)user solved it by upgradeing BIOS. however my BIOS is supposedly already at max version and officially radeon 4xxx cards are supported. so pcie 2.0 cards. does this mean card is just not supported by the motherboard+linux combo?

the other one is no better as the board is even older. should I try to get an older card (630)? or just another OS? :P

oh right system specs:
Celeron E3300 - 2,4 Ghz (I believe)
ASRock [4CoreDual-SATA2]("http://www.asrock.com/mb/VIA/4COREDUAL-SATA2/index.asp?cat=")
2 GB DDR2 ram 800mMhz dual channel Corsair but clocked at 667Mhz
Seagate Baracuda HDD - 1 TB SATA
WD green 750 GB SATA
DVD drive +
CD drive
Asus Monitor - now this I need to check the model. I doubt it's the monitor issue since the much newer LG TV didn't work and that one works with no issues in all versions including in RPi.
It has HD VIA sound chip built in. VIA and Linux don't mix. anyway it's an Intel HD chip actually.
Currently the GPU is ATI Radeon 9600 XT 256 MB AGP - working good expect crashes in some openGL games.

motherboard:
> 
[LIST=1]
[*]LGA 775 for Intel[SUP][SIZE=2]®[/SIZE][/SUP] Core™ 2 Quad / Core™ 2 Extreme / Core™ 2 Duo / Pentium[SUP][SIZE=2]®[/SIZE][/SUP] XE / Pentium[SUP][SIZE=2]®[/SIZE][/SUP] D / Pentium[SUP][SIZE=2]®[/SIZE][/SUP] Dual Core / Pentium[SUP][SIZE=2]®[/SIZE][/SUP] 4 / Celeron[SUP][SIZE=2]®[/SIZE][/SUP] / Celeron[SUP][SIZE=2]®[/SIZE][/SUP] D, supporting Quad Core Kentsfield processors
[*]VIA[SUP][SIZE=2]®[/SIZE][/SUP] PT880 Pro/PT880 Ultra Chipsets
[*]Supports FSB1066/800/533MHz processors and H-T Technology
[*]Supports Dual Channel DDR2 667 (DDR2 x 2 DIMM slots) and DDR400 (DDR x 2 DIMM slots)
[*]Untied Overclocking : During Overclocking, FSB enjoys better margin due to fixed AGP/PCIE/ PCI Buses
[*]1 x PCI Express Graphics slot (@ x4 mode)
[*]1 x AGP 8X slot
[*][Hybrid Booster]("http://www.asrock.com/feature/HybridBooster/HybridBooster.html") - Safe Overclocking Technology
[*]2 x SATA2 3.0 Gb/s connectors, support RAID (RAID 0, RAID 1, and JBOD) and Hot Plug functions
[*]HDMI_SPDIF header, providing SPDIF audio output to HDMI VGA card, allows the system to connect HDMI Digital TV/projector/LCD devices.
[*]7.1 CH Windows[SUP][SIZE=2]®[/SIZE][/SUP] Vista™ Premium Level HD Audio (ALC888 Audio Codec), 10/100 Ethernet LAN
[*]Windows[SUP][SIZE=2]®[/SIZE][/SUP] Vista™ Premium 2007 Logo Ready
[*]HD 8CH I/O: 4 ready-to-use USB 2.0 ports, HD 7.1 channel audio jacks
[/LIST]


---

### Post by mastablasta on 2015-03-26
BUMP - if anyone knows what's up - I added current Hardware info (NVidia card not inserted)

---

### Post by oldfred on 2015-03-26
Some newer Asrock cards have extra SATA Asmedia ports that cause issues of any device plugged into them.
I to not see a reference to them, so maybe you do not have them.
Not sure if VIA an issue or not. 
I have had two different LGA775 boards but Intel chips that worked without issue.

---

### Post by mastablasta on 2015-03-27
well I guess this is it. I posted on NVidia forums, sent question to NVidia and was met with silence. only the manufacturer replied with a generic response - "of course it works in PCIe 1, have you checked the manual on how to install drivers?". the only thing left is to test the PCI slot with a different card and to test this card in a different system. although since it worked with opensource driver then it is all probably working just not the drivers. one thing that puzzles me is how come when I first inserted the card I got better resolution with nouveau and it all worked faster. just resolution was wrong after I installed the NVidia drivers I can't get passed 640x480. in any case this second attempt at getting a new graphics card into older hardware seems to also be a failure.
also NVidia support is bad. not with drivers but their tech support. how can they leave a customer for 4 days with no answer at all.

---

### Post by mastablasta on 2015-03-27
i am about to give up. i took the card into the other old PC with Windows XP on it. the card works fine. 

i then moved the Radeon HD 3650 PCIe from that old pc into this one i am trying to upgrade. the PC booted fine, resoluiton recognised etc. so PCIe port seems to be working. i ran the glmark and it passed it (note: the current old card can not pass last 2 or 3 tests). i then tried to ran some OpenGL games (supertux cart , enemy territory, doomsday jdoom doom engine). it crashed on all occassions. mouse stillworked but no windows worked. i coudl still switch to tty and reboot. might be somethign to do with user's settings?! i removed the xorg didn't help. 

in any case i would say this adventure points to two things - bad nvidia drivers (remember how opensource ones kind of worked but at bad resolution?!) + bad motherboard design/BIOS. i think it's itme to start aving up for a new PC or maybe some console for the kids (but they have such expencive games).

---

### Post by tokyobadger on 2015-03-28
It could be the new card on PCIe 1.? - might be just exotic enough for the linux nvidia-drivers to not work (they're supposed to be universal though so...)
I've had horrible experiences (long long ago) with VIA and *nix so the earlier comment on that possibility could also be a pointer.

I have run into issues with nvidia over the years but they have paled against what I read about ATI (now AMD) users were facing (and there used to be more players like Matrox etc) and I think their commitment to continuing driver support (even if closed) is still worthy of praise - I have driver release 349.12 for my GTX680 - if I had Windows I'd have 347.88 - there were 3 releases in the 343 series and 4 releases in the 346 series; as far as I understand only Intel is putting in similar effort these days.

Without physically being there, I'm kind of loathe to say that your hardware won't work. I've run into problems with display many times and after a bit of time away I usually find the solution, and usually (not always) it was something I overlooked.

---

### Post by mastablasta on 2015-03-28
Actually AMD is moving more and more of it's drivers into opensource. unlike nvidia they are actually helping with opensource drivers, which is why these days opensource are not far behind the closed source fglrx. i read somewhere that their goal is to actually move it all into FOSS like intel.

this card works well in iwndows on another PC. i dont' plan to install widnows here on linux PC. my guess it it has somethign to do with motherboard or BIOS. the issue that AMD card (officially supported by motherboard manufacturer) showed on same PC kind of points to this. it could be a setting needs to be made in BIOS. perhaps somethign with voltage or something like that. i thikn i will try same AMD card in the other PC under live linux boot see if it can run the games or not.

well my issue was escalated at nvidia tech support. le'ts see if they can help. otherwise i will just make do with what i have and save for another PC (or at least the motherboard). just kind of dissapointed it didnt' all work out of the box so i could just get on with it.

EDIT: if anyone knwos about hardware, motherboards and BISO here are the various settings available in BIOS related to PCIE. i am not sure what they do exactly and explanation is mostly it enables this or disables that:
[B]
2.18 Untied Overclocking Technology[/B]
This motherboard supports Untied Overclocking Technology, which means during
overclocking, FSB enjoys better margin due to fixed AGP / PCI / PCIE bus. You may
set &#8220;CPU Host Frequency&#8221; option of BIOS setup to [Auto], which will show you
the actual CPU host frequency in the following item. Therefore, CPU FSB is untied
during overclocking, but AGP / PCI / PCIE bus is in the fixed mode so that FSB can
operate under a more stable overclocking environment.

**PCIE Clock**
Use this item to select PCIE clock. Configuration options: [Auto], [Sync with
CPU] and [100 MHz].

**PCIE Downstream Pipeline**
This allows you to enable or disable the feature of PCIE Downstream Pipeline.
The default value is [Auto].

**PCI Delay Transaction**
Enable PCI Delay Transaction feature will free the PCI Bus when the CPU is
accessing 8-bit ISA cards. Disable this feature when using ISA cards that
are not PCI 2.1 compliant.

**PCIE Downstream Pipeline**
This allows you to enable or disable the feature of PCIE Downstream Pipeline.
The default value is [Auto].

---

### Post by tokyobadger on 2015-03-29
I had another look at your /var/log/Xorg.0.log on the first page of this thread
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-46-generic root=UUID=3f43c7a8-003b-4564-9f0d-a7a4c0393e06 ro quiet splash xforcevesa
```
and compared it to mine
```
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-10-generic root=UUID=84981009-575e-484d-a6f2-354b06036c8e ro elevator=noop quiet splash nomodeset video=uvesafb:mode_option=2560x1600-32,mtrr=3,scroll=ywrap
```
Maybe change xforcevesa to nomodeset

---

### Post by mastablasta on 2015-03-29
nah, xforcevesa was just a try to get it working after nomodeset failed.

---

### Post by mastablasta on 2015-04-07
Well NVidia also didn't know where the problem is, so I returned the card. I think  we can now close this. 

it seems a combination of BIOS, the way NVidia drivers and Linux kernel interfaces with hardware and the chip influenced the experience. I saw I was not alone with this chip's issues. but others somehow, someway managed to resolve it. in Windows the card worked fine. motherboard is also good as AMD card worked in it. so much for NVidia on Linux. it is my first NVidia ever. I will now join in Linus's opinion toward NVidia. :P

also their troubleshooting script should be run like dmesg or just simply log the stuff, rather than pull info from various logs. otherwise how are you supposed to run it on a PC where monitor that doesn't work and on computer that is not responding to keyboard commands after the X crash?

---

