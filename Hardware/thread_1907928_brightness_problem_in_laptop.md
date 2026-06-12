---
title: "brightness problem in laptop"
date: 2012-01-12
forum: Hardware
---

### Post by KRISHNASHK on 2012-01-12
[B]hi i just installed ubuntu 10.10 on my lenovo z 570 laptop. i am not able to change the screen brightness.even the function keys are not working. please help
thanks.
[/B]

---

### Post by KRISHNASHK on 2012-01-14
Help?????????????

---

### Post by madvinegar on 2012-01-14
Have you tried through compiz config settings manager? (under accesibility section enable "opacity, saturation and brightness").

If you don't have the compiz config settings manager you can download same via the ubuntu software center.

---

### Post by KRISHNASHK on 2012-01-15
thanks for the reply ! i downloaded that software but i am unable to change it!. I changed it using the slider. is it right o is there an other way?? thanks

---

### Post by madvinegar on 2012-01-15
The second tab is "brightness".
Press the first button (which says "increase brightness") and change the "disabled" to "enabled".

This may get your keyboard keys functional again and you can change the brightness.

---

### Post by KRISHNASHK on 2012-01-15
i did the steps that u specified. It asked me for a key configuration. I used function key with the lower brightness button . but it did not have any changes. 
But the function keys are working fine with sounds.

---

### Post by Toz on 2012-01-15
If your system comes with an nvidia video card and you are using the proprietary driver, try adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the DEVICE section of your /etc/X11/xorg.conf file (logout and back in again to test).

Otherwise, try booting with the following kernel parameters:
- **acpi_backlight=vendor**
- **acpi_osi=Linux**
- **acpi_osi=**
- **acpi_osi=Linux acpi_backlight=vendor**
See here for instructions on how to test these parameters: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot")

---

