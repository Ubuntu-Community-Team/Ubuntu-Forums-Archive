---
title: "Problems getting nouveau working and getting rid of nvidia"
date: 2015-09-20
forum: Hardware
---

### Post by Casey_Herrman on 2015-09-20
This is my first fray into ubuntu and the video is driving my insane. I used to be good at computers at a young age i used to have mess with dos to play games but i have forgot all that so i will need a little help.

So i installed ubuntu 14.04 lts on a computer i got for free, dell xps a2420 w/ 9600m gt, and it worked great at 1920 res, had to load a driver off the internet for wifi but that was all. I pretty much am only going to play games on this thing and medieval total war 2 worked great except in battles because of no 3d support. So i tried the nvidia drivers and they work great in battles but make the computer freeze, grey out, and shows acp pci failed on boot(sorry i cant remember the correct spelling, internet told me to edit the grub with nomodeset to fix with no effect). So i tried to go back to nouveau but not its stuck at 640:480 res and will not change. When it boots i still get the acp pci boot error and when the gui loads i have 3 system errors, far as i can tell there is no xorg config file. So if you guys can help me i would like to:

fix grub and remove changes that i did, nomodeset
purge nvidia and fix xorg file if i need too
reinstall nouveau with 3d mesa

thanks!

---

### Post by Bashing-om on 2015-09-20
Casey_Herrman; Hi ! Welcome to the forum .

Sure ! Let's see what the hardware is that we are dealing with, and then consider what the options are for real.
Post back - Between Code Tags -  the outputs of terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo ubuntu-drivers devices

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

For grub, let's look at what you changed:
```

cat /etc/default/grub
ls -al /etc/grub.d

```

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-09-20
thanks for the reply!

```
04:00.0 VGA compatible controller [0300]: NVIDIA Corporation G96M [GeForce 9600M GT] [10de:0649] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:9013]
```

```
== /sys/devices/pci0000:00/0000:00:01.0/0000:04:00.0 ==
vendor   : NVIDIA Corporation
model    : G96M [GeForce 9600M GT]
modalias : pci:v000010DEd00000649sv00001043sd00009013bc03sc00i00
driver   : nvidia-304 - third-party free
driver   : nvidia-340 - third-party free recommended
driver   : nvidia-340-updates - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-304-updates - distro non-free
driver   : nvidia-173 - distro non-free

== /sys/devices/pci0000:00/0000:00:1c.0/0000:03:00.0 ==
vendor   : Broadcom Corporation
model    : BCM4321 802.11a/b/g/n
modalias : pci:v000014E4d00004328sv00001028sd00000226bc02sc80i00
driver   : bcmwl-kernel-source - distro non-free
```

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`


GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_CMDLINE_LINUX=""

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
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```


```
total 92
drwxr-xr-x   2 root root  4096 Aug  5 00:20 .
drwxr-xr-x 134 root root 12288 Sep 20 15:16 ..
-rwxr-xr-x   1 root root  9424 Jun 26 06:16 00_header
-rwxr-xr-x   1 root root  6058 May 13 09:51 05_debian_theme
-rwxr-xr-x   1 root root 11608 Jun 26 06:16 10_linux
-rwxr-xr-x   1 root root 10412 Jun 26 06:16 20_linux_xen
-rwxr-xr-x   1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x   1 root root 11692 Jun 26 06:16 30_os-prober
-rwxr-xr-x   1 root root  1416 Jun 26 06:16 30_uefi-firmware
-rwxr-xr-x   1 root root   214 Jun 26 06:16 40_custom
-rwxr-xr-x   1 root root   216 Jun 26 06:16 41_custom
-rw-r--r--   1 root root   483 Jun 26 06:16 README



```

---

### Post by Bashing-om on 2015-09-20
Casey_Herrman; Hey hey.

look'n promising.

Confirmed that with that graphic's set the correct driver is the 340 version; Let's see what is installed:
```

dpkg -l | grep -i nvidia
dpkg-query -l nvidia* | grep ii

```
Look'n at purging all, and (re-)installing the 340 version.

As to grub in the /etc/default/grub file, the line:
> 
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

Back up the files - as standard operating procedure - never can tell what might happen, Power outages never happen when expected.
Change it with your favorite text editor to:
```

GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"

```
to change it back to the default value. Remember to SAVE the file once the change is made.
Now one MUST propagate the change to the system:
```

sudo update-grub

```

All else looks to be the default files.

