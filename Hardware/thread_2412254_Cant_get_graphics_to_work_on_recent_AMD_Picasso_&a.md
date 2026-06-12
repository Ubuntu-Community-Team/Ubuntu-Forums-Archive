---
title: "Cant get graphics to work on recent AMD Picasso &amp; Radeon RX 460/560D"
date: 2019-02-10
forum: Hardware
---

### Post by lawilog on 2019-02-10
Hi,

I'm trying to get X to work on bleeding edge hardware (Asus TUF FX705DY-AU047 notebook). The automatic installation of Ubuntu 18.10 (kernel 4.18.0) leaves me a white cursor blinking on a black screen. I wrote my own xorg.conf and now have 800x600 pixel output using the "fbdev" framebuffer (yay! :-) ). Here are two lines from lspci:
```

01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Baffin [Radeon RX 460/560D / Pro 450/455/460/555/555X/560/560X] (rev e5)
05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Picasso (rev c2)
```

When running X -configure it creates 3 device sections with bus ids "1:0:0", "5:0:0" and "5:0:1". In the ideal case, this would allow me hybrid graphics, i.e. desktop stuff on the integrated card and "GPU offloading" to the dedicated card for, e.g., games. For now, I would be happy to get full screen resolution (1920x1080 or so) over any of the cards.

I tried several combinations of the 3 BusIDs and Drivers ("amdgpu", "ati", "radeon", "vesa") in the xorg.conf. None worked: "radeon" gives a dead black screen with blincking cursor (requireing hard restart) all the others cause a crash of X with error messages. I will attach the Xorg log for amdgpu.

I also downloaded the picasso_*.bin files from [https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/amdgpu](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/tree/amdgpu) and copied them into /lib/firmware/amdgpu  - this does not seem to have any effect.

On [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics) it was mentioned to update grub with the kernel line radeon.modeset=1, but that didn't help either.

By the way: I also booted a recent manjaro linux (kernel 4.19.13), same problem.

Any advise for what else I could try? Any more info that I could provide and would be helpful?

Best,
Lars

PS: For people with the same hardware: The WiFi driver is not (yet?) in the kernel, but it worked for me by using [https://askubuntu.com/questions/1071299/how-to-install-wi-fi-driver-for-realtek-rtl8821ce-on-ubuntu-18-04](https://askubuntu.com/questions/1071299/how-to-install-wi-fi-driver-for-realtek-rtl8821ce-on-ubuntu-18-04) .

xorg.conf
> 
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/Type1"
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
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "amdgpu"
    BusID       "PCI:1:0:0"
#    BusID       "PCI:5:0:0"
#    BusID       "PCI:5:0:1"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Modes "1920x1080" "1024x768" "1024x624"
    EndSubSection
EndSection


Xorg.1.log
> 
[   446.699] 
X.Org X Server 1.20.1
X Protocol Version 11, Revision 0
[   446.699] Build Operating System: Linux 4.4.0-138-generic x86_64 Ubuntu
[   446.699] Current Operating System: Linux andreeasNotebook 4.18.0-15-generic #16-Ubuntu SMP Thu Feb 7 10:56:39 UTC 2019 x86_64
[   446.699] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.18.0-15-generic root=UUID=bac2ad0c-9a31-43d0-bb2e-617b0381a9c1 ro quiet splash radeon.modeset=1 vt.handoff=1
[   446.699] Build Date: 25 October 2018  02:53:34PM
[   446.699] xorg-server 2:1.20.1-3ubuntu2.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   446.699] Current version of pixman: 0.34.0
[   446.699]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   446.699] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   446.699] (==) Log file: "/var/log/Xorg.1.log", Time: Sun Feb 10 11:27:13 2019
[   446.699] (++) Using config file: "xorg.conf.amd"
[   446.699] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   446.699] (==) ServerLayout "X.org Configured"
[   446.699] (**) |-->Screen "Screen0" (0)
[   446.699] (**) |   |-->Monitor "Monitor0"
[   446.700] (**) |   |-->Device "Card0"
[   446.700] (**) |-->Input Device "Mouse0"
[   446.700] (**) |-->Input Device "Keyboard0"
[   446.700] (==) Automatically adding devices
[   446.700] (==) Automatically enabling devices
[   446.700] (==) Automatically adding GPU devices
[   446.700] (==) Automatically binding GPU devices
[   446.700] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   446.700] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   446.700]     Entry deleted from font path.
[   446.700] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   446.700]     Entry deleted from font path.
[   446.700] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   446.700]     Entry deleted from font path.
[   446.700] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   446.700]     Entry deleted from font path.
[   446.700] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   446.700]     Entry deleted from font path.
[   446.700] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   446.700]     Entry deleted from font path.
[   446.700] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   446.700] (**) ModulePath set to "/usr/lib/xorg/modules"
[   446.700] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   446.700] (WW) Disabling Mouse0
[   446.700] (WW) Disabling Keyboard0
[   446.700] (II) Loader magic: 0x55f215439020
[   446.700] (II) Module ABI versions:
[   446.701]     X.Org ANSI C Emulation: 0.4
[   446.701]     X.Org Video Driver: 24.0
[   446.701]     X.Org XInput driver : 24.1
[   446.701]     X.Org Server Extension : 10.0
[   446.702] (--) using VT number 2