### Post by KRISHNASHK on 2012-01-16
> **Toz said:**
> If your system comes with an nvidia video card and you are using the proprietary driver, try adding:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```...to the DEVICE section of your /etc/X11/xorg.conf file (logout and back in again to test).

Otherwise, try booting with the following kernel parameters:
- **acpi_backlight=vendor**
- **acpi_osi=Linux**
- **acpi_osi=**
- **acpi_osi=Linux acpi_backlight=vendor**
See here for instructions on how to test these parameters: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot](https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot)
thanks for reply!

yes i do have a nvidia g card, but i dont have any proprietary driver for that.

But there is no file named xorg.conf

And i tried these parameter as well they did not work.

---

### Post by Toz on 2012-01-16
> **KRISHNASHK said:**
> yes i do have a nvidia g card, but i dont have any proprietary driver for that.

Do you have an option to install an nvidia driver in the Additional Drivers (Restricted Drivers) screen? See: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by KRISHNASHK on 2012-01-16
> **Toz said:**
> Do you have an option to install an nvidia driver in the Additional Drivers (Restricted Drivers) screen? See: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
no i just got an notification  for broadcom driver for wifi, i just installed them. Now wen i hit additional driver only that broad com driver is shown up.



and this is the output of grub file.


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by Toz on 2012-01-16
What do the following commands return:
```
sudo lspci -vnn | grep -A10 VGA
```
```
ls /sys/class/backlight
```

And can you post back the contents of your /var/log/Xorg.0.log file?

---

### Post by KRISHNASHK on 2012-01-17
> **Toz said:**
> What do the following commands return:
```
sudo lspci -vnn | grep -A10 VGA
``````
ls /sys/class/backlight
```And can you post back the contents of your /var/log/Xorg.0.log file?

sudo lspci -vnn | grep -A10 VGA

00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:397d]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f1000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:1050] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:397d]
    Flags: fast devsel, IRQ 16
    Memory at f0000000 (32-bit, non-prefetchable) [disabled] [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [disabled] [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [disabled] [size=32M]
    I/O ports at 3000 [disabled] [size=128]
    Expansion ROM at <ignored> [disabled]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00

ls /sys/class/backlight

no files were listed for the above,

 /var/log/Xorg.0.log

[    13.552] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    13.552] X Protocol Version 11, Revision 0
[    13.552] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    13.552] Current Operating System: Linux krishna-Ideapad-Z570 2.6.35-31-generic-pae #63-Ubuntu SMP Mon Nov 28 20:48:50 UTC 2011 i686
[    13.552] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-31-generic-pae root=UUID=a81da772-f9fe-40cc-8387-c42e1d800020 ro acpi_osi=Linux acpi_backlight=vendor quiet splash acpi_backlight=vendor
[    13.552] Build Date: 20 October 2011  03:03:54PM
[    13.552] xorg-server 2:1.9.0-0ubuntu7.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    13.552] Current version of pixman: 0.18.4
[    13.552]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    13.552] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.552] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 17 16:08:00 2012
[    13.565] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.565] (==) No Layout section.  Using the first Screen section.
[    13.565] (==) No screen section available. Using defaults.
[    13.565] (**) |-->Screen "Default Screen Section" (0)
[    13.565] (**) |   |-->Monitor "<default monitor>"
[    13.566] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    13.566] (==) Automatically adding devices
[    13.566] (==) Automatically enabling devices
[    13.566] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.566]     Entry deleted from font path.
[    13.566] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    13.566] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.566] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.566] (II) Loader magic: 0x81f8e00
[    13.566] (II) Module ABI versions:
[    13.566]     X.Org ANSI C Emulation: 0.4
[    13.566]     X.Org Video Driver: 8.0
[    13.566]     X.Org XInput driver : 11.0
[    13.566]     X.Org Server Extension : 4.0
[    13.567] (--) PCI:*(0:0:2:0) 8086:0116:17aa:397d rev 9, Mem @ 0xf1000000/4194304, 0xe0000000/268435456, I/O @ 0x00004000/64
[    13.567] (--) PCI: (0:1:0:0) 10de:1050:17aa:397d rev 161, Mem @ 0xf0000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00003000/128
[    13.567] (II) Open ACPI successful (/var/run/acpid.socket)
[    13.567] (II) LoadModule: "extmod"
[    13.579] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.579] (II) Module extmod: vendor="X.Org Foundation"
[    13.579]     compiled for 1.9.0, module version = 1.0.0
[    13.579]     Module class: X.Org Server Extension
[    13.579]     ABI class: X.Org Server Extension, version 4.0
[    13.579] (II) Loading extension MIT-SCREEN-SAVER
[    13.579] (II) Loading extension XFree86-VidModeExtension
[    13.579] (II) Loading extension XFree86-DGA
[    13.579] (II) Loading extension DPMS
[    13.579] (II) Loading extension XVideo
[    13.579] (II) Loading extension XVideo-MotionCompensation
[    13.579] (II) Loading extension X-Resource
[    13.579] (II) LoadModule: "dbe"
[    13.580] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.580] (II) Module dbe: vendor="X.Org Foundation"
[    13.580]     compiled for 1.9.0, module version = 1.0.0
[    13.580]     Module class: X.Org Server Extension
[    13.580]     ABI class: X.Org Server Extension, version 4.0
[    13.580] (II) Loading extension DOUBLE-BUFFER
[    13.580] (II) LoadModule: "glx"
[    13.580] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    13.580] (II) Module glx: vendor="X.Org Foundation"
[    13.580]     compiled for 1.9.0, module version = 1.0.0
[    13.580]     ABI class: X.Org Server Extension, version 4.0
[    13.580] (==) AIGLX enabled
[    13.580] (II) Loading extension GLX
[    13.580] (II) LoadModule: "record"
[    13.581] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.581] (II) Module record: vendor="X.Org Foundation"
[    13.581]     compiled for 1.9.0, module version = 1.13.0
[    13.581]     Module class: X.Org Server Extension
[    13.581]     ABI class: X.Org Server Extension, version 4.0
[    13.581] (II) Loading extension RECORD
[    13.581] (II) LoadModule: "dri"
[    13.581] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.581] (II) Module dri: vendor="X.Org Foundation"
[    13.581]     compiled for 1.9.0, module version = 1.0.0
[    13.581]     ABI class: X.Org Server Extension, version 4.0
[    13.581] (II) Loading extension XFree86-DRI
[    13.581] (II) LoadModule: "dri2"
[    13.581] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.581] (II) Module dri2: vendor="X.Org Foundation"
[    13.581]     compiled for 1.9.0, module version = 1.2.0
[    13.581]     ABI class: X.Org Server Extension, version 4.0
[    13.581] (II) Loading extension DRI2
[    13.581] (==) Matched intel as autoconfigured driver 0
[    13.581] (==) Matched vesa as autoconfigured driver 1
[    13.582] (==) Matched fbdev as autoconfigured driver 2
[    13.582] (==) Assigned the driver to the xf86ConfigLayout
[    13.582] (II) LoadModule: "intel"
[    13.582] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    13.582] (II) Module intel: vendor="X.Org Foundation"
[    13.582]     compiled for 1.9.0, module version = 2.12.0
[    13.582]     Module class: X.Org Video Driver
[    13.582]     ABI class: X.Org Video Driver, version 8.0
[    13.582] (II) LoadModule: "vesa"
[    13.582] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    13.582] (II) Module vesa: vendor="X.Org Foundation"
[    13.582]     compiled for 1.8.99.905, module version = 2.3.0
[    13.582]     Module class: X.Org Video Driver
[    13.582]     ABI class: X.Org Video Driver, version 8.0
[    13.582] (II) LoadModule: "fbdev"
[    13.582] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.582] (II) Module fbdev: vendor="X.Org Foundation"
[    13.582]     compiled for 1.8.99.905, module version = 0.4.2
[    13.582]     ABI class: X.Org Video Driver, version 8.0
[    13.582] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    13.583] (II) VESA: driver for VESA chipsets: vesa
[    13.583] (II) FBDEV: driver for framebuffer: fbdev
[    13.583] (++) using VT number 7

[    13.583] (WW) Falling back to old probe method for vesa
[    13.583] (WW) Falling back to old probe method for fbdev
[    13.583] (II) Loading sub module "fbdevhw"
[    13.583] (II) LoadModule: "fbdevhw"
[    13.583] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.583] (II) Module fbdevhw: vendor="X.Org Foundation"
[    13.583]     compiled for 1.9.0, module version = 0.0.2
[    13.583]     ABI class: X.Org Video Driver, version 8.0
[    13.585] drmOpenDevice: node name is /dev/dri/card0
[    13.585] drmOpenDevice: open result is 9, (OK)
[    13.585] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    13.585] drmOpenDevice: node name is /dev/dri/card0
[    13.585] drmOpenDevice: open result is 9, (OK)
[    13.585] drmOpenByBusid: drmOpenMinor returns 9
[    13.585] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    13.585] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    13.585] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    13.585] (==) intel(0): RGB weight 888
[    13.585] (==) intel(0): Default visual is TrueColor
[    13.585] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge
[    13.585] (--) intel(0): Chipset: "Unknown i8xx"
[    13.585] (==) intel(0): video overlay key set to 0x101fe
[    13.602] (II) intel(0): Output VGA1 has no monitor section
[    13.602] (II) intel(0): Output LVDS1 has no monitor section
[    13.612] (II) intel(0): Output HDMI1 has no monitor section
[    13.613] (II) intel(0): Output DP1 has no monitor section
[    13.631] (II) intel(0): EDID for output VGA1
[    13.631] (II) intel(0): EDID for output LVDS1
[    13.631] (II) intel(0): Manufacturer: AUO  Model: 22ec  Serial#: 0
[    13.631] (II) intel(0): Year: 2009  Week: 1
[    13.631] (II) intel(0): EDID Version: 1.3
[    13.631] (II) intel(0): Digital Display Input
[    13.631] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    13.631] (II) intel(0): Gamma: 2.20
[    13.631] (II) intel(0): No DPMS capabilities specified
[    13.631] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    13.631] (II) intel(0): First detailed timing is preferred mode
[    13.631] (II) intel(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.570
[    13.631] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    13.631] (II) intel(0): Manufacturer's mask: 0
[    13.631] (II) intel(0): Supported detailed timing:
[    13.631] (II) intel(0): clock: 69.3 MHz   Image Size:  344 x 193 mm
[    13.631] (II) intel(0): h_active: 1366  h_sync: 1398  h_sync_end 1422 h_blank_end 1432 h_border: 0
[    13.631] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 775 v_blanking: 806 v_border: 0
[    13.631] (II) intel(0): Unknown vendor-specific block f
[    13.631] (II) intel(0):  AUO
[    13.631] (II) intel(0):  B156XW02 V2
[    13.631] (II) intel(0): EDID (in hex):
[    13.631] (II) intel(0):     00ffffffffffff0006afec2200000000
[    13.631] (II) intel(0):     01130103802213780ac8959e57549226
[    13.631] (II) intel(0):     0f505400000001010101010101010101
[    13.631] (II) intel(0):     010101010101121b5642500026302018
[    13.631] (II) intel(0):     340058c1100000180000000f00000000
[    13.631] (II) intel(0):     00000000000000000020000000fe0041
[    13.631] (II) intel(0):     554f0a202020202020202020000000fe
[    13.631] (II) intel(0):     004231353658573032205632200a00c0
[    13.632] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    13.632] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    13.632] (II) intel(0): Printing probed modes for output LVDS1
[    13.632] (II) intel(0): Modeline "1366x768"x60.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    13.632] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    13.632] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    13.632] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    13.632] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    13.632] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    13.632] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    13.642] (II) intel(0): EDID for output HDMI1
[    13.713] (II) intel(0): EDID for output DP1
[    13.713] (II) intel(0): Output VGA1 disconnected
[    13.713] (II) intel(0): Output LVDS1 connected
[    13.713] (II) intel(0): Output HDMI1 disconnected
[    13.713] (II) intel(0): Output DP1 disconnected
[    13.713] (II) intel(0): Using exact sizes for initial modes
[    13.713] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    13.713] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    13.713] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    13.713] (==) intel(0): DPI set to (96, 96)
[    13.713] (II) Loading sub module "fb"
[    13.713] (II) LoadModule: "fb"
[    13.714] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.714] (II) Module fb: vendor="X.Org Foundation"
[    13.714]     compiled for 1.9.0, module version = 1.0.0
[    13.714]     ABI class: X.Org ANSI C Emulation, version 0.4
[    13.714] (II) UnloadModule: "vesa"
[    13.714] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    13.714] (II) UnloadModule: "fbdev"
[    13.714] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.714] (II) UnloadModule: "fbdevhw"
[    13.714] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    13.714] (==) Depth 24 pixmap format is 32 bpp
[    13.714] (**) intel(0): Tiling enabled
[    13.714] (**) intel(0): SwapBuffers wait enabled
[    13.714] (==) intel(0): VideoRam: 262144 KB
[    13.714] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    13.721] (II) UXA(0): Driver registered support for the following operations:
[    13.721] (II)         solid
[    13.721] (II)         copy
[    13.721] (II)         composite (RENDER acceleration)
[    13.721] (II)         put_image
[    13.721] (II)         get_image
[    13.721] (==) intel(0): Backing store disabled
[    13.721] (==) intel(0): Silken mouse enabled
[    13.721] (II) intel(0): Initializing HW Cursor
[    13.748] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    13.748] (==) intel(0): DPMS enabled
[    13.748] (==) intel(0): Intel XvMC decoder enabled
[    13.748] (II) intel(0): direct rendering: Disabled
[    13.748] (--) RandR disabled
[    13.748] (II) Initializing built-in extension Generic Event Extension
[    13.748] (II) Initializing built-in extension SHAPE
[    13.748] (II) Initializing built-in extension MIT-SHM
[    13.748] (II) Initializing built-in extension XInputExtension
[    13.748] (II) Initializing built-in extension XTEST
[    13.748] (II) Initializing built-in extension BIG-REQUESTS
[    13.748] (II) Initializing built-in extension SYNC
[    13.748] (II) Initializing built-in extension XKEYBOARD
[    13.748] (II) Initializing built-in extension XC-MISC
[    13.748] (II) Initializing built-in extension SECURITY
[    13.748] (II) Initializing built-in extension XINERAMA
[    13.748] (II) Initializing built-in extension XFIXES
[    13.748] (II) Initializing built-in extension RENDER
[    13.748] (II) Initializing built-in extension RANDR
[    13.748] (II) Initializing built-in extension COMPOSITE
[    13.748] (II) Initializing built-in extension DAMAGE
[    13.748] (II) Initializing built-in extension GESTURE
[    13.760] (II) AIGLX: Screen 0 is not DRI2 capable
[    13.760] (II) AIGLX: Screen 0 is not DRI capable
[    13.762] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    13.763] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    13.763] (II) intel(0): Setting screen physical size to 361 x 203
[    13.779] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.786] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    13.786] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.786] (II) LoadModule: "evdev"
[    13.786] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.786] (II) Module evdev: vendor="X.Org Foundation"
[    13.786]     compiled for 1.9.0, module version = 2.3.2
[    13.786]     Module class: X.Org XInput Driver
[    13.786]     ABI class: X.Org XInput driver, version 11.0
[    13.786] (**) Power Button: always reports core events
[    13.786] (**) Power Button: Device: "/dev/input/event2"
[    13.804] (II) Power Button: Found keys
[    13.804] (II) Power Button: Configuring as keyboard
[    13.804] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.804] (**) Option "xkb_rules" "evdev"
[    13.804] (**) Option "xkb_model" "pc105"
[    13.804] (**) Option "xkb_layout" "us"
[    13.805] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    13.805] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    13.805] (**) Video Bus: always reports core events
[    13.805] (**) Video Bus: Device: "/dev/input/event7"
[    13.816] (II) Video Bus: Found keys
[    13.816] (II) Video Bus: Configuring as keyboard
[    13.816] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    13.816] (**) Option "xkb_rules" "evdev"
[    13.816] (**) Option "xkb_model" "pc105"
[    13.816] (**) Option "xkb_layout" "us"
[    13.818] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    13.818] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    13.818] (**) Video Bus: always reports core events
[    13.818] (**) Video Bus: Device: "/dev/input/event6"
[    13.832] (II) Video Bus: Found keys
[    13.832] (II) Video Bus: Configuring as keyboard
[    13.832] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    13.832] (**) Option "xkb_rules" "evdev"
[    13.832] (**) Option "xkb_model" "pc105"
[    13.832] (**) Option "xkb_layout" "us"
[    13.832] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    13.832] (II) No input driver/identifier specified (ignoring)
[    13.833] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    13.833] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    13.833] (**) Sleep Button: always reports core events
[    13.833] (**) Sleep Button: Device: "/dev/input/event1"
[    13.848] (II) Sleep Button: Found keys
[    13.848] (II) Sleep Button: Configuring as keyboard
[    13.848] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    13.848] (**) Option "xkb_rules" "evdev"
[    13.848] (**) Option "xkb_model" "pc105"
[    13.848] (**) Option "xkb_layout" "us"
[    13.849] (II) config/udev: Adding input device Lenovo easy camera (/dev/input/event4)
[    13.849] (**) Lenovo easy camera: Applying InputClass "evdev keyboard catchall"
[    13.849] (**) Lenovo easy camera: always reports core events
[    13.849] (**) Lenovo easy camera: Device: "/dev/input/event4"
[    13.868] (II) Lenovo easy camera: Found keys
[    13.868] (II) Lenovo easy camera: Configuring as keyboard
[    13.868] (II) XINPUT: Adding extended input device "Lenovo easy camera" (type: KEYBOARD)
[    13.868] (**) Option "xkb_rules" "evdev"
[    13.868] (**) Option "xkb_model" "pc105"
[    13.868] (**) Option "xkb_layout" "us"
[    13.871] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    13.871] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    13.871] (**) AT Translated Set 2 keyboard: always reports core events
[    13.871] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    13.900] (II) AT Translated Set 2 keyboard: Found keys
[    13.900] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    13.900] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    13.900] (**) Option "xkb_rules" "evdev"
[    13.900] (**) Option "xkb_model" "pc105"
[    13.900] (**) Option "xkb_layout" "us"
[    13.900] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    13.901] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    13.901] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    13.901] (II) LoadModule: "synaptics"
[    13.901] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    13.901] (II) Module synaptics: vendor="X.Org Foundation"
[    13.901]     compiled for 1.9.0, module version = 1.2.2
[    13.901]     Module class: X.Org XInput Driver
[    13.901]     ABI class: X.Org XInput driver, version 11.0
[    13.901] (II) Synaptics touchpad driver version 1.2.2
[    13.901] (**) Option "Device" "/dev/input/event5"
[    14.060] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5728
[    14.060] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4902
[    14.060] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    14.060] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    14.060] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    14.188] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    14.188] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    14.252] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    14.252] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    14.252] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    14.252] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    14.252] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    14.340] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    14.340] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    14.340] (II) No input driver/identifier specified (ignoring)
[    15.067] (II) intel(0): EDID vendor "AUO", prod id 8940
[    15.067] (II) intel(0): Printing DDC gathered Modelines:
[    15.067] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    15.096] (II) intel(0): EDID vendor "AUO", prod id 8940
[    15.096] (II) intel(0): Printing DDC gathered Modelines:
[    15.096] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    15.152] (II) intel(0): EDID vendor "AUO", prod id 8940
[    15.152] (II) intel(0): Printing DDC gathered Modelines:
[    15.152] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    15.180] (II) intel(0): EDID vendor "AUO", prod id 8940
[    15.180] (II) intel(0): Printing DDC gathered Modelines:
[    15.180] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    26.806] (II) intel(0): EDID vendor "AUO", prod id 8940
[    26.806] (II) intel(0): Printing DDC gathered Modelines:
[    26.806] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    26.835] (II) intel(0): EDID vendor "AUO", prod id 8940
[    26.835] (II) intel(0): Printing DDC gathered Modelines:
[    26.835] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    26.863] (II) intel(0): EDID vendor "AUO", prod id 8940
[    26.863] (II) intel(0): Printing DDC gathered Modelines:
[    26.863] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    32.186] (II) intel(0): EDID vendor "AUO", prod id 8940
[    32.186] (II) intel(0): Printing DDC gathered Modelines:
[    32.186] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)

---

### Post by Toz on 2012-01-17
According to this information, your system is not using the nvidia card, but rather the integrated intel card. You might want to try the following kernel parameters:

- **acpi_osi=Linux acpi_backlight=vendor**

See: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot")

Or, if you're interested in getting the nvidia card to work - have a look at this link: [http://askubuntu.com/questions/82105/how-do-i-get-nvidia-drivers-working-on-an-ideapad-z570]("http://askubuntu.com/questions/82105/how-do-i-get-nvidia-drivers-working-on-an-ideapad-z570").

---

### Post by KRISHNASHK on 2012-01-18
will installing the graphics card driver solve my brightness problem??

---

### Post by Toz on 2012-01-18
I can't say. I neither own that laptop nor an nvidia card. According to the askubuntu link above, there is a switch on the case that allows you to switch between the nvidia and intel card. If not, there may be a setting in the bios that allows you to specify which card to use.

It may be a matter of testing to see.

---

### Post by KRISHNASHK on 2012-01-21
> **Toz said:**
> According to this information, your system is not using the nvidia card, but rather the integrated intel card. You might want to try the following kernel parameters:

- **acpi_osi=Linux acpi_backlight=vendor**

See: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot](https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot)

Or, if you're interested in getting the nvidia card to work - have a look at this link: [http://askubuntu.com/questions/82105/how-do-i-get-nvidia-drivers-working-on-an-ideapad-z570](http://askubuntu.com/questions/82105/how-do-i-get-nvidia-drivers-working-on-an-ideapad-z570).
That kernel parameter did not work. Yes i would like to make the nvidia graphics card work, i installed nvidia settings but when i  run it it shows the following error message.


You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

---

### Post by Toz on 2012-01-21
> Yes i would like to make the nvidia graphics card work

If your bios allows you to turn off the intel card and use the nvidia card instead, then enable that.

Otherwise, you will need to install and configure something called bumblebee (see: [https://github.com/Bumblebee-Project/Bumblebee/wiki/]("https://github.com/Bumblebee-Project/Bumblebee/wiki/")). Information about bumblebee is located at that link.

---

### Post by Basher101 on 2012-01-21
I have had similar problems with onboard graphic chips on a few Laptops i tried installing Ubuntu to. I will paste my fix from another post i made: > type in a terminal: ```
gksu gedit /etc/rc.local
``` and there you will see at the very most bottom a red colored [COLOR="Red"]EXIT[/COLOR]. Just above that "exit" type the command ```
setpci -s 00:02.0 F4.B=00
``` and save the settings. Next file you will have to edit is your Grub config file. Type into a terminal ```
gksu gedit /etc/default/grub
``` there you will see different settings. Now look for the line that looks like this: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and add "acpi_osi=Linux" at the end so that the line looks like this after editing:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Green"]acpi_osi=Linux[/COLOR]"

this should fix your problem. the only thing that got BROKEN is the indicator app that shows you that "bar" of the brighntess and that it is reversed (UP arrow increses brightness and DOWN decreses the brightness). But this is a price i gladly pay to change the brightness. 

If you do not want to make those "permanent" changes, you can also just adjust it by command with ```
sudo setpci -s 00:02.0 F4.B=[COLOR="Red"]XX[/COLOR]
``` where in XX you replace it with HEX code (reaching from 00 = 0 ([COLOR="DarkOrange"]brightest[/COLOR]) to FF = 255 ([COLOR="Navy"]darkest[/COLOR]))

regards

---

### Post by Basher101 on 2012-01-21
as for your nVidia drivers, you will need the 3 packages installed: nvidia-current , nvidia-common and nvidia-settings. You can do this with either the terminal or (the way i did it) using the synaptic package manager. You can install synaptic package manager from the software center. Once you got it installed type in the search box "nvidia-common" and it should display you the package. Rightclick it and "mark for installation". Do this for the other two packages as well. Once you marked all three, click on the small arrow at the top to apply and it will install all packages. 

Once installed, the driver should show up in your "Additional Drivers" to use it simply reboot.

regards


*note: be careful when using Synaptic Package manager. Do not delete anything as you can mess up your system if you do not know what you are doing.

---

### Post by KRISHNASHK on 2012-01-22
> **Basher101 said:**
> I have had similar problems with onboard graphic chips on a few Laptops i tried installing Ubuntu to. I will paste my fix from another post i made: 

regards
i tried the command but it did not seem to change the brightness

---

### Post by KRISHNASHK on 2012-01-22
> **Basher101 said:**
> as for your nVidia drivers, you will need the 3 packages installed: nvidia-current , nvidia-common and nvidia-settings. You can do this with either the terminal or (the way i did it) using the synaptic package manager. You can install synaptic package manager from the software center. Once you got it installed type in the search box "nvidia-common" and it should display you the package. Rightclick it and "mark for installation". Do this for the other two packages as well. Once you marked all three, click on the small arrow at the top to apply and it will install all packages. 

Once installed, the driver should show up in your "Additional Drivers" to use it simply reboot.

regards


*note: be careful when using Synaptic Package manager. Do not delete anything as you can mess up your system if you do not know what you are doing.
can you specify which nvidia-current? i found 3 package wen i searched for it?

---

### Post by KRISHNASHK on 2012-01-23
bump

---

### Post by KRISHNASHK on 2012-01-25
bump

---

### Post by Toz on 2012-01-25
According to: [http://www.lenovo.com/shop/americas/content/user_guides/z370_z470_z570_ug_en.pdf]("http://www.lenovo.com/shop/americas/content/user_guides/z370_z470_z570_ug_en.pdf"), page 8, some models have a GPU switch on the front of the device to enable/disable nvidia optimus graphics. 

If you have this switch, is it set to enable the nvidia GPU?
If not, is there a setting in your bios to enable the nvidia GPU?

With the nvidia GPU enabled and the system rebooted, are you offered to install nvidia drivers through "Additional Drivers" applet?
If not, have you had a look at the Bumblebee project ([https://github.com/Bumblebee-Project/Bumblebee/wiki/]("https://github.com/Bumblebee-Project/Bumblebee/wiki/")) and also the ubuntu wiki at [https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee") for information on accessing the nvidia GPU?

Also: [http://askubuntu.com/questions/82105/how-do-i-get-nvidia-drivers-working-on-an-ideapad-z570]("http://askubuntu.com/questions/82105/how-do-i-get-nvidia-drivers-working-on-an-ideapad-z570")

---

### Post by KRISHNASHK on 2012-01-27
> **Toz said:**
> According to: [http://www.lenovo.com/shop/americas/content/user_guides/z370_z470_z570_ug_en.pdf](http://www.lenovo.com/shop/americas/content/user_guides/z370_z470_z570_ug_en.pdf), page 8, some models have a GPU switch on the front of the device to enable/disable nvidia optimus graphics. 

If you have this switch, is it set to enable the nvidia GPU?
If not, is there a setting in your bios to enable the nvidia GPU?

With the nvidia GPU enabled and the system rebooted, are you offered to install nvidia drivers through "Additional Drivers" applet?
If not, have you had a look at the Bumblebee project ([https://github.com/Bumblebee-Project/Bumblebee/wiki/](https://github.com/Bumblebee-Project/Bumblebee/wiki/)) and also the ubuntu wiki at [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee) for information on accessing the nvidia GPU?

Also: [http://askubuntu.com/questions/82105/how-do-i-get-nvidia-drivers-working-on-an-ideapad-z570](http://askubuntu.com/questions/82105/how-do-i-get-nvidia-drivers-working-on-an-ideapad-z570)
yes i do have a switch in laptop for changing to nvidia graphics.
I tried enabling and disabling the switch but did not get any notification in the additional driver applet.

In bios i have two option for the graphics one is the "optimus" and "UMA only", i tried both of them did not get any additional driver.

i googled around and found that my laptop has optimus technology and i need to use bumblebee for it.

This link [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)  has the procedure to install bumblebee.

but at the third step in the link i am getting the following error.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bumblee-nvidia



in the second step everything went well but got an error at the last line> please take a look.


Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/bumblebee/stable/ubuntu/](http://ppa.launchpad.net/bumblebee/stable/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/bumblebee/stable/ubuntu/](http://ppa.launchpad.net/bumblebee/stable/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release.gpg                              
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en              
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release                      
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources/DiffIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources/DiffIndex 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources/DiffIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages/DiffIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages/DiffIndex   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Fetched 198B in 2s (97B/s)
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


please help!
thanks for reply!

---

### Post by Toz on 2012-01-28
Try this:
```

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