Progress
[INDENT][INDENT][INDENT]one step at a time
[/INDENT][/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-09-20
i tried using the 340 driver from the additional drivers tab and it worked the best but it still hung up, may have been because i tried others first.

```
ii  bbswitch-dkms                                         0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
rc  libcuda1-304                                          304.125-0ubuntu1~xedgers14.04.1                     amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                          340.76-0ubuntu1~xedgers14.04.4                      amd64        NVIDIA CUDA runtime library
ii  libcuda1-340-updates                                  340.76-0ubuntu0.1                                   amd64        NVIDIA CUDA runtime library
ii  nouveau-firmware                                      20091212-0ubuntu1                                   all          Firmware for nVidia graphics cards
rc  nvidia-340-updates                                    340.76-0ubuntu0.1                                   amd64        NVIDIA binary driver - version 340.76
ii  nvidia-opencl-icd-340-updates                         340.76-0ubuntu0.1                                   amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime

```

```
ii  nvidia-opencl-icd-340-updates                         340.76-0ubuntu0.1                                   amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime



```

---

### Post by Bashing-om on 2015-09-20
Casey_Herrman; Well ..

No real fault seen. I do understand that for gaming the proprietary driver gives better performance. You say you want to try the open source driver, and we can. However, ya want to see what results if we purge all and (RE-)install Nvidia driver ?
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get remove --purge nvidia*
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
sudo ubuntu-drivers autoinstall
sudo nvidia-xconfig

```
To purge all the Nvidia stuff and have the system install the Nvidia proprietary driver and a new config file is generated .

If that fails to give satisfaction, then I do recommend to purge Nvidia and install the open source driver .

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-09-20
fixed the grub, back in any res i want to be in, acp error is gone, still have 3 system errors on boot, will try the nvidia driver soon (your last post), thanks

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
GRUB_CMDLINE_LINUX=""

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
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```

---

### Post by Yellow Pasque on 2015-09-20
Make sure the GPU is not overheating..

---

### Post by Casey_Herrman on 2015-09-20
Didnt have a xorg file but the last command made one, rebooted and the acp error during boot came back along with the same 3 system errors that have been always showing up and i check the driver in the additional drivers tab, 340 open source, closed that out to open firefox and then it locked up, could move the mouse buts thats all. I just shut it off i will try again tomorrow night. Thanks for the help.

I thought about it overheating, but when things happen im not doing anything, i havent even pushed the card with a nvidia driver, i did play maybe 30min to a hour with nouveau and it just ran slow during a battle, campaign map ran fine. Thanks

---

### Post by Bashing-om on 2015-09-20
Casey_Herrman; Ooohhww;

Post the errors and we see what we can do.
Take a look at :
```

cat /var/log/Xorg.0.log

``` see what the system reports for any problems.

it is cause -> effect -> 
[INDENT][INDENT][INDENT]resolution
[/INDENT][/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-09-25
well after working 66 hours this week in 5 days i had some time.

the boot screen error is:
0.580310 acpi pcc probe failed

```
[     5.676]     compiled for 4.0.2, module version = 1.0.0
[     5.676]     Module class: X.Org Video Driver
[     5.676] (II) NVIDIA dlloader X Driver  340.76  Thu Jan 22 11:03:05 PST 2015
[     5.676] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     5.676] (++) using VT number 7

[     5.677] (II) Loading sub module "fb"
[     5.677] (II) LoadModule: "fb"
[     5.678] (II) Loading /usr/lib/xorg/modules/libfb.so
[     5.679] (II) Module fb: vendor="X.Org Foundation"
[     5.679]     compiled for 1.17.1, module version = 1.0.0
[     5.679]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.679] (WW) Unresolved symbol: fbGetGCPrivateKey
[     5.679] (II) Loading sub module "wfb"
[     5.679] (II) LoadModule: "wfb"
[     5.679] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     5.679] (II) Module wfb: vendor="X.Org Foundation"
[     5.679]     compiled for 1.17.1, module version = 1.0.0
[     5.679]     ABI class: X.Org ANSI C Emulation, version 0.4
[     5.679] (II) Loading sub module "ramdac"
[     5.679] (II) LoadModule: "ramdac"
[     5.679] (II) Module "ramdac" already built-in
[     5.679] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[     5.679] (==) NVIDIA(0): RGB weight 888
[     5.679] (==) NVIDIA(0): Default visual is TrueColor
[     5.679] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     5.679] (**) NVIDIA(0): Enabling 2D acceleration
[     6.836] (II) NVIDIA(0): Display (Nvidia Default Flat Panel (DFP-0)) does not support
[     6.836] (II) NVIDIA(0):     NVIDIA 3D Vision stereo.
[     6.836] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[     6.837] (II) NVIDIA(0): NVIDIA GPU GeForce 9600M GT (G96) at PCI:4:0:0 (GPU-0)
[     6.837] (--) NVIDIA(0): Memory: 524288 kBytes
[     6.837] (--) NVIDIA(0): VideoBIOS: 62.94.2a.00.10
[     6.837] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     6.839] (--) NVIDIA(0): Valid display device(s) on GeForce 9600M GT at PCI:4:0:0
[     6.839] (--) NVIDIA(0):     CRT-0
[     6.839] (--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0) (boot, connected)
[     6.839] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     6.839] (--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal LVDS
[     6.839] (--) NVIDIA(GPU-0): Nvidia Default Flat Panel (DFP-0): 330.0 MHz maximum pixel clock
[     6.839] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     6.839] (**) NVIDIA(0):     device Nvidia Default Flat Panel (DFP-0) (Using EDID
[     6.839] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[     6.840] (==) NVIDIA(0): 
[     6.840] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     6.840] (==) NVIDIA(0):     will be used as the requested mode.
[     6.840] (==) NVIDIA(0): 
[     6.840] (II) NVIDIA(0): Validated MetaModes:
[     6.840] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[     6.840] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[     8.203] (--) NVIDIA(0): DPI set to (152, 152); computed from "UseEdidDpi" X config
[     8.203] (--) NVIDIA(0):     option
[     8.203] (--) Depth 24 pixmap format is 32 bpp
[     8.203] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[     8.206] (WW) NVIDIA(0): ACPI: AC power state information is not available under
[     8.206] (WW) NVIDIA(0):     /sys/class/power_supply/ , nor under
[     8.206] (WW) NVIDIA(0):     /proc/acpi/ac_adapter/
[     8.208] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[     8.805] (==) NVIDIA(0): Disabling shared memory pixmaps
[     8.805] (==) NVIDIA(0): Backing store enabled
[     8.805] (==) NVIDIA(0): Silken mouse enabled
[     8.805] (**) NVIDIA(0): DPMS enabled
[     8.805] (II) Loading sub module "dri2"
[     8.805] (II) LoadModule: "dri2"
[     8.805] (II) Module "dri2" already built-in
[     8.805] (II) NVIDIA(0): [DRI2] Setup complete
[     8.805] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     8.805] (--) RandR disabled
[     8.811] (II) Initializing extension GLX
[     8.811] (II) Indirect GLX disabled.(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     8.828] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     8.828] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     8.828] (II) LoadModule: "evdev"
[     8.829] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     8.831] (II) Module evdev: vendor="X.Org Foundation"
[     8.831]     compiled for 1.17.1, module version = 2.9.0
[     8.831]     Module class: X.Org XInput Driver
[     8.831]     ABI class: X.Org XInput driver, version 21.0
[     8.831] (II) Using input driver 'evdev' for 'Power Button'
[     8.831] (**) Power Button: always reports core events
[     8.831] (**) evdev: Power Button: Device: "/dev/input/event1"
[     8.831] (--) evdev: Power Button: Vendor 0 Product 0x1
[     8.831] (--) evdev: Power Button: Found keys
[     8.831] (II) evdev: Power Button: Configuring as keyboard
[     8.831] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     8.831] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     8.831] (**) Option "xkb_rules" "evdev"
[     8.831] (**) Option "xkb_model" "pc105"
[     8.831] (**) Option "xkb_layout" "us"
[     8.832] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[     8.832] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     8.832] (II) Using input driver 'evdev' for 'Video Bus'
[     8.832] (**) Video Bus: always reports core events
[     8.832] (**) evdev: Video Bus: Device: "/dev/input/event7"
[     8.832] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     8.832] (--) evdev: Video Bus: Found keys
[     8.832] (II) evdev: Video Bus: Configuring as keyboard
[     8.832] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input10/event7"
[     8.832] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     8.832] (**) Option "xkb_rules" "evdev"
[     8.832] (**) Option "xkb_model" "pc105"
[     8.832] (**) Option "xkb_layout" "us"
[     8.833] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     8.833] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     8.833] (II) Using input driver 'evdev' for 'Power Button'
[     8.833] (**) Power Button: always reports core events
[     8.833] (**) evdev: Power Button: Device: "/dev/input/event0"
[     8.833] (--) evdev: Power Button: Vendor 0 Product 0x1
[     8.833] (--) evdev: Power Button: Found keys
[     8.833] (II) evdev: Power Button: Configuring as keyboard
[     8.833] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     8.833] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     8.833] (**) Option "xkb_rules" "evdev"
[     8.833] (**) Option "xkb_model" "pc105"
[     8.833] (**) Option "xkb_layout" "us"
[     8.833] (II) config/udev: Adding input device Logitech 2.4GHz Cordless Desktop (/dev/input/event2)
[     8.833] (**) Logitech 2.4GHz Cordless Desktop: Applying InputClass "evdev keyboard catchall"
[     8.834] (II) Using input driver 'evdev' for 'Logitech 2.4GHz Cordless Desktop'
[     8.834] (**) Logitech 2.4GHz Cordless Desktop: always reports core events
[     8.834] (**) evdev: Logitech 2.4GHz Cordless Desktop: Device: "/dev/input/event2"
[     8.834] (--) evdev: Logitech 2.4GHz Cordless Desktop: Vendor 0x46d Product 0xc512
[     8.834] (--) evdev: Logitech 2.4GHz Cordless Desktop: Found keys
[     8.834] (II) evdev: Logitech 2.4GHz Cordless Desktop: Configuring as keyboard
[     8.834] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/0003:046D:C512.0001/input/input5/event2"
[     8.834] (II) XINPUT: Adding extended input device "Logitech 2.4GHz Cordless Desktop" (type: KEYBOARD, id 9)
[     8.834] (**) Option "xkb_rules" "evdev"
[     8.834] (**) Option "xkb_model" "pc105"
[     8.834] (**) Option "xkb_layout" "us"
[     8.834] (II) config/udev: Adding input device Logitech 2.4GHz Cordless Desktop (/dev/input/event3)
[     8.834] (**) Logitech 2.4GHz Cordless Desktop: Applying InputClass "evdev pointer catchall"
[     8.834] (**) Logitech 2.4GHz Cordless Desktop: Applying InputClass "evdev keyboard catchall"
[     8.834] (II) Using input driver 'evdev' for 'Logitech 2.4GHz Cordless Desktop'
[     8.834] (**) Logitech 2.4GHz Cordless Desktop: always reports core events
[     8.834] (**) evdev: Logitech 2.4GHz Cordless Desktop: Device: "/dev/input/event3"
[     8.834] (--) evdev: Logitech 2.4GHz Cordless Desktop: Vendor 0x46d Product 0xc512
[     8.834] (--) evdev: Logitech 2.4GHz Cordless Desktop: Found 10 mouse buttons
[     8.834] (--) evdev: Logitech 2.4GHz Cordless Desktop: Found scroll wheel(s)
[     8.834] (--) evdev: Logitech 2.4GHz Cordless Desktop: Found relative axes
[     8.834] (--) evdev: Logitech 2.4GHz Cordless Desktop: Found x and y relative axes
[     8.834] (--) evdev: Logitech 2.4GHz Cordless Desktop: Found absolute axes
[     8.834] (II) evdev: Logitech 2.4GHz Cordless Desktop: Forcing absolute x/y axes to exist.
[     8.834] (--) evdev: Logitech 2.4GHz Cordless Desktop: Found keys
[     8.834] (II) evdev: Logitech 2.4GHz Cordless Desktop: Configuring as mouse
[     8.834] (II) evdev: Logitech 2.4GHz Cordless Desktop: Configuring as keyboard
[     8.834] (II) evdev: Logitech 2.4GHz Cordless Desktop: Adding scrollwheel support
[     8.834] (**) evdev: Logitech 2.4GHz Cordless Desktop: YAxisMapping: buttons 4 and 5
[     8.834] (**) evdev: Logitech 2.4GHz Cordless Desktop: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     8.834] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.1/0003:046D:C512.0002/input/input6/event3"
[     8.834] (II) XINPUT: Adding extended input device "Logitech 2.4GHz Cordless Desktop" (type: KEYBOARD, id 10)
[     8.834] (**) Option "xkb_rules" "evdev"
[     8.835] (**) Option "xkb_model" "pc105"
[     8.835] (**) Option "xkb_layout" "us"
[     8.835] (II) evdev: Logitech 2.4GHz Cordless Desktop: initialized for relative axes.
[     8.835] (WW) evdev: Logitech 2.4GHz Cordless Desktop: ignoring absolute axes.
[     8.835] (**) Logitech 2.4GHz Cordless Desktop: (accel) keeping acceleration scheme 1
[     8.835] (**) Logitech 2.4GHz Cordless Desktop: (accel) acceleration profile 0
[     8.835] (**) Logitech 2.4GHz Cordless Desktop: (accel) acceleration factor: 2.000
[     8.835] (**) Logitech 2.4GHz Cordless Desktop: (accel) acceleration threshold: 4
[     8.835] (II) config/udev: Adding input device Logitech 2.4GHz Cordless Desktop (/dev/input/mouse0)
[     8.835] (II) No input driver specified, ignoring this device.
[     8.835] (II) This device may have been added with another device file.
[     8.836] (II) config/udev: Adding input device Media Center Ed. eHome Infrared Remote Transceiver (1934:0702) (/dev/input/event12)
[     8.836] (**) Media Center Ed. eHome Infrared Remote Transceiver (1934:0702): Applying InputClass "evdev keyboard catchall"
[     8.836] (II) Using input driver 'evdev' for 'Media Center Ed. eHome Infrared Remote Transceiver (1934:0702)'
[     8.836] (**) Media Center Ed. eHome Infrared Remote Transceiver (1934:0702): always reports core events
[     8.836] (**) evdev: Media Center Ed. eHome Infrared Remote Transceiver (1934:0702): Device: "/dev/input/event12"
[     8.836] (--) evdev: Media Center Ed. eHome Infrared Remote Transceiver (1934:0702): Vendor 0x1934 Product 0x702
[     8.836] (--) evdev: Media Center Ed. eHome Infrared Remote Transceiver (1934:0702): Found keys
[     8.836] (II) evdev: Media Center Ed. eHome Infrared Remote Transceiver (1934:0702): Configuring as keyboard
[     8.836] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/rc/rc0/input11/event12"
[     8.836] (II) XINPUT: Adding extended input device "Media Center Ed. eHome Infrared Remote Transceiver (1934:0702)" (type: KEYBOARD, id 11)
[     8.836] (**) Option "xkb_rules" "evdev"
[     8.836] (**) Option "xkb_model" "pc105"
[     8.836] (**) Option "xkb_layout" "us"
[     8.836] (II) config/udev: Adding input device Integrated_Webcam_2M (/dev/input/event8)
[     8.836] (**) Integrated_Webcam_2M: Applying InputClass "evdev keyboard catchall"
[     8.836] (II) Using input driver 'evdev' for 'Integrated_Webcam_2M'
[     8.836] (**) Integrated_Webcam_2M: always reports core events
[     8.836] (**) evdev: Integrated_Webcam_2M: Device: "/dev/input/event8"
[     8.836] (--) evdev: Integrated_Webcam_2M: Vendor 0xc45 Product 0x63e2
[     8.836] (--) evdev: Integrated_Webcam_2M: Found keys
[     8.836] (II) evdev: Integrated_Webcam_2M: Configuring as keyboard
[     8.836] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/input/input12/event8"
[     8.836] (II) XINPUT: Adding extended input device "Integrated_Webcam_2M" (type: KEYBOARD, id 12)
[     8.836] (**) Option "xkb_rules" "evdev"
[     8.836] (**) Option "xkb_model" "pc105"
[     8.836] (**) Option "xkb_layout" "us"
[     8.837] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event9)
[     8.837] (II) No input driver specified, ignoring this device.
[     8.837] (II) This device may have been added with another device file.
[     8.837] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event10)
[     8.837] (II) No input driver specified, ignoring this device.
[     8.837] (II) This device may have been added with another device file.
[     8.837] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event11)
[     8.837] (II) No input driver specified, ignoring this device.
[     8.837] (II) This device may have been added with another device file.
[     8.838] (II) config/udev: Adding input device Logitech K400 (/dev/input/event13)
[     8.838] (**) Logitech K400: Applying InputClass "evdev pointer catchall"
[     8.838] (**) Logitech K400: Applying InputClass "evdev keyboard catchall"
[     8.838] (II) Using input driver 'evdev' for 'Logitech K400'
[     8.838] (**) Logitech K400: always reports core events
[     8.838] (**) evdev: Logitech K400: Device: "/dev/input/event13"
[     8.838] (--) evdev: Logitech K400: Vendor 0x46d Product 0x4024
[     8.838] (--) evdev: Logitech K400: Found 20 mouse buttons
[     8.838] (--) evdev: Logitech K400: Found scroll wheel(s)
[     8.838] (--) evdev: Logitech K400: Found relative axes
[     8.838] (--) evdev: Logitech K400: Found x and y relative axes
[     8.838] (--) evdev: Logitech K400: Found absolute axes
[     8.838] (II) evdev: Logitech K400: Forcing absolute x/y axes to exist.
[     8.838] (--) evdev: Logitech K400: Found keys
[     8.838] (II) evdev: Logitech K400: Configuring as mouse
[     8.838] (II) evdev: Logitech K400: Configuring as keyboard
[     8.838] (II) evdev: Logitech K400: Adding scrollwheel support
[     8.838] (**) evdev: Logitech K400: YAxisMapping: buttons 4 and 5
[     8.838] (**) evdev: Logitech K400: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     8.838] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.2/0003:046D:C52B.0008/0003:046D:4024.0009/input/input16/event13"
[     8.838] (II) XINPUT: Adding extended input device "Logitech K400" (type: KEYBOARD, id 13)
[     8.838] (**) Option "xkb_rules" "evdev"
[     8.838] (**) Option "xkb_model" "pc105"
[     8.838] (**) Option "xkb_layout" "us"
[     8.838] (II) evdev: Logitech K400: initialized for relative axes.
[     8.838] (WW) evdev: Logitech K400: ignoring absolute axes.
[     8.838] (**) Logitech K400: (accel) keeping acceleration scheme 1
[     8.838] (**) Logitech K400: (accel) acceleration profile 0
[     8.838] (**) Logitech K400: (accel) acceleration factor: 2.000
[     8.839] (**) Logitech K400: (accel) acceleration threshold: 4
[     8.839] (II) config/udev: Adding input device Logitech K400 (/dev/input/mouse2)
[     8.839] (II) No input driver specified, ignoring this device.
[     8.839] (II) This device may have been added with another device file.
[     8.839] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event4)
[     8.839] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[     8.839] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[     8.839] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[     8.839] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event4"
[     8.839] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Vendor 0x45e Product 0x745
[     8.839] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[     8.839] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[     8.839] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/0003:045E:0745.0003/input/input7/event4"
[     8.839] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD, id 14)
[     8.839] (**) Option "xkb_rules" "evdev"
[     8.839] (**) Option "xkb_model" "pc105"
[     8.839] (**) Option "xkb_layout" "us"
[     8.840] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event5)
[     8.840] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev pointer catchall"
[     8.840] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[     8.840] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[     8.840] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[     8.840] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event5"
[     8.840] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Vendor 0x45e Product 0x745
[     8.840] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found 9 mouse buttons
[     8.840] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found scroll wheel(s)
[     8.840] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found relative axes
[     8.840] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found x and y relative axes
[     8.840] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found absolute axes
[     8.840] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Forcing absolute x/y axes to exist.
[     8.840] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[     8.840] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as mouse
[     8.840] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[     8.840] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Adding scrollwheel support
[     8.840] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: YAxisMapping: buttons 4 and 5
[     8.840] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     8.840] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/0003:045E:0745.0004/input/input8/event5"
[     8.840] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD, id 15)
[     8.840] (**) Option "xkb_rules" "evdev"
[     8.840] (**) Option "xkb_model" "pc105"
[     8.840] (**) Option "xkb_layout" "us"
[     8.840] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: initialized for relative axes.
[     8.840] (WW) evdev: Microsoft Microsoft® Nano Transceiver v2.0: ignoring absolute axes.
[     8.841] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) keeping acceleration scheme 1
[     8.841] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration profile 0
[     8.841] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration factor: 2.000
[     8.841] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration threshold: 4
[     8.841] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/mouse1)
[     8.841] (II) No input driver specified, ignoring this device.
[     8.841] (II) This device may have been added with another device file.
[     8.841] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/event6)
[     8.841] (**) Microsoft Microsoft® Nano Transceiver v2.0: Applying InputClass "evdev keyboard catchall"
[     8.841] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v2.0'
[     8.841] (**) Microsoft Microsoft® Nano Transceiver v2.0: always reports core events
[     8.841] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Device: "/dev/input/event6"
[     8.841] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Vendor 0x45e Product 0x745
[     8.841] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found 1 mouse buttons
[     8.841] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found scroll wheel(s)
[     8.841] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found relative axes
[     8.841] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found absolute axes
[     8.841] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found absolute multitouch axes
[     8.842] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found x and y absolute axes
[     8.842] (--) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Found keys
[     8.842] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Forcing relative x/y axes to exist.
[     8.842] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as mouse
[     8.842] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Configuring as keyboard
[     8.842] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: Adding scrollwheel support
[     8.842] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: YAxisMapping: buttons 4 and 5
[     8.842] (**) evdev: Microsoft Microsoft® Nano Transceiver v2.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     8.842] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.2/0003:045E:0745.0005/input/input9/event6"
[     8.842] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v2.0" (type: KEYBOARD, id 16)
[     8.842] (**) Option "xkb_rules" "evdev"
[     8.842] (**) Option "xkb_model" "pc105"
[     8.842] (**) Option "xkb_layout" "us"
[     8.842] (II) evdev: Microsoft Microsoft® Nano Transceiver v2.0: initialized for relative axes.
[     8.842] (WW) evdev: Microsoft Microsoft® Nano Transceiver v2.0: ignoring absolute axes.
[     8.842] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) keeping acceleration scheme 1
[     8.842] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration profile 0
[     8.842] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration factor: 2.000
[     8.842] (**) Microsoft Microsoft® Nano Transceiver v2.0: (accel) acceleration threshold: 4
[     8.842] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v2.0 (/dev/input/js0)
[     8.842] (II) No input driver specified, ignoring this device.
[     8.842] (II) This device may have been added with another device file.
[     8.844] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (mceusb) (/dev/input/event14)
[     8.844] (**) MCE IR Keyboard/Mouse (mceusb): Applying InputClass "evdev pointer catchall"
[     8.844] (**) MCE IR Keyboard/Mouse (mceusb): Applying InputClass "evdev keyboard catchall"
[     8.844] (II) Using input driver 'evdev' for 'MCE IR Keyboard/Mouse (mceusb)'
[     8.844] (**) MCE IR Keyboard/Mouse (mceusb): always reports core events
[     8.844] (**) evdev: MCE IR Keyboard/Mouse (mceusb): Device: "/dev/input/event14"
[     8.844] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Vendor 0 Product 0
[     8.844] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found 3 mouse buttons
[     8.844] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found relative axes
[     8.844] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found x and y relative axes
[     8.844] (--) evdev: MCE IR Keyboard/Mouse (mceusb): Found keys
[     8.844] (II) evdev: MCE IR Keyboard/Mouse (mceusb): Configuring as mouse
[     8.844] (II) evdev: MCE IR Keyboard/Mouse (mceusb): Configuring as keyboard
[     8.844] (**) evdev: MCE IR Keyboard/Mouse (mceusb): YAxisMapping: buttons 4 and 5
[     8.844] (**) evdev: MCE IR Keyboard/Mouse (mceusb): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     8.844] (**) Option "config_info" "udev:/sys/devices/virtual/input/input17/event14"
[     8.844] (II) XINPUT: Adding extended input device "MCE IR Keyboard/Mouse (mceusb)" (type: KEYBOARD, id 17)
[     8.844] (**) Option "xkb_rules" "evdev"
[     8.844] (**) Option "xkb_model" "pc105"
[     8.844] (**) Option "xkb_layout" "us"
[     8.845] (II) evdev: MCE IR Keyboard/Mouse (mceusb): initialized for relative axes.
[     8.845] (**) MCE IR Keyboard/Mouse (mceusb): (accel) keeping acceleration scheme 1
[     8.845] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration profile 0
[     8.845] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration factor: 2.000
[     8.845] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration threshold: 4
[     8.845] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (mceusb) (/dev/input/mouse3)
[     8.845] (II) No input driver specified, ignoring this device.
[     8.845] (II) This device may have been added with another device file.
[     9.576] (II) NVIDIA(GPU-0): Display (Nvidia Default Flat Panel (DFP-0)) does not support
[     9.576] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[    10.098] (II) NVIDIA(GPU-0): Display (Nvidia Default Flat Panel (DFP-0)) does not support
[    10.098] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[    10.207] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    10.593] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    10.620] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    10.650] (II) NVIDIA(GPU-0): Display (Nvidia Default Flat Panel (DFP-0)) does not support
[    10.650] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[    10.667] (II) NVIDIA(GPU-0): Display (Nvidia Default Flat Panel (DFP-0)) does not support
[    10.667] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[    11.748] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    25.966] (II) NVIDIA(GPU-0): Display (Nvidia Default Flat Panel (DFP-0)) does not support
[    25.966] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
herrman@bigone:~$ 

```

---

### Post by Bashing-om on 2015-10-01
Casey_Herrman; Well ..

I do not see anything glaring in the xorg file
I am not sure at all .. but after looking up the machines specs I have to question if there is enough ram installed ?
The machine may have as little as 1 Gig of ram to a max of 4.

What to you see for memory management with the game running, and open a new terminal ?
run the terminal command:
```

free -m 

```
Are you running short of memory and really hammering swap ?

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-01
Machene has 4 gigs of ram and i ran gparted mem test prior to installing ubuntu, ill run the command tomorrow,  thanks

---

### Post by Bashing-om on 2015-10-02
Casey_Herrman; Welp;

4 Gigs of ram, memory should not be a problem. Maybe try an older version for the graphic's driver ?

[INDENT][INDENT]just do not know
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-02
I rather try nouveau as i know it works but i need to clear what causing errors

[Img]http://s9.postimg.org/mu72zej33/20150925_194751.jpg [/img]

---

### Post by Bashing-om on 2015-10-02
Casey_Herrman; hey;

Sure, we can remove Nvidia and install the open source driver. But 1st from your last is the reported system problem with Xorg concerning the HardWare Enablement stack.
That is the issue presently at hand, Until Xorg is satisfied, no driver is going to work.

From your 1st post :
> 
purge nvidia and fix xorg file if i need too


I think we are at that point ->
So, let's find the problem:
```

hwe-support-status --verbose
ls -al /usr/bin/hwe-support-status
dpkg -l linux-generic-lts-vivid
dpkg -l libgl1-mesa-glx-lts-vivid
dpkg -l xserver-xorg-lts-vivid
dpkg -l linux-image-generic-lts-vivid

```
Post those results, and we see where we go from there.
Once Xorg is functional; Then we purge Nvidia and install nouveau .

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2015-10-02
Hey, Bashing.

Not settling in for another one of your 'marathons', are you? :lol: Man alive, you and the Hardware Enablement Stack seem to have an unholy attraction to one another.....

I seem to recall another individual kept you at it for nearly 18 pages..!


Mike. ;)

---

### Post by Bashing-om on 2015-10-02
@ Mike_Walsh ;; Wheeall, ole buddy

Like unto this, get to the root of the problem, finger out what it takes to fix that, and all else will then fall into place.

Now that said, How long does it take for the 'root' to penetrate through the denseness of my ignorance.
Anything worth doing is worth doing to the best of my ability and even after all these years .................
[INDENT][INDENT]I have done so much
[INDENT][INDENT][INDENT]with so little
[INDENT][INDENT][INDENT][INDENT]for so long
I am qualified to the anything with nothing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

:)

---

### Post by Mike_Walsh on 2015-10-02
Hah! Methinks you're too modest, old son. From recollection, if anybody can sort these pesky Xorg.files out, you's the man! Go for it; and pray ignore my untimely interruptions... :D


Mike. ;)

Hey; everybody alive on this dirt ball is good at something.....you know that as well as I do. "If you've got it..." I'm jealous; I got a loooong way to go yet..!

I have nothing but admiration. Besides, you must be aware of the old saying; "The mark of the true craftsman is to make the truly difficult look easy". Add a generous helping of modesty, seasoned with a dash of self-deprecation.....it's a winning combination.

---

### Post by Bashing-om on 2015-10-02
@ Mike ..

Even with all the quips I do ... I can not top that .

Hummm ..
[INDENT][INDENT][INDENT]less said the better
[/INDENT][/INDENT][/INDENT]