[   446.702] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[   446.702] (II) xfree86: Adding drm device (/dev/dri/card0)
[   446.706] (--) PCI: (1@0:0:0) 1002:67ef:1043:1eae rev 229, Mem @ 0xe0000000/268435456, 0xf0000000/2097152, 0xfea00000/262144, I/O @ 0x0000f000/256, BIOS @ 0x????????/131072
[   446.706] (--) PCI:*(5@0:0:0) 1002:15d8:1043:1eae rev 194, Mem @ 0xc0000000/268435456, 0xd0000000/2097152, 0xfe600000/524288, I/O @ 0x0000b000/256
[   446.706] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[   446.706] (II) LoadModule: "glx"
[   446.706] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   446.707] (II) Module glx: vendor="X.Org Foundation"
[   446.707]     compiled for 1.20.1, module version = 1.0.0
[   446.707]     ABI class: X.Org Server Extension, version 10.0
[   446.707] (II) LoadModule: "amdgpu"
[   446.707] (II) Loading /usr/lib/xorg/modules/drivers/amdgpu_drv.so
[   446.711] (II) Module amdgpu: vendor="X.Org Foundation"
[   446.711]     compiled for 1.20.1, module version = 18.1.0
[   446.711]     Module class: X.Org Video Driver
[   446.711]     ABI class: X.Org Video Driver, version 24.0
[   446.711] (II) AMDGPU: Driver for AMD Radeon:
    All GPUs supported by the amdgpu kernel driver
[   446.983] (II) AMDGPU(0): [KMS] Kernel modesetting enabled.
[   446.985] (==) AMDGPU(0): Depth 24, (--) framebuffer bpp 32
[   446.985] (II) AMDGPU(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   446.985] (==) AMDGPU(0): Default visual is TrueColor
[   446.985] (==) AMDGPU(0): RGB weight 888
[   446.985] (II) AMDGPU(0): Using 8 bits per RGB (8 bit DAC)
[   446.985] (--) AMDGPU(0): Chipset: "Radeon RX 560 Series" (ChipID = 0x67ef)
[   446.985] (II) Loading sub module "fb"
[   446.985] (II) LoadModule: "fb"
[   446.985] (II) Loading /usr/lib/xorg/modules/libfb.so
[   446.985] (II) Module fb: vendor="X.Org Foundation"
[   446.985]     compiled for 1.20.1, module version = 1.0.0
[   446.985]     ABI class: X.Org ANSI C Emulation, version 0.4
[   446.985] (II) Loading sub module "dri2"
[   446.985] (II) LoadModule: "dri2"
[   446.985] (II) Module "dri2" already built-in
[   447.070] (II) Loading sub module "glamoregl"
[   447.070] (II) LoadModule: "glamoregl"
[   447.070] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[   447.074] (II) Module glamoregl: vendor="X.Org Foundation"
[   447.074]     compiled for 1.20.1, module version = 1.0.1
[   447.074]     ABI class: X.Org ANSI C Emulation, version 0.4
[   447.092] (II) AMDGPU(0): glamor X acceleration enabled on Radeon RX 560 Series (POLARIS11, DRM 3.26.0, 4.18.0-15-generic, LLVM 7.0.0)
[   447.092] (II) AMDGPU(0): glamor detected, initialising EGL layer.
[   447.092] (==) AMDGPU(0): TearFree property default: auto
[   447.092] (II) AMDGPU(0): KMS Pageflipping: enabled
[   447.092] (WW) AMDGPU(0): No outputs definitely connected, trying again...
[   447.092] (WW) AMDGPU(0): Unable to find connected outputs - setting 1024x768 initial framebuffer
[   447.092] (II) AMDGPU(0): mem size init: gart size :ff96f000 vram size: s:ffad8000 visible:fad8000
[   447.092] (==) AMDGPU(0): DPI set to (96, 96)
[   447.092] (==) AMDGPU(0): Using gamma correction (1.0, 1.0, 1.0)
[   447.092] (II) Loading sub module "ramdac"
[   447.092] (II) LoadModule: "ramdac"
[   447.092] (II) Module "ramdac" already built-in
[   447.092] (EE) AMDGPU(0): No modes.
[   447.093] (II) UnloadModule: "amdgpu"
[   447.093] (II) UnloadSubModule: "glamoregl"
[   447.093] (II) Unloading glamoregl
[   447.093] (II) UnloadSubModule: "fb"
[   447.093] (II) Unloading fb
[   447.093] (EE) Screen(s) found, but none have a usable configuration.
[   447.093] (EE) 
Fatal server error:
[   447.093] (EE) no screens found(EE) 
[   447.093] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   447.093] (EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[   447.093] (EE) 
[   447.095] (EE) Server terminated with error (1). Closing log file.


---

### Post by lawilog on 2019-02-10
Ha! A kernel update helped. At least, I can now use fbdev with 1920x1080 resolution. However, the "amdgpu" driver is still not working.

(So I downloaded from [https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/) : in version 4.20.7 the linux-headers-*_all.deb , linux-headers-*-generic_*.deb , linux-image-unsigned-*-generic_*.deb , linux-modules-*-generic_*.deb in the amd64 version and `sudo dpkg -i *.deb` them)

(On a side note, Xorg's log is flooded with "(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument", maybe that has to do with the incompatibility of the latest, now-installed kernel and an older Xorg?)

---

### Post by lawilog on 2019-02-10
Huh. Installing the latest graphics drivers helped! (to get full resolution) :-)

[FONT=courier new]  sudo add-apt-repository ppa:oibaf/graphics-drivers && sudo apt update && sudo apt upgrade[/FONT]

I will try to mark this as "Solved". Will try to figure out hybrid graphics later.

---

### Post by lavs2 on 2019-03-23
For hybrid graphics: older howtos tell you to set the offload device with xrandr. This seems to be no longer necessary. **It just works by prefixing "DRI_PRIME=1 "**: :D
> $ glxinfo | grep "OpenGL renderer"
OpenGL renderer string: AMD RAVEN (DRM 3.27.0, 5.0.3-050003-generic, LLVM 8.0.0)

> $ DRI_PRIME=1 glxinfo | grep "OpenGL renderer"
OpenGL renderer string: Radeon RX 560 Series (POLARIS11, DRM 3.27.0, 5.0.3-050003-generic, LLVM 8.0.0)

real world example: ;-)
DRI_PRIME=1 steam steam://rungameid/289070

