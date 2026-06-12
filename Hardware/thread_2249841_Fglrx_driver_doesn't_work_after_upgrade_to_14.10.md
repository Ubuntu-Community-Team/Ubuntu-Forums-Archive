---
title: "Fglrx driver doesn't work after upgrade to 14.10"
date: 2014-10-24
forum: Hardware
---

### Post by gnarlin2 on 2014-10-24
I just upgraded yesterday to 14.10. 
After rebooting I got the ubuntu logo but X wouldn't start.
Anticipating possible problems I had already downloaded the fglrx driver from amd's website and uncompressed it.
I generated the deb packages and let the fglrx-installer install the packages and then rebooted. No change.
I purged the fglrx driver, the amdccc -dev, xorg.conf and everything, rebooted and got X to start using the libre/open driver.
That's fine, but I play games using wine a lot, so I really need fglrx to work like it did in 14.04.
I tried to install fglrx through the "additional drivers" tab in "software & updates", but it automagically jumps back to the open source
driver after I click apply for some reason. Something is broken, but I'm not sure what.
I've tried to run apt-get install -f to see if there were some dependency problems, but nothing.
Can someone please help me?

---

### Post by JDorfler on 2014-10-25
For some reason 14.10 doesn't like the AMD drivers from the AMD site.  You will probably need to install the drivers in the repository.  My fix action was to;

```
sudo aptitude remove fglrx
sudo aptitude install fglrx
```

---

### Post by robcharest on 2014-10-25
> **JDorfler said:**
> For some reason 14.10 doesn't like the AMD drivers from the AMD site.  You will probably need to install the drivers in the repository.  My fix action was to;

```
sudo aptitude remove fglrx
sudo aptitude install fglrx
```


I have tried that option and It did not work for me whatsoever.  On reboot, I get an error window which says that the system will load in Low-res, but It xserver simply stalls at a blank screen.  I am still waiting on a permanent solution because my laptop does not wake from suspend without the proprietary fglrx drivers



             product: BeaverCreek [Radeon HD 6520G]
             vendor: Advanced Micro Devices, Inc. [AMD/ATI]

---

### Post by okl on 2014-10-25
I've had the same problem on a ThinkPad laptop. Solved it by removing fglrx with purge option:
sudo apt-get remove fglrx* --purge
You will notice that not everything is deleted.
Please delete the following files manually:
rm -Rf /etc/ati
rm -Rf /usr/lib/fglrx
Then you can install fglrx again:
sudo apt-get install fglrx
aticonfig --initial --force

Voila.. Everything works (at least for me)

---

### Post by charboma38 on 2014-10-29
Same here, I have a black screen at start up, after the Ubuntu splash screen. Only tty* are available.
Note that, I have also observed, but not anymore, a message box saying that I run in low resolution mode.

I tried to install fglrx again and again, nothing works.

Here is my Xorg log. As one can see, there is a problem with libfglrxdrm.so "**Can't load FireGL DRM library (libfglrxdrm.so).**". Don't know if it is related.

Do you observe the same?