```

If that doesn't work, then try this:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5

```

---

### Post by KRISHNASHK on 2012-01-29
yeah those commands worked i installed the bumblebee successfully. But where do i change the brightness?

---

### Post by KRISHNASHK on 2012-01-29
bump

---

### Post by Toz on 2012-01-29
Try booting with the kernel parameter **acpi_backlight=vendor**. After you've successfully booted with this parameter, try to change the brightness.

Also, while still booted with this kernel parameter, post back the results of the following commands:
```
cat /proc/cmdline
uname -a
ls /sys/class/backlight
sudo lspci | grep -A10 VGA

```

---

### Post by KRISHNASHK on 2012-01-30
> **Toz said:**
> Try booting with the kernel parameter **acpi_backlight=vendor**. After you've successfully booted with this parameter, try to change the brightness.

Also, while still booted with this kernel parameter, post back the results of the following commands:
```
cat /proc/cmdline
uname -a
ls /sys/class/backlight
sudo lspci | grep -A10 VGA

```
i rebooted withe following kernel parameter i could not change the brightness!

cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-2.6.35-32-generic-pae root=UUID=a81da772-f9fe-40cc-8387-c42e1d800020 ro acpi_osi=Linux acpi_backlight=vendor quiet splash acpi_osi=Linux

uname -a

Linux krishna-Ideapad-Z570 2.6.35-32-generic-pae #64-Ubuntu SMP Tue Jan 3 00:57:30 UTC 2012 i686 GNU/Linux

ls /sys/class/backlight

no files listed!

sudo lspci | grep -A10 VGA


00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Cougar Point LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 1050 (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

---

### Post by Toz on 2012-01-30
This time, remove the _two_ **acpi_osi=Linux** and the **acpi_vendor=backlight** kernel parameters. Reboot.

Upon reboot, try brightness and report back the following:
```

cat /proc/cmdline
uname -a
ls /sys/class/backlight
sudo lspci -vnn | grep -A10 VGA

```

Also, try the following commands to see if they adjust brightness:
```

sudo setpci -s 00:02.0 F4.B=00
sudo setpci -s 00:02.0 F4.B=f7
sudo setpci -s 00:02.0 F4.B=ff

```
...and
```

sudo setpci -s 01:00.0 F4.B=00
sudo setpci -s 01:00.0 F4.B=f7
sudo setpci -s 01:00.0 F4.B=ff

```

---

### Post by KRISHNASHK on 2012-01-31
> **Toz said:**
> This time, remove the _two_ **acpi_osi=Linux** and the **acpi_vendor=backlight** kernel parameters. Reboot.

Upon reboot, try brightness and report back the following:
```

cat /proc/cmdline
uname -a
ls /sys/class/backlight
sudo lspci -vnn | grep -A10 VGA

```Also, try the following commands to see if they adjust brightness:
```

sudo setpci -s 00:02.0 F4.B=00
sudo setpci -s 00:02.0 F4.B=f7
sudo setpci -s 00:02.0 F4.B=ff

```...and
```

sudo setpci -s 01:00.0 F4.B=00
sudo setpci -s 01:00.0 F4.B=f7
sudo setpci -s 01:00.0 F4.B=ff

```


i tried changing the kernel parameters it did not work. I am changing the brightness using the function key of laptop, is that the right procedure?
i tried the codes as well they did not work either.

cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-2.6.35-32-generic-pae root=UUID=a81da772-f9fe-40cc-8387-c42e1d800020 ro acpi_osi=Linux acpi_backlight=vendor quiet splash acpi_osi=Linux

uname -a

Linux krishna-Ideapad-Z570 2.6.35-32-generic-pae #64-Ubuntu SMP Tue Jan 3 00:57:30 UTC 2012 i686 GNU/Linux

ls /sys/class/backlight

no files listed again!

sudo lspci -vnn | grep -A10 VGA

00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:397d]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f1000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:1050] (rev ff) (prog-if ff)
    !!! Unknown header type 7f

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f1500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00

---

### Post by Toz on 2012-01-31
> **KRISHNASHK said:**
> cat /proc/cmdline

BOOT_IMAGE=/boot/vmlinuz-2.6.35-32-generic-pae root=UUID=a81da772-f9fe-40cc-8387-c42e1d800020 ro [COLOR="Red"]acpi_osi=Linux acpi_backlight=vendor[/COLOR] quiet splash [COLOR="Red"]acpi_osi=Linux[/COLOR]


Can you please remove these kernel parameters (the ones in red) and try again? Post back as per my previous post.

---

### Post by KRISHNASHK on 2012-02-01
shall i remove it from the 

 /proc/cmdline

or from 

/etc/default/grub

---

### Post by Toz on 2012-02-01
Remove it from /etc/default/grub and run:
```
sudo update-grub
```

Also, what version of ubuntu are you running?

---

### Post by KRISHNASHK on 2012-02-01
cat /proc/cmdline



BOOT_IMAGE=/boot/vmlinuz-2.6.35-32-generic-pae root=UUID=a81da772-f9fe-40cc-8387-c42e1d800020 ro quiet splash


uname -a

Linux krishna-Ideapad-Z570 2.6.35-32-generic-pae #64-Ubuntu SMP Tue Jan 3 00:57:30 UTC 2012 i686 GNU/Linux


ls /sys/class/backlight
no files

sudo lspci -vnn | grep -A10 VGA


00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:397d]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f1000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:1050] (rev ff) (prog-if ff)
    !!! Unknown header type 7f

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f1500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Vendor Specific Information: Len=78 <?>
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [d0] Express Endpoint, MSI 00


i am running 10.10

---

### Post by Toz on 2012-02-02
> ls /sys/class/backlight
no filesI am surprised that you have no backlight interface.

Can you try this kernel parameter: **acpi_osi=**

Other than that, is it possible for you to boot your computer with the live ISO of a later version of ubuntu (say 11.10) to see if that makes a difference. Later kernel versions support more hardware.

EDIT: Can you also post the results of:
```
dmesg
```
...and the contents of **/var/log/Xorg.0.log**?

---