Just for reference (and others with this hardware): I upgraded to mainline kernel 5.0.3 now and I'm using the bleeding edge graphic drivers in this ppa: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers) . I also did a BIOS-update (for this particular notebook [https://www.asus.com/me-en/Laptops/ASUS-TUF-Gaming-FX705DY/HelpDesk_BIOS/](https://www.asus.com/me-en/Laptops/ASUS-TUF-Gaming-FX705DY/HelpDesk_BIOS/)  which got keyboard backlight to work!).

I want to mention that I still got errors in the system logs. However, things seem to work nevertheless. For reference, here are some messages I see (some might not be GPU-related):
In dmesg:
> [    0.336160] ACPI BIOS Error (bug): Could not resolve [\_SB.PCI0.GPP0.SWUS], AE_NOT_FOUND (20181213/dswload2-160)
[    0.336168] ACPI Error: AE_NOT_FOUND, During name lookup/catalog (20181213/psobject-221)
[    1.329546] ACPI Error: Attempt to CreateField of length zero (20181213/dsopcode-134)
[    1.329610] ACPI Error: Method parse/execution failed \_SB.PCI0.GP17.VGA.ATRM, AE_AML_OPERAND_VALUE (20181213/psparse-531)
[    1.579869] [drm] amdgpu: 128M of VRAM memory ready
[    1.579870] [drm] amdgpu: 3072M of GTT memory ready.
[    1.579887] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    1.821799] [drm:construct [amdgpu]] *ERROR* construct: Invalid Connector ObjectID from Adapter Service for connector index:2! type 0 expected 3
[    1.821863] [drm:construct [amdgpu]] *ERROR* construct: Invalid Connector ObjectID from Adapter Service for connector index:3! type 0 expected 3
[    1.847146] fbcon: amdgpudrmfb (fb0) is primary device

> $ journalctl -b | egrep 'smpboot.*AMD|modesetting'
Mar 23 09:39:09 TUF kernel: smpboot: CPU0: AMD Ryzen 5 3550H with Radeon Vega Mobile Gfx (family: 0x17, model: 0x18, stepping: 0x1)
Mar 23 09:39:09 TUF kernel: [drm] amdgpu kernel modesetting enabled.
Mar 23 09:39:09 TUF kernel: [drm] initializing kernel modesetting (POLARIS11 0x1002:0x67EF 0x1043:0x1EAE 0xE5).
Mar 23 09:39:09 TUF kernel: [drm] initializing kernel modesetting (RAVEN 0x1002:0x15D8 0x1043:0x1EAE 0xC2).

> $ xandr --listproviders
Providers: number : 2
Provider 0: id: 0x7a cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 2 associated providers: 1 name:Unknown AMD Radeon GPU @ pci:0000:05:00.0
Provider 1: id: 0x44 cap: 0x6, Sink Output, Source Offload crtcs: 5 outputs: 0 associated providers: 1 name:Radeon RX 560 Series @ pci:0000:01:00.0

---