```

[    41.236] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[    41.236] X Protocol Version 11, Revision 0
[    41.236] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    41.236] Current Operating System: Linux botteur-de-culs 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    41.236] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=db2f8f73-b267-49f7-8f5d-bac94bc981e1 ro quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw vt.handoff=7
[    41.236] Build Date: 10 September 2014  01:10:01PM
[    41.236] xorg-server 2:1.16.0-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[    41.236] Current version of pixman: 0.32.4
[    41.236]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    41.236] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    41.236] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 28 20:53:45 2014
[    41.236] (==) Using config file: "/etc/X11/xorg.conf"
[    41.237] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    41.237] (==) ServerLayout "X.org Configured"
[    41.237] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    41.237] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    41.237] (**) |   |-->Device "aticonfig-Device[0]-0"
[    41.237] (**) |-->Input Device "Mouse0"
[    41.237] (**) |-->Input Device "Keyboard0"
[    41.237] (==) Automatically adding devices
[    41.237] (==) Automatically enabling devices
[    41.237] (==) Automatically adding GPU devices
[    41.237] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    41.237]     Entry deleted from font path.
[    41.237] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    41.237]     Entry deleted from font path.
[    41.237] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    41.237]     Entry deleted from font path.
[    41.237] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    41.237]     Entry deleted from font path.
[    41.237] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    41.237]     Entry deleted from font path.
[    41.237] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    41.237]     Entry deleted from font path.
[    41.237] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    41.237]     Entry deleted from font path.
[    41.237] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    41.237]     Entry deleted from font path.
[    41.237] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    41.237]     Entry deleted from font path.
[    41.237] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    41.237]     Entry deleted from font path.
[    41.237] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    41.237] (**) ModulePath set to "/usr/lib/xorg/modules"
[    41.237] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    41.237] (WW) Disabling Mouse0
[    41.237] (WW) Disabling Keyboard0
[    41.237] (II) Loader magic: 0x7f46bc39dd80
[    41.237] (II) Module ABI versions:
[    41.237]     X.Org ANSI C Emulation: 0.4
[    41.237]     X.Org Video Driver: 18.0
[    41.237]     X.Org XInput driver : 21.0
[    41.237]     X.Org Server Extension : 8.0
[    41.238] (--) PCI:*(0:0:1:0) 1002:1313:1849:1313 rev 0, Mem @ 0xc0000000/268435456, 0xd0000000/8388608, 0xff700000/262144, I/O @ 0x0000f000/256, BIOS @ 0x????????/131072
[    41.238] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    41.238] (WW) "xmir" is not to be loaded by default. Skipping.
[    41.238] (II) LoadModule: "glx"
[    41.238] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    41.239] (II) Module glx: vendor="X.Org Foundation"
[    41.239]     compiled for 1.16.0, module version = 1.0.0
[    41.239]     ABI class: X.Org Server Extension, version 8.0
[    41.239] (==) AIGLX enabled
[    41.239] (II) LoadModule: "fglrx"
[    41.240] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    41.260] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    41.260]     compiled for 1.4.99.906, module version = 14.30.4
[    41.260]     Module class: X.Org Video Driver
[    41.260] (II) Loading sub module "fglrxdrm"
[    41.260] (II) LoadModule: "fglrxdrm"
[    41.261] (WW) Warning, couldn't open module fglrxdrm
[    41.261] (II) UnloadModule: "fglrxdrm"
[    41.261] (II) Unloading fglrxdrm
[    41.261] (EE) Can't load FireGL DRM library (libfglrxdrm.so).
[    41.261] (II) AMD Proprietary Linux Driver Version Identifier:14.30.4
[    41.261] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-14.301.1001              
[    41.261] (II) AMD Proprietary Linux Driver Build Date: Sep 15 2014 18:11:36
[    41.261] (++) using VT number 7

[    41.261] (WW) Falling back to old probe method for fglrx
[    41.268] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    41.271] (--) Chipset Supported AMD Graphics Processor (0x1313) found
[    41.271] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:1:1) found
[    41.272] (II) fglrx(0): pEnt->device->identifier=0x7f46bd0a7d20
[    41.272] (II) fglrx(0): === [xdl_xs115_atiddxPreInit] === begin
[    41.272] (II) fglrx(0): FB driver is enabled
[    41.272] (II) Loading sub module "vgahw"
[    41.272] (II) LoadModule: "vgahw"
[    41.272] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    41.272] (II) Module vgahw: vendor="X.Org Foundation"
[    41.272]     compiled for 1.16.0, module version = 0.1.0
[    41.272]     ABI class: X.Org Video Driver, version 18.0
[    41.273] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    41.273] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    41.273] (==) fglrx(0): Default visual is TrueColor
[    41.273] (**) fglrx(0): Option "DPMS" "true"
[    41.273] (==) fglrx(0): RGB weight 888
[    41.273] (II) fglrx(0): Using 8 bits per RGB 
[    41.273] (==) fglrx(0): Buffer Tiling is ON
[    41.273] (II) Loading sub module "fglrxdrm"
[    41.273] (II) LoadModule: "fglrxdrm"
[    41.273] (WW) Warning, couldn't open module fglrxdrm
[    41.273] (II) UnloadModule: "fglrxdrm"
[    41.273] (II) Unloading fglrxdrm
[    41.273] (EE) fglrx: Failed to load module "fglrxdrm" (module does not exist, 0)
[    41.273] (EE) fglrx(0): Failed to load DRM library
[    41.273] (EE) fglrx(0): PreInit failed
[    41.273] (II) fglrx(0): === [xdl_xs115_atiddxPreInit] === end
[    41.275] (II) UnloadModule: "fglrx"
[    41.275] (II) UnloadSubModule: "vgahw"
[    41.275] (II) Unloading vgahw
[    41.275] (EE) Screen(s) found, but none have a usable configuration.
[    41.275] (EE) 
Fatal server error:
[    41.275] (EE) no screens found(EE) 
[    41.275] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    41.275] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    41.275] (EE) 
[    41.292] (EE) Server terminated with error (1). Closing log file.

```