### Post by KRISHNASHK on 2012-02-03
dmesg 
```
[    0.547712] pci 0000:00:1c.1:   bridge window [mem 0xf1500000-0xf15fffff]
[    0.547718] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.547895] pci 0000:04:00.0: reg 10: [io  0x2000-0x20ff]
[    0.547976] pci 0000:04:00.0: reg 18: [mem 0xf1404000-0xf1404fff 64bit pref]
[    0.548032] pci 0000:04:00.0: reg 20: [mem 0xf1400000-0xf1403fff 64bit pref]
[    0.548229] pci 0000:04:00.0: supports D1 D2
[    0.548230] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.548245] pci 0000:04:00.0: PME# disabled
[    0.555693] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
[    0.555698] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
[    0.555703] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.555710] pci 0000:00:1c.3:   bridge window [mem 0xf1400000-0xf14fffff 64bit pref]
[    0.555730] pci_bus 0000:00: on NUMA node 0
[    0.555741] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.555986] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.556089] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.556197] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.556331] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEG0._PRT]
[    0.556533] \_SB_.PCI0:_OSC invalid UUID
[    0.556535] _OSC request data:1 1f 1f 
[    0.561803] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.561951] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.562093] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.562234] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.562374] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.562517] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.562659] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 10 *11 12 14 15)
[    0.562803] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *10 11 12 14 15)
[    0.562857] HEST: Table is not found!
[    0.562918] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.562926] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.562929] vgaarb: loaded
[    0.563065] SCSI subsystem initialized
[    0.563164] libata version 3.00 loaded.
[    0.563214] usbcore: registered new interface driver usbfs
[    0.563225] usbcore: registered new interface driver hub
[    0.563250] usbcore: registered new device driver usb
[    0.563455] ACPI: WMI: Mapper loaded
[    0.563457] PCI: Using ACPI for IRQ routing
[    0.563459] PCI: pci_cache_line_size set to 64 bytes
[    0.563566] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
[    0.563568] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    0.563570] reserve RAM buffer: 00000000bac87000 - 00000000bbffffff 
[    0.563574] reserve RAM buffer: 00000000bb000000 - 00000000bbffffff 
[    0.563575] reserve RAM buffer: 000000013fe00000 - 000000013fffffff 
[    0.563656] NetLabel: Initializing
[    0.563658] NetLabel:  domain hash size = 128
[    0.563659] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.563669] NetLabel:  unlabeled traffic allowed by default
[    0.563701] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.563707] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.565722] Switching to clocksource tsc
[    0.573267] AppArmor: AppArmor Filesystem Enabled
[    0.573279] pnp: PnP ACPI init
[    0.573292] ACPI: bus type pnp registered
[    0.574887] pnp 00:0a: disabling [mem 0xfffff000-0xffffffff] because it overlaps 0000:01:00.0 BAR 6 [mem 0xfff80000-0xffffffff pref]
[    0.575531] pnp: PnP ACPI: found 12 devices
[    0.575533] ACPI: ACPI bus type pnp unregistered
[    0.575535] PnPBIOS: Disabled by ACPI PNP
[    0.575545] system 00:05: [io  0x1000-0x100f] has been reserved
[    0.575547] system 00:05: [io  0xffff] has been reserved
[    0.575549] system 00:05: [io  0xffff] has been reserved
[    0.575552] system 00:05: [io  0x0400-0x0453] has been reserved
[    0.575554] system 00:05: [io  0x0458-0x047f] has been reserved
[    0.575556] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.575559] system 00:05: [mem 0xfe800000-0xfe80ffff] has been reserved
[    0.575563] system 00:07: [io  0x0454-0x0457] has been reserved
[    0.575567] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.575570] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.575572] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.575574] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.575576] system 00:0a: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.575578] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.575580] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.575582] system 00:0a: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.575584] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    0.575587] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.575591] system 00:0b: [mem 0x20000000-0x201fffff] could not be reserved
[    0.575593] system 00:0b: [mem 0x40000000-0x401fffff] could not be reserved
[    0.611240] pci 0000:01:00.0: no compatible bridge window for [mem 0xfff80000-0xffffffff pref]
[    0.611280] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x80000)
[    0.611282] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.611284] pci 0000:00:01.0:   bridge window [io  0x3000-0x3fff]
[    0.611287] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf0ffffff]
[    0.611290] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.611294] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.611295] pci 0000:00:1c.0:   bridge window [io  disabled]
[    0.611301] pci 0000:00:1c.0:   bridge window [mem disabled]
[    0.611305] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    0.611311] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.611313] pci 0000:00:1c.1:   bridge window [io  disabled]
[    0.611318] pci 0000:00:1c.1:   bridge window [mem 0xf1500000-0xf15fffff]
[    0.611322] pci 0000:00:1c.1:   bridge window [mem pref disabled]
[    0.611329] pci 0000:00:1c.3: PCI bridge to [bus 04-04]
[    0.611332] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
[    0.611337] pci 0000:00:1c.3:   bridge window [mem disabled]
[    0.611342] pci 0000:00:1c.3:   bridge window [mem 0xf1400000-0xf14fffff 64bit pref]
[    0.611356]   alloc irq_desc for 16 on node -1
[    0.611358]   alloc kstat_irqs on node -1
[    0.611363] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.611366] pci 0000:00:01.0: setting latency timer to 64
[    0.611375] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.611381] pci 0000:00:1c.0: setting latency timer to 64
[    0.611391]   alloc irq_desc for 17 on node -1
[    0.611392]   alloc kstat_irqs on node -1
[    0.611396] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.611400] pci 0000:00:1c.1: setting latency timer to 64
[    0.611410]   alloc irq_desc for 19 on node -1
[    0.611411]   alloc kstat_irqs on node -1
[    0.611414] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.611418] pci 0000:00:1c.3: setting latency timer to 64
[    0.611423] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.611425] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.611426] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.611428] pci_bus 0000:00: resource 7 [mem 0xbfa00000-0xfeafffff]
[    0.611430] pci_bus 0000:00: resource 8 [mem 0xfed40000-0xfed44fff]
[    0.611432] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.611433] pci_bus 0000:01: resource 1 [mem 0xf0000000-0xf0ffffff]
[    0.611435] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xd1ffffff 64bit pref]
[    0.611437] pci_bus 0000:03: resource 1 [mem 0xf1500000-0xf15fffff]
[    0.611439] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.611441] pci_bus 0000:04: resource 2 [mem 0xf1400000-0xf14fffff 64bit pref]
[    0.611471] NET: Registered protocol family 2
[    0.611528] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.611723] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.611954] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.612067] TCP: Hash tables configured (established 131072 bind 65536)
[    0.612069] TCP reno registered
[    0.612071] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.612076] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.612153] NET: Registered protocol family 1
[    0.612166] pci 0000:00:02.0: Boot video device
[    0.612275] PCI: CLS 64 bytes, default 64
[    0.612551] cpufreq-nforce2: No nForce2 chipset.
[    0.612577] Scanning for low memory corruption every 60 seconds
[    0.612681] audit: initializing netlink socket (disabled)
[    0.612687] type=2000 audit(1328294290.452:1): initialized
[    0.621502] highmem bounce pool size: 64 pages
[    0.621506] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.622618] VFS: Disk quotas dquot_6.5.2
[    0.622666] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.623112] fuse init (API version 7.14)
[    0.623182] msgmni has been set to 1611
[    0.715980] Freeing initrd memory: 10532k freed
[    0.720422] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.720425] io scheduler noop registered
[    0.720426] io scheduler deadline registered
[    0.720435] io scheduler cfq registered (default)
[    0.720518] pcieport 0000:00:01.0: setting latency timer to 64
[    0.720538]   alloc irq_desc for 40 on node -1
[    0.720539]   alloc kstat_irqs on node -1
[    0.720546] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.720600] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.720635]   alloc irq_desc for 41 on node -1
[    0.720636]   alloc kstat_irqs on node -1
[    0.720643] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.720706] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.720740]   alloc irq_desc for 42 on node -1
[    0.720741]   alloc kstat_irqs on node -1
[    0.720748] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.720811] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.720846]   alloc irq_desc for 43 on node -1
[    0.720847]   alloc kstat_irqs on node -1
[    0.720855] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.720931] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.720953] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.721026] intel_idle: MWAIT substates: 0x21120
[    0.721027] intel_idle: v0.4 model 0x2A
[    0.721028] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.721200] ACPI: AC Adapter [ADP1] (off-line)
[    0.721269] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.721331] ACPI: Lid Switch [LID0]
[    0.721367] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.721371] ACPI: Sleep Button [SLPB]
[    0.721404] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.721407] ACPI: Power Button [PWRF]
[    0.721782] ACPI: acpi_idle yielding to intel_idle
[    0.726433] thermal LNXTHERM:01: registered as thermal_zone0
[    0.726440] ACPI: Thermal Zone [TZS0] (55 C)
[    0.726755] thermal LNXTHERM:02: registered as thermal_zone1
[    0.726761] ACPI: Thermal Zone [TZS1] (40 C)
[    0.726826] ERST: Table is not found!
[    0.726868] isapnp: Scanning for PnP cards...
[    0.727775] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.728101] ACPI: Battery Slot [BAT0] (battery present)
[    0.728991] brd: module loaded
[    0.729413] loop: module loaded
[    0.729861] Fixed MDIO Bus: probed
[    0.729891] PPP generic driver version 2.4.2
[    0.729919] tun: Universal TUN/TAP device driver, 1.6
[    0.729920] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.729980] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.729998] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.730010] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.730013] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.730038] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.730068] ehci_hcd 0000:00:1a.0: debug port 2
[    0.733942] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    0.733958] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf160a000
[    0.747543] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.747642] hub 1-0:1.0: USB hub found
[    0.747647] hub 1-0:1.0: 2 ports detected
[    0.747695]   alloc irq_desc for 23 on node -1
[    0.747696]   alloc kstat_irqs on node -1
[    0.747701] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.747711] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.747714] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.747739] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.747766] ehci_hcd 0000:00:1d.0: debug port 2
[    0.751636] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    0.751649] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf1609000
[    0.767531] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.767608] hub 2-0:1.0: USB hub found
[    0.767611] hub 2-0:1.0: 2 ports detected
[    0.767657] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.767668] uhci_hcd: USB Universal Host Controller Interface driver
[    0.767743] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.769962] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.769967] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.770031] mice: PS/2 mouse device common for all mice
[    0.770136] rtc_cmos 00:06: RTC can wake from S4
[    0.770165] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.770193] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.770268] device-mapper: uevent: version 1.0.3
[    0.770354] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.770440] device-mapper: multipath: version 1.1.1 loaded
[    0.770443] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.770531] EISA: Probing bus 0 at eisa.0
[    0.770533] EISA: Cannot allocate resource for mainboard
[    0.770535] Cannot allocate resource for EISA slot 1
[    0.770537] Cannot allocate resource for EISA slot 2
[    0.770539] Cannot allocate resource for EISA slot 3
[    0.770541] Cannot allocate resource for EISA slot 4
[    0.770542] Cannot allocate resource for EISA slot 5
[    0.770544] Cannot allocate resource for EISA slot 6
[    0.770546] Cannot allocate resource for EISA slot 7
[    0.770548] Cannot allocate resource for EISA slot 8
[    0.770549] EISA: Detected 0 cards.
[    0.770806] cpuidle: using governor ladder
[    0.771048] cpuidle: using governor menu
[    0.771245] TCP cubic registered
[    0.771348] NET: Registered protocol family 10
[    0.771874] NET: Registered protocol family 17
[    0.773256] Using IPI No-Shortcut mode
[    0.773338] PM: Resume from disk failed.
[    0.773348] registered taskstats version 1
[    0.773692]   Magic number: 0:689:644
[    0.773750] rtc_cmos 00:06: setting system clock to 2012-02-03 18:38:11 UTC (1328294291)
[    0.773753] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.773755] EDD information not available.
[    0.784358] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.059459] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.080655] isapnp: No Plug & Play device found
[    1.080677] Freeing unused kernel memory: 708k freed
[    1.080982] Write protecting the kernel text: 5104k
[    1.081053] Write protecting the kernel read-only data: 2016k
[    1.096594] udev[99]: starting version 163
[    1.156842] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.156886] r8169 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.156940] r8169 0000:04:00.0: setting latency timer to 64
[    1.156947] r8169 0000:04:00.0: (unregistered net_device): unknown MAC, using family default
[    1.157006]   alloc irq_desc for 44 on node -1
[    1.157008]   alloc kstat_irqs on node -1
[    1.157027] r8169 0000:04:00.0: irq 44 for MSI/MSI-X
[    1.157211] ahci 0000:00:1f.2: version 3.0
[    1.157227] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.157267]   alloc irq_desc for 45 on node -1
[    1.157270]   alloc kstat_irqs on node -1
[    1.157282] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.157332] ahci: SSS flag set, parallel bus scan disabled
[    1.157554] r8169 0000:04:00.0: eth0: RTL8101e at 0xf84bc000, f0:de:f1:a4:05:11, XID 00a00000 IRQ 44
[    1.173966] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x39 impl SATA mode
[    1.173972] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pio slum part ems sxs apst 
[    1.173980] ahci 0000:00:1f.2: setting latency timer to 64
[    1.194188] hub 1-1:1.0: USB hub found
[    1.194269] hub 1-1:1.0: 6 ports detected
[    1.198112] scsi0 : ahci
[    1.198268] scsi1 : ahci
[    1.198347] scsi2 : ahci
[    1.198449] scsi3 : ahci
[    1.198562] scsi4 : ahci
[    1.198672] scsi5 : ahci
[    1.198733] ata1: SATA max UDMA/133 abar m2048@0xf1608000 port 0xf1608100 irq 45
[    1.198735] ata2: DUMMY
[    1.198736] ata3: DUMMY
[    1.198739] ata4: SATA max UDMA/133 abar m2048@0xf1608000 port 0xf1608280 irq 45
[    1.198742] ata5: SATA max UDMA/133 abar m2048@0xf1608000 port 0xf1608300 irq 45
[    1.198745] ata6: SATA max UDMA/133 abar m2048@0xf1608000 port 0xf1608380 irq 45
[    1.305442] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.438100] hub 2-1:1.0: USB hub found
[    1.438303] hub 2-1:1.0: 6 ports detected
[    1.513551] usb 1-1.5: new high speed USB device using ehci_hcd and address 3
[    1.517335] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.575097] ata1.00: ATA-8: ST9500325AS, 0011LVM1, max UDMA/100
[    1.575108] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.577292] ata1.00: configured for UDMA/100
[    1.593478] scsi 0:0:0:0: Direct-Access     ATA      ST9500325AS      0011 PQ: 0 ANSI: 5
[    1.593645] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.593648] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.593718] sd 0:0:0:0: [sda] Write Protect is off
[    1.593721] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.593750] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.593886]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    1.613261] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.813394] usb 2-1.4: new full speed USB device using ehci_hcd and address 3
[    1.913877] ata4: SATA link down (SStatus 0 SControl 300)
[    1.981319] usb 2-1.6: new high speed USB device using ehci_hcd and address 4
[    2.653480] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.665979] ata5.00: ATAPI: MATSHITADVD-RAM UJ8B1AS, 8.21, max UDMA/100
[    2.684176] ata5.00: configured for UDMA/100
[    2.713712] scsi 4:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ8B1AS  8.21 PQ: 0 ANSI: 5
[    2.746124] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.746142] Uniform CD-ROM driver Revision: 3.20
[    2.746298] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.746388] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    3.064549] ata6: SATA link down (SStatus 0 SControl 300)
[    3.837450] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   10.552635] udev[418]: starting version 163
[   10.576225] lp: driver loaded but no devices found
[   10.588721] Linux agpgart interface v0.103
[   10.643157] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[   10.644469] agpgart-intel 0000:00:00.0: detected 65532K stolen memory, trimming to 32768K
[   10.676758] lib80211: common routines for IEEE802.11 drivers
[   10.676763] lib80211_crypt: registered algorithm 'NULL'
[   10.681245] wl: module license 'MIXED/Proprietary' taints kernel.
[   10.681249] Disabling lock debugging due to kernel taint
[   10.712949] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.712958] wl 0000:03:00.0: setting latency timer to 64
[   10.775904] EXT4-fs (sda6): warning: maximal mount count reached, running e2fsck is recommended
[   10.780202] Linux video capture interface: v2.00
[   10.780851] type=1400 audit(1328274501.509:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=698 comm="apparmor_parser"
[   10.781588] type=1400 audit(1328274501.509:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=698 comm="apparmor_parser"
[   10.781979] type=1400 audit(1328274501.509:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=698 comm="apparmor_parser"
[   10.785661] Bluetooth: Core ver 2.15
[   10.785684] NET: Registered protocol family 31
[   10.785686] Bluetooth: HCI device and connection manager initialized
[   10.785688] Bluetooth: HCI socket layer initialized
[   10.789445] acer-wmi: Acer Laptop ACPI-WMI Extras
[   10.798175] uvcvideo: Found UVC 1.00 device Lenovo easy camera (0bda:58ea)
[   10.802104] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   10.804976] input: Lenovo easy camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input4
[   10.805331] usbcore: registered new interface driver uvcvideo
[   10.805334] USB Video Class driver (v0.1.0)
[   10.806113] usbcore: registered new interface driver btusb
[   10.828953] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[   10.830896] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   10.830948] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   10.830954] nvidia 0000:01:00.0: enabling device (0000 -> 0003)
[   10.830961] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.830971] nvidia 0000:01:00.0: setting latency timer to 64
[   10.830977] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   10.831378] NVRM: loading NVIDIA UNIX x86 Kernel Module  290.10  Wed Nov 16 19:27:25 PST 2011
[   10.835739] lib80211_crypt: registered algorithm 'TKIP'
[   10.835944] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.60.48.36 
[   10.861457] [drm] Initialized drm 1.1.0 20060810
[   10.895059]   alloc irq_desc for 22 on node -1
[   10.895062]   alloc kstat_irqs on node -1
[   10.895068] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.895109]   alloc irq_desc for 46 on node -1
[   10.895110]   alloc kstat_irqs on node -1
[   10.895120] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   10.895151] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.928965] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,user_xattr
[   11.141122] type=1400 audit(1328274501.869:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=937 comm="apparmor_parser"
[   11.141842] type=1400 audit(1328274501.869:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=937 comm="apparmor_parser"
[   11.142336] type=1400 audit(1328274501.869:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=937 comm="apparmor_parser"
[   11.144755] type=1400 audit(1328274501.873:8): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=936 comm="apparmor_parser"
[   11.147440] type=1400 audit(1328274501.873:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=938 comm="apparmor_parser"
[   11.147578] type=1400 audit(1328274501.873:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=941 comm="apparmor_parser"
[   11.153394] type=1400 audit(1328274501.881:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=940 comm="apparmor_parser"
[   11.197113] r8169 0000:04:00.0: eth0: link down
[   11.197263] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.348434] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
[   11.380758] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[   11.385062] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   11.385077] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[   11.385468] bbswitch: detected an Optimus _DSM function
[   11.385477] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[   11.404327] nvidia 0000:01:00.0: PCI INT A disabled
[   11.405463] bbswitch: disabling discrete graphics
[   11.405863] bbswitch: Result of Optimus _DSM call: 11000059
[   11.407636] Bluetooth: L2CAP ver 2.14
[   11.407639] Bluetooth: L2CAP socket layer initialized
[   11.412288] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   11.412292] Bluetooth: BNEP filters: protocol multicast
[   11.416310] Bluetooth: SCO (Voice Link) ver 0.6
[   11.416313] Bluetooth: SCO socket layer initialized
[   11.448514] hda_codec: ALC272: BIOS auto-probing.
[   11.461969] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.461974] i915 0000:00:02.0: setting latency timer to 64
[   11.482353] [drm] detected 63M stolen memory, trimming to 32M
[   11.482420]   alloc irq_desc for 47 on node -1
[   11.482423]   alloc kstat_irqs on node -1
[   11.482432] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[   11.482442] [drm] set up 32M of stolen space
[   11.492373] Bluetooth: RFCOMM TTY layer initialized
[   11.492379] Bluetooth: RFCOMM socket layer initialized
[   11.492381] Bluetooth: RFCOMM ver 1.11
[   11.620326] pci 0000:01:00.0: power state changed by ACPI to D3
[   11.961330] Skipping EDID probe due to cached edid
[   12.437942] Console: switching to colour frame buffer device 170x48
[   12.440707] fb0: inteldrmfb frame buffer device
[   12.440709] drm: registered panic notifier
[   12.440713] Slow work thread pool: Starting up
[   12.440829] Slow work thread pool: Ready
[   12.441502] ACPI Warning for \_SB_.PCI0.PEG0.PEGP._DOD: Return type mismatch - found Integer, expected Package (20100428/nspredef-1053)
[   12.441508] ACPI Exception: AE_OK, Invalid _DOD data (20100428/video-1943)
[   12.444143] ACPI Error: Current brightness invalid (20100428/video-544)
[   12.444405] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:34/LNXVIDEO:00/input/input6
[   12.444466] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[   12.448821] ACPI Error: Current brightness invalid (20100428/video-544)
[   12.449340] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
[   12.449425] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.449479] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   12.481158] Skipping EDID probe due to cached edid
[   12.560803] ppdev: user-space parallel port driver
[   13.300109] Skipping EDID probe due to cached edid
[   13.328658] Skipping EDID probe due to cached edid
[   13.484103] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,user_xattr,commit=600
[   14.101314] Skipping EDID probe due to cached edid
[   14.129626] Skipping EDID probe due to cached edid
[   14.158184] Skipping EDID probe due to cached edid
[   14.186075] Skipping EDID probe due to cached edid
[   14.567430] Skipping EDID probe due to cached edid
[   20.424102] Skipping EDID probe due to cached edid
[   20.461575] Skipping EDID probe due to cached edid
[   20.489510] Skipping EDID probe due to cached edid
[   20.617291] Skipping EDID probe due to cached edid
[   25.885584] Skipping EDID probe due to cached edid
[   46.350417] eth1: no IPv6 routers present
[   71.887022] ACPI: Failed to switch the brightness
[   72.078920] ACPI: Failed to switch the brightness
[   72.260324] ACPI: Failed to switch the brightness
[   72.431410] ACPI: Failed to switch the brightness
[   72.620685] ACPI: Failed to switch the brightness
[   72.818973] ACPI: Failed to switch the brightness
[   72.989093] ACPI: Failed to switch the brightness
[   73.244522] ACPI: Failed to switch the brightness
[   73.454066] ACPI: Failed to switch the brightness
[   73.653843] ACPI: Failed to switch the brightness
[   73.854066] ACPI: Failed to switch the brightness
[   74.050345] ACPI: Failed to switch the brightness

[B]var/log/Xorg.0.log

[/B][    13.029] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    13.029] X Protocol Version 11, Revision 0
[    13.029] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    13.029] Current Operating System: Linux krishna-Ideapad-Z570 2.6.35-32-generic-pae #64-Ubuntu SMP Tue Jan 3 00:57:30 UTC 2012 i686
[    13.029] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-32-generic-pae root=UUID=a81da772-f9fe-40cc-8387-c42e1d800020 ro quiet splash
[    13.029] Build Date: 20 October 2011  03:03:54PM
[    13.030] xorg-server 2:1.9.0-0ubuntu7.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    13.030] Current version of pixman: 0.18.4
[    13.030]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    13.030] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.030] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb  3 18:38:23 2012
[    13.061] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.069] (==) No Layout section.  Using the first Screen section.
[    13.069] (==) No screen section available. Using defaults.
[    13.069] (**) |-->Screen "Default Screen Section" (0)
[    13.069] (**) |   |-->Monitor "<default monitor>"
[    13.069] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    13.069] (==) Automatically adding devices
[    13.069] (==) Automatically enabling devices
[    13.069] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.069]     Entry deleted from font path.
[    13.069] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    13.069] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.069] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.069] (II) Loader magic: 0x81f8e00
[    13.069] (II) Module ABI versions:
[    13.069]     X.Org ANSI C Emulation: 0.4
[    13.069]     X.Org Video Driver: 8.0
[    13.069]     X.Org XInput driver : 11.0
[    13.069]     X.Org Server Extension : 4.0
[    13.070] (--) PCI:*(0:0:2:0) 8086:0116:17aa:397d rev 9, Mem @ 0xf1000000/4194304, 0xe0000000/268435456, I/O @ 0x00004000/64
[    13.070] (II) Open ACPI successful (/var/run/acpid.socket)
[    13.070] (II) LoadModule: "extmod"
[    13.116] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.126] (II) Module extmod: vendor="X.Org Foundation"
[    13.126]     compiled for 1.9.0, module version = 1.0.0
[    13.126]     Module class: X.Org Server Extension
[    13.126]     ABI class: X.Org Server Extension, version 4.0
[    13.126] (II) Loading extension MIT-SCREEN-SAVER
[    13.126] (II) Loading extension XFree86-VidModeExtension
[    13.126] (II) Loading extension XFree86-DGA
[    13.126] (II) Loading extension DPMS
[    13.126] (II) Loading extension XVideo
[    13.126] (II) Loading extension XVideo-MotionCompensation
[    13.126] (II) Loading extension X-Resource
[    13.126] (II) LoadModule: "dbe"
[    13.126] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.126] (II) Module dbe: vendor="X.Org Foundation"
[    13.126]     compiled for 1.9.0, module version = 1.0.0
[    13.126]     Module class: X.Org Server Extension
[    13.126]     ABI class: X.Org Server Extension, version 4.0
[    13.126] (II) Loading extension DOUBLE-BUFFER
[    13.126] (II) LoadModule: "glx"
[    13.126] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    13.127] (II) Module glx: vendor="X.Org Foundation"
[    13.127]     compiled for 1.9.0, module version = 1.0.0
[    13.127]     ABI class: X.Org Server Extension, version 4.0
[    13.127] (==) AIGLX enabled
[    13.127] (II) Loading extension GLX
[    13.127] (II) LoadModule: "record"
[    13.127] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.127] (II) Module record: vendor="X.Org Foundation"
[    13.127]     compiled for 1.9.0, module version = 1.13.0
[    13.127]     Module class: X.Org Server Extension
[    13.127]     ABI class: X.Org Server Extension, version 4.0
[    13.127] (II) Loading extension RECORD
[    13.127] (II) LoadModule: "dri"
[    13.127] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.127] (II) Module dri: vendor="X.Org Foundation"
[    13.127]     compiled for 1.9.0, module version = 1.0.0
[    13.127]     ABI class: X.Org Server Extension, version 4.0
[    13.127] (II) Loading extension XFree86-DRI
[    13.127] (II) LoadModule: "dri2"
[    13.128] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.128] (II) Module dri2: vendor="X.Org Foundation"
[    13.128]     compiled for 1.9.0, module version = 1.2.0
[    13.128]     ABI class: X.Org Server Extension, version 4.0
[    13.128] (II) Loading extension DRI2
[    13.128] (==) Matched intel as autoconfigured driver 0
[    13.128] (==) Matched vesa as autoconfigured driver 1
[    13.128] (==) Matched fbdev as autoconfigured driver 2
[    13.128] (==) Assigned the driver to the xf86ConfigLayout
[    13.128] (II) LoadModule: "intel"
[    13.128] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    13.128] (II) Module intel: vendor="X.Org Foundation"
[    13.128]     compiled for 1.9.0, module version = 2.13.901
[    13.128]     Module class: X.Org Video Driver
[    13.128]     ABI class: X.Org Video Driver, version 8.0
[    13.128] (II) LoadModule: "vesa"
[    13.128] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    13.128] (II) Module vesa: vendor="X.Org Foundation"
[    13.128]     compiled for 1.8.99.905, module version = 2.3.0
[    13.128]     Module class: X.Org Video Driver
[    13.128]     ABI class: X.Org Video Driver, version 8.0
[    13.128] (II) LoadModule: "fbdev"
[    13.129] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.129] (II) Module fbdev: vendor="X.Org Foundation"
[    13.129]     compiled for 1.8.99.905, module version = 0.4.2
[    13.129]     ABI class: X.Org Video Driver, version 8.0
[    13.129] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    13.129] (II) VESA: driver for VESA chipsets: vesa
[    13.129] (II) FBDEV: driver for framebuffer: fbdev
[    13.129] (++) using VT number 7

[    13.131] (WW) Falling back to old probe method for vesa
[    13.131] (WW) Falling back to old probe method for fbdev
[    13.131] (II) Loading sub module "fbdevhw"
[    13.131] (II) LoadModule: "fbdevhw"
[    13.131] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    13.131] (II) Module fbdevhw: vendor="X.Org Foundation"
[    13.131]     compiled for 1.9.0, module version = 0.0.2
[    13.131]     ABI class: X.Org Video Driver, version 8.0
[    13.131] drmOpenDevice: node name is /dev/dri/card0
[    13.131] drmOpenDevice: open result is 9, (OK)
[    13.131] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    13.131] drmOpenDevice: node name is /dev/dri/card0
[    13.131] drmOpenDevice: open result is 9, (OK)
[    13.131] drmOpenByBusid: drmOpenMinor returns 9
[    13.131] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    13.131] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    13.131] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    13.131] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    13.131] (==) intel(0): RGB weight 888
[    13.131] (==) intel(0): Default visual is TrueColor
[    13.131] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge
[    13.131] (--) intel(0): Chipset: "Sandybridge"
[    13.131] (**) intel(0): Shadow buffer enabled, GPU acceleration disabled.
[    13.131] (**) intel(0): Tiling enabled
[    13.131] (**) intel(0): SwapBuffers wait disabled
[    13.131] (==) intel(0): video overlay key set to 0x101fe
[    13.148] (II) intel(0): Output VGA1 has no monitor section
[    13.148] (II) intel(0): Output LVDS1 has no monitor section
[    13.157] (II) intel(0): Output HDMI1 has no monitor section
[    13.159] (II) intel(0): Output DP1 has no monitor section
[    13.175] (II) intel(0): EDID for output VGA1
[    13.177] (II) intel(0): EDID for output LVDS1
[    13.177] (II) intel(0): Manufacturer: AUO  Model: 22ec  Serial#: 0
[    13.177] (II) intel(0): Year: 2009  Week: 1
[    13.177] (II) intel(0): EDID Version: 1.3
[    13.177] (II) intel(0): Digital Display Input
[    13.177] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    13.177] (II) intel(0): Gamma: 2.20
[    13.177] (II) intel(0): No DPMS capabilities specified
[    13.177] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    13.177] (II) intel(0): First detailed timing is preferred mode
[    13.177] (II) intel(0): redX: 0.620 redY: 0.340   greenX: 0.330 greenY: 0.570
[    13.177] (II) intel(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    13.177] (II) intel(0): Manufacturer's mask: 0
[    13.177] (II) intel(0): Supported detailed timing:
[    13.177] (II) intel(0): clock: 69.3 MHz   Image Size:  344 x 193 mm
[    13.177] (II) intel(0): h_active: 1366  h_sync: 1398  h_sync_end 1422 h_blank_end 1432 h_border: 0
[    13.177] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 775 v_blanking: 806 v_border: 0
[    13.177] (II) intel(0): Unknown vendor-specific block f
[    13.177] (II) intel(0):  AUO
[    13.177] (II) intel(0):  B156XW02 V2
[    13.177] (II) intel(0): EDID (in hex):
[    13.177] (II) intel(0):     00ffffffffffff0006afec2200000000
[    13.177] (II) intel(0):     01130103802213780ac8959e57549226
[    13.177] (II) intel(0):     0f505400000001010101010101010101
[    13.177] (II) intel(0):     010101010101121b5642500026302018
[    13.177] (II) intel(0):     340058c1100000180000000f00000000
[    13.177] (II) intel(0):     00000000000000000020000000fe0041
[    13.177] (II) intel(0):     554f0a202020202020202020000000fe
[    13.177] (II) intel(0):     004231353658573032205632200a00c0
[    13.177] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    13.177] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    13.177] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    13.177] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    13.177] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    13.177] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    13.177] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    13.178] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    13.178] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    13.178] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    13.178] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    13.178] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    13.178] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    13.178] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    13.178] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    13.178] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    13.178] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    13.178] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    13.178] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    13.178] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    13.178] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    13.178] (II) intel(0): Printing probed modes for output LVDS1
[    13.178] (II) intel(0): Modeline "1366x768"x60.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    13.178] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    13.178] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    13.178] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    13.178] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    13.178] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    13.178] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    13.187] (II) intel(0): EDID for output HDMI1
[    13.188] (II) intel(0): EDID for output DP1
[    13.188] (II) intel(0): Output VGA1 disconnected
[    13.188] (II) intel(0): Output LVDS1 connected
[    13.188] (II) intel(0): Output HDMI1 disconnected
[    13.188] (II) intel(0): Output DP1 disconnected
[    13.188] (II) intel(0): Using exact sizes for initial modes
[    13.188] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    13.188] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    13.188] (II) intel(0): Kernel page flipping support detected, enabling
[    13.188] (==) intel(0): DPI set to (96, 96)
[    13.188] (II) Loading sub module "fb"
[    13.188] (II) LoadModule: "fb"
[    13.188] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.188] (II) Module fb: vendor="X.Org Foundation"
[    13.188]     compiled for 1.9.0, module version = 1.0.0
[    13.188]     ABI class: X.Org ANSI C Emulation, version 0.4
[    13.188] (II) UnloadModule: "vesa"
[    13.188] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    13.188] (II) UnloadModule: "fbdev"
[    13.188] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    13.188] (II) UnloadModule: "fbdevhw"
[    13.188] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    13.188] (==) Depth 24 pixmap format is 32 bpp
[    13.188] (==) intel(0): VideoRam: 262144 KB
[    13.188] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    13.189] (II) UXA(0): Driver registered support for the following operations:
[    13.189] (II)         solid
[    13.189] (II)         copy
[    13.189] (II)         composite (RENDER acceleration)
[    13.189] (II)         put_image
[    13.189] (II)         get_image
[    13.189] (==) intel(0): Backing store disabled
[    13.189] (==) intel(0): Silken mouse enabled
[    13.189] (II) intel(0): Initializing HW Cursor
[    13.189] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    13.216] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    13.216] (==) intel(0): DPMS enabled
[    13.216] (==) intel(0): Intel XvMC decoder enabled
[    13.216] (WW) intel(0): Disabling Xv because no adaptors could be initialized.
[    13.216] (II) intel(0): direct rendering: Disabled
[    13.216] (==) intel(0): hotplug detection: "enabled"
[    13.216] (--) RandR disabled
[    13.216] (II) Initializing built-in extension Generic Event Extension
[    13.216] (II) Initializing built-in extension SHAPE
[    13.216] (II) Initializing built-in extension MIT-SHM
[    13.216] (II) Initializing built-in extension XInputExtension
[    13.216] (II) Initializing built-in extension XTEST
[    13.216] (II) Initializing built-in extension BIG-REQUESTS
[    13.216] (II) Initializing built-in extension SYNC
[    13.216] (II) Initializing built-in extension XKEYBOARD
[    13.216] (II) Initializing built-in extension XC-MISC
[    13.216] (II) Initializing built-in extension SECURITY
[    13.216] (II) Initializing built-in extension XINERAMA
[    13.216] (II) Initializing built-in extension XFIXES
[    13.216] (II) Initializing built-in extension RENDER
[    13.216] (II) Initializing built-in extension RANDR
[    13.216] (II) Initializing built-in extension COMPOSITE
[    13.216] (II) Initializing built-in extension DAMAGE
[    13.216] (II) Initializing built-in extension GESTURE
[    13.224] (II) AIGLX: Screen 0 is not DRI2 capable
[    13.224] (II) AIGLX: Screen 0 is not DRI capable
[    13.226] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    13.226] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    13.226] (II) intel(0): Setting screen physical size to 361 x 203
[    13.242] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.248] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    13.249] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    13.249] (II) LoadModule: "evdev"
[    13.249] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.249] (II) Module evdev: vendor="X.Org Foundation"
[    13.249]     compiled for 1.9.0, module version = 2.3.2
[    13.249]     Module class: X.Org XInput Driver
[    13.249]     ABI class: X.Org XInput driver, version 11.0
[    13.249] (**) Power Button: always reports core events
[    13.249] (**) Power Button: Device: "/dev/input/event2"
[    13.280] (II) Power Button: Found keys
[    13.280] (II) Power Button: Configuring as keyboard
[    13.280] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    13.280] (**) Option "xkb_rules" "evdev"
[    13.280] (**) Option "xkb_model" "pc105"
[    13.280] (**) Option "xkb_layout" "us"
[    13.281] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    13.281] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    13.281] (**) Video Bus: always reports core events
[    13.281] (**) Video Bus: Device: "/dev/input/event7"
[    13.328] (II) Video Bus: Found keys
[    13.328] (II) Video Bus: Configuring as keyboard
[    13.328] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    13.328] (**) Option "xkb_rules" "evdev"
[    13.328] (**) Option "xkb_model" "pc105"
[    13.328] (**) Option "xkb_layout" "us"
[    13.330] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    13.330] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    13.330] (**) Video Bus: always reports core events
[    13.330] (**) Video Bus: Device: "/dev/input/event6"
[    13.348] (II) Video Bus: Found keys
[    13.348] (II) Video Bus: Configuring as keyboard
[    13.348] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    13.348] (**) Option "xkb_rules" "evdev"
[    13.348] (**) Option "xkb_model" "pc105"
[    13.348] (**) Option "xkb_layout" "us"
[    13.348] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    13.349] (II) No input driver/identifier specified (ignoring)
[    13.349] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    13.349] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    13.349] (**) Sleep Button: always reports core events
[    13.349] (**) Sleep Button: Device: "/dev/input/event1"
[    13.364] (II) Sleep Button: Found keys
[    13.364] (II) Sleep Button: Configuring as keyboard
[    13.364] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    13.364] (**) Option "xkb_rules" "evdev"
[    13.364] (**) Option "xkb_model" "pc105"
[    13.364] (**) Option "xkb_layout" "us"
[    13.365] (II) config/udev: Adding input device Lenovo easy camera (/dev/input/event4)
[    13.365] (**) Lenovo easy camera: Applying InputClass "evdev keyboard catchall"
[    13.365] (**) Lenovo easy camera: always reports core events
[    13.365] (**) Lenovo easy camera: Device: "/dev/input/event4"
[    13.376] (II) Lenovo easy camera: Found keys
[    13.376] (II) Lenovo easy camera: Configuring as keyboard
[    13.376] (II) XINPUT: Adding extended input device "Lenovo easy camera" (type: KEYBOARD)
[    13.376] (**) Option "xkb_rules" "evdev"
[    13.376] (**) Option "xkb_model" "pc105"
[    13.376] (**) Option "xkb_layout" "us"
[    13.379] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    13.379] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    13.379] (**) AT Translated Set 2 keyboard: always reports core events
[    13.379] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    13.396] (II) AT Translated Set 2 keyboard: Found keys
[    13.396] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    13.396] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    13.396] (**) Option "xkb_rules" "evdev"
[    13.396] (**) Option "xkb_model" "pc105"
[    13.396] (**) Option "xkb_layout" "us"
[    13.396] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    13.396] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    13.396] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    13.396] (II) LoadModule: "synaptics"
[    13.396] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    13.397] (II) Module synaptics: vendor="X.Org Foundation"
[    13.397]     compiled for 1.9.0, module version = 1.2.2
[    13.397]     Module class: X.Org XInput Driver
[    13.397]     ABI class: X.Org XInput driver, version 11.0
[    13.397] (II) Synaptics touchpad driver version 1.2.2
[    13.397] (**) Option "Device" "/dev/input/event5"
[    13.468] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5728
[    13.468] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4902
[    13.468] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    13.468] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    13.468] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    13.576] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    13.576] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    13.636] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    13.636] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    13.636] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    13.636] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    13.636] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    13.732] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    13.732] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    13.732] (II) No input driver/identifier specified (ignoring)
[    13.741] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    13.950] (II) intel(0): EDID vendor "AUO", prod id 8940
[    13.950] (II) intel(0): Printing DDC gathered Modelines:
[    13.950] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    13.978] (II) intel(0): EDID vendor "AUO", prod id 8940
[    13.978] (II) intel(0): Printing DDC gathered Modelines:
[    13.978] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    14.007] (II) intel(0): EDID vendor "AUO", prod id 8940
[    14.007] (II) intel(0): Printing DDC gathered Modelines:
[    14.007] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    14.035] (II) intel(0): EDID vendor "AUO", prod id 8940
[    14.035] (II) intel(0): Printing DDC gathered Modelines:
[    14.035] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    14.048] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.284] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.350] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.366] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.380] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.397] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.416] (II) intel(0): EDID vendor "AUO", prod id 8940
[    14.416] (II) intel(0): Printing DDC gathered Modelines:
[    14.416] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    14.431] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.436] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.451] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.467] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.498] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.506] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.508] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.518] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.518] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.520] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.522] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.522] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.523] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.531] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.533] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.535] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.547] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.551] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.562] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.567] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.578] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.583] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.584] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.584] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.593] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.599] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.609] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.614] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.624] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.630] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.640] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.646] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.646] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.647] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.656] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.660] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.663] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.666] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.670] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.671] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.676] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.676] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.677] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.678] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.680] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.686] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.687] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.694] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.695] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.695] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.701] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.710] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.717] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.726] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.726] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.727] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.732] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.741] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.748] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.757] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.763] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.773] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.774] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.774] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.778] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.789] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.794] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.805] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.809] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.809] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.810] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.825] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.825] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.840] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.841] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.841] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.842] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.856] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.856] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.872] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.872] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.888] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.888] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.888] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.889] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.903] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.903] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.919] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.919] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.919] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.920] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.934] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.935] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.950] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.950] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.950] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.951] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.965] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.966] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.966] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.967] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.981] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.981] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.997] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.997] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.997] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    14.998] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.012] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.013] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.028] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.028] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.029] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.029] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.036] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.044] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.044] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.059] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.060] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.060] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.060] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.075] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.075] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.090] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.091] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.091] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.092] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.106] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.106] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.107] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.107] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.123] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.123] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.139] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.139] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.139] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.140] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.154] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.155] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.155] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.156] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.170] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.171] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.186] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.186] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.187] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.187] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.202] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.202] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.217] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.218] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.218] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.219] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.233] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.233] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.234] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.234] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.249] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.249] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.264] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.265] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.265] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.265] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.280] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.280] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.281] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.281] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.296] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.296] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.296] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.297] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.311] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.312] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.327] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.327] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.328] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.328] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.343] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.343] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.343] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.344] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.355] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.359] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.374] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.374] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.389] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.405] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    15.407] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.067] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.082] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.084] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.098] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.100] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.113] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.115] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.129] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.132] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.145] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.147] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.161] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.163] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.545] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.547] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.553] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.562] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.563] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.563] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.693] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    17.869] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    18.781] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    18.882] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    19.024] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    20.276] (II) intel(0): EDID vendor "AUO", prod id 8940
[    20.276] (II) intel(0): Printing DDC gathered Modelines:
[    20.276] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    20.314] (II) intel(0): EDID vendor "AUO", prod id 8940
[    20.314] (II) intel(0): Printing DDC gathered Modelines:
[    20.314] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    20.341] (II) intel(0): EDID vendor "AUO", prod id 8940
[    20.342] (II) intel(0): Printing DDC gathered Modelines:
[    20.342] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    20.395] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    20.469] (II) intel(0): EDID vendor "AUO", prod id 8940
[    20.469] (II) intel(0): Printing DDC gathered Modelines:
[    20.469] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    25.740] (II) intel(0): EDID vendor "AUO", prod id 8940
[    25.740] (II) intel(0): Printing DDC gathered Modelines:
[    25.740] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1422 1432  768 771 775 806 -hsync -vsync (48.4 kHz)
[    26.746] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    26.751] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    26.984] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    27.037] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    27.614] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    27.617] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    27.716] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    28.554] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    28.554] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    28.555] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    28.556] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    28.557] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    28.557] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    28.559] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    28.564] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    28.578] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    31.825] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    31.825] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    31.827] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    31.827] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    31.842] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    31.843] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    31.843] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    31.843] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    31.844] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    33.421] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    33.650] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    33.722] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    33.729] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    33.879] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    34.365] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    34.437] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    35.290] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    35.291] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    39.719] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    39.792] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    39.799] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    39.849] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    39.927] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    39.927] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    45.761] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    45.833] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    45.841] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    45.892] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    45.964] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    45.971] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    49.128] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    51.806] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    51.878] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    51.886] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    51.937] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    52.010] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    52.016] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    57.849] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    57.921] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    57.929] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    57.980] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    58.052] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    58.059] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    61.412] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    61.412] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    61.413] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    61.512] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    61.612] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    61.711] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    61.811] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    61.911] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    62.011] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    62.111] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    62.213] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    62.313] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    62.413] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    62.513] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    62.613] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    62.713] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    62.813] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    62.913] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    63.013] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    63.113] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    63.214] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    63.314] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    63.414] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    63.514] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    63.614] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    63.714] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    63.814] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    63.893] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    63.915] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    63.966] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    63.974] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    64.014] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    64.025] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    64.098] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    64.104] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    64.114] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    64.215] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    64.315] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    64.415] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    64.515] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    64.615] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    64.715] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    64.815] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    64.915] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    65.015] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    65.115] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    65.216] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    65.316] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    65.416] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    65.516] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    65.617] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    65.717] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    65.817] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    65.917] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    66.017] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    66.118] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    66.218] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    66.318] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    66.418] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    66.518] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    66.618] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    66.718] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    66.818] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    66.918] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    67.018] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    67.119] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    67.219] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    67.260] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    67.319] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    67.419] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    67.519] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    67.619] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    67.719] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    67.819] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    67.919] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    68.019] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    68.120] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    68.220] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    68.312] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    68.320] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    68.420] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    68.520] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    68.853] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    68.854] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    69.458] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    69.938] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    70.011] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    70.019] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    70.070] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    70.143] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    70.150] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    75.261] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    75.657] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    75.664] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    75.708] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    75.714] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    75.768] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    75.890] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    75.993] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    75.994] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    76.151] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    76.651] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    76.951] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    77.027] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    77.037] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    77.151] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    77.651] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.153] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.451] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.452] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.654] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.695] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.695] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.827] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.835] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.835] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.835] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.853] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.862] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.865] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.866] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.970] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.982] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    78.989] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    79.155] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    79.206] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    79.581] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    79.655] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    80.092] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    80.157] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    80.211] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    80.583] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    81.137] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    81.246] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    81.784] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    81.785] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    81.786] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.020] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.026] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.034] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.034] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.040] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.041] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.044] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.045] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.058] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.058] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.239] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.283] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.285] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.315] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.315] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.317] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.348] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.352] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.381] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.384] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.415] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.415] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.417] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.448] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.448] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.451] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.481] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.482] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.484] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.515] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.515] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.518] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.549] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.549] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.552] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.583] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.583] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.586] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.614] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.614] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.617] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.644] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.645] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.681] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.682] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.685] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.702] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.704] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.708] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.708] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.715] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.727] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.729] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.746] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.746] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.750] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.782] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.785] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.813] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.816] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.843] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.876] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.877] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.908] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    82.909] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.296] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.382] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.394] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.400] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.422] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.457] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.458] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.475] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.476] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.540] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.542] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.551] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.982] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.987] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    83.987] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.151] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.155] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.156] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.156] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.159] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.159] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.161] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.161] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.198] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.202] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.204] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.204] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.354] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.356] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.358] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.358] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.478] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.480] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.481] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.482] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.485] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.486] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.488] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.488] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.664] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.664] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.667] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.737] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.758] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.768] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.785] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.785] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.788] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.806] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.808] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.810] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.819] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.822] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.822] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.823] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.859] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.859] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.862] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.942] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.943] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.963] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.963] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.983] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.985] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.987] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    84.989] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.100] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.103] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.177] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.184] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.184] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.334] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.334] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.337] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.459] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.479] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.498] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.499] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.519] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.520] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.538] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.555] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.572] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    85.604] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    86.220] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    86.223] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    86.307] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    86.309] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    86.349] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    86.368] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.046] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.047] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.301] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.313] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.319] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.358] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.408] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.457] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.477] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.509] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.565] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.568] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.625] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.683] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.707] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.751] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.754] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.820] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.823] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.888] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    87.952] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.028] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.029] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.129] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.168] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.198] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.232] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.254] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.270] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.308] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.348] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.390] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.394] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.434] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.478] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.529] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.574] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.621] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.671] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.725] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.860] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.903] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.915] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    88.967] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.017] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.060] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.066] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.091] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.132] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.132] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.137] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.138] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.216] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.236] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.254] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.291] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.331] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.397] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.397] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.422] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.450] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.640] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.644] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.665] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.700] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.711] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.725] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.729] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    89.729] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    90.058] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    90.104] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    90.380] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    91.292] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    91.293] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    92.041] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    92.041] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    92.048] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    92.113] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    92.113] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    92.859] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    93.252] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    93.609] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    93.621] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    93.623] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    93.626] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    94.462] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    94.465] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    94.605] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    94.606] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    94.608] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    94.791] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    94.791] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    94.797] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    94.955] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    94.955] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    94.963] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.129] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.129] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.134] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.311] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.312] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.314] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.491] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.491] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.494] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.649] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.649] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.652] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.762] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.762] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.769] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.973] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.973] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    95.975] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.268] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.268] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.273] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.425] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.425] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.430] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.645] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.645] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.647] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.984] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.985] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.989] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.990] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.995] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.995] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.998] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    96.998] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.274] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.292] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.294] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.295] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.296] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.304] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.308] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.348] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.393] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.437] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.480] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.532] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.576] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.684] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.717] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.729] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.767] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.805] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.844] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.882] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.927] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    97.976] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.030] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.086] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.146] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.175] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.202] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.256] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.309] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.337] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.358] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.406] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.455] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.503] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.553] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.603] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.647] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.658] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.707] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.757] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.806] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.857] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.907] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    98.955] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.003] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.051] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.099] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.148] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.197] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.247] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.297] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.345] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.394] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.457] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.466] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.515] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.523] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.532] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.566] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.613] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.665] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.714] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.763] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.812] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.861] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.912] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[    99.962] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   100.012] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   100.066] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   100.444] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   100.717] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.089] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.137] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.199] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.259] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.319] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.380] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.440] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.478] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.500] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.561] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.621] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.682] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.742] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.803] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.864] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.924] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   102.985] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.007] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.059] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.110] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.161] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.164] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.210] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.261] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.311] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.362] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.412] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.462] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.513] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.563] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.613] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.664] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.713] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.764] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.815] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.865] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.916] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   103.966] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.016] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.067] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.117] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.167] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.218] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.268] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.319] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.369] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.419] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.470] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.520] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.571] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.621] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.671] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.722] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.772] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.823] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.873] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.923] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   104.974] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.024] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.075] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.126] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.175] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.226] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.276] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.327] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.377] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.427] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.478] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.528] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.579] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.629] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.679] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.730] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.780] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.831] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.881] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.931] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   105.982] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.032] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.083] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.133] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.184] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.234] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.284] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.335] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.385] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.435] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.486] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.536] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.587] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.637] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.687] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.738] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.788] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.839] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.889] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   106.960] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.029] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.076] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.122] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.167] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.223] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.223] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.264] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.329] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.335] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.356] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.416] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.455] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.501] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.539] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.547] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.595] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.642] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.645] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   107.645] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   108.093] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   108.309] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   109.154] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   109.356] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   109.365] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   109.373] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   109.382] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   109.393] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   109.704] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   109.763] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   109.780] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   109.794] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   110.145] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   110.179] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   110.220] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   110.265] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.093] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.140] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.199] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.259] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.318] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.378] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.437] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.485] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.495] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.555] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.613] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.675] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.733] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.760] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.768] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.772] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.793] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.795] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.853] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.909] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   111.981] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.002] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.041] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.043] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.100] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.159] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.217] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.275] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.335] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.394] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.453] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.513] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.570] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.629] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.732] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.756] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.803] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.852] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.901] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.950] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   112.999] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.049] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.096] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.148] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.197] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.247] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.296] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.346] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.395] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.444] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.493] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.541] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.593] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.641] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.690] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.739] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.788] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.837] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.887] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.936] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   113.982] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.033] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.080] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.136] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.186] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.236] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.287] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.337] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.388] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.438] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.488] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.537] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.585] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.640] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.690] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.740] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.788] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.841] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.892] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.942] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   114.992] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.040] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.088] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.144] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.194] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.244] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.295] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.345] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.396] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.446] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.496] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.545] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.593] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.648] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.698] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.748] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.797] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.849] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.900] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.950] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   115.996] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.049] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.098] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.152] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.182] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.200] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.252] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.303] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.357] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.404] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.454] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.504] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.557] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.606] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.656] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.707] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.711] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.757] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.805] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.858] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.909] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   116.959] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.009] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.059] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.110] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.160] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.211] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.261] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.309] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.362] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.413] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.463] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.513] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.564] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.614] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.665] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.691] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.714] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.751] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.754] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.757] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.759] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.784] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.836] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.884] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.906] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.933] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   117.981] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.012] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.026] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.077] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.124] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.175] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.224] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.274] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.323] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.373] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.422] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.471] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.521] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.573] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.625] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.676] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.725] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.778] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.829] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.879] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.929] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   118.981] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.033] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.084] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.134] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.184] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.234] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.284] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.377] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.400] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.433] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.448] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.492] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.534] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.582] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.631] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   119.633] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   120.017] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   120.293] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   120.721] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   120.870] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   120.885] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   120.896] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   120.916] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   120.935] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   120.955] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   120.977] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   120.998] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   121.373] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   121.395] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   121.495] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   121.549] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   121.608] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   121.665] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   121.689] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   121.725] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   121.783] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   121.844] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   121.901] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   121.954] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   121.964] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   121.992] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.043] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.095] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.120] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.140] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.146] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.194] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.248] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.300] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.303] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.345] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.397] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.400] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.449] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.500] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.551] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.554] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.584] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.600] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.646] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.696] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.751] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.800] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.850] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.899] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   122.950] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.000] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.051] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.164] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.206] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.249] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.294] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.329] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.339] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.385] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.401] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.401] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.402] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.403] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.409] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.429] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.477] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.524] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.556] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.571] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.618] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.665] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.713] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.762] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.810] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.858] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.906] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   123.958] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.012] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.065] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.120] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.173] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.227] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.282] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.353] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.407] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.456] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.500] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.540] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.549] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.603] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.651] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.693] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.696] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.748] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.792] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.860] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.904] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   124.953] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.005] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.050] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.101] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.153] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.154] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.205] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.251] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.310] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.368] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.377] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.409] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.458] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.505] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.537] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.555] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.606] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.664] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.670] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.702] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.753] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.803] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.852] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.901] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   125.992] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.049] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.094] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.098] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.138] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.187] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.235] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.263] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.283] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.332] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.380] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.429] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.472] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.525] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.579] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.630] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.680] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.731] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.781] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.832] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.936] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.945] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   126.980] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.026] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.071] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.114] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.160] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.209] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.256] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.281] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.308] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.317] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.328] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.338] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.370] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.371] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.377] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.405] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.406] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.417] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.421] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.434] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.434] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.437] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.449] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.459] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.471] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.485] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.486] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.495] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.530] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.578] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.625] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.673] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.721] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.772] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.825] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.839] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.856] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.876] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.892] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.906] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.929] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.941] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.953] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.963] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.974] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   127.993] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.008] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.028] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.034] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.056] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.089] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.138] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.188] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.237] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.286] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.336] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.385] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.438] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.441] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.453] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.467] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.484] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.507] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.519] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.530] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.543] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.555] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.565] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.575] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.586] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.588] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.628] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.637] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.690] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.739] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.788] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.838] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.888] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.939] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   128.989] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.039] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.090] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.140] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.187] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.241] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.309] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.369] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.381] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.419] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.421] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.453] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.470] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.479] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.499] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.512] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.522] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.524] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.552] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.573] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.597] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.622] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.676] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.726] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.776] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.827] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.878] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.928] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.974] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   129.984] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.007] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.008] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.030] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.079] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.129] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.178] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.227] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.262] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.277] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.327] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.376] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.425] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.472] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.525] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.698] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.710] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.715] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.729] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.745] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.771] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.796] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.821] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.846] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.864] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.881] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.913] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.948] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.979] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   130.982] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   131.424] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   131.637] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   135.527] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   135.967] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   135.983] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   136.005] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   137.401] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   137.508] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   137.520] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   137.532] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   137.545] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   137.977] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   138.098] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   138.229] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   138.264] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   139.531] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   139.534] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   139.534] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   139.538] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   139.538] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   139.821] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   140.309] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   140.335] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   140.344] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   140.622] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   140.913] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   140.934] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   140.957] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   140.960] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   141.441] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   141.474] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   141.480] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   141.615] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   141.628] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   141.630] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   141.639] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   141.640] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   141.884] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   141.894] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   141.935] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   141.954] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.058] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.069] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.082] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.091] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.092] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.093] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.094] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.096] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.097] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.107] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.113] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.635] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.636] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.636] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.643] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   142.693] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   143.152] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   143.294] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   143.822] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   144.270] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   144.581] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   145.150] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   145.708] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   145.719] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   145.750] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   146.067] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   146.144] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   146.352] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   146.952] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   147.398] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   147.423] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   147.553] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   147.912] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.067] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.068] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.068] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.080] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.081] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.081] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.092] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.093] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.094] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.104] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.105] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.106] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.116] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.117] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.118] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.129] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.130] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.130] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.141] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.141] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.142] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.153] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.154] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.154] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.164] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.165] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.165] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.176] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.177] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.177] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.188] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.188] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.189] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.200] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.200] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.201] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.212] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.213] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.213] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.224] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.225] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.225] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.235] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.236] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.236] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.247] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.248] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.248] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.258] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.259] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.260] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.271] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.272] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.273] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.284] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.285] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.285] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.297] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.297] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.298] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.308] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.308] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.309] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.318] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.319] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.320] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.331] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.331] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.331] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.343] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.343] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.344] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   148.701] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   149.302] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   149.853] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   149.855] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   149.859] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   149.859] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   149.866] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   149.867] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   151.565] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   151.611] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   151.960] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   152.104] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   152.595] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   153.856] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   154.356] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   154.728] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   154.775] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   154.787] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   155.557] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   155.761] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   155.763] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   155.842] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   155.844] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   155.856] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   155.862] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   155.869] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   155.871] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   155.872] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   155.874] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   155.877] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   155.878] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   156.082] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   156.086] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   156.465] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   157.321] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   157.757] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   158.356] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   158.822] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   158.834] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   158.885] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   158.914] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   159.390] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   159.990] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.042] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.081] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.110] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.137] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.171] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.197] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.226] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.257] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.290] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.318] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.654] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.687] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.722] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.749] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   160.781] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   161.038] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   161.079] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   161.109] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   161.139] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   161.167] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   161.570] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   161.602] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   163.918] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   163.955] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   163.990] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   164.038] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   164.080] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   164.109] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   164.139] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   164.182] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   164.534] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   164.571] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   164.600] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   164.950] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   164.992] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   165.019] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   165.051] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   165.079] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   165.109] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   165.139] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   165.505] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   165.537] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   165.571] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   165.600] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   165.629] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   165.973] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   166.011] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   166.040] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   166.069] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   166.098] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   166.414] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   166.449] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   166.483] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   166.513] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   166.542] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   166.882] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   166.923] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   166.946] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   166.977] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   167.254] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   167.295] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   167.319] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   167.353] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   167.382] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   167.689] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   167.721] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   167.757] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   167.781] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   168.058] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   168.093] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   168.129] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   168.154] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   168.467] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   168.502] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   168.537] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   168.561] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   168.874] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   168.909] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   168.944] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   168.969] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   169.004] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   169.161] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   169.282] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   169.317] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   174.295] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   174.296] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   174.296] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   174.493] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   174.503] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   174.504] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   174.505] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   174.513] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   174.518] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   174.518] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   174.563] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   176.533] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   176.773] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   177.262] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   177.337] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   177.562] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   177.613] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   177.901] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.118] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.159] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.184] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.213] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.245] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.277] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.387] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.424] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.449] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.476] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.512] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.535] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.855] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.883] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.917] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.942] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   179.977] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   181.599] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   181.643] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   181.664] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   181.703] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   181.724] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   181.755] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   181.803] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   182.159] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   182.186] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   182.221] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   182.243] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   182.281] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   182.306] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   182.603] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   182.630] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   182.665] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   182.697] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   182.723] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   183.070] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   183.108] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   183.128] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   183.167] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   183.188] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   183.575] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   183.605] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   183.638] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   183.662] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   183.696] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   184.059] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   184.103] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   184.123] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   184.162] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   184.507] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   185.107] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   185.707] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   185.811] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   185.847] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   185.881] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   185.910] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   185.941] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   185.966] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   186.252] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   186.281] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   186.316] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   186.347] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   186.370] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   186.675] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   186.719] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   186.740] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   186.771] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   187.037] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   187.079] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   187.099] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   187.138] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   187.394] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   187.439] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   187.460] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   187.499] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   187.739] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   187.775] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   187.796] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   187.835] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   188.103] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   188.148] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   188.174] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   188.427] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   188.466] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   188.497] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   188.530] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   188.807] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   188.843] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   188.868] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   193.278] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   193.399] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.108] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.224] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.226] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.232] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.242] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.245] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.251] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.251] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.252] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.255] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.255] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.588] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.600] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.621] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.643] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.655] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.667] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.678] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   194.991] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   195.015] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   195.039] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   195.238] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   195.711] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   195.811] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   195.813] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   195.824] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   195.829] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   195.831] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   195.833] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   195.841] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   195.841] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.019] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.035] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.040] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.041] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.046] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.060] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.064] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.067] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.068] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.076] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.076] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.339] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.341] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.342] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.352] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   196.655] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   197.093] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   197.413] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   197.858] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   198.220] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   198.248] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   198.297] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   198.321] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   198.346] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   198.791] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   199.391] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   199.990] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   200.590] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   200.681] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   200.717] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   200.746] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   200.771] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   200.806] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   200.870] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   200.911] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   200.936] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   200.968] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   201.014] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   201.294] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   201.322] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   201.360] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   201.389] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   201.746] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   201.806] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   202.392] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   202.992] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   203.066] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   203.101] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   203.137] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   203.163] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   203.197] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.038] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.076] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.109] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.140] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.165] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.200] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.222] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.281] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.314] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.362] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.410] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.450] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.734] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.771] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.802] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.834] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.861] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.892] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   204.942] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   205.254] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   205.287] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   205.318] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   205.349] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   205.379] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   205.407] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   205.795] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   205.832] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   205.862] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   205.890] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   205.921] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   205.946] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   205.980] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   206.234] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   206.271] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   206.301] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   206.335] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   206.361] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   206.658] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   206.686] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   207.196] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   207.796] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   208.396] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   208.996] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.087] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.100] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.123] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.147] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.158] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.171] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.184] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.207] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.219] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.231] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.244] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.280] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.291] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.596] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.663] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.688] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.711] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.723] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.736] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.747] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.759] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.772] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.784] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   209.807] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.197] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.527] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.568] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.597] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.629] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.678] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.716] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.744] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.770] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.801] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.833] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.861] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.894] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.921] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.952] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   210.982] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   211.628] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   211.631] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   211.644] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   211.655] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   211.667] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   211.679] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   211.691] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   211.703] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   211.715] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   211.728] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   211.739] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   211.751] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   211.787] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   212.291] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   212.327] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   212.375] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   212.399] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   212.459] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   212.544] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   212.566] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   212.603] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   212.638] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   213.018] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   213.050] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   213.084] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   213.115] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   213.147] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   213.170] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   213.202] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   213.234] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   213.944] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   213.946] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   213.959] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   213.970] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   213.982] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   213.995] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.008] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.030] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.043] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.055] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.067] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.079] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.188] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.247] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.259] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.282] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.307] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.318] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.380] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.817] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.855] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.884] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.914] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.942] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   214.973] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   215.001] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   215.030] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   215.060] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   215.090] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   215.118] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   215.148] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   215.191] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   215.256] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   215.874] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   215.911] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   215.938] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   215.969] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   215.996] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.028] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.057] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.085] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.149] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.193] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.222] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.266] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.305] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.353] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.416] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.803] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.842] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.875] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.905] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.934] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.959] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   216.992] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.017] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.052] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.082] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.112] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.158] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.195] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.721] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.758] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.785] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.818] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.847] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.873] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.903] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.933] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.959] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   217.993] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   218.022] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   218.051] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   218.082] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   219.104] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   219.119] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   219.191] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   219.238] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   219.695] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   219.732] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   219.764] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   219.790] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   219.825] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   219.858] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   219.887] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   219.911] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   219.946] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   219.971] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   220.006] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   220.030] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   220.064] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   220.089] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   220.123] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   220.640] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   220.641] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   220.654] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   220.666] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   220.680] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   220.702] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   220.751] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.190] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.222] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.255] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.287] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.315] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.347] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.372] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.399] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.435] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.459] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.491] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.517] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.546] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.576] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   221.610] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   223.889] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   223.926] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   223.954] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   223.986] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   224.014] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   224.045] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   224.073] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   224.378] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   224.418] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   224.448] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   224.477] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   224.508] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   224.537] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   224.566] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   224.814] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   224.849] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   224.877] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   224.909] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   225.209] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   225.242] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   225.275] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   225.306] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   225.594] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   225.630] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   225.657] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   225.691] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   225.718] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   226.013] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   226.049] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   227.104] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   227.465] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   227.759] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   227.858] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   227.961] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   228.059] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   228.158] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   228.261] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   228.358] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   228.458] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   228.472] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   228.605] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   228.688] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   228.712] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   228.759] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   228.869] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.000] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.165] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.217] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.627] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.858] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.867] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.899] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.914] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.921] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.927] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.959] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.975] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.982] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.988] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   229.998] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   230.012] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   230.028] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   230.045] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   230.061] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   230.073] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   230.082] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   230.097] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   230.115] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   230.132] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   230.574] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   230.885] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   232.402] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   232.450] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   233.317] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.211] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.234] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.246] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.258] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.271] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.282] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.294] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.318] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.330] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.342] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.582] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.606] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.619] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.666] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.690] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.702] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.726] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.739] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   235.749] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   236.100] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   236.111] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   236.123] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   236.134] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   236.147] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   236.159] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   236.171] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   236.183] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   236.206] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   236.217] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   236.230] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.066] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.102] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.130] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.160] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.189] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.221] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.249] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.282] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.311] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.338] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.369] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.401] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.429] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.833] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.869] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.899] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   237.923] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   238.338] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   238.373] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   238.404] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   238.433] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   238.463] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   238.493] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   238.805] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   238.838] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   238.869] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   238.896] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   238.930] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   238.960] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   239.243] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   239.284] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   239.310] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   239.339] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   239.372] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   239.394] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   239.669] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   239.706] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   239.737] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   239.766] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   239.795] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   240.101] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   240.137] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   240.165] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   240.197] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   240.225] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   240.256] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   240.546] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   240.581] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   240.609] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   240.809] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.409] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.647] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.667] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.678] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.690] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.702] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.714] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.727] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.738] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.750] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.774] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.846] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.859] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.883] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.906] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.919] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.931] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.943] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.954] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.966] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   241.991] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   242.003] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   242.009] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   242.026] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   242.039] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   242.506] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   242.567] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   242.609] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   243.209] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   243.808] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   244.330] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   244.807] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   244.880] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   244.937] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   244.964] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   245.009] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   245.059] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   245.890] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   245.891] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   245.897] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   245.900] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   246.496] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.095] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.420] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.695] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.806] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.822] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.834] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.835] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.836] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.843] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.844] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.844] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.848] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.854] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.854] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.854] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.865] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.866] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.880] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.881] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.895] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.896] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.910] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.911] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.925] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.925] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.940] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.941] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.954] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.955] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.969] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.970] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.984] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.985] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   247.999] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.000] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.014] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.024] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.025] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.028] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.029] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.043] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.055] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.056] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.058] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.059] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.073] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.074] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.076] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.081] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   248.083] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   249.477] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   250.953] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.120] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.135] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.152] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.175] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.192] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.205] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.223] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.241] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.303] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.374] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.428] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.488] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.548] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.608] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.638] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.664] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.725] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.790] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.850] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.911] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   251.971] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.031] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.092] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.152] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.212] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.268] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.333] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.389] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.453] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.514] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.573] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.633] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.693] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.754] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.814] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.872] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.937] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   252.998] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.058] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.118] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.179] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.240] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.300] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.360] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.421] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.481] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.541] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.602] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.662] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.723] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.783] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.843] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.904] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   253.964] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.024] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.080] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.145] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.205] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.273] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.280] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.317] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.371] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.420] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.440] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.469] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.519] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.560] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.565] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.616] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.668] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.719] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.722] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.764] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.817] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.866] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.920] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.945] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   254.971] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.020] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.069] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.104] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.119] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.172] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.222] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.271] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.320] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.369] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.392] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.416] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.472] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.522] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.572] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.621] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.669] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.722] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.728] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.777] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.829] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.879] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.929] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   255.977] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.027] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.075] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.126] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.173] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.220] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.271] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.323] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.373] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.424] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.473] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.525] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.575] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.626] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.676] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.727] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.777] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.828] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.878] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.928] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   256.977] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.025] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.080] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.130] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.180] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.231] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.282] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.332] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.382] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.432] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.481] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.531] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.584] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.635] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.685] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.734] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.786] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.837] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.887] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.937] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   257.988] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.039] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.089] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.140] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.189] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.236] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.290] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.341] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.392] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.441] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.493] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.543] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.594] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.644] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.692] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.745] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.880] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.924] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   258.965] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.055] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.055] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.069] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.076] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.076] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.077] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.078] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.079] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.104] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.135] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.172] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.204] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.258] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.259] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.297] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.346] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.395] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.442] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.497] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.500] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.556] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.655] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.676] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.700] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.745] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.789] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.828] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.834] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.878] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.928] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   259.975] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.021] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.069] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.120] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.125] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.172] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.225] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.277] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.330] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.381] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.432] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.477] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.529] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.578] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.620] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.623] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.966] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.990] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   260.990] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   261.005] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   261.013] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   261.058] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   261.063] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   261.097] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   261.151] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   261.152] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   261.163] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   261.283] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   261.459] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   262.545] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   262.582] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   263.744] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   264.302] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   264.331] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   264.342] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   264.344] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   265.532] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   266.725] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   267.506] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   267.920] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   268.017] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   268.026] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   268.324] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   268.326] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   268.500] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.116] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.265] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.412] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.428] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.432] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.660] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.670] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.703] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.711] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.757] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.764] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.768] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.801] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.808] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.811] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.847] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.859] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.864] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.892] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.901] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.904] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.936] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.945] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.980] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   269.989] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   270.029] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   270.037] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   270.080] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   270.087] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   270.144] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   270.231] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   270.310] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   270.322] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   270.371] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   270.681] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.091] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.336] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.348] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.365] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.387] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.407] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.420] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.430] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.441] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.457] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.469] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.480] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.493] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.507] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.517] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.530] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.541] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.550] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.560] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.572] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.587] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.603] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.613] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.626] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.637] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.650] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.661] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.674] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.686] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.704] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.720] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.736] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.745] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.758] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.769] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   271.770] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   272.360] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   272.701] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   275.038] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   275.447] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   275.450] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   275.899] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   275.902] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   275.906] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   276.656] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   276.659] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   277.707] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   277.710] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   277.714] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   277.823] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   278.089] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   278.093] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   278.096] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   278.318] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   278.321] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   278.325] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   278.580] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   278.584] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   278.587] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   278.875] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   278.879] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   278.882] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   279.312] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   279.316] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   279.319] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   280.522] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   281.160] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   281.163] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   281.219] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   281.219] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   281.735] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   281.738] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   281.741] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   282.945] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   283.872] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   283.877] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   283.893] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   283.896] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   283.907] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   283.908] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   283.917] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   283.922] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   283.935] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   283.937] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   283.950] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   283.959] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.330] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.331] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.347] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.360] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.361] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.369] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.370] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.379] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.390] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.403] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.416] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.428] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.441] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.442] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.451] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.483] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.784] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.785] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.793] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.794] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.803] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.804] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.814] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.816] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.831] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.831] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.840] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.841] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.850] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.852] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.862] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.864] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.873] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.874] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.884] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.896] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   284.927] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.243] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.250] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.252] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.259] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.259] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.269] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.279] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.286] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.294] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.304] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.315] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.325] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.337] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.351] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.357] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.376] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.684] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.685] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.693] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.696] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.703] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.703] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.713] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.726] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.726] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.738] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.750] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.756] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.769] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.772] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.779] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.781] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.795] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.807] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   285.840] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.105] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.109] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.124] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.141] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.144] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.158] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.184] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.194] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.195] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.216] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.216] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.228] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.537] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.538] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.551] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.561] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.564] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.577] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.591] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   286.592] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   287.964] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   289.031] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   289.079] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   289.188] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   289.851] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   289.853] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   289.890] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   289.893] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   289.897] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   289.976] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   289.976] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   290.090] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   290.093] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   290.104] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   290.108] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.037] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.085] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.220] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.226] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.229] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.413] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.418] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.422] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.488] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.491] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.495] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.597] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.601] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.604] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.718] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.721] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.725] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.873] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.877] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   291.880] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.065] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.068] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.071] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.592] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.596] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.599] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.774] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.777] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.781] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.858] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.861] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.866] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.941] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.944] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   292.948] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   293.073] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   293.077] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   293.080] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   293.779] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   293.783] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   293.786] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   293.986] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   293.990] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   293.993] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   294.111] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   294.113] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   294.177] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   294.181] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   294.184] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.202] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.209] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.212] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.390] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.393] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.397] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.544] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.548] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.551] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.641] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.644] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.647] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.700] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.704] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.713] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.857] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.861] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   295.864] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.010] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.014] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.018] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.121] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.124] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.127] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.218] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.221] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.224] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.782] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.785] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.788] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.894] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.901] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   296.905] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.198] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.202] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.206] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.310] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.313] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.317] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.491] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.494] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.498] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.630] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.635] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.645] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.882] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.886] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   297.889] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   298.795] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   298.799] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   298.802] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   298.940] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   298.944] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   298.947] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   299.193] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   299.196] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   299.199] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   299.314] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   299.317] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   299.321] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   299.480] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   299.483] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   299.487] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   300.409] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   300.412] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   300.416] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   300.710] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   300.713] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   300.717] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   301.344] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   301.347] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   301.351] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   301.511] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   301.515] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   301.518] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   301.721] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   301.729] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   301.732] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   301.887] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   301.890] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   301.893] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   302.350] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   302.355] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   302.358] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   302.534] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   302.537] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   302.541] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   302.745] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   302.750] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   302.753] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   302.915] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   302.919] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   302.922] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   303.099] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   303.102] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   303.105] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   303.257] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   303.260] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   303.263] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   303.372] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   303.375] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   303.378] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   303.866] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   303.869] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   303.872] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.239] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.242] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.245] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.394] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.397] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.401] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.478] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.481] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.484] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.645] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.648] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.652] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.801] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.805] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   304.808] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   305.003] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   305.006] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   305.010] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   305.839] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   305.845] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   305.849] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   306.992] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   306.998] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.001] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.153] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.157] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.160] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.324] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.332] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.335] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.569] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.574] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.577] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.717] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.721] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.724] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.882] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.887] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   307.890] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   308.053] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   308.056] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   308.059] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   308.246] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   308.250] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   308.253] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   308.553] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   308.558] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   308.561] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   309.767] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   310.968] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   311.665] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   311.674] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   311.678] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   312.883] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   314.084] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   315.283] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   316.484] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   316.766] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   316.770] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   316.773] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   317.497] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   317.500] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   317.503] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   317.771] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   317.778] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   317.781] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   317.906] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   317.909] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   317.912] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.039] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.042] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.045] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.387] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.390] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.393] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.578] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.581] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.585] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.686] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.689] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.693] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.862] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.866] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   318.869] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   319.498] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   319.503] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   319.506] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   319.718] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   319.721] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   319.725] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   319.874] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   319.878] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   319.881] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   319.958] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   319.961] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   319.964] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   320.138] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   320.142] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   320.145] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   320.281] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   320.285] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   320.288] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   320.582] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   320.586] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   320.589] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   320.749] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   320.752] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   320.755] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   321.036] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   321.039] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   321.042] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   321.411] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   321.414] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   321.417] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   321.490] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   321.494] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   321.498] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   321.637] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   321.640] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   321.643] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   321.877] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   323.602] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   324.208] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   324.214] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   324.219] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   324.225] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   324.229] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   324.233] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   324.909] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   324.914] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   324.917] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   325.154] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   325.157] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   325.160] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   326.362] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   326.780] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   326.973] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   326.976] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   326.980] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   327.986] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   327.989] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   327.993] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   328.966] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   328.972] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   329.198] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   330.402] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   330.636] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   330.668] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   330.668] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   330.701] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   330.723] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   330.737] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   330.763] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   330.780] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   330.833] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   330.863] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   330.899] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   330.930] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   330.977] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   331.006] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   331.469] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   331.499] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   331.528] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   331.547] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   331.838] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   331.848] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   331.850] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   331.864] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   331.864] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   331.889] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   331.890] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   331.901] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   331.928] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.001] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.538] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.574] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.588] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.588] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.597] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.614] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.633] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.645] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.645] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.655] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.678] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.686] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.714] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.747] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   332.861] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   335.387] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   335.828] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   335.831] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.211] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.295] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.306] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.317] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.329] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.341] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.353] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.377] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.439] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.546] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.834] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.871] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.893] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.906] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.930] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   337.966] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   338.039] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   338.086] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   338.653] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   338.911] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   338.913] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   339.575] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   339.900] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   339.955] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   339.957] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.067] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.068] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.584] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.787] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.787] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.792] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.793] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.845] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.854] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.854] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.857] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.868] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.871] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.871] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.871] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.873] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.876] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.880] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.884] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   340.939] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   341.265] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   341.277] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   341.289] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   341.289] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   341.292] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   341.292] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   341.471] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   342.071] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   342.340] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   342.428] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   342.880] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   343.472] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   343.612] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   343.708] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   344.207] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   344.221] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   344.788] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   345.264] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   345.380] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   345.480] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   346.000] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   346.219] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   346.221] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   346.237] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   346.239] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   346.239] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   346.520] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   346.644] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   346.830] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   347.244] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   347.400] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   347.505] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   348.075] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   348.215] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   348.217] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   348.229] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   348.229] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   348.232] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   348.233] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   348.808] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   348.888] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   349.040] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   349.181] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   349.500] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   349.672] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   349.868] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   350.067] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   350.069] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   350.075] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   350.076] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   350.077] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   350.077] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   350.643] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   351.244] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   351.844] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   352.446] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   353.046] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   353.647] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   354.044] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   354.376] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   354.964] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   355.148] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   355.436] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   355.848] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   356.012] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   356.244] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   356.448] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   356.604] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   356.856] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   357.425] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   357.964] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   358.384] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   358.956] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   359.320] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   359.889] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   360.348] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   360.910] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   361.224] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   361.795] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   362.024] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   362.353] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   362.560] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   362.748] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   363.317] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   363.518] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   363.532] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   363.637] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   364.097] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   364.698] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   365.299] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   365.792] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   365.807] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   366.374] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   366.947] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   366.954] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   366.961] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   366.963] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   366.963] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   366.965] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   366.965] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   366.973] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   366.978] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   366.978] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   367.023] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   367.370] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   367.374] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   367.377] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   367.452] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   367.614] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   367.631] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   367.640] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   367.767] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   368.170] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   368.189] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   368.971] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   369.372] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   369.944] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   370.173] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   370.502] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   370.573] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   370.598] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   371.373] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   371.432] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   371.986] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   373.135] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   373.141] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   373.693] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   373.699] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   374.405] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   374.406] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   374.410] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   374.643] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   374.898] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   375.298] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   376.098] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   376.498] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   377.299] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   377.699] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   378.498] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   378.529] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   378.565] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   378.898] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   379.105] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   379.361] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   379.698] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   380.098] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   380.247] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   380.353] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   380.368] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   380.730] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   381.132] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   381.932] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   382.145] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   382.150] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   382.693] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   382.753] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   383.345] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   383.725] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   384.043] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   384.061] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   384.089] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   384.124] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   384.713] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   384.924] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   385.077] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   385.145] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   385.152] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   385.156] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   385.161] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   385.163] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   385.169] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   385.173] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   385.174] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   385.179] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   385.179] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   385.180] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   385.673] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   385.749] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   386.350] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   386.561] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   386.950] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   387.551] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   388.152] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   388.753] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   389.354] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   389.954] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   390.555] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   391.156] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   391.756] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   392.265] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   392.266] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   392.357] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   392.641] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   392.645] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   392.653] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   392.654] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   392.655] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   392.657] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   392.660] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   392.669] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   392.679] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   392.881] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.189] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.192] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.208] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.239] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.262] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.304] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.319] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.346] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.370] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.614] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.788] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.817] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.827] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.828] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.837] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.845] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.848] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.924] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   393.984] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   394.014] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   394.083] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   394.485] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   394.485] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   394.498] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   394.529] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   395.121] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   395.130] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   395.746] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   395.847] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   395.847] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   396.942] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   397.417] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   398.536] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   398.539] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   398.543] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   398.837] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   398.847] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   398.850] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   399.020] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   399.028] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   399.790] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   399.794] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   400.822] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   402.469] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   402.472] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   403.892] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   403.895] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   403.912] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   403.919] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   405.084] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   405.826] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   405.840] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.154] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.156] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.253] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.636] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.636] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.732] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.734] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.761] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.762] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.765] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.769] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.772] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.774] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.779] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   406.782] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   407.365] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   407.965] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   408.521] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   409.088] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   409.142] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   409.696] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   409.711] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.171] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.178] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.180] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.184] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.184] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.185] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.187] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.191] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.191] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.192] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.244] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.277] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.280] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.283] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.
[   410.286] (EE) intel(0): Failed to submit batch buffer, expect rendering corruption or even a frozen display: Invalid argument.

```
i think i am running the latest kernel , i always update the system if the updates are found.

