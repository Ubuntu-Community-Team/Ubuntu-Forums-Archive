---
title: "nVidia gt 520"
date: 2013-01-26
forum: Hardware
---

### Post by dah81 on 2013-01-26
I know there's already quite a few threads on this and some have kinda of helped, but I still can't get this working.

I have an HTPC hooked up to my Panasonic 1080p Plasma with an HDMI cable.
TV: [Panasonic TC-P50G15]("http://shop.panasonic.com/shop/model/TC-P50G15?t=specs&support#tabs")
CPU: Intel Core 2 Duo E6300
Mobo: [Gigabyte GA-EP45-UD3L P45]("http://ca.gigabyte.com/products/product-page.aspx?pid=3285#sp")
Vid: [Gigabyte Nvidia GeForce GT 520 GV-N520SL-1GI]("http://www.gigabyte.com/products/product-page.aspx?pid=4006#sp")

I originally couldn't get audio through HDMI with Nouveau and I read that it needs the Nvidia proprietary driver.

Tried Ubuntu 12.04.1, 12.10, Lubuntu 12.04.1, 12.10, XBMCbuntu 11.0, 12.0 RC3 with the following.

What I've tried (I fresh re-installed each of the above OS's after each try):
Fresh install, install all software updates, activate nvidia-current in jockey. Reboot, shows blank aubergine screen right after GRUB loads. Fixed GRUB and Plymouth using this tutorial: [http://jechem.blogspot.ca/2011/04/fix-plymouth-splash-screen-in-ubuntu-on.html](http://jechem.blogspot.ca/2011/04/fix-plymouth-splash-screen-in-ubuntu-on.html)
It then will show the Plymouth them but then boots straight to tty and startx then fails.

I've tried with the x-swat ppa and the xorg-edgers ppa. I've also tried installing the Nvidia drivers from the website using this tut: [http://ubuntuforums.org/showpost.php?p=12429420&postcount=1124](http://ubuntuforums.org/showpost.php?p=12429420&postcount=1124)
I've tried with nvidia-current, nvidia-current-updates, nvidia-experimental-310, and the newest on nvidia.com

My Xorg.0.log has this error no matter what I try
```
(EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.
```My xorg.conf looks like:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 520"
    BusID "PCI:01:00:0"
EndSection
```of course I need to end this post with the requisite "it all worked in windows 7"...grrr, don't you just hate reading that?

Any help would be appreciated!

---

### Post by dah81 on 2013-01-27
bump? any ideas anyone?

---

### Post by papibe on 2013-01-27
Hi dah81.

Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste the file here: [paste.ubuntu.com]("http://paste.ubuntu.com/"), and post back the link to it.

Regards.

---

### Post by dah81 on 2013-01-29
Thank you!
[http://paste.ubuntu.com/1584667/](http://paste.ubuntu.com/1584667/)

---

### Post by ooleyguy on 2013-01-29
You can get the "current" "approved" nVidia drivers doing the following:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

I don't know if this will fix your problems, but it did mine and I have a seemingly stable system with the 304.xx drivers installed and the nVidia settings tool and all that.

[http://news.softpedia.com/news/How-to-Install-The-Latest-Nvidia-Driver-on-Ubuntu-12-04-295542.shtml](http://news.softpedia.com/news/How-to-Install-The-Latest-Nvidia-Driver-on-Ubuntu-12-04-295542.shtml) may offer more help and hope.

---

### Post by papibe on 2013-01-29
Thanks.

Unfortunately there's no much information in the log. There's a bunch of people that have solved their Nvidia card issues by adding the nomodeset option to grub.

I would try that first. Take a look at the first answer  [here]("http://askubuntu.com/questions/140640/nvidia-drivers-and-kernel-update-problems-nomodeset") to see how to do it.

Let us know how it goes.
Regards.

---

### Post by dah81 on 2013-01-29
I added
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1920x1080-24,mtrr=3,scroll=ywrap"
```to GRUB already, that is the only way I even get past Plymouth.

I have already tried x-swat's nvidia-current with the same results.

Any other ideas?

---

### Post by papibe on 2013-01-29
Could you post the result of these commands?
```
lspci -nnk | grep -iA2 vga

sudo lshw -C display
```
Regards.

---

### Post by dah81 on 2013-01-29
lspci -nnk | grep -iA2 vga
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119 [GeForce GT 520] [10de:1040] (rev a1)
        Subsystem: Giga-byte Technology Device [1458:352f]
        Kernel driver in use: nvidia
```

sudo lshw -C display
```
  *-display
       description: VGA compatible controller
       product: GF119 [GeForce GT 520]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fb000000-fbffffff memory:e0000000-e7ffffff memory:ee000000-efffffff ioport:ef00(size=128) memory:e8000000-e807ffff
```

---

### Post by dah81 on 2013-01-31
bump again? any ideas?

---

### Post by typhoon_tip on 2013-01-31
Your installs are all correct, xorg file is totally wrong. After install, just run:
```
sudo nvidia-xconfig
```

... then reboot, it will start to work normally. For some unknown reasons the file don't get created correctly after the install.

Cheers,
Simone

---

### Post by dah81 on 2013-02-01
reinstalled the OS from scratch again. went through the same steps.

after nvidia-xconfig
xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 310.32  (buildmeister@swio-display-x86-rhel47-09)  Mon Jan 14 15:46:49 PST 2013

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```still no luck.

/var/log/Xorg.0.log
```
[   398.778]
X.Org X Server 1.12.3
Release Date: 2012-07-09
[   398.779] X Protocol Version 11, Revision 0
[   398.779] Build Operating System: Linux 2.6.24-31-xen i686 Ubuntu
[   398.779] Current Operating System: Linux xbmc 3.5.0-18-generic #29-Ubuntu SMP Wed Oct 24 19:51:55 UTC 2012 i686
[   398.779] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-18-generic root=UUID=192c0fa8-f5c3-4b18-8f16-9821a417140c ro quiet splash video=uvesafb:mode_option=1920x1080-24,mtrr=3,scroll=ywrap
[   398.779] Build Date: 09 July 2012  05:18:23PM
[   398.779] xorg-server 2:1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz~precise (For technical support please see http://www.ubuntu.com/support)
[   398.779] Current version of pixman: 0.28.2
[   398.779]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[   398.779] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   398.779] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 31 21:51:20 2013
[   398.779] (==) Using config file: "/etc/X11/xorg.conf"
[   398.779] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   398.780] (==) ServerLayout "Layout0"
[   398.780] (**) |-->Screen "Screen0" (0)
[   398.780] (**) |   |-->Monitor "Monitor0"
[   398.780] (**) |   |-->Device "Device0"
[   398.780] (**) |-->Input Device "Keyboard0"
[   398.780] (**) |-->Input Device "Mouse0"
[   398.780] (==) Automatically adding devices
[   398.780] (==) Automatically enabling devices
[   398.780] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   398.780]    Entry deleted from font path.
[   398.780] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   398.780]    Entry deleted from font path.
[   398.780] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   398.780]    Entry deleted from font path.
[   398.780] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[   398.780]    Entry deleted from font path.
[   398.780] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   398.780]    Entry deleted from font path.
[   398.780] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   398.780]    Entry deleted from font path.
[   398.780] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   398.780]    Entry deleted from font path.
[   398.780] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        built-ins
[   398.780] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   398.780] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   398.780] (WW) Disabling Keyboard0
[   398.780] (WW) Disabling Mouse0
[   398.781] (II) Loader magic: 0xb77b45a0
[   398.781] (II) Module ABI versions:
[   398.781]    X.Org ANSI C Emulation: 0.4
[   398.781]    X.Org Video Driver: 12.0
[   398.781]    X.Org ANSI C Emulation: 0.4
[   398.781]    X.Org Video Driver: 12.0
[   398.781]    X.Org XInput driver : 16.0
[   398.781]    X.Org Server Extension : 6.0
[   398.782] (--) PCI:*(0:1:0:0) 10de:1040:1458:352f rev 161, Mem @ 0xfb000000/16777216, 0xe0000000/134217728, 0xee000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[   398.782] (--) PCI: (0:5:1:0) 14f1:5b7a:0070:7400 rev 0, Mem @ 0xf0000000/67108864
[   398.782] (II) Open ACPI successful (/var/run/acpid.socket)
[   398.782] (II) LoadModule: "extmod"
[   398.782] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   398.782] (II) Module extmod: vendor="X.Org Foundation"
[   398.783]    compiled for 1.12.3, module version = 1.0.0
[   398.783]    Module class: X.Org Server Extension
[   398.783]    ABI class: X.Org Server Extension, version 6.0
[   398.783] (II) Loading extension MIT-SCREEN-SAVER
[   398.783] (II) Loading extension XFree86-VidModeExtension
[   398.783] (II) Loading extension XFree86-DGA
[   398.783] (II) Loading extension DPMS
[   398.783] (II) Loading extension XVideo
[   398.783] (II) Loading extension XVideo-MotionCompensation
[   398.783] (II) Loading extension X-Resource
[   398.783] (II) LoadModule: "dbe"
[   398.783] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   398.783] (II) Module dbe: vendor="X.Org Foundation"
[   398.783]    compiled for 1.12.3, module version = 1.0.0
[   398.783]    Module class: X.Org Server Extension
[   398.783]    ABI class: X.Org Server Extension, version 6.0
[   398.783] (II) Loading extension DOUBLE-BUFFER
[   398.783] (II) LoadModule: "glx"
[   398.783] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[   398.820] (II) Module glx: vendor="NVIDIA Corporation"
[   398.820]    compiled for 4.0.2, module version = 1.0.0
[   398.820]    Module class: X.Org Server Extension
[   398.820] (II) NVIDIA GLX Module  310.32  Mon Jan 14 14:59:59 PST 2013
[   398.820] (II) Loading extension GLX
[   398.820] (II) LoadModule: "record"
[   398.820] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   398.820] (II) Module record: vendor="X.Org Foundation"
[   398.820]    compiled for 1.12.3, module version = 1.13.0
[   398.820]    Module class: X.Org Server Extension
[   398.820]    ABI class: X.Org Server Extension, version 6.0
[   398.820] (II) Loading extension RECORD
[   398.821] (II) LoadModule: "dri"
[   398.821] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   398.821] (II) Module dri: vendor="X.Org Foundation"
[   398.821]    compiled for 1.12.3, module version = 1.0.0
[   398.821]    ABI class: X.Org Server Extension, version 6.0
[   398.821] (II) Loading extension XFree86-DRI
[   398.821] (II) LoadModule: "dri2"
[   398.821] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   398.821] (II) Module dri2: vendor="X.Org Foundation"
[   398.821]    compiled for 1.12.3, module version = 1.2.0
[   398.821] (II) Module dri2: vendor="X.Org Foundation"
[   398.821]    compiled for 1.12.3, module version = 1.2.0
[   398.821]    ABI class: X.Org Server Extension, version 6.0
[   398.821] (II) Loading extension DRI2
[   398.821] (II) LoadModule: "nvidia"
[   398.821] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   398.822] (II) Module nvidia: vendor="NVIDIA Corporation"
[   398.822]    compiled for 4.0.2, module version = 1.0.0
[   398.822]    Module class: X.Org Video Driver
[   398.822] (II) NVIDIA dlloader X Driver  310.32  Mon Jan 14 14:40:21 PST 2013
[   398.822] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   398.822] (--) using VT number 7
[   398.834] (II) Loading sub module "wfb"
[   398.834] (II) LoadModule: "wfb"
[   398.834] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   398.834] (II) Module wfb: vendor="X.Org Foundation"
[   398.834]    compiled for 1.12.3, module version = 1.0.0
[   398.834]    ABI class: X.Org ANSI C Emulation, version 0.4
[   398.834] (II) Loading sub module "ramdac"
[   398.834] (II) LoadModule: "ramdac"
[   398.834] (II) Module "ramdac" already built-in
[   398.834] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   398.834] (==) NVIDIA(0): RGB weight 888
[   398.834] (==) NVIDIA(0): Default visual is TrueColor
[   398.834] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   398.835] (**) NVIDIA(0): Enabling 2D acceleration
[   399.285] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please
[   399.285] (EE) NVIDIA(0):     check your system's kernel log for additional error
[   399.285] (EE) NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
[   399.285] (EE) NVIDIA(0):     README for additional information.
[   399.285] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[   399.285] (EE) NVIDIA(0): Failing initialization of X screen 0
[   399.285] (II) UnloadModule: "nvidia"
[   399.285] (II) UnloadSubModule: "wfb"
[   399.285] (EE) Screen(s) found, but none have a usable configuration.
[   399.285]
Fatal server error:
[   399.285] no screens found
[   399.285]
Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
[   399.285] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   399.285]
[   400.156]  ddxSigGiveUp: Closing log
[   400.156] Server terminated with error (1). Closing log file.
```same issue as before. any other ideas?

---

### Post by typhoon_tip on 2013-02-01
Can you post the kernel log as instructed in the error ? Seems everything is normal up to the point the driver tries to enable 2D acceleration on the device...

---

### Post by dah81 on 2013-02-02
Thanks for your help!
/var/log/kern.log
[http://paste.ubuntu.com/1600336/](http://paste.ubuntu.com/1600336/)

---

### Post by typhoon_tip on 2013-02-02
Have you tried 12.10 or 12.04 ? I think the problem now may be related to a bug in kernel at this point:

```
Feb  2 00:43:12 xbmc kernel: [    5.311444] NVRM: loading NVIDIA UNIX x86 Kernel Module  310.32  Mon Jan 14 14:38:50 PST 2013
Feb  2 00:43:12 xbmc kernel: [    5.357556] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
Feb  2 00:43:12 xbmc kernel: [    5.396264] lp0: using parport0 (interrupt-driven).
Feb  2 00:43:12 xbmc kernel: [    5.402123] ACPI Warning: 0xfed1f410-0xfed1f414 SystemMemory conflicts with Region \RCRB 1 (20120320/utaddress-251)
Feb  2 00:43:12 xbmc kernel: [    5.402132] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Feb  2 00:43:12 xbmc kernel: [    5.402135] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
Feb  2 00:43:12 xbmc kernel: [    5.402138] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \GP2C 1 (20120320/utaddress-251)
Feb  2 00:43:12 xbmc kernel: [    5.402144] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Feb  2 00:43:12 xbmc kernel: [    5.402197] lpc_ich: Resource conflict(s) found affecting gpio_ich
```

This is a known bug in kernel 3.5.

Can you try the same above procedure in 12.04, since you can reinstall the system ? Remember to make the X conf file manually with nvidia-xconfig command.

Cheers,
Simone

---

### Post by dah81 on 2013-02-02
This was with 12.04 but with the xorg-edgers ppa which updated the kernel to 3.5.
So should I reinstall 12.04 but not enable that ppa so it stays at 3.2?

---

### Post by typhoon_tip on 2013-02-02
> **dah81 said:**
> This was with 12.04 but with the xorg-edgers ppa which updated the kernel to 3.5.
So should I reinstall 12.04 but not enable that ppa so it stays at 3.2?

YES, do not add any PPA, just plain install 12.04 and use the nvidia-current driver in the repository. Remember to do nvidia-xconfig after install and then reboot.

Good luck !

---

### Post by dah81 on 2013-02-05
okay, reinstalled fresh.
installed nvidia-current through jockey
ran nvidia-xconfig through terminal
rebooted.
no luck, blank screen.

xorg.conf
[http://paste.ubuntu.com/1611666/](http://paste.ubuntu.com/1611666/)

xorg.0.log
[http://paste.ubuntu.com/1611667/](http://paste.ubuntu.com/1611667/)

lspci -nnk | grep -iA2 vga
[http://paste.ubuntu.com/1611672/](http://paste.ubuntu.com/1611672/)

sudo lshw -C display
[http://paste.ubuntu.com/1611675/](http://paste.ubuntu.com/1611675/)

kern.log
[http://paste.ubuntu.com/1611677/](http://paste.ubuntu.com/1611677/)

not sure what to do from here...

---

### Post by dah81 on 2013-02-06
holy htpc batman!
solved! It was the TV Tuner card causing issues and not letting the vid card have the resources it needs.
fixed by:
[http://ubuntuforums.org/showpost.php?p=8623564&postcount=10](http://ubuntuforums.org/showpost.php?p=8623564&postcount=10)

/etc/default/grub
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vmalloc=512M nomodeset video=uvesafb:mode_option=1920x1080-24,mtrr=3,scroll=ywrap"
GRUB_GFXMODE=1920x1080
```

Thanks all that helped!

---