Here is my Xorg.conf
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:0:1:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

Here are the command line I use to clear fglrx:
```

## stops graphic server
sudo service lightdm stop
## remove FGLRX
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon  
## install radeon driver
sudo apt-get install xserver-xorg-video-radeon
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
## reconfigure xorg
sudo dpkg-reconfigure xserver-xorg
sudo Xorg -configure
sudo cp xorg.conf.new /etc/X11/xorg.conf
sudo rm xorg.conf.new
## starts graphic server
sudo service lightdm start

```

---

### Post by charboma38 on 2014-10-30
> **okl said:**
> I've had the same problem on a ThinkPad laptop. Solved it by removing fglrx with purge option:
sudo apt-get remove fglrx* --purge
You will notice that not everything is deleted.
Please delete the following files manually:
rm -Rf /etc/ati
rm -Rf /usr/lib/fglrx
Then you can install fglrx again:
sudo apt-get install fglrx
aticonfig --initial --force

Voila.. Everything works (at least for me)

In my case, everything is removed,  don't have to manually remove these two folders. At least removing fglrx works... :)

---

### Post by Stephen_at on 2014-10-31
Do you have Wine installed? in 14.10 there seems to be a conflict between Wine and FGLRX

---

### Post by charboma38 on 2014-11-03
Yes, wine was installed, but I tried removing it and reinstalling FGLRX, I still have the problem.

My solution that worked:
- Make a fresh install of Ubuntu 14.10. (Easy if you do not have to much apps installed.)

However, Wine will not work out of box, since it conflicts with FGLRX. I'm waiting the SRU for [this ]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1129409")bug that I expect soon, but if you don't want to wait for it, some workaround are available, at least [here]("http://askubuntu.com/questions/540780/14-10-wine-and-fglrx-conflict").

Regards,
Matthieu.

---

### Post by dacohen on 2014-12-08
I had this same problem. I solved it by disabling the spash screen:

On file /etc/default/grub, look for this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet spash"
Change to:
GRUB_CMDLINE_LINUX_DEFAULT=""

Then:
# update-grub2

---

### Post by alexmyl91 on 2015-03-15
Having the same problem after upgrading to 14.04.2 , from what i gathered it's a problem with the new linux kernel 3.16 (if i am correct), thats why affects 14.10 and 12.04.5 too. 

I suggest you click "Affects me!" in this bug [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491) . 

And lets hope for a quick solution

---

### Post by Mark Phelps on 2015-03-15
> from what i gathered it's a problem with the new linux kernel 3.16 

More likely, it's a problem with the video chipset you have -- as the "legacy" chipsets only work with Ubuntu versions up through 12.04.1.  Upgrading beyond that loads a newer X-server version that is incompatible with the "legacy" chipset drivers.

There is no "quick solution" as the last AMD drivers for their "legacy" cards are NOT going to be updated to work with the newer X-server versions.

---