---

### Post by Toz on 2012-02-03
From dmesg:
> [ 12.444143] ACPI Error: Current brightness invalid (20100428/video-544)

> i think i am running the latest kernel , i always update the system if the updates are found.
You're running the latest kernel version for 10.10, but there are newer kernel versions available. Newer kernels support newer devices/functionality. The easiest way to test this is to try a newer ubuntu live cd to see if it works any better.

What directories do you have in this location:
```
ls /sys/devices/platform/
```

Now also boot with the **acpi_backlight=vendor** kernel paramater. Are there any differences:
```
ls /sys/devices/platform/
```

---

### Post by KRISHNASHK on 2012-02-07
[FONT=monospace]ls /sys/devices/platform/[/FONT]


acer-wmi  eisa.0  Fixed MDIO bus.0  i8042  pcspkr  power  serial8250  uevent


[FONT=monospace]no there are no changes. i could not find a new version of ubuntu. I will try to get it as soon as possible. Dont we have any other go?[/FONT]

---

### Post by Toz on 2012-02-07
Newer ubuntu versions can be downloaded here: [http://www.ubuntu.com/download/ubuntu/download]("http://www.ubuntu.com/download/ubuntu/download").

Does xrandr change screen brightness? First get the output name:
```
xrandr -q | grep " connected"
```
...I get:
> LVDS1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
...so my output name is **LVDS1**

Then try changing brightness:
```
xrandr --output LVDS1 --brightness 0.5
```

If it works, you can change it back via:
```
xrandr --output LVDS1 --brightness 1.0
```

---

### Post by KRISHNASHK on 2012-02-08
yeah it worked. I just wanna know was bumblebee necessary for this o will it work with out it.
thanks for the support.

---

### Post by KRISHNASHK on 2012-02-09
i have to change it at every boot up . How can i  make it permanent ?

---

### Post by Toz on 2012-02-09
10.10 uses gdm as the display manager. See here: [http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html") for information on getting xrandr scripts to run during gdm initialization.

---

### Post by KRISHNASHK on 2012-02-09
ok thank you!

---