Meanwhile, back at the ranch
[INDENT][INDENT][INDENT]back on topic
[/INDENT][/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-03
tried the first two......

```

herrman@bigone:~$ hwe-support-status --verbose
hwe-support-status: command not found
herrman@bigone:~$ ls -al /usr/bin/hwe-support-status
ls: cannot access /usr/bin/hwe-support-status: No such file or directory
herrman@bigone:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3887       1396       2490         12         55        613
-/+ buffers/cache:        726       3160
Swap:         4028          0       4028
herrman@bigone:~$ 


```

id like to change it to nouveau for the time being for reliability until we figure out the problem, hate having to restart the machene to do something. thanks

---

### Post by Bashing-om on 2015-10-03
Casey_Herrman; K;

Won't hurt a thing :
> 
id like to change it to nouveau for the time being for reliability 

to do so: ....BUT there is for sure a problem with HWE. The system is screaming and hollering, but the package manager says it is not installed.
To install nouveau:
```

sudo apt update
sudo apt upgrade
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get purge nvidia*
sudo apt-get install linux-headers-generic
sudo apt-get install xserver-xorg-video-nouveau

```
Reboot to see the effect. Mind you I will not be surprised if Xorg has it's problems due to HWE . 
IF in that event, we go back and re-focus our attention on that prerequisite .

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by mc4man on 2015-10-03
After returning to nouveau by purging nvidia clean your crash folder & reboot. See if any xorg crashes reappear
```
sudo rm /var/crash/*.*
```

(- there is no command in any current Ubuntu package of hwe-support-status, where did that come from??

---

### Post by Bashing-om on 2015-10-03
mc4man; 

IRT: hwe-support-status,
Could be that it no longer applies; But I will be surprised .
My reference:
[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

I will be pleased to have my think'n corrected.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by mc4man on 2015-10-03
> **Bashing-om said:**
> mc4man; 

IRT: hwe-support-status,
Could be that it no longer applies; But I will be surprised .
My reference:
[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

I will be pleased to have my think'n corrected.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]
Don't see it anywhere, examples - 
[http://packages.ubuntu.com/search?searchon=contents&keywords=hwe-support-status&mode=exactfilename&suite=trusty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=hwe-support-status&mode=exactfilename&suite=trusty&arch=any)
[http://packages.ubuntu.com/trusty/update-manager/filelist](http://packages.ubuntu.com/trusty/update-manager/filelist)
[http://packages.ubuntu.com/trusty/admin/update-manager-core/filelist](http://packages.ubuntu.com/trusty/admin/update-manager-core/filelist)

There is also no changelog entry for update-manager source that shows this tool (command) ever actually being added to update-manager package(s), that's going back to 12.04

---

### Post by Bashing-om on 2015-10-03
> **mc4man said:**
> Don't see it anywhere, examples - 
[http://packages.ubuntu.com/search?searchon=contents&keywords=hwe-support-status&mode=exactfilename&suite=trusty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=hwe-support-status&mode=exactfilename&suite=trusty&arch=any)
[http://packages.ubuntu.com/trusty/update-manager/filelist](http://packages.ubuntu.com/trusty/update-manager/filelist)
[http://packages.ubuntu.com/trusty/admin/update-manager-core/filelist](http://packages.ubuntu.com/trusty/admin/update-manager-core/filelist)

There is also no changelog entry for update-manager source that shows this tool (command) ever actually being added to update-manager package(s), that's going back to 12.04

Yepper, No longer applies .. My think'n is re-directed.. A huge thank you.

Ouch, it hurts when I am in error, but
[INDENT][INDENT]only makes me stronger
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-04
did the purge, got this, gonna reboot after

```

herrman@bigone:~$ sudo apt-get install xserver-xorg-video-nouveau
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg-video-nouveau : Depends: xorg-video-abi-15
                              Depends: xserver-xorg-core (>= 2:1.14.99.902)
                              Recommends: libgl1-mesa-dri (>= 9.0)
E: Unable to correct problems, you have held broken packages.


```

it crashed berfore i could reboot, most crashes i can move the most but cant do anything, did a hard reset and the 3 errors were gone and nouveu was listed as the driver, ran the crash log command and got nothing, seems to run fine. Think it would be okay to load a 3d for noeveau now? thanks

```
herrman@bigone:~$ sudo rm /var/crash/*.*
[sudo] password for herrman: 
rm: cannot remove ‘/var/crash/*.*’: No such file or directory
herrman@bigone:~$ 
```

---

### Post by Bashing-om on 2015-10-05
Casey_Herrman; OK;

Running fine is what we want. But, let's verify that the package manager is happy and in a consistent state:
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade
sudo apt-get -f install
sudo dpkg -C

```

Then if there are no errors .. then yeah .. stress test and put the system under full load. Let's see how it performs with the nouveau driver.

[INDENT][INDENT]a solid stable system
[INDENT][INDENT][INDENT][INDENT]feels good all over
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-07
left the machene on acidently for 3 days and no crash, ran the codes, ill push it later and let you know, thanks

```


Unpacking libxatracker2-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) over (10.5.2-0ubuntu1~trusty1) ...
Selecting previously unselected package linux-image-3.19.0-30-generic.
Preparing to unpack .../linux-image-3.19.0-30-generic_3.19.0-30.34~14.04.1_amd64.deb ...
Done.
Unpacking linux-image-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...
Preparing to unpack .../libsystemd-journal0_204-5ubuntu20.14_amd64.deb ...
Unpacking libsystemd-journal0:amd64 (204-5ubuntu20.14) over (204-5ubuntu20.13) ...
Preparing to unpack .../sudo_1.8.9p5-1ubuntu1.2_amd64.deb ...
Unpacking sudo (1.8.9p5-1ubuntu1.2) over (1.8.9p5-1ubuntu1.1) ...
Preparing to unpack .../libapparmor1_2.8.95~2430-0ubuntu5.3_amd64.deb ...
Unpacking libapparmor1:amd64 (2.8.95~2430-0ubuntu5.3) over (2.8.95~2430-0ubuntu5.2) ...
Preparing to unpack .../libapparmor-perl_2.8.95~2430-0ubuntu5.3_amd64.deb ...
Unpacking libapparmor-perl (2.8.95~2430-0ubuntu5.3) over (2.8.95~2430-0ubuntu5.2) ...
Preparing to unpack .../apparmor_2.8.95~2430-0ubuntu5.3_amd64.deb ...
Unpacking apparmor (2.8.95~2430-0ubuntu5.3) over (2.8.95~2430-0ubuntu5.2) ...
Preparing to unpack .../bind9-host_1%3a9.9.5.dfsg-3ubuntu0.5_amd64.deb ...
Unpacking bind9-host (1:9.9.5.dfsg-3ubuntu0.5) over (1:9.9.5.dfsg-3ubuntu0.4) ...
Preparing to unpack .../dnsutils_1%3a9.9.5.dfsg-3ubuntu0.5_amd64.deb ...
Unpacking dnsutils (1:9.9.5.dfsg-3ubuntu0.5) over (1:9.9.5.dfsg-3ubuntu0.4) ...
Preparing to unpack .../libisc95_1%3a9.9.5.dfsg-3ubuntu0.5_amd64.deb ...
Unpacking libisc95 (1:9.9.5.dfsg-3ubuntu0.5) over (1:9.9.5.dfsg-3ubuntu0.4) ...
Preparing to unpack .../libdns100_1%3a9.9.5.dfsg-3ubuntu0.5_amd64.deb ...
Unpacking libdns100 (1:9.9.5.dfsg-3ubuntu0.5) over (1:9.9.5.dfsg-3ubuntu0.4) ...
Preparing to unpack .../libisccc90_1%3a9.9.5.dfsg-3ubuntu0.5_amd64.deb ...
Unpacking libisccc90 (1:9.9.5.dfsg-3ubuntu0.5) over (1:9.9.5.dfsg-3ubuntu0.4) ...
Preparing to unpack .../libisccfg90_1%3a9.9.5.dfsg-3ubuntu0.5_amd64.deb ...
Unpacking libisccfg90 (1:9.9.5.dfsg-3ubuntu0.5) over (1:9.9.5.dfsg-3ubuntu0.4) ...
Preparing to unpack .../liblwres90_1%3a9.9.5.dfsg-3ubuntu0.5_amd64.deb ...
Unpacking liblwres90 (1:9.9.5.dfsg-3ubuntu0.5) over (1:9.9.5.dfsg-3ubuntu0.4) ...
Preparing to unpack .../libbind9-90_1%3a9.9.5.dfsg-3ubuntu0.5_amd64.deb ...
Unpacking libbind9-90 (1:9.9.5.dfsg-3ubuntu0.5) over (1:9.9.5.dfsg-3ubuntu0.4) ...
Preparing to unpack .../irqbalance_1.0.6-2ubuntu0.14.04.4_amd64.deb ...
irqbalance stop/waiting
Unpacking irqbalance (1.0.6-2ubuntu0.14.04.4) over (1.0.6-2ubuntu0.14.04.2) ...
Preparing to unpack .../lshw_02.16-2ubuntu1.3_amd64.deb ...
Unpacking lshw (02.16-2ubuntu1.3) over (02.16-2ubuntu1.2) ...
Preparing to unpack .../openssh-client_1%3a6.6p1-2ubuntu2.3_amd64.deb ...
Unpacking openssh-client (1:6.6p1-2ubuntu2.3) over (1:6.6p1-2ubuntu2) ...
Preparing to unpack .../python3-gdbm_3.4.3-1~14.04.2_amd64.deb ...
Unpacking python3-gdbm:amd64 (3.4.3-1~14.04.2) over (3.4.0-0ubuntu1) ...
Preparing to unpack .../python3-update-manager_1%3a0.196.14_all.deb ...
Unpacking python3-update-manager (1:0.196.14) over (1:0.196.13) ...
Preparing to unpack .../update-manager-core_1%3a0.196.14_all.deb ...
Unpacking update-manager-core (1:0.196.14) over (1:0.196.13) ...
Preparing to unpack .../update-manager_1%3a0.196.14_all.deb ...
Unpacking update-manager (1:0.196.14) over (1:0.196.13) ...
Preparing to unpack .../uuid-runtime_2.20.1-5.1ubuntu20.7_amd64.deb ...
Unpacking uuid-runtime (2.20.1-5.1ubuntu20.7) over (2.20.1-5.1ubuntu20.6) ...
Preparing to unpack .../python3-problem-report_2.14.1-0ubuntu3.15_all.deb ...
Unpacking python3-problem-report (2.14.1-0ubuntu3.15) over (2.14.1-0ubuntu3.11) ...
Preparing to unpack .../python3-apport_2.14.1-0ubuntu3.15_all.deb ...
Unpacking python3-apport (2.14.1-0ubuntu3.15) over (2.14.1-0ubuntu3.11) ...
Preparing to unpack .../apport_2.14.1-0ubuntu3.15_all.deb ...
apport stop/waiting
Unpacking apport (2.14.1-0ubuntu3.15) over (2.14.1-0ubuntu3.11) ...
Preparing to unpack .../apport-gtk_2.14.1-0ubuntu3.15_all.deb ...
Unpacking apport-gtk (2.14.1-0ubuntu3.15) over (2.14.1-0ubuntu3.11) ...
Preparing to unpack .../binutils_2.24-5ubuntu14_amd64.deb ...
Unpacking binutils (2.24-5ubuntu14) over (2.24-5ubuntu13) ...
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5.14.04.5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04.5) over (2.2.0.3-1.1ubuntu5.14.04.2) ...
Preparing to unpack .../xul-ext-webaccounts_0.5-0ubuntu2.14.04.1_amd64.deb ...
Unpacking xul-ext-webaccounts (0.5-0ubuntu2.14.04.1) over (0.5-0ubuntu2) ...
Preparing to unpack .../webaccounts-extension-common_0.5-0ubuntu2.14.04.1_amd64.deb ...
Unpacking webaccounts-extension-common (0.5-0ubuntu2.14.04.1) over (0.5-0ubuntu2) ...
Preparing to unpack .../libufe-xidgetter0_3.0.0+14.04.20140416-0ubuntu1.14.04.1_amd64.deb ...
Unpacking libufe-xidgetter0 (3.0.0+14.04.20140416-0ubuntu1.14.04.1) over (3.0.0+14.04.20140416-0ubuntu1) ...
Preparing to unpack .../xul-ext-websites-integration_2.3.6+13.10.20130920.1-0ubuntu1.2_all.deb ...
Unpacking xul-ext-websites-integration (2.3.6+13.10.20130920.1-0ubuntu1.2) over (2.3.6+13.10.20130920.1-0ubuntu1.1) ...
Preparing to unpack .../xul-ext-unity_3.0.0+14.04.20140416-0ubuntu1.14.04.1_all.deb ...
Unpacking xul-ext-unity (3.0.0+14.04.20140416-0ubuntu1.14.04.1) over (3.0.0+14.04.20140416-0ubuntu1) ...
Preparing to unpack .../firefox_41.0.1+build2-0ubuntu0.14.04.1_amd64.deb ...
Unpacking firefox (41.0.1+build2-0ubuntu0.14.04.1) over (39.0+build5-0ubuntu0.14.04.1) ...
Preparing to unpack .../firefox-locale-en_41.0.1+build2-0ubuntu0.14.04.1_amd64.deb ...
Unpacking firefox-locale-en (41.0.1+build2-0ubuntu0.14.04.1) over (39.0+build5-0ubuntu0.14.04.1) ...
Preparing to unpack .../flashplugin-installer_11.2.202.521ubuntu0.14.04.1_amd64.deb ...
Unpacking flashplugin-installer (11.2.202.521ubuntu0.14.04.1) over (11.2.202.508ubuntu0.14.04.1) ...
Preparing to unpack .../gir1.2-gdkpixbuf-2.0_2.30.7-0ubuntu1.1_amd64.deb ...
Unpacking gir1.2-gdkpixbuf-2.0 (2.30.7-0ubuntu1.1) over (2.30.7-0ubuntu1) ...
Preparing to unpack .../gir1.2-gudev-1.0_1%3a204-5ubuntu20.14_amd64.deb ...
Unpacking gir1.2-gudev-1.0 (1:204-5ubuntu20.14) over (1:204-5ubuntu20.13) ...
Preparing to unpack .../gvfs-fuse_1.20.3-0ubuntu1.2_amd64.deb ...
Unpacking gvfs-fuse (1.20.3-0ubuntu1.2) over (1.20.3-0ubuntu1.1) ...
Preparing to unpack .../gvfs-bin_1.20.3-0ubuntu1.2_amd64.deb ...
Unpacking gvfs-bin (1.20.3-0ubuntu1.2) over (1.20.3-0ubuntu1.1) ...
Preparing to unpack .../gvfs-backends_1.20.3-0ubuntu1.2_amd64.deb ...
Unpacking gvfs-backends (1.20.3-0ubuntu1.2) over (1.20.3-0ubuntu1.1) ...
Preparing to unpack .../gvfs-libs_1.20.3-0ubuntu1.2_amd64.deb ...
Unpacking gvfs-libs:amd64 (1.20.3-0ubuntu1.2) over (1.20.3-0ubuntu1.1) ...
Preparing to unpack .../gvfs_1.20.3-0ubuntu1.2_amd64.deb ...
Unpacking gvfs:amd64 (1.20.3-0ubuntu1.2) over (1.20.3-0ubuntu1.1) ...
Preparing to unpack .../gvfs-daemons_1.20.3-0ubuntu1.2_amd64.deb ...
Unpacking gvfs-daemons (1.20.3-0ubuntu1.2) over (1.20.3-0ubuntu1.1) ...
Preparing to unpack .../gvfs-common_1.20.3-0ubuntu1.2_all.deb ...
Unpacking gvfs-common (1.20.3-0ubuntu1.2) over (1.20.3-0ubuntu1.1) ...
Preparing to unpack .../intel-gpu-tools_1.8-1~xedgers~trusty_amd64.deb ...
Unpacking intel-gpu-tools (1.8-1~xedgers~trusty) over (1.3-0ubuntu2.1) ...
Preparing to unpack .../libcuda1-340_340.93-0ubuntu0.0.1_amd64.deb ...
Unpacking libcuda1-340 (340.93-0ubuntu0.0.1) over (340.76-0ubuntu1~xedgers14.04.4) ...
Preparing to unpack .../linux-firmware_1.127.15_all.deb ...
Unpacking linux-firmware (1.127.15) over (1.127.14) ...
Selecting previously unselected package linux-image-extra-3.19.0-30-generic.
Preparing to unpack .../linux-image-extra-3.19.0-30-generic_3.19.0-30.34~14.04.1_amd64.deb ...
Unpacking linux-image-extra-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...
Preparing to unpack .../linux-generic-lts-vivid_3.19.0.30.17_amd64.deb ...
Unpacking linux-generic-lts-vivid (3.19.0.30.17) over (3.19.0.28.15) ...
Preparing to unpack .../linux-image-generic-lts-vivid_3.19.0.30.17_amd64.deb ...
Unpacking linux-image-generic-lts-vivid (3.19.0.30.17) over (3.19.0.28.15) ...
Selecting previously unselected package linux-headers-3.19.0-30.
Preparing to unpack .../linux-headers-3.19.0-30_3.19.0-30.34~14.04.1_all.deb ...
Unpacking linux-headers-3.19.0-30 (3.19.0-30.34~14.04.1) ...
Selecting previously unselected package linux-headers-3.19.0-30-generic.
Preparing to unpack .../linux-headers-3.19.0-30-generic_3.19.0-30.34~14.04.1_amd64.deb ...
Unpacking linux-headers-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...
Preparing to unpack .../linux-headers-generic-lts-vivid_3.19.0.30.17_amd64.deb ...
Unpacking linux-headers-generic-lts-vivid (3.19.0.30.17) over (3.19.0.28.15) ...
Preparing to unpack .../linux-headers-3.13.0-65_3.13.0-65.106_all.deb ...
Unpacking linux-headers-3.13.0-65 (3.13.0-65.106) over (3.13.0-65.105) ...
Preparing to unpack .../linux-headers-3.13.0-65-generic_3.13.0-65.106_amd64.deb ...
Unpacking linux-headers-3.13.0-65-generic (3.13.0-65.106) over (3.13.0-65.105) ...
Preparing to unpack .../linux-libc-dev_3.13.0-65.106_amd64.deb ...
Unpacking linux-libc-dev:amd64 (3.13.0-65.106) over (3.13.0-61.100) ...
Preparing to unpack .../onboard_1.0.1-0ubuntu1_amd64.deb ...
Unpacking onboard (1.0.1-0ubuntu1) over (1.0.0-0ubuntu4) ...

(gtk-update-icon-cache-3.0:16756):  GdkPixbuf-WARNING **: Cannot open pixbuf loader module file  '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such  file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.

(gtk-update-icon-cache-3.0:16757):  GdkPixbuf-WARNING **: Cannot open pixbuf loader module file  '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such  file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.

(gtk-update-icon-cache-3.0:16758):  GdkPixbuf-WARNING **: Cannot open pixbuf loader module file  '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such  file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
Preparing to unpack .../onboard-data_1.0.1-0ubuntu1_all.deb ...
Unpacking onboard-data (1.0.1-0ubuntu1) over (1.0.0-0ubuntu4) ...
Preparing to unpack .../software-properties-common_0.92.37.5_all.deb ...
Unpacking software-properties-common (0.92.37.5) over (0.92.37.3) ...
Preparing to unpack .../software-properties-gtk_0.92.37.5_all.deb ...
Unpacking software-properties-gtk (0.92.37.5) over (0.92.37.3) ...
Preparing to unpack .../python3-software-properties_0.92.37.5_all.deb ...
Unpacking python3-software-properties (0.92.37.5) over (0.92.37.3) ...
Preparing to unpack .../ssh-askpass-gnome_1%3a6.6p1-2ubuntu2.3_amd64.deb ...
Unpacking ssh-askpass-gnome (1:6.6p1-2ubuntu2.3) over (1:6.6p1-2ubuntu2) ...
Preparing to unpack .../thermald_1.4.3-5~14.04.1_amd64.deb ...
thermald stop/waiting
Unpacking thermald (1.4.3-5~14.04.1) over (1.4.3-3~14.04.1) ...
Preparing to unpack .../thunderbird_1%3a38.3.0+build1-0ubuntu0.14.04.1_amd64.deb ...
Unpacking thunderbird (1:38.3.0+build1-0ubuntu0.14.04.1) over (1:31.8.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird-gnome-support_1%3a38.3.0+build1-0ubuntu0.14.04.1_amd64.deb ...
Unpacking thunderbird-gnome-support (1:38.3.0+build1-0ubuntu0.14.04.1) over (1:31.8.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../unity-settings-daemon_14.04.0+14.04.20150825-0ubuntu2_amd64.deb ...
Unpacking unity-settings-daemon (14.04.0+14.04.20150825-0ubuntu2) over (14.04.0+14.04.20140606-0ubuntu3) ...
Preparing to unpack .../xul-ext-ubufox_3.2-0ubuntu0.14.04.1_all.deb ...
Moving obsolete conffile /etc/xul-ext/ubufox.js out of the way...
Unpacking xul-ext-ubufox (3.2-0ubuntu0.14.04.1) over (3.0-0ubuntu0.14.04.1) ...
dpkg: warning: unable to delete old directory '/etc/xul-ext': Directory not empty
Preparing to unpack .../liboxideqt-qmlplugin_1.9.5-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqt-qmlplugin:amd64 (1.9.5-0ubuntu0.14.04.1) over (1.8.4-0ubuntu0.14.04.2) ...
Preparing to unpack .../liboxideqtquick0_1.9.5-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqtquick0:amd64 (1.9.5-0ubuntu0.14.04.1) over (1.8.4-0ubuntu0.14.04.2) ...
Preparing to unpack .../liboxideqtcore0_1.9.5-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqtcore0:amd64 (1.9.5-0ubuntu0.14.04.1) over (1.8.4-0ubuntu0.14.04.2) ...
Preparing to unpack .../oxideqt-codecs_1.9.5-0ubuntu0.14.04.1_amd64.deb ...
Unpacking oxideqt-codecs:amd64 (1.9.5-0ubuntu0.14.04.1) over (1.8.4-0ubuntu0.14.04.2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.40.2-0ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...

(gtk-update-icon-cache-3.0:18122):  GdkPixbuf-WARNING **: Cannot open pixbuf loader module file  '/usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': No such  file or directory

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/x86_64-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for update-notifier-common (0.154.1ubuntu1) ...
flashplugin-installer:  downloading  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20150921.1.orig.tar.gz
Installing from local file /tmp/tmp8N4EXl.gz
Flash Plugin installed.
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/andale32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arial32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/arialb32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/comic32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/courie32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/georgi32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/impact32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/times32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/trebuc32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/verdan32.exe
ttf-mscorefonts-installer: downloading http://downloads.sourceforge.net/corefonts/webdin32.exe
user did not accept the  license
The fonts are NOT installed.
Please run 'dpkg-reconfigure ttf-mscorefonts-installer' to perform the installation again
Setting up libcgmanager0:i386 (0.24-0ubuntu7.5) ...
Setting up libcgmanager0:amd64 (0.24-0ubuntu7.5) ...
Setting up libudev1:amd64 (204-5ubuntu20.14) ...
Setting up libudev1:i386 (204-5ubuntu20.14) ...
Setting up udev (204-5ubuntu20.14) ...
udev stop/waiting
udev start/running, process 18214
Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up bash-completion (1:2.1-4ubuntu0.1) ...
Setting up libldap-2.4-2:amd64 (2.4.31-1+nmu2ubuntu8.2) ...
Setting up libldap-2.4-2:i386 (2.4.31-1+nmu2ubuntu8.2) ...
Setting up libsystemd-daemon0:amd64 (204-5ubuntu20.14) ...
Setting up systemd-services (204-5ubuntu20.14) ...
Setting up libpam-systemd:amd64 (204-5ubuntu20.14) ...
systemd-logind start/running, process 18837
Setting up libsystemd-login0:amd64 (204-5ubuntu20.14) ...
Setting up libfreetype6:i386 (2.5.2-1ubuntu2.5) ...
Setting up libfreetype6:amd64 (2.5.2-1ubuntu2.5) ...
Setting up libgdk-pixbuf2.0-common (2.30.7-0ubuntu1.1) ...
Setting up libgdk-pixbuf2.0-0:amd64 (2.30.7-0ubuntu1.1) ...
Setting up libgtk2.0-common (2.24.23-0ubuntu1.3) ...
Setting up libgtk2.0-0:amd64 (2.24.23-0ubuntu1.3) ...
Setting up libgtk2.0-bin (2.24.23-0ubuntu1.3) ...
Setting up libgail18:amd64 (2.24.23-0ubuntu1.3) ...
Setting up libgail-common:amd64 (2.24.23-0ubuntu1.3) ...
Setting up google-chrome-stable (45.0.2454.101-1) ...
Setting up libdrm2:i386 (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Setting up libdrm2:amd64 (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Setting up libdrm-intel1:amd64 (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Setting up libdrm-intel1:i386 (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Setting up libdrm-nouveau2:amd64 (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Setting up libdrm-nouveau2:i386 (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Setting up libdrm-radeon1:amd64 (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Setting up libdrm-radeon1:i386 (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Setting up libwayland-client0:amd64 (1.7.0-0ubuntu1~trusty1) ...
Setting up libwayland-server0:amd64 (1.7.0-0ubuntu1~trusty1) ...
Setting up libgl1-mesa-dri-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Installing new version of config file /etc/drirc ...
Setting up libgl1-mesa-dri-lts-vivid:i386 (10.5.9-2ubuntu1~trusty2) ...
Setting up libgbm1-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Setting up libegl1-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Setting up libwayland-egl1-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Setting up libglapi-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Setting up libglapi-mesa-lts-vivid:i386 (10.5.9-2ubuntu1~trusty2) ...
Setting up libgles1-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Setting up libgles2-mesa-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Setting up libgl1-mesa-glx-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Setting up libgl1-mesa-glx-lts-vivid:i386 (10.5.9-2ubuntu1~trusty2) ...
Setting up xserver-xorg-core-lts-vivid (2:1.17.1-0ubuntu3.1~trusty1) ...
Setting up libgudev-1.0-0:amd64 (1:204-5ubuntu20.14) ...
Setting up libicu52:amd64 (52.1-3ubuntu0.4) ...
Setting up libsnmp-base (5.7.2~dfsg-8.1ubuntu3.1) ...
Setting up libsnmp30:amd64 (5.7.2~dfsg-8.1ubuntu3.1) ...
Setting up libwayland-cursor0:amd64 (1.7.0-0ubuntu1~trusty1) ...
Setting up libxatracker2-lts-vivid:amd64 (10.5.9-2ubuntu1~trusty2) ...
Setting up linux-image-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up libsystemd-journal0:amd64 (204-5ubuntu20.14) ...
Setting up sudo (1.8.9p5-1ubuntu1.2) ...
Setting up libapparmor1:amd64 (2.8.95~2430-0ubuntu5.3) ...
Setting up libapparmor-perl (2.8.95~2430-0ubuntu5.3) ...
Setting up apparmor (2.8.95~2430-0ubuntu5.3) ...
 *  Starting AppArmor  profiles                                                   Skipping  profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
 *  Reloading AppArmor  profiles                                                  Skipping  profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
                                                                         [ OK ]
Setting up libisc95 (1:9.9.5.dfsg-3ubuntu0.5) ...
Setting up libdns100 (1:9.9.5.dfsg-3ubuntu0.5) ...
Setting up libisccc90 (1:9.9.5.dfsg-3ubuntu0.5) ...
Setting up libisccfg90 (1:9.9.5.dfsg-3ubuntu0.5) ...
Setting up libbind9-90 (1:9.9.5.dfsg-3ubuntu0.5) ...
Setting up liblwres90 (1:9.9.5.dfsg-3ubuntu0.5) ...
Setting up bind9-host (1:9.9.5.dfsg-3ubuntu0.5) ...
Setting up dnsutils (1:9.9.5.dfsg-3ubuntu0.5) ...
Setting up irqbalance (1.0.6-2ubuntu0.14.04.4) ...
irqbalance start/running, process 28134
Setting up lshw (02.16-2ubuntu1.3) ...
Setting up openssh-client (1:6.6p1-2ubuntu2.3) ...
Setting up python3-gdbm:amd64 (3.4.3-1~14.04.2) ...
Setting up python3-update-manager (1:0.196.14) ...
Setting up update-manager-core (1:0.196.14) ...
Setting up update-manager (1:0.196.14) ...
Setting up uuid-runtime (2.20.1-5.1ubuntu20.7) ...
Setting up python3-problem-report (2.14.1-0ubuntu3.15) ...
Setting up python3-apport (2.14.1-0ubuntu3.15) ...
Setting up apport (2.14.1-0ubuntu3.15) ...
apport start/running
Setting up apport-gtk (2.14.1-0ubuntu3.15) ...
Setting up binutils (2.24-5ubuntu14) ...
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04.5) ...
Setting up webaccounts-extension-common (0.5-0ubuntu2.14.04.1) ...
Setting up xul-ext-webaccounts (0.5-0ubuntu2.14.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up libufe-xidgetter0 (3.0.0+14.04.20140416-0ubuntu1.14.04.1) ...
Setting up xul-ext-websites-integration (2.3.6+13.10.20130920.1-0ubuntu1.2) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up xul-ext-unity (3.0.0+14.04.20140416-0ubuntu1.14.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox (41.0.1+build2-0ubuntu0.14.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/firefox ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-locale-en (41.0.1+build2-0ubuntu0.14.04.1) ...
Setting up flashplugin-installer (11.2.202.521ubuntu0.14.04.1) ...
Setting up gir1.2-gdkpixbuf-2.0 (2.30.7-0ubuntu1.1) ...
Setting up gir1.2-gudev-1.0 (1:204-5ubuntu20.14) ...
Setting up gvfs-common (1.20.3-0ubuntu1.2) ...
Setting up gvfs-libs:amd64 (1.20.3-0ubuntu1.2) ...
Setting up gvfs-daemons (1.20.3-0ubuntu1.2) ...
Setting up gvfs:amd64 (1.20.3-0ubuntu1.2) ...
Setting up gvfs-fuse (1.20.3-0ubuntu1.2) ...
Setting up gvfs-bin (1.20.3-0ubuntu1.2) ...
Setting up gvfs-backends (1.20.3-0ubuntu1.2) ...
Setting up intel-gpu-tools (1.8-1~xedgers~trusty) ...
Setting up libcuda1-340 (340.93-0ubuntu0.0.1) ...
Setting up linux-firmware (1.127.15) ...
Setting up linux-image-extra-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic-lts-vivid (3.19.0.30.17) ...
Setting up linux-headers-3.19.0-30 (3.19.0-30.34~14.04.1) ...
Setting up linux-headers-3.19.0-30-generic (3.19.0-30.34~14.04.1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.19.0-30-generic /boot/vmlinuz-3.19.0-30-generic
Setting up linux-headers-generic-lts-vivid (3.19.0.30.17) ...
Setting up linux-generic-lts-vivid (3.19.0.30.17) ...
Setting up linux-headers-3.13.0-65 (3.13.0-65.106) ...
Setting up linux-headers-3.13.0-65-generic (3.13.0-65.106) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
Setting up linux-libc-dev:amd64 (3.13.0-65.106) ...
Setting up onboard (1.0.1-0ubuntu1) ...
Setting up onboard-data (1.0.1-0ubuntu1) ...
Setting up python3-software-properties (0.92.37.5) ...
Setting up software-properties-common (0.92.37.5) ...
Setting up software-properties-gtk (0.92.37.5) ...
Setting up ssh-askpass-gnome (1:6.6p1-2ubuntu2.3) ...
Setting up thermald (1.4.3-5~14.04.1) ...
thermald start/running, process 4249
Setting up thunderbird (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/thunderbird ...
Setting up thunderbird-gnome-support (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Setting up unity-settings-daemon (14.04.0+14.04.20150825-0ubuntu2) ...
Setting up xul-ext-ubufox (3.2-0ubuntu0.14.04.1) ...
Removing obsolete conffile /etc/xul-ext/ubufox.js ...
Setting up oxideqt-codecs:amd64 (1.9.5-0ubuntu0.14.04.1) ...
Setting up liboxideqtcore0:amd64 (1.9.5-0ubuntu0.14.04.1) ...
Setting up liboxideqtquick0:amd64 (1.9.5-0ubuntu0.14.04.1) ...
Setting up liboxideqt-qmlplugin:amd64 (1.9.5-0ubuntu0.14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-30-generic
herrman@bigone:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms lib32gcc1 libc6-i386 libcuda1-340 libjansson4 libvdpau1
  libxnvctrl0 linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
  screen-resolution-extra
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
herrman@bigone:~$ sudo dpkg -C
herrman@bigone:~$ 



```

---

### Post by Bashing-om on 2015-10-07
Casey_Herrman; Hey, hey .....

Not to shabby ! A couple of minor hic-ups that may not mean a thing.
But there is :
> 
0 upgraded, 0 newly installed, 0 to remove and [color=red]1 not upgraded]/color].

see if terminal command:
```

sudo apt full-upgrade

```
will take care of that. 

Before cleanup, what kernel is booted ?
```

uname -r

```

[INDENT][INDENT]who says there is no 
[INDENT][INDENT][INDENT]rest for the weary
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-08
```

herrman@bigone:~$ uname -r
3.19.0-28-generic
herrman@bigone:~$ sudo apt full-upgrade
[sudo] password for herrman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms lib32gcc1 libc6-i386 libcuda1-340 libdrm-amdgpu1 libjansson4
  libvdpau1 libxnvctrl0 linux-headers-3.19.0-25
  linux-headers-3.19.0-25-generic linux-image-3.19.0-25-generic
  linux-image-extra-3.19.0-25-generic screen-resolution-extra
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  libgbm1
The following packages will be upgraded:
  libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau2 libdrm-nouveau2:i386
  libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386
8 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 299 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main libdrm2 amd64 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty [34.4 kB]
Get:2 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main libdrm2 i386 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty [35.1 kB]
Get:3 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main libdrm-intel1 i386 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty [62.0 kB]
Get:4 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main libdrm-intel1 amd64 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty [62.5 kB]
Get:5 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main libdrm-nouveau2 i386 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty [22.9 kB]
Get:6 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main libdrm-nouveau2 amd64 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty [22.2 kB]
Get:7 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main libdrm-radeon1 i386 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty [30.3 kB]
Get:8 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main libdrm-radeon1 amd64 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty [29.5 kB]
Fetched 299 kB in 6s (47.8 kB/s)                                               
(Reading database ... 257104 files and directories currently installed.)
Preparing to unpack .../libdrm2_2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty_amd64.deb ...
De-configuring libdrm2:i386 (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Unpacking libdrm2:amd64 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) over (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Preparing to unpack .../libdrm2_2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty_i386.deb ...
Unpacking libdrm2:i386 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) over (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Preparing to unpack .../libdrm-intel1_2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty_i386.deb ...
De-configuring libdrm-intel1:amd64 (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Unpacking libdrm-intel1:i386 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) over (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Preparing to unpack .../libdrm-intel1_2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty_amd64.deb ...
Unpacking libdrm-intel1:amd64 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) over (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Preparing to unpack .../libdrm-nouveau2_2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty_i386.deb ...
De-configuring libdrm-nouveau2:amd64 (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Unpacking libdrm-nouveau2:i386 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) over (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Preparing to unpack .../libdrm-nouveau2_2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty_amd64.deb ...
Unpacking libdrm-nouveau2:amd64 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) over (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Preparing to unpack .../libdrm-radeon1_2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty_i386.deb ...
De-configuring libdrm-radeon1:amd64 (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Unpacking libdrm-radeon1:i386 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) over (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Preparing to unpack .../libdrm-radeon1_2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty_amd64.deb ...
Unpacking libdrm-radeon1:amd64 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) over (2.4.65+git20150922.f3c6740f-0ubuntu0ricotz~trusty) ...
Setting up libdrm2:i386 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
Setting up libdrm2:amd64 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
Setting up libdrm-intel1:amd64 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
Setting up libdrm-intel1:i386 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
Setting up libdrm-nouveau2:amd64 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
Setting up libdrm-nouveau2:i386 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
Setting up libdrm-radeon1:amd64 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
Setting up libdrm-radeon1:i386 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
herrman@bigone:~$ 


```

---

### Post by Bashing-om on 2015-10-08
Casey_Herrman; Humm ..

Still a nag in the works:
> 
The following packages have been kept back:
  libgbm1

I do not see where it installed.
What have we got ?
```

apt list libgbm1
dpkg -l libgbm1
apt-cache policy libgbm1

```

See now if we are ready for that final cleanup .

[INDENT][INDENT]it is going to happen
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-08
played some medieval total war and it runs great until you get a lot going on in a battle which i believe is from no 3d from nouveau which i will add 3d later.

```

herrman@bigone:~$ apt list libgbm1
Listing... Done
libgbm1/trusty 11.0.2+git20151008+11.0.b1230e3e-0ubuntu0ricotz~trusty amd64 [upgradable from: 10.1.3-0ubuntu0.4]
herrman@bigone:~$ dpkg -l libgbm1
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libgbm1:amd64  10.1.3-0ubun amd64        generic buffer management API -- 
herrman@bigone:~$ apt-cache policy libgbm1
libgbm1:
  Installed: 10.1.3-0ubuntu0.4
  Candidate: 11.0.2+git20151008+11.0.b1230e3e-0ubuntu0ricotz~trusty
  Version table:
     11.0.2+git20151008+11.0.b1230e3e-0ubuntu0ricotz~trusty 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main amd64 Packages
 *** 10.1.3-0ubuntu0.4 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     10.1.0-4ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
herrman@bigone:~$ 


```

thanks!

---

### Post by Bashing-om on 2015-10-09
Casey_Herrman; Well ;

For what it is worth, and for what I think: We have:
> 
ii  libgbm1:amd64  10.1.3-0ubun
11.0.2+git20151008+11.0.b1230e3e-0ubuntu0ricotz~trusty 0
        500 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) trusty/main amd64 Packages

Which seems to indicate to me that the higher version requirement comes from a 'xorg-edgers' PPA.
As you are presently running nouveau, I see no reason to have that PPA active on the system . 
I would suggest that we try and 'ppa-purge' "xorg-edgers" resulting in installing the driver from repo. Then I would remove the PPA from /etc/apt/sources.list.d directory and next purge nvidia once more.

You may find that game performance is better running the nvidia proprietary driver. If we can install the nvidia driver from our repo the maintenance overhead will be a lot less than installing from PPA.

[INDENT][INDENT]something to think about
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-09
sure im game to try if you are, just let me know the commands, still learning Linux. thanks

---

### Post by Bashing-om on 2015-10-09
Casey_Herrman; Hey now that is the spirit.

Nothing ventured, nothing gained.
Let's do this in little steps .. so my little mind does not get confused.
We purge: 
```

sudo ppa-purge xorg-edgers

```
Which will revert the package from the PPA to the driver in our repo.
Now we need to "look" and see what is to be done to remove the old source:
Post back the results:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
Yes there are more direct ways to get the info, but let's keep this at a level that is easy to understand - for your benefit .
Once we have the source removed, We look and see if Nvidia driver did install ... and again check the status of the package management system.

[INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-10
hmm

```

herrman@bigone:~$ sudo ppa-purge xorg-edgers
[sudo] password for herrman: 
sudo: ppa-purge: command not found
herrman@bigone:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    37    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    41    deb http://security.ubuntu.com/ubuntu trusty-security universe
    42    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    43    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu trusty partner
    51    # deb-src http://archive.canonical.com/ubuntu trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu trusty main
    56    deb-src http://extras.ubuntu.com/ubuntu trusty main
herrman@bigone:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/xorg-edgers-nouveau-trusty.list <==
deb http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu trusty main

==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
herrman@bigone:~$ 


```

---

### Post by Bashing-om on 2015-10-10
Casey_Herrman; Ho-Kay ...

We install the tool:
```

sudo apt-get install ppa-purge

```
And continue along our merry way.

[INDENT][INDENT]progress made slowly
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-11
```

herrman@bigone:~$ sudo apt-get install ppa-purge
[sudo] password for herrman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms lib32gcc1 libc6-i386 libcuda1-340 libjansson4 libvdpau1
  libxnvctrl0 linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
  screen-resolution-extra
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ppa-purge
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 5,606 B of archives.
After this operation, 45.1 kB of additional disk space will be used.
Get:1 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main ppa-purge all 0.2.8+bzr57+edgers2 [5,606 B]
Fetched 5,606 B in 6s (860 B/s)                    
Selecting previously unselected package ppa-purge.
(Reading database ... 257104 files and directories currently installed.)
Preparing to unpack .../ppa-purge_0.2.8+bzr57+edgers2_all.deb ...
Unpacking ppa-purge (0.2.8+bzr57+edgers2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up ppa-purge (0.2.8+bzr57+edgers2) ...
herrman@bigone:~$ 


```

---

### Post by Bashing-om on 2015-10-11
Casey_Herrman; Well ...

Step 1 done>

step 2:
Edit : Because I loose track of where we are and what we are doing: Revert the PPA to our repo:
```

sudo ppa-purge xorg-edgers

```
step 3 is to comment out the fetch line  - suggest with your favorite text editor:
/etc/apt/sources.list.d/
> 
deb [http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu](http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu) trusty main

by commenting this line out.
Save the file. . and let's see what is installed for nvidia drivers at this time:
```

dpkg -l grep -i nvidia

```
And we see where we go from here.

[INDENT][INDENT]moving along smartly
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-17
took a break

```

herrman@bigone:~$ sudo ppa-purge xorg-edgers
[sudo] password for herrman: 
Updating packages lists
W: Failed to fetch http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
herrman@bigone:~$ 

```

---

### Post by Bashing-om on 2015-10-17
Casey_Herrman; OH, I see

said the blind man:
The PPA " http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/trusty/main/binary-amd64/Packages" does not exist ! the 404 is a true statement, per:
[http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/](http://ppa.launchpad.net/xorg-edgers/nouveau/ubuntu/dists/)

Let's see if we can back out of this:
```

sudo add-apt-repository -r ppa:xorg-edgers/nouveau

```
Maybe, not 100% sure of my syntax here.

If that runs then we delete that fetch from the sources.list.d directory .

See then what we can do.

[INDENT][INDENT]we make this happen yet
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-18
```

herrman@bigone:~$ sudo add-apt-repository -r ppa:xorg-edgers/nouveau
[sudo] password for herrman: 
 tag:launchpad.net:2008:redacted
 More info: https://launchpad.net/~xorg-edgers/+archive/ubuntu/nouveau
Press [ENTER] to continue or ctrl-c to cancel removing it

herrman@bigone:~$ 


```

---

### Post by Bashing-om on 2015-10-18
Casey_Herrman; UMphhhh ....

I do not know what to think here .. Others ... help !
Looking to obtain that " More info:" I get stonewalled:
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/nouveau](https://launchpad.net/~xorg-edgers/+archive/ubuntu/nouveau)  >> Sorry, you don't have permission to access this page or the information in this page is not shared with you. >>> You are logged in as bashing-om.

We need to remove this PPA in a sane way .

[INDENT][INDENT]1st time for everything
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-19
did some looking, hoping i did good

```


herrman@bigone:~$  sudo ppa-purge ppa:xorg-edgers/ppa
[sudo] password for herrman: 
Updating packages lists
PPA to be removed: xorg-edgers ppa
Note: Not removing ppa-purge package
Package revert list generated:
 intel-gpu-tools/trusty libdrm-intel1:amd64/trusty libdrm-intel1:i386/trusty 
libdrm-nouveau2:amd64/trusty libdrm-nouveau2:i386/trusty 
libdrm-radeon1:amd64/trusty libdrm-radeon1:i386/trusty libdrm2:amd64/trusty 
libdrm2:i386/trusty libgbm1:amd64/trusty libllvm3.6:amd64/trusty 
libllvm3.6:i386/trusty libvdpau1:amd64/trusty libwayland-client0:amd64/trusty 
libwayland-cursor0:amd64/trusty libwayland-server0:amd64/trusty 
libxcb-dri2-0:amd64/trusty libxcb-dri2-0:i386/trusty libxcb-dri3-0:amd64/trusty 
libxcb-dri3-0:i386/trusty libxcb-glx0:amd64/trusty libxcb-glx0:i386/trusty 
libxcb-present0:amd64/trusty libxcb-present0:i386/trusty 
libxcb-randr0:amd64/trusty libxcb-render0:amd64/trusty 
libxcb-shape0:amd64/trusty libxcb-shm0:amd64/trusty libxcb-sync1:amd64/trusty 
libxcb-sync1:i386/trusty libxcb-xfixes0:amd64/trusty libxcb-xkb1:amd64/trusty 
libxcb1:amd64/trusty libxcb1:i386/trusty

Disabling xorg-edgers PPA from 
/etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxcb-dri2-0 is already the newest version.
libxcb-dri2-0 set to manually installed.
libxcb-dri3-0 is already the newest version.
libxcb-dri3-0 set to manually installed.
libxcb-glx0 is already the newest version.
libxcb-glx0 set to manually installed.
libxcb-present0 is already the newest version.
libxcb-present0 set to manually installed.
libxcb-randr0 is already the newest version.
libxcb-randr0 set to manually installed.
libxcb-render0 is already the newest version.
libxcb-render0 set to manually installed.
libxcb-shape0 is already the newest version.
libxcb-shape0 set to manually installed.
libxcb-shm0 is already the newest version.
libxcb-shm0 set to manually installed.
libxcb-sync1 is already the newest version.
libxcb-sync1 set to manually installed.
libxcb-xfixes0 is already the newest version.
libxcb-xfixes0 set to manually installed.
libxcb-xkb1 is already the newest version.
libxcb-xkb1 set to manually installed.
libxcb1 is already the newest version.
libxcb1 set to manually installed.
libxcb-dri2-0:i386 is already the newest version.
libxcb-dri2-0:i386 set to manually installed.
libxcb-dri3-0:i386 is already the newest version.
libxcb-dri3-0:i386 set to manually installed.
libxcb-glx0:i386 is already the newest version.
libxcb-glx0:i386 set to manually installed.
libxcb-present0:i386 is already the newest version.
libxcb-present0:i386 set to manually installed.
libxcb-sync1:i386 is already the newest version.
libxcb-sync1:i386 set to manually installed.
libxcb1:i386 is already the newest version.
libxcb1:i386 set to manually installed.
libllvm3.6 is already the newest version.
libllvm3.6 set to manually installed.
libllvm3.6:i386 is already the newest version.
libllvm3.6:i386 set to manually installed.
Selected version '1.3-0ubuntu2.1' (Ubuntu:14.04/trusty-updates [amd64]) for 'intel-gpu-tools'
Selected version '2.4.60-2~ubuntu14.04.1' (Ubuntu:14.04/trusty-updates [amd64]) for 'libdrm-intel1'
Selected version '2.4.60-2~ubuntu14.04.1' (Ubuntu:14.04/trusty-updates [i386]) for 'libdrm-intel1:i386'
Selected version '2.4.60-2~ubuntu14.04.1' (Ubuntu:14.04/trusty-updates [amd64]) for 'libdrm-nouveau2'
Selected version '2.4.60-2~ubuntu14.04.1' (Ubuntu:14.04/trusty-updates [i386]) for 'libdrm-nouveau2:i386'
Selected version '2.4.60-2~ubuntu14.04.1' (Ubuntu:14.04/trusty-updates [amd64]) for 'libdrm-radeon1'
Selected version '2.4.60-2~ubuntu14.04.1' (Ubuntu:14.04/trusty-updates [i386]) for 'libdrm-radeon1:i386'
Selected version '2.4.60-2~ubuntu14.04.1' (Ubuntu:14.04/trusty-updates [amd64]) for 'libdrm2'
Selected version '2.4.60-2~ubuntu14.04.1' (Ubuntu:14.04/trusty-updates [i386]) for 'libdrm2:i386'
Selected version '10.1.3-0ubuntu0.5' (Ubuntu:14.04/trusty-updates [amd64]) for 'libgbm1'
Selected version '1:3.6-2ubuntu1~trusty1' (Ubuntu:14.04/trusty-updates [amd64]) for 'libllvm3.6'
Selected version '1:3.6-2ubuntu1~trusty1' (Ubuntu:14.04/trusty-updates [i386]) for 'libllvm3.6:i386'
Selected version '0.7-1ubuntu0.1' (Ubuntu:14.04/trusty-updates [amd64]) for 'libvdpau1'
Selected version '1.4.0-1ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libwayland-client0'
Selected version '1.4.0-1ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libwayland-cursor0'
Selected version '1.4.0-1ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libwayland-server0'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libxcb-dri2-0'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [i386]) for 'libxcb-dri2-0:i386'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libxcb-dri3-0'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [i386]) for 'libxcb-dri3-0:i386'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libxcb-glx0'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [i386]) for 'libxcb-glx0:i386'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libxcb-present0'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [i386]) for 'libxcb-present0:i386'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libxcb-randr0'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libxcb-render0'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libxcb-shape0'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libxcb-shm0'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libxcb-sync1'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [i386]) for 'libxcb-sync1:i386'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libxcb-xfixes0'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libxcb-xkb1'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [amd64]) for 'libxcb1'
Selected version '1.10-2ubuntu1' (Ubuntu:14.04/trusty [i386]) for 'libxcb1:i386'
The following packages were automatically installed and are no longer required:
  bbswitch-dkms lib32gcc1 libc6-i386 libcuda1-340 libjansson4 libxnvctrl0
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
  screen-resolution-extra
Use 'apt-get autoremove' to remove them.
Suggested packages:
  nvidia-vdpau-driver vdpau-driver
The following packages will be upgraded:
  libgbm1
The following packages will be DOWNGRADED:
  intel-gpu-tools libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau2
  libdrm-nouveau2:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386
  libvdpau1 libwayland-client0 libwayland-cursor0 libwayland-server0
1 upgraded, 0 newly installed, 13 downgraded, 0 to remove and 28 not upgraded.
Need to get 439 kB of archives.
After this operation, 2,984 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libdrm2 i386 2.4.60-2~ubuntu14.04.1 [24.1 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libdrm2 amd64 2.4.60-2~ubuntu14.04.1 [23.5 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libdrm-intel1 i386 2.4.60-2~ubuntu14.04.1 [55.2 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libdrm-intel1 amd64 2.4.60-2~ubuntu14.04.1 [55.8 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libdrm-nouveau2 i386 2.4.60-2~ubuntu14.04.1 [14.3 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libdrm-nouveau2 amd64 2.4.60-2~ubuntu14.04.1 [13.7 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libdrm-radeon1 i386 2.4.60-2~ubuntu14.04.1 [24.1 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libdrm-radeon1 amd64 2.4.60-2~ubuntu14.04.1 [23.3 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty/main libwayland-client0 amd64 1.4.0-1ubuntu1 [22.1 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty/main libwayland-server0 amd64 1.4.0-1ubuntu1 [27.1 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libgbm1 amd64 10.1.3-0ubuntu0.5 [19.1 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libvdpau1 amd64 0.7-1ubuntu0.1 [23.9 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ trusty/main libwayland-cursor0 amd64 1.4.0-1ubuntu1 [9,918 B]
Get:14 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main intel-gpu-tools amd64 1.3-0ubuntu2.1 [102 kB]
Fetched 439 kB in 5s (76.6 kB/s)          
dpkg: warning: downgrading libdrm2:i386 from 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty to 2.4.60-2~ubuntu14.04.1
(Reading database ... 257131 files and directories currently installed.)
Preparing to unpack .../libdrm2_2.4.60-2~ubuntu14.04.1_i386.deb ...
De-configuring libdrm2:amd64 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
Unpacking libdrm2:i386 (2.4.60-2~ubuntu14.04.1) over (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
dpkg: warning: downgrading libdrm2:amd64 from 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty to 2.4.60-2~ubuntu14.04.1
Preparing to unpack .../libdrm2_2.4.60-2~ubuntu14.04.1_amd64.deb ...
Unpacking libdrm2:amd64 (2.4.60-2~ubuntu14.04.1) over (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
dpkg: warning: downgrading libdrm-intel1:i386 from 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty to 2.4.60-2~ubuntu14.04.1
Preparing to unpack .../libdrm-intel1_2.4.60-2~ubuntu14.04.1_i386.deb ...
De-configuring libdrm-intel1:amd64 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
Unpacking libdrm-intel1:i386 (2.4.60-2~ubuntu14.04.1) over (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
dpkg: warning: downgrading libdrm-intel1:amd64 from 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty to 2.4.60-2~ubuntu14.04.1
Preparing to unpack .../libdrm-intel1_2.4.60-2~ubuntu14.04.1_amd64.deb ...
Unpacking libdrm-intel1:amd64 (2.4.60-2~ubuntu14.04.1) over (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
dpkg: warning: downgrading libdrm-nouveau2:i386 from 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty to 2.4.60-2~ubuntu14.04.1
Preparing to unpack .../libdrm-nouveau2_2.4.60-2~ubuntu14.04.1_i386.deb ...
De-configuring libdrm-nouveau2:amd64 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
Unpacking libdrm-nouveau2:i386 (2.4.60-2~ubuntu14.04.1) over (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
dpkg:  warning: downgrading libdrm-nouveau2:amd64 from  2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty to  2.4.60-2~ubuntu14.04.1
Preparing to unpack .../libdrm-nouveau2_2.4.60-2~ubuntu14.04.1_amd64.deb ...
Unpacking libdrm-nouveau2:amd64 (2.4.60-2~ubuntu14.04.1) over (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
dpkg: warning: downgrading libdrm-radeon1:i386 from 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty to 2.4.60-2~ubuntu14.04.1
Preparing to unpack .../libdrm-radeon1_2.4.60-2~ubuntu14.04.1_i386.deb ...
De-configuring libdrm-radeon1:amd64 (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
Unpacking libdrm-radeon1:i386 (2.4.60-2~ubuntu14.04.1) over (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
dpkg: warning: downgrading libdrm-radeon1:amd64 from 2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty to 2.4.60-2~ubuntu14.04.1
Preparing to unpack .../libdrm-radeon1_2.4.60-2~ubuntu14.04.1_amd64.deb ...
Unpacking libdrm-radeon1:amd64 (2.4.60-2~ubuntu14.04.1) over (2.4.65+git20151008.8c4a1cbd-0ubuntu0ricotz~trusty) ...
dpkg: warning: downgrading libwayland-client0:amd64 from 1.7.0-0ubuntu1~trusty1 to 1.4.0-1ubuntu1
Preparing to unpack .../libwayland-client0_1.4.0-1ubuntu1_amd64.deb ...
Unpacking libwayland-client0:amd64 (1.4.0-1ubuntu1) over (1.7.0-0ubuntu1~trusty1) ...
dpkg: warning: downgrading libwayland-server0:amd64 from 1.7.0-0ubuntu1~trusty1 to 1.4.0-1ubuntu1
Preparing to unpack .../libwayland-server0_1.4.0-1ubuntu1_amd64.deb ...
Unpacking libwayland-server0:amd64 (1.4.0-1ubuntu1) over (1.7.0-0ubuntu1~trusty1) ...
Preparing to unpack .../libgbm1_10.1.3-0ubuntu0.5_amd64.deb ...
Unpacking libgbm1:amd64 (10.1.3-0ubuntu0.5) over (10.1.3-0ubuntu0.4) ...
dpkg: warning: downgrading libvdpau1:amd64 from 1.1-0ubuntu1~xedgers14.04.1 to 0.7-1ubuntu0.1
Preparing to unpack .../libvdpau1_0.7-1ubuntu0.1_amd64.deb ...
Unpacking libvdpau1:amd64 (0.7-1ubuntu0.1) over (1.1-0ubuntu1~xedgers14.04.1) ...
dpkg: warning: downgrading libwayland-cursor0:amd64 from 1.7.0-0ubuntu1~trusty1 to 1.4.0-1ubuntu1
Preparing to unpack .../libwayland-cursor0_1.4.0-1ubuntu1_amd64.deb ...
Unpacking libwayland-cursor0:amd64 (1.4.0-1ubuntu1) over (1.7.0-0ubuntu1~trusty1) ...
dpkg: warning: downgrading intel-gpu-tools from 1.8-1~xedgers~trusty to 1.3-0ubuntu2.1
Preparing to unpack .../intel-gpu-tools_1.3-0ubuntu2.1_amd64.deb ...
Unpacking intel-gpu-tools (1.3-0ubuntu2.1) over (1.8-1~xedgers~trusty) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libdrm2:amd64 (2.4.60-2~ubuntu14.04.1) ...
Setting up libdrm2:i386 (2.4.60-2~ubuntu14.04.1) ...
Setting up libdrm-intel1:amd64 (2.4.60-2~ubuntu14.04.1) ...
Setting up libdrm-intel1:i386 (2.4.60-2~ubuntu14.04.1) ...
Setting up libdrm-nouveau2:amd64 (2.4.60-2~ubuntu14.04.1) ...
Setting up libdrm-nouveau2:i386 (2.4.60-2~ubuntu14.04.1) ...
Setting up libdrm-radeon1:amd64 (2.4.60-2~ubuntu14.04.1) ...
Setting up libdrm-radeon1:i386 (2.4.60-2~ubuntu14.04.1) ...
Setting up libwayland-client0:amd64 (1.4.0-1ubuntu1) ...
Setting up libwayland-server0:amd64 (1.4.0-1ubuntu1) ...
Setting up libgbm1:amd64 (10.1.3-0ubuntu0.5) ...
Setting up libvdpau1:amd64 (0.7-1ubuntu0.1) ...
Setting up libwayland-cursor0:amd64 (1.4.0-1ubuntu1) ...
Setting up intel-gpu-tools (1.3-0ubuntu2.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
PPA purged successfully
herrman@bigone:~$ 


```

---

### Post by Bashing-om on 2015-10-19
Casey_Herrman; Yeah !

That do look to be some good !

Ok;
in /etc/apt/sources.list.d/ directory comment out ( or in the software sources ) or remove the ppa:xorg-edgers/ppa listing.

Then what does the package manager relate when:
```

sudo apt update
sudo apt full-upgrade
sudo apt-get -f install
sudo dpkg -C

``` are run ?

What have we now installed for the graphic's driver ?
```

sudo lshw -C display

```

[INDENT][INDENT]could be all 
[INDENT][INDENT][INDENT]home free
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-20
acidently ran the update and the upgrade then i saw the remove xorg ppa so i did that, then the others

```

herrman@bigone:~$ sudo rm /etc/apt/sources.list.d/xorg-edgers-nouveau-trusty.list
herrman@bigone:~$ sudo rm /etc/apt/sources.list.d/xorg-edgers-nouveau-trusty.list
rm: cannot remove &#8216;/etc/apt/sources.list.d/xorg-edgers-nouveau-trusty.list&#8217;: No such file or directory
herrman@bigone:~$ sudo rm /etc/apt/sources.list.d/xorg-edgers-nouveau-trusty.list
rm: cannot remove &#8216;/etc/apt/sources.list.d/xorg-edgers-nouveau-trusty.list&#8217;: No such file or directory
herrman@bigone:~$ sudo rm /etc/apt/sources.list.d/xorg-edgers-nouveau-trusty.list.save
herrman@bigone:~$ sudo rm /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list
herrman@bigone:~$ sudo rm /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list.save
herrman@bigone:~$ 


```

```

herrman@bigone:~$ sudo apt-get -f install
[sudo] password for herrman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms lib32gcc1 libc6-i386 libcuda1-340 libjansson4 libxnvctrl0
  linux-headers-3.13.0-65 linux-headers-3.13.0-65-generic
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-image-3.19.0-25-generic linux-image-extra-3.19.0-25-generic
  screen-resolution-extra
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
herrman@bigone:~$ sudo dpkg -C
herrman@bigone:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: G96M [GeForce 9600M GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:29 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:ec00(size=128) memory:feb80000-febfffff
herrman@bigone:~$ 


```

---

### Post by Bashing-om on 2015-10-20
Casey_Herrman; Umphhh ..

'fraid the damage:
> 
acidently ran the update and the upgrade then i saw the remove xorg ppa 

Has been done. You lost all that you had gained in doing the ppa-purge. The update/upgrade process with the PPA active possible/probably put them all back.

The PPA no longer exists, so we can not put it back and then remove .. We may now have a real mess on our hands.
Maybe we can start crawling out of the mess by comparing each and every file that the 'ppa-purge' command touched, and see what is installed as opposed to what should be installed.

EDIT:
Maybe the non-existent PPA just errored out, and no damage has been done ... maybe we will be lucky ?? But we must check. Do the following anyway just to be on firm ground.

As one instance :
```

dpkg -l intel-gpu-tools
apt-cache show intel-gpu-tools
apt-cache policy intel-gpu-tools

```
Verify that the version numbers for each and every instance from what the ppa-purge then reinstall did that what version is now installed is in accord with the standard versions in the software repository (apt-cache). 
I can not think of an easier way to verify what is now  Than this painstaking process to check and list every file that is not standard as indicated by the 2 'apt-cache' commands. A lot of time and frustration I know . But everything must be consistent and the package manager MUST be in a happy state.

The only other alternative I can come up with is to back up your personal data, and do a clean fresh (RE-)install . Take what you have learned in this install and apply the better to this new install . It is your time and effort, I am more than willing to keep plugging away trying to fix this present install. Your call as to what you want to do.

All we wanted to do
[INDENT][INDENT]was install a driver !
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-20
Ok i did run "sudo ppa-purge ppa:xorg-edgers/ppa" before running the "sudo apt-get -f install" and "sudo dpkg -C" and it said there is no such package. I will check when i get home.

little out of my league but it looks good to me, what you think?

```


herrman@bigone:~$ dpkg -l intel-gpu-tools
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  intel-gpu-tool 1.3-0ubuntu2 amd64        tools for debugging the Intel gra
herrman@bigone:~$ apt-cache show intel-gpu-tools
Package: intel-gpu-tools
Priority: optional
Section: x11
Installed-Size: 622
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: amd64
Version: 1.3-0ubuntu2.1
Depends: libc6 (>= 2.14), libcairo2 (>= 1.2.4), libdrm-intel1 (>= 2.4.36), libdrm2 (>= 2.4.30), libpciaccess0 (>= 0.8.0+git20071002)
Conflicts: xserver-xorg-video-intel (<< 2.9.1)
Filename: pool/main/i/intel-gpu-tools/intel-gpu-tools_1.3-0ubuntu2.1_amd64.deb
Size: 102370
MD5sum: 6611d2fd6ce3d95c3c1cc302f93c15da
SHA1: 3094c48192d2585b120830ce226165d9517cda21
SHA256: 9cceb9e34ae36bdf9f22fb11486fe4725fb2e6fdce8007eeaf8d348b23de9f3a
Description-en: tools for debugging the Intel graphics driver
 intel-gpu-tools is a package of tools for debugging the Intel graphics driver,
 including a GPU hang dumping program, performance monitor, and performance
 microbenchmarks for regression testing the DRM.
Description-md5: 564f3bda44ca25bdb6227f2b18149b73
Homepage: http://www.intellinuxgraphics.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, kubuntu-full, kubuntu-active-full, edubuntu-desktop, edubuntu-usb, ubuntu-gnome-desktop

Package: intel-gpu-tools
Priority: optional
Section: x11
Installed-Size: 646
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Architecture: amd64
Version: 1.3-0ubuntu2
Depends: libc6 (>= 2.14), libcairo2 (>= 1.2.4), libdrm-intel1 (>= 2.4.36), libdrm2 (>= 2.4.30), libpciaccess0 (>= 0.8.0+git20071002)
Conflicts: xserver-xorg-video-intel (<< 2.9.1)
Filename: pool/main/i/intel-gpu-tools/intel-gpu-tools_1.3-0ubuntu2_amd64.deb
Size: 188730
MD5sum: 42d41105379bdcf1aa8529563299cdf7
SHA1: 8e02e200b77b5f3db7d77d3ed9b57b2ef24dd5a9
SHA256: df1fe246294bf2f0b28fcf6f75c15025ef8464340665a55cdd4182885d284bda
Description-en: tools for debugging the Intel graphics driver
 intel-gpu-tools is a package of tools for debugging the Intel graphics driver,
 including a GPU hang dumping program, performance monitor, and performance
 microbenchmarks for regression testing the DRM.
Description-md5: 564f3bda44ca25bdb6227f2b18149b73
Homepage: http://www.intellinuxgraphics.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, kubuntu-full, kubuntu-active-full, edubuntu-desktop, edubuntu-usb, ubuntu-gnome-desktop

herrman@bigone:~$ apt-cache policy intel-gpu-tools
intel-gpu-tools:
  Installed: 1.3-0ubuntu2.1
  Candidate: 1.3-0ubuntu2.1
  Version table:
 *** 1.3-0ubuntu2.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.3-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
herrman@bigone:~$ 



```

---

### Post by Bashing-om on 2015-10-20
Casey_Herrman; Welpl

> 
little out of my league

Nawww .. this is a far cry from rocket science. All we are doing is looking at what is installed and the version as opposed to what should be installed .
So far for 1 instance looks good, and bodes well for the others .. pick a few more from the ppa-purge from your post #47 .
```

The following packages will be DOWNGRADED:
  intel-gpu-tools libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau2
  libdrm-nouveau2:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386
  libvdpau1 libwayland-client0 libwayland-cursor0 libwayland-server0

```
And as well check a few of the libraries :
Selected version '1.3-0ubuntu2.1' _>>>>

and repeat the procedure a few times for as many packages and you feel comfortable in doing; so we are comfortable that those packages that were downgraded are still at the standard version as depicted by 'apt-cache' .

Then if all is 'standard' we proceed to look at the graphic's driver situation.


[INDENT][INDENT]maybe we lucked out
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-20
okay so how to you check the installed version? i found what you are talking about on post 47 just dont know how one checks this out on Linux? thanks

edit, with dpkg -l?

---

### Post by Bashing-om on 2015-10-20
Casey_Herrman; Hey ...

Ain't no step for a stepper, just do like you have already done, just change the name:
as in :
```

dpkg -l libdrm-intel1
apt-cache show libdrm-intel1
apt-cache policy libdrm-intel1

dpkg -l libdrm-intel1:i386
apt-cache show libdrm-intel1:i386
apt-cache policy libdrm-intel1:i386

```

And so on. All versions should be same same for each package .

Hang in here, keep at it .. ask what you do not understand .. we will make a systems admin of you yet . You are getting comfortable with this operating system .

[INDENT][INDENT]do you see the silver lining
[INDENT][INDENT][INDENT]in this little dark cloud
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-20
running terminal on Linux is like trying to speak German but knowing English, its humorous.

i ran over half the 2.4.60 ones and about half of the others, everything was turning up good and in the correct version. whats next freund?

---

### Post by Bashing-om on 2015-10-21
Casey_Herrman; Outstanding !

No damage done .. 
And yeah .. communicating with your system is another language. The more fluent one is in terminal the better the communications are.
- I too have a long way to go -
Next is my thought to verify the x-server that versions here also match with what is installed and what we are going to install.
```

lsb_release -a
uname -r
dpkg -l xorg
dpkg -l xserver-xorg
sudo lshw -C display

```
Looking to see if HardWare Enablement (HWE) is a factor here in what driver support we may require to install.

[INDENT][INDENT]we be stepp'n
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-21
```

herrman@bigone:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
herrman@bigone:~$ uname -r
3.19.0-30-generic
herrman@bigone:~$ dpkg -l xorg
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  xorg           1:7.7+1ubunt amd64        X.Org X Window System
herrman@bigone:~$ dpkg -l xserver-xorg
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  xserver-xorg   <none>       <none>       (no description available)
herrman@bigone:~$ sudo lshw -C display
[sudo] password for herrman: 
  *-display               
       description: VGA compatible controller
       product: G96M [GeForce 9600M GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:29 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:ec00(size=128) memory:feb80000-febfffff
herrman@bigone:~$ 


```

---

### Post by Bashing-om on 2015-10-21
Casey_Herrman; Well !

Looks good, and you are HWE on 14.04.3. 
Presently with the open source graphic's driver loaded .

We should be good to go - unless you want to see how the proprietary driver works now . How is your desktop performing ? 

Maybe a final check on the package manager:
```

sudo apt update
sudo apt full-upgrade
sudo apt-get -f install
sudo dpkg -C

```

[INDENT][INDENT]are we there yet ?
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-21
the desktop runs great, 3d games that have a lot going on slow down, i believe i need to load either a 3d for nouveau or run the nvidia driver. whats the best way to do that? thanks

```


herrman@bigone:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bbswitch-dkms lib32gcc1 libc6-i386 libcuda1-340 libjansson4 libxnvctrl0
  linux-headers-3.13.0-65 linux-headers-3.13.0-65-generic
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-headers-3.19.0-28 linux-headers-3.19.0-28-generic
  linux-image-3.19.0-25-generic linux-image-3.19.0-28-generic
  linux-image-extra-3.19.0-25-generic linux-image-extra-3.19.0-28-generic
  screen-resolution-extra
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
herrman@bigone:~$ sudo dpkg -C
herrman@bigone:~$ 


```

---

### Post by Bashing-om on 2015-10-21
Casey_Herrman; Well ...

Good news that last ... look'n great .

Now :
per:
[http://ubuntuforum.webs.com/proprietarydrivers.htm](http://ubuntuforum.webs.com/proprietarydrivers.htm)
> 
Ubuntu proprietary drivers.
Proprietary drivers in Ubuntu are drivers for your hardware devices that are not freely-available or open source, and must be obtained from the hardware manufacturer. The free and open source video driver, Nouveau, is the driver Ubuntu will use as the default for Nvidia graphics cards. Nouveau does not have support for 3D and may not work at all with latest video cards from Nvidia. Proprietary drivers, closed source, are the alternative for Nouveau, and most of the time provide superb 3D acceleration and overall video card support/performance. 


So if ya want gaming 3D, well we continue the fight and install a proprietary driver .

[INDENT][INDENT]still, your call
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-21
yeah we can try the nvidia driver

---

### Post by Bashing-om on 2015-10-21
Casey_Herrman; Ho-Kay !


Once more, with feeling:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo apt-get remove --purge nvidia*
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge
sudo ubuntu-drivers autoinstall
sudo nvidia-xconfig

```
Reboot to see the effect.

[INDENT][INDENT]how now brown cow
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-22
well, ummph as you say......

played mtw2 for about 30 mins and pushed with somewhat, where nouveau would stumble this driver just ran great and fast, thought my problems were over. Quit the game messed around a bit turned it off. Next day the random freezing came back, and it will hardly do anything including play a game it flawlessly did the night before. I followed the previous instructions in this thread to get back to nouveau and was checking it out and now the mouse doesnt like to move randomly and playing mtw2 is a lot slower then before, something is wrong and i am wondering if its hanging up the proper driver........

---

### Post by Bashing-om on 2015-10-22
Casey_Herrman; Hummm ...

Any hints in the log files /var/log/{Xorg.0.log, Xorg.0.log.old, Xorg.1.log} or in your home directory the file .xsession-errors ?
If X is misbehaving a report may have been generated .

[INDENT][INDENT]worth look'n at .
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-22
xorg log file, skipped to end then the last two lines repeat for a long time

```


[     6.668] (**) MCE IR Keyboard/Mouse (mceusb): (accel) keeping acceleration scheme 1
[     6.668] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration profile 0
[     6.668] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration factor: 2.000
[     6.668] (**) MCE IR Keyboard/Mouse (mceusb): (accel) acceleration threshold: 4
[     6.668] (II) config/udev: Adding input device MCE IR Keyboard/Mouse (mceusb) (/dev/input/mouse3)
[     6.668] (II) No input driver specified, ignoring this device.
[     6.668] (II) This device may have been added with another device file.
[     7.700] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     9.195] resize called 1680 1050
[    10.110] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    10.146] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    11.017] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    11.810] (WW) NOUVEAU(0): nouveau_dri2_flip_event_handler: Pageflip has impossible msc 261 < target_msc 262
[    21.114] (WW) NOUVEAU(0): nouveau_dri2_flip_event_handler: Pageflip has impossible msc 729 < target_msc 730
[    21.180] (WW) NOUVEAU(0): nouveau_dri2_flip_event_handler: Pageflip has impossible msc 732 < target_msc 733
[    21.214] (WW) NOUVEAU(0): nouveau_dri2_flip_event_handler: Pageflip has impossible msc 733 < target_msc 734
[    22.581] (WW) NOUVEAU(0): nouveau_dri2_flip_event_handler: Pageflip has impossible msc 797 < target_msc 798
[    22.615] (WW) NOUVEAU(0): nouveau_dri2_flip_event_handler:

```

---

### Post by Bashing-om on 2015-10-22
Casey_Herrman; erraahhh ....

Yeah, I tend to agree that something is seriously misaligned in (memory ?).
However, above my skill set to interpret those warnings.

Let's let it sit a a bit and see if some GURU offers an explanation.

Meanwhile I will consider a means to maybe purge nouveau ... 

[INDENT][INDENT]sometimes, I just do not know
[/INDENT][/INDENT]

---

### Post by Dukenukemx on 2015-10-22
Anyone suggest for him to use the Oibaf PPA?  It's really good.

[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by Casey_Herrman on 2015-10-22
Left it on for awhile on nouveau and it cleared up and ran fine like standard nouveau. For giggles and pits i installed nvidia 340 as detailed in this thread and after the initial reboot i went straight away and hammered with a game, empire total war which wont even run on nouveau, for around one or two hours got the fan running and the machene ran great. Quit the game and just left it on and ill report back tomorrow and see how it runs. Thanks

---

### Post by Bashing-om on 2015-10-23
Casey_Herrman; Welp;

A curious state of affairs.
IN the event of a continued problem, as you are running trusty with vivid's kernel, maybe of benefit to make sure the supporting  packages for HWE are fully installed .

@ Dukenukemx ; Yeah, is a thought .. Appreciate the good inout to this problem resolution.
Keep in mind that now there is an "official" PPA:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
While the 1st option is always to install from our software repository (tested and approved !) ,

[INDENT][INDENT]not done 'till
[INDENT][INDENT][INDENT][INDENT]we are done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-24
gonna try to ppa, but stuck on how to do it, i run:

```


sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update


```

now what do i do?

---

### Post by Bashing-om on 2015-10-24
Casey_Herrman; Ho Kay;

Worth a shot.
Make sure all the HWE dependencies are met as you are running the 3.19 (vivid) series kernel on a trusty install:
```

sudo apt-get install --install-recommends linux-generic-lts-vivid libgl1-mesa-glx-lts-vivid xserver-xorg-lts-vivid linux-image-generic-lts-vivid

```

Make sure that /etc/X11/xorg.conf file does not exist . And if it does exist at this time, remove it !
and now install the driver from PPA:
```

sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-340

``` 

As we know the 340 version is the recommended driver for that card.

Reboot to see the effect .

[INDENT][INDENT][INDENT]how now brown cow
[/INDENT][/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-24
i did the 340 one, i do wonder about the 355 since that looks like thats what the ppa wants, im still learning here.

gonna reboot and ill check it out later, thanks!

```


herrman@bigone:~$ sudo apt-get install --install-recommends linux-generic-lts-vivid libgl1-mesa-glx-lts-vivid xserver-xorg-lts-vivid linux-image-generic-lts-vivid
[sudo] password for herrman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgl1-mesa-glx-lts-vivid is already the newest version.
libgl1-mesa-glx-lts-vivid set to manually installed.
linux-image-generic-lts-vivid is already the newest version.
linux-image-generic-lts-vivid set to manually installed.
xserver-xorg-lts-vivid is already the newest version.
The following packages were automatically installed and are no longer required:
  libjansson4 libxnvctrl0 linux-headers-3.13.0-65
  linux-headers-3.13.0-65-generic linux-headers-3.19.0-25
  linux-headers-3.19.0-25-generic linux-headers-3.19.0-28
  linux-headers-3.19.0-28-generic linux-image-3.19.0-25-generic
  linux-image-3.19.0-28-generic linux-image-extra-3.19.0-25-generic
  linux-image-extra-3.19.0-28-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-generic-lts-vivid
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 0 B/1,798 B of archives.
After this operation, 27.6 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Abort.
herrman@bigone:~$ sudo rm /etc/x11/xorg.conf
rm: cannot remove &#8216;/etc/x11/xorg.conf&#8217;: No such file or directory
herrman@bigone:~$ sudo apt-add-repository ppa:graphics-drivers/ppa
 Fresh drivers from upstream, currently shipping Nvidia.

## What we're working on right now:

- Normal driver updates
- Investigating how to bring this goodness to distro on a cadence.

## WARNINGS:

This PPA is currently in testing, you should be experienced with packaging before you dive in here. Give us a few days to sort out the kinks.

Volunteers welcome! See also: https://github.com/mamarley/nvidia-graphics-drivers/

### How you can help:

## Install PTS and benchmark your gear:

    sudo apt-get install phoronix-test-suite

Run the benchmark:

    phoronix-test-suite default-benchmark openarena xonotic tesseract gputest unigine-valley

and then say yes when it asks you to submit your results to openbechmarking.org. Then grab a cup of coffee, it takes a bit for the benchmarks to run. Depending on the version of Ubuntu you're using it might preferable for you to grabs PTS from upstream directly: http://www.phoronix-test-suite.com/?k=downloads

## Share your results with the community:

Post a link to your results (or any other feedback to): https://launchpad.net/~graphics-drivers-testers

Remember to rerun and resubmit the benchmarks after driver upgrades, this will allow us to gather a bunch of data on performance that we can share with everybody.

If you run into old documentation referring to other PPAs, you can help us by consolidating references to this PPA.

If someone wants to go ahead and start prototyping on `software-properties-gtk` on what the GUI should look like, please start hacking!
 More info: https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpqgr6f39b/secring.gpg' created
gpg: keyring `/tmp/tmpqgr6f39b/pubring.gpg' created
gpg: requesting key 1118213C from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpqgr6f39b/trustdb.gpg: trustdb created
gpg: key 1118213C: public key "Launchpad PPA for Graphics Drivers Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
herrman@bigone:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Hit http://security.ubuntu.com trusty-security InRelease                       
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://dl.google.com stable Release.gpg                                    
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Hit http://repo.steampowered.com precise InRelease                             
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://dl.google.com stable Release                                        
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Get:2 http://us.archive.ubuntu.com trusty-updates/main Sources [240 kB]        
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://ppa.launchpad.net trusty Release                                    
Get:3 http://us.archive.ubuntu.com trusty-updates/restricted Sources [4,722 B] 
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Get:4 http://us.archive.ubuntu.com trusty-updates/universe Sources [140 kB]    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:5 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,145 B] 
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Get:6 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [635 kB] 
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit https://private-ppa.launchpad.net trusty Release                           
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                       
Hit https://private-ppa.launchpad.net trusty/main i386 Packages
Get:7 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Get:8 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [323 kB]
Get:9 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:10 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [615 kB] 
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US
Ign https://private-ppa.launchpad.net trusty/main Translation-en
Get:11 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.1 kB]
Get:12 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [324 kB]
Get:13 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Ign http://repo.steampowered.com precise/steam Translation-en
Fetched 2,407 kB in 53s (45.0 kB/s)
Reading package lists... Done
herrman@bigone:~$ sudo apt-get install nvidia-340
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-340 is already the newest version.
The following packages were automatically installed and are no longer required:
  libjansson4 libxnvctrl0 linux-headers-3.13.0-65
  linux-headers-3.13.0-65-generic linux-headers-3.19.0-25
  linux-headers-3.19.0-25-generic linux-headers-3.19.0-28
  linux-headers-3.19.0-28-generic linux-headers-generic-lts-vivid
  linux-image-3.19.0-25-generic linux-image-3.19.0-28-generic
  linux-image-extra-3.19.0-25-generic linux-image-extra-3.19.0-28-generic
  linux-image-generic-lts-vivid thermald
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
herrman@bigone:~$ 


```

---

### Post by Bashing-om on 2015-10-24
Casey_Herrman; Wekp:

How is it now ?
There were and are a few issues :
1) From the 340 driver install:
> 
nvidia-340 is already the newest version.
Have you not learned to this time, that in order to install (re-install) a driver the old one must be removed ? Maybe the install from PPA went OK, maybe not .. All we can do now is try and see .

2) There are packages on the system needing upgrading:
[quote]
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

we need to see what these 4 packages are and get them upgraded.

3) The package manager is wanting us to remove:
[code]
The following packages were automatically installed and are no longer required:
  libjansson4 libxnvctrl0 linux-headers-3.13.0-65
<snip>
[/quote]
I have to question what is going on that " linux-headers-3.13.0-65" is orphaned ; as that is a late kernel . Maybe best to consider to (RE-)install that kernel image . 

4) Ouch .. huh ??
> 
The following packages were automatically installed and are no longer required:
<snip>
 linux-image-generic-lts-vivid

what in the world is going on that the package manager is willing to remove this meta control file ? That raises a big red flag .

[INDENT][INDENT]all this background
[INDENT][INDENT][INDENT]just to install a driver
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-25
so you recommend removing the driver and/or ppa and then reinstalling the ppa?

---

### Post by Bashing-om on 2015-10-25
Casey_Herrman; Hey:
Like this:
> 
so you recommend removing the driver and/or ppa and then reinstalling the ppa?

IF it works, do not fix it .

I am concerned about the kernel issues . That is the base of everything on the system.
I do suggest to get that system fully updated and see what else remains to be done to make sure the system is in a consistent state.
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade
sudo apt-get -f install
sudo dpkg -C

```

If the kernel(s) are inconsistent, nothing else will be consistent . Nothing you do will be reliable.

[INDENT][INDENT]just my opinion
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-25
computer locked up after running the first two, so i reran them
```

herrman@bigone:~$ sudo apt update
[sudo] password for herrman: 
Hit http://repo.steampowered.com precise InRelease
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://repo.steampowered.com precise/steam Sources                         
Ign http://dl.google.com stable InRelease                                      
Hit http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security InRelease                       
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://us.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://dl.google.com stable Release                                        
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Ign http://dl.google.com stable/main Translation-en_US                         
Hit https://private-ppa.launchpad.net trusty Release                           
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://security.ubuntu.com trusty-security/universe Translation-en  
Hit http://us.archive.ubuntu.com trusty Release   
Hit https://private-ppa.launchpad.net trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US
Ign https://private-ppa.launchpad.net trusty/main Translation-en
Reading package lists... Done
herrman@bigone:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-65 linux-headers-3.13.0-65-generic
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-headers-3.19.0-28 linux-headers-3.19.0-28-generic
  linux-headers-generic-lts-vivid linux-image-3.19.0-25-generic
  linux-image-3.19.0-28-generic linux-image-extra-3.19.0-25-generic
  linux-image-extra-3.19.0-28-generic linux-image-generic-lts-vivid thermald
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
herrman@bigone:~$ 


```

```

herrman@bigone:~$ sudo apt full-upgrade
[sudo] password for herrman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-65 linux-headers-3.13.0-65-generic
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-headers-3.19.0-28 linux-headers-3.19.0-28-generic
  linux-headers-generic-lts-vivid linux-image-3.19.0-25-generic
  linux-image-3.19.0-28-generic linux-image-extra-3.19.0-25-generic
  linux-image-extra-3.19.0-28-generic linux-image-generic-lts-vivid thermald
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
herrman@bigone:~$ 


```

```

herrman@bigone:~$ sudo apt-get -f install
[sudo] password for herrman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-65 linux-headers-3.13.0-65-generic
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-headers-3.19.0-28 linux-headers-3.19.0-28-generic
  linux-headers-generic-lts-vivid linux-image-3.19.0-25-generic
  linux-image-3.19.0-28-generic linux-image-extra-3.19.0-25-generic
  linux-image-extra-3.19.0-28-generic linux-image-generic-lts-vivid thermald
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
herrman@bigone:~$ 


```

---

### Post by Bashing-om on 2015-10-25
Casey_Herrman; Hey !

That looks great to me !

Let me have a bit to clear my head and see a way to look and see why the package manager wants to remove:
```

linux-headers-3.13.0-65 linux-headers-3.13.0-65-generic
linux-headers-generic-lts-vivid
linux-image-generic-lts-vivid

```
Not something I think we want to do !

[INDENT][INDENT]look before we leap
[/INDENT][/INDENT]

---

### Post by blm-ubunet on 2015-10-25
The nVidia driver (proprietary) has to build the (open source portion of) kernel module against the currently installed kernel. That's why the linux-headers-xxxx are installed & support for later kernels is not guaranteed.
There might not be support in the video driver ppa for the HWE kernel version.
or..
I noticed in previous posts there was an installed package named "linux-generic-lts-vivid".
This is a meta-package available in 14.04.03 LTS repos & is currently at version 3.19.0.31.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
This diagram shows that 14.04.03 LTS will have 3.19 as vivid HWE kernel.

sudo apt-get update
sudo apt-get -s dist-upgrade

---

### Post by Bashing-om on 2015-10-26
@blm-ubunet; Thanks;

Always good to have an extra set of eyes on things, and another brain in motion .

@ Casey_Herrman; Much refreshed this AM .

You are booting the 3.19.0-30 kernel .. no problem with removing the 3.13 series kernels ( comparing your HWE system to my non-HWE 14.04 system confused my mind just a bit ).
Still do not know why the system is content to remove linux-headers-generic-lts-vivid and linux-image-generic-lts-vivid.
Let's take a look and see what is presently installed:
Post back:
```

ls -al /boot/
dpkg -l | grep linux-

``` and make an educated choice .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-27
worked late yesterday

```

herrman@bigone:~$ ls -al /boot/
total 123432
drwxr-xr-x  3 root root     4096 Oct 22 21:29 .
drwxr-xr-x 24 root root     4096 Oct 21 18:59 ..
-rw-r--r--  1 root root  1270417 Jul 24 18:19 abi-3.19.0-25-generic
-rw-r--r--  1 root root  1271100 Sep  1 06:08 abi-3.19.0-28-generic
-rw-r--r--  1 root root  1271518 Oct  2 18:54 abi-3.19.0-30-generic
-rw-r--r--  1 root root  1271689 Oct  8 07:01 abi-3.19.0-31-generic
-rw-r--r--  1 root root   177779 Jul 24 18:19 config-3.19.0-25-generic
-rw-r--r--  1 root root   177651 Sep  1 06:08 config-3.19.0-28-generic
-rw-r--r--  1 root root   177730 Oct  2 18:54 config-3.19.0-30-generic
-rw-r--r--  1 root root   177790 Oct  8 07:01 config-3.19.0-31-generic
drwxr-xr-x  5 root root     4096 Oct 22 21:28 grub
-rw-r--r--  1 root root 19801204 Sep 12 15:50 initrd.img-3.19.0-25-generic
-rw-r--r--  1 root root 19799268 Oct  4 10:25 initrd.img-3.19.0-28-generic
-rw-r--r--  1 root root 19808755 Oct 22 09:54 initrd.img-3.19.0-30-generic
-rw-r--r--  1 root root 19807119 Oct 22 21:29 initrd.img-3.19.0-31-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3623533 Jul 24 18:19 System.map-3.19.0-25-generic
-rw-------  1 root root  3626779 Sep  1 06:08 System.map-3.19.0-28-generic
-rw-------  1 root root  3627906 Oct  2 18:54 System.map-3.19.0-30-generic
-rw-------  1 root root  3628177 Oct  8 07:01 System.map-3.19.0-31-generic
-rw-r--r--  1 root root  6565984 Aug 30 14:52 vmlinuz-3.19.0-25-generic
-rw-------  1 root root  6568848 Sep  1 06:08 vmlinuz-3.19.0-28-generic
-rw-------  1 root root  6572496 Oct  2 18:54 vmlinuz-3.19.0-30-generic
-rw-------  1 root root  6572336 Oct  8 07:01 vmlinuz-3.19.0-31-generic
herrman@bigone:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.127.15                                            all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-65                               3.13.0-65.106                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                       3.13.0-65.106                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-66                               3.13.0-66.108                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                       3.13.0-66.108                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-25                               3.19.0-25.26~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-25-generic                       3.19.0-25.26~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-28                               3.19.0-28.30~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic                       3.19.0-28.30~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-30                               3.19.0-30.34~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-30-generic                       3.19.0-30.34~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-31                               3.19.0-31.36~14.04.1                                all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-31-generic                       3.19.0-31.36~14.04.1                                amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.66.72                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-vivid                       3.19.0.31.18                                        amd64        Generic Linux kernel headers
ii  linux-image-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-generic                         3.19.0-28.30~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic                         3.19.0-30.34~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-generic                         3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-25-generic                   3.19.0-25.26~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic                   3.19.0-28.30~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-30-generic                   3.19.0-30.34~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic                   3.19.0-31.36~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-vivid                         3.19.0.31.18                                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-66.108                                       amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies
herrman@bigone:~$ 


```

---

### Post by Bashing-om on 2015-10-28
Casey_Herrman; Welp;

We know we have a small problem with the installed kernels. Per 'dpkg' the system thinks old kernels are still installed, but the output from /boot says otherwise.
Let's take a gentle poke and see if the package manager can operate to remove these partial installs of old kernels:
```

sudo apt-get purge linux-headers-3.13.0-65-generic
sudo apt-get purge linux-headers-3.13.0-65

```
Depending on what the package manager does in this instance determines our approach to removing the other partials .
I can see where this might get real dirty . We try the clean way first.

[INDENT][INDENT]but, where there is a will
[INDENT][INDENT][INDENT][INDENT]there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-28
```

herrman@bigone:~$ sudo apt-get purge linux-headers-3.13.0-65-generic
[sudo] password for herrman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-65 linux-headers-3.19.0-25
  linux-headers-3.19.0-25-generic linux-headers-3.19.0-28
  linux-headers-3.19.0-28-generic linux-headers-generic-lts-vivid
  linux-image-3.19.0-25-generic linux-image-3.19.0-28-generic
  linux-image-extra-3.19.0-25-generic linux-image-extra-3.19.0-28-generic
  linux-image-generic-lts-vivid thermald
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-3.13.0-65-generic*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 13.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 312570 files and directories currently installed.)
Removing linux-headers-3.13.0-65-generic (3.13.0-65.106) ...
dpkg: warning: while removing linux-headers-3.13.0-65-generic, directory '/lib/modules/3.13.0-65-generic' not empty so not removed
herrman@bigone:~$ sudo apt-get purge linux-headers-3.13.0-65
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-headers-3.19.0-28 linux-headers-3.19.0-28-generic
  linux-headers-generic-lts-vivid linux-image-3.19.0-25-generic
  linux-image-3.19.0-28-generic linux-image-extra-3.19.0-25-generic
  linux-image-extra-3.19.0-28-generic linux-image-generic-lts-vivid thermald
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-3.13.0-65*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 63.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 303006 files and directories currently installed.)
Removing linux-headers-3.13.0-65 (3.13.0-65.106) ...
herrman@bigone:~$ 



```

---

### Post by Bashing-om on 2015-10-28
Casey_Herrman; Great !

That looked good .
Repeat for the -66 kernel:
```

sudo apt-get purge linux-headers-3.13.0-66-generic
sudo apt-get purge linux-headers-3.13.0-66

```

And then we take a pause to look over and see where we are.

[INDENT][INDENT]moving along smartly
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-28
```

herrman@bigone:~$ sudo apt-get purge linux-headers-3.13.0-66-generic
[sudo] password for herrman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-66 linux-headers-3.19.0-25
  linux-headers-3.19.0-25-generic linux-headers-3.19.0-28
  linux-headers-3.19.0-28-generic linux-headers-generic-lts-vivid
  linux-image-3.19.0-25-generic linux-image-3.19.0-28-generic
  linux-image-extra-3.19.0-25-generic linux-image-extra-3.19.0-28-generic
  linux-image-generic-lts-vivid thermald
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-3.13.0-66-generic* linux-headers-generic*
0 upgraded, 0 newly installed, 2 to remove and 11 not upgraded.
After this operation, 13.5 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 287749 files and directories currently installed.)
Removing linux-headers-generic (3.13.0.66.72) ...
Removing linux-headers-3.13.0-66-generic (3.13.0-66.108) ...
dpkg: warning: while removing linux-headers-3.13.0-66-generic, directory '/lib/modules/3.13.0-66-generic' not empty so not removed
herrman@bigone:~$ sudo apt-get purge linux-headers-3.13.0-66
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-headers-3.19.0-28 linux-headers-3.19.0-28-generic
  linux-headers-generic-lts-vivid linux-image-3.19.0-25-generic
  linux-image-3.19.0-28-generic linux-image-extra-3.19.0-25-generic
  linux-image-extra-3.19.0-28-generic linux-image-generic-lts-vivid thermald
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-3.13.0-66*
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
After this operation, 63.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 278182 files and directories currently installed.)
Removing linux-headers-3.13.0-66 (3.13.0-66.108) ...
herrman@bigone:~$ 


```

---

### Post by Bashing-om on 2015-10-28
Casey_Herrman; OK;

That too went well ..
Let's now address:
> 
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded

And clean up the system:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C

```

See how this goes .
I am done for this session, I will pick this back up on my morrow - after chores .

[INDENT][INDENT]a good day's work
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-29
sure the one i dont look at has something different in it lol. thanks

```

herrman@bigone:~$ sudo apt-get clean
[sudo] password for herrman: 
herrman@bigone:~$ apt-get autoclean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
herrman@bigone:~$ 


```

---

### Post by Bashing-om on 2015-10-30
Casey_Herrman; Hey !

My bad .. system administration requires admin authorization ... I did not direct you with the attainment of that authorization .
Correct the command to be:
```

sudo apt-get autoclean

```
sudo ---- Super User DO .

[INDENT][INDENT]carry on
[INDENT][INDENT][INDENT]smartly
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-30
```

herrman@bigone:~$ sudo apt-get autoremove
[sudo] password for herrman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.19.0-25 linux-headers-3.19.0-25-generic
  linux-headers-3.19.0-28 linux-headers-3.19.0-28-generic
  linux-headers-generic-lts-vivid linux-image-3.19.0-25-generic
  linux-image-3.19.0-28-generic linux-image-extra-3.19.0-25-generic
  linux-image-extra-3.19.0-28-generic linux-image-generic-lts-vivid thermald
0 upgraded, 0 newly installed, 11 to remove and 11 not upgraded.
After this operation, 576 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 262925 files and directories currently installed.)
Removing linux-headers-3.19.0-25-generic (3.19.0-25.26~14.04.1) ...
Removing linux-headers-3.19.0-25 (3.19.0-25.26~14.04.1) ...
Removing linux-headers-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...
Removing linux-headers-3.19.0-28 (3.19.0-28.30~14.04.1) ...
Removing linux-headers-generic-lts-vivid (3.19.0.31.18) ...
Removing linux-image-extra-3.19.0-25-generic (3.19.0-25.26~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
Error! Your kernel headers for kernel 3.19.0-25-generic cannot be found.
Please install the linux-headers-3.19.0-25-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.19.0-25-generic cannot be found.
Please install the linux-headers-3.19.0-25-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-25-generic
Found initrd image: /boot/initrd.img-3.19.0-25-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Removing linux-image-3.19.0-25-generic (3.19.0-25.26~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
dkms: removing: bbswitch 0.7 (3.19.0-25-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.7
Kernel:  3.19.0-25-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Removing linux-image-extra-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
Error! Your kernel headers for kernel 3.19.0-28-generic cannot be found.
Please install the linux-headers-3.19.0-28-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-28-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Removing linux-image-3.19.0-28-generic (3.19.0-28.30~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
dkms: removing: bbswitch 0.7 (3.19.0-28-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.7
Kernel:  3.19.0-28-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-28-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
dkms: removing: bcmwl 6.30.223.248+bdcom (3.19.0-28-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  3.19.0-28-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-28-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-28-generic /boot/vmlinuz-3.19.0-28-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Removing linux-image-generic-lts-vivid (3.19.0.31.18) ...
Removing thermald (1.4.3-5~14.04.1) ...
thermald stop/waiting
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
herrman@bigone:~$ 


```

```

herrman@bigone:~$ sudo apt-get update
[sudo] password for herrman: 
Ign http://dl.google.com stable InRelease
Hit http://repo.steampowered.com precise InRelease                             
Ign http://us.archive.ubuntu.com trusty InRelease                              
Hit http://repo.steampowered.com precise/steam Sources                         
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Hit http://dl.google.com stable Release.gpg                                    
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:2 http://security.ubuntu.com trusty-security InRelease [64.4 kB]           
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://extras.ubuntu.com trusty/main Sources                               
Get:3 http://security.ubuntu.com trusty-security/main Sources [98.0 kB]        
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:4 http://us.archive.ubuntu.com trusty-backports InRelease [64.5 kB]        
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Get:5 http://security.ubuntu.com trusty-security/restricted Sources [3,357 B]  
Hit http://ppa.launchpad.net trusty Release                                    
Get:6 http://security.ubuntu.com trusty-security/universe Sources [31.0 kB]    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit https://private-ppa.launchpad.net trusty Release                           
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Get:7 http://security.ubuntu.com trusty-security/multiverse Sources [2,346 B]
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Get:8 http://us.archive.ubuntu.com trusty-updates/main Sources [242 kB]        
Ign http://repo.steampowered.com precise/steam Translation-en                  
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [357 kB]  
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Get:10 http://us.archive.ubuntu.com trusty-updates/restricted Sources [4,722 B]
Get:11 http://us.archive.ubuntu.com trusty-updates/universe Sources [143 kB]   
Get:12 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,145 B]
Get:13 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [639 kB]
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Get:14 http://security.ubuntu.com trusty-security/restricted amd64 Packages [12.4 kB]
Get:15 http://security.ubuntu.com trusty-security/universe amd64 Packages [117 kB]
Get:16 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,688 B]
Get:17 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Get:18 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [326 kB]
Get:19 http://security.ubuntu.com trusty-security/main i386 Packages [338 kB]  
Get:20 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:21 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [619 kB] 
Get:22 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.1 kB]
Get:23 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [327 kB]
Get:24 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Get:25 http://us.archive.ubuntu.com trusty-updates/main Translation-en [310 kB]
Get:26 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.2 kB]
Get:27 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,148 B]
Get:28 http://security.ubuntu.com trusty-security/universe i386 Packages [117 kB]
Get:29 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,569 B]
Get:30 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [172 kB]
Get:31 http://us.archive.ubuntu.com trusty-backports/main Sources [6,687 B]    
Get:32 http://us.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:33 http://us.archive.ubuntu.com trusty-backports/universe Sources [30.4 kB]
Get:34 http://us.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:35 http://us.archive.ubuntu.com trusty-backports/main amd64 Packages [7,380 B]
Get:36 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,846 B]
Get:37 http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:38 http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages [36.4 kB]
Get:39 http://security.ubuntu.com trusty-security/main Translation-en [194 kB] 
Get:40 http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
Get:41 http://us.archive.ubuntu.com trusty-backports/main i386 Packages [7,407 B]
Get:42 http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:43 http://us.archive.ubuntu.com trusty-backports/universe i386 Packages [36.4 kB]
Get:44 http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:45 http://us.archive.ubuntu.com trusty-backports/main Translation-en [4,138 B]
Get:46 http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:47 http://us.archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]
Get:48 http://us.archive.ubuntu.com trusty-backports/universe Translation-en [32.2 kB]
Get:49 http://security.ubuntu.com trusty-security/multiverse Translation-en [1,679 B]
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Get:50 http://security.ubuntu.com trusty-security/restricted Translation-en [3,076 B]
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Get:51 http://security.ubuntu.com trusty-security/universe Translation-en [68.4 kB]
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 4,577 kB in 20s (225 kB/s)                                             
Reading package lists... Done
herrman@bigone:~$ 


```

locked up after update

```


herrman@bigone:~$ sudo apt-get dist-upgrade
[sudo] password for herrman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-30 linux-headers-3.19.0-30-generic
  linux-image-3.19.0-30-generic linux-image-extra-3.19.0-30-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
herrman@bigone:~$ 




```

```

herrman@bigone:~$ sudo apt-get -f install
[sudo] password for herrman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-30 linux-headers-3.19.0-30-generic
  linux-image-3.19.0-30-generic linux-image-extra-3.19.0-30-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
herrman@bigone:~$ sudo dpkg -C
herrman@bigone:~$ 




```

---

### Post by Bashing-om on 2015-10-30
Casey_Herrman; Looks great !

How is the system performing ?

What graphic's driver is presently loaded ?
```

sudo lshw -C display

```

[INDENT][INDENT]maybe all over with but the shouting
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-10-31
Locked up again, its been showing a error for awhile now ill post it when i get back home? Thanks

---

### Post by Bashing-om on 2015-10-31
Casey_Herrman; K;

Seeing the errors would be a good thing. Might now be a good time to start reading the logs also, see what the system reports .

[INDENT][INDENT]when all else fails
[INDENT][INDENT][INDENT]read the instructions
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-11-10
Took a break, which logs would be good to look at?

---

### Post by Bashing-om on 2015-11-11
Casey_Herrman; Humm ....

Locking up can be caused by any number of things.
Let's make sure it is not GUI related as a place to re-start:
```

dpkg -l | grep -i nvidia
sudo lshw -C display
lspci | grep "VGA\|3D"
cat /var/log/Xorg.0.log

```

see where we go from here ... A new thread ?? ......

[INDENT][INDENT]the process of fault isolation
[/INDENT][/INDENT]

---

### Post by Casey_Herrman on 2015-11-11
well about a hour ago i started a reinstall on ubuntu, so i have been looking over this thread for the correct way to install nvidia. Sorry to give up but this should fix the problem.

---

### Post by Bashing-om on 2015-11-11
Casey_Herrman; Hey, hey ...

The nuclear solution is often times the fastest solution, and sometimes the best solution.

once installed:
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```
Should be all that is needed to install a Nvidia proprietary driver.

[INDENT][INDENT]there is that
[/INDENT][/INDENT]

---

