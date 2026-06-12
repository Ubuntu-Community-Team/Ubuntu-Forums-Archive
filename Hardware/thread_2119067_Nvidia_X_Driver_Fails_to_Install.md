---
title: "Nvidia X Driver Fails to Install"
date: 2013-02-22
forum: Hardware
---

### Post by fowlslegs on 2013-02-22
My laptop is the Acer Timeline Ultra M5-481TG. It has an Nvidia Geforce GT 640M LE gpu. I am running Ubuntu Studio 12.10.
  I have tried to install this driver many ways because Nouveau eats my  battery and I believe is somewhat out of date. I have even tried using  'sudo stop lightdm' in another console. I have tried nvidia_current,  nvidia_current_updates, nvidia_experimental_310, and the .run file off  their website. Every time I open nvidia-settings it tells me to run the  'nvidia-xconfig' as root then restart X. I tried this both in X and with  X stopped in an alternate console. I have also installed bumblebee and  that did nothing to get the Nvidia X Driver Running. I installed jockey  common as well and enabled these drivers using it, but again to no  avail. When I run 'nvidia-xconfig' it does create the necessary changes  to the config file, but these don't result in it actually running or  resolving the error. I have read very many articles and tried so many  things. i.e.  'sudo apt-add-repository ppa:xorg-edgers/ppa' and of  course apt's update, upgrade, and dist-upgrade. I have purged and  reinstalled everything in numerous ways looking for just the right  combination--no luck thus far.
  This has eaten hours of my time! Please help and thanks!
  Edit: sudo apt-get remove nvidia-common nvidia-current  nvidia-settings && sudo apt-get update && sudo apt-get  upgrade && sudo apt-get dist-upgrade && sudo apt-get  install nvidia-common nvidia-current nvidia-settings && sudo  jockey-text -e kmod:nvidia_current && sudo nvidia-xconfig  && sudo restart lightdm
  I made a "meta"-command for lulz and to give it one last shot--still no luck.

---

### Post by Yellow Pasque on 2013-02-22
Remove any proprietary nvidia driver you tried to install and then:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by fowlslegs on 2013-02-23
I removed nvidia-current, nvidia-common, and nvidia-settings with the synaptic package manager then followed the bumblebee instructions step by step. These instructions ended up asking me to reinstall so I did at the appropriate time. After a reboot nothing changed and my resolution is still horribly dystopic.

So I tried a couple other things. Bumblebee makes it impossible to run nvidia-xconfig; when run it displays an error saying package is not found even though nvidia-settings says to run it as root still. I still cannot find it in additional drivers and sudo jockey-text -e kmod:nvidia_current said driver could not be installed. I also edited the xorg file related to bumblebee and pointed it to the nvidia driver instead of nouveau, although maybe I did this step wrong. I tried to follow the directions that came up in the terminal window during step 1 of Bumblebee's Ubuntu installation instructions. All the code I thought I needed was already there. I just put octothorpes before the nouveau related stuff and removed them before the nvidia related stuff.

---

### Post by fowlslegs on 2013-02-23
According to this log, it seems the nvidia driver is not recognizing my gpu. When i run an lspci it comes up as 01:00.0 VGA compatible controller: NVIDIA Corporation Device 0fd3 (rev ff).

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Feb 22 19:11:41 2013
installer version: 310.32

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
WARNING: You do not appear to have an NVIDIA GPU supported by the 310.32 NVIDIA Linux graphics driver installed in this system.  For further details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).
-> License accepted.
-> Installing NVIDIA driver version 310.32.
-> There appears to already be a driver installed on your system (version: 310.32).  As part of installing this driver (version: 310.32), the existing driver will be uninstalled.  Are you sure you want to continue? ('no' will abort installation) (Answer: Yes)
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation anyway? (Answer: Yes)
-> Would you like to register the kernel module sources with DKMS? This will allow DKMS to automatically build a new module, if you install a different kernel later. (Answer: Yes)
-> Installing both new and classic TLS OpenGL libraries.
-> Installing both new and classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32-bit compatibility OpenGL libraries? (Answer: Yes)
-> Parsing log file:
-> done.
-> Validating previous installation:
-> Unable to access previously installed file '/usr/lib/xorg/modules/drivers/nvidia_drv.so' (No such file or directory).
-> Unable to access previously installed file '/usr/bin/nvidia-smi' (No such file or directory).
-> Unable to access previously installed file '/usr/share/man/man1/nvidia-smi.1.gz' (No such file or directory).
-> Unable to access previously installed file '/usr/bin/nvidia-xconfig' (No such file or directory).
-> Unable to access previously installed file '/usr/share/man/man1/nvidia-xconfig.1.gz' (No such file or directory).
-> Unable to access previously installed file '/usr/bin/nvidia-settings' (No such file or directory).
-> Unable to access previously installed file '/usr/share/man/man1/nvidia-settings.1.gz' (No such file or directory).
-> Unable to access previously installed file '/usr/bin/nvidia-bug-report.sh' (No such file or directory).
-> Unable to access previously installed file '/etc/OpenCL/vendors/nvidia.icd' (No such file or directory).
-> Unable to access previously installed symlink '/usr/lib/libOpenCL.so' (No such file or directory).
-> Unable to access previously installed symlink '/usr/lib/vdpau/libvdpau_nvidia.so.1' (No such file or directory).
-> Unable to access previously installed symlink '/usr/lib/libvdpau_nvidia.so' (No such file or directory).
-> Unable to access previously installed symlink '/usr/lib32/libOpenCL.so' (No such file or directory).
-> Unable to access previously installed symlink '/usr/lib32/libvdpau_nvidia.so' (No such file or directory).
-> Unable to access previously installed symlink '/usr/lib32/vdpau/libvdpau_nvidia.so.1' (No such file or directory).
-> done.
WARNING: Your driver installation has been altered since it was initially installed; this may happen, for example, if you have since installed the NVIDIA driver through a mechanism other than nvidia-installer (such as your distribution's native package management system).  nvidia-installer will attempt to uninstall as best it can.  Please see the file '/var/log/nvidia-installer.log' for details.
-> Uninstalling NVIDIA Accelerated Graphics Driver for Linux-x86_64 (1.0-31032 (310.32)):
WARNING: Failed to delete the directory '/usr/share/doc/NVIDIA_GLX-1.0' (Directory not empty).
WARNING: Failed to delete the directory '/etc/OpenCL/vendors' (No such file or directory).
WARNING: Failed to delete the directory '/etc/OpenCL' (No such file or directory).
WARNING: Failed to delete the directory '/usr/lib32' (Directory not empty).
-> Unable to delete directories created by previous installation.
-> done.
-> Uninstallation of existing driver: NVIDIA Accelerated Graphics Driver for Linux-x86_64 (310.32) is complete.
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64' (310.32):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Installing DKMS kernel module:
-> done.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Would you like to run the nvidia-xconfig utility to automatically update your X configuration file so that the NVIDIA X driver will be used when you restart X?  Any pre-existing X configuration file will be backed up. (Answer: Yes)
-> Your X configuration file has been successfully updated.  Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86_64 (version: 310.32) is now complete.

---

### Post by fowlslegs on 2013-02-23
I ctrl f'd my Xorg.0.log and this is all I found:

[    22.237] (II) LoadModule: "nvidia-current"
[    22.238] (WW) Warning, couldn't open module nvidia-current
[    22.238] (II) UnloadModule: "nvidia-current"
[    22.238] (II) Unloading nvidia-current
[    22.238] (EE) Failed to load module "nvidia-current" (module does not exist, 0)

---

### Post by fowlslegs on 2013-02-23
My Xorg.8.log has a lot more related information so I will post the whole thing

```
[   488.245] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[   488.245] X Protocol Version 11, Revision 0
[   488.245] Build Operating System: Linux 3.2.0-32-generic x86_64 Ubuntu
[   488.245] Current Operating System: Linux noah-Aspire-M5-481TG 3.5.0-25-lowlatency #24-Ubuntu SMP PREEMPT Wed Feb 20 23:44:07 UTC 2013 x86_64
[   488.245] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-25-lowlatency root=UUID=9182da1e-3bba-4d4a-9643-e145e36cb54b ro quiet splash
[   488.245] Build Date: 27 November 2012  07:44:35AM
[   488.245] xorg-server 2:1.13.0-0ubuntu6.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   488.245] Current version of pixman: 0.26.0
[   488.245]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   488.245] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   488.245] (==) Log file: "/var/log/Xorg.8.log", Time: Fri Feb 22 19:03:25 2013
[   488.245] (++) Using config file: "/etc/bumblebee/xorg.conf.nvidia"
[   488.245] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   488.269] (==) ServerLayout "Layout0"
[   488.269] (==) No screen section available. Using defaults.
[   488.269] (**) |-->Screen "Default Screen Section" (0)
[   488.269] (**) |   |-->Monitor "<default monitor>"
[   488.269] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[   488.269] (**) |   |-->Device "Device1"
[   488.269] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   488.269] (**) Option "AutoAddDevices" "false"
[   488.269] (**) Not automatically adding devices
[   488.269] (==) Automatically enabling devices
[   488.269] (==) Automatically adding GPU devices
[   488.270] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   488.270]     Entry deleted from font path.
[   488.270] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   488.270]     Entry deleted from font path.
[   488.270] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   488.270]     Entry deleted from font path.
[   488.270] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   488.270]     Entry deleted from font path.
[   488.270] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   488.270]     Entry deleted from font path.
[   488.270] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   488.270]     Entry deleted from font path.
[   488.270] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   488.270] (++) ModulePath set to "/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules"
[   488.270] (==) |-->Input Device "<default pointer>"
[   488.270] (==) |-->Input Device "<default keyboard>"
[   488.270] (==) The core pointer device wasn't specified explicitly in the layout.
    Using the default mouse configuration.
[   488.270] (==) The core keyboard device wasn't specified explicitly in the layout.
    Using the default keyboard configuration.
[   488.270] (II) Loader magic: 0x7f9036cbbc40
[   488.270] (II) Module ABI versions:
[   488.270]     X.Org ANSI C Emulation: 0.4
[   488.270]     X.Org Video Driver: 13.0
[   488.270]     X.Org XInput driver : 18.0
[   488.270]     X.Org Server Extension : 7.0
[   488.271] (II) config/udev: Adding drm device (/dev/dri/card0)
[   488.271] setversion 1.4 failed
[   488.273] (--) PCI:*(0:1:0:0) 10de:0fd3:1025:0713 rev 161, Mem @ 0xd2000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00003000/128, BIOS @ 0x????????/524288
[   488.273] (II) Open ACPI successful (/var/run/acpid.socket)
[   488.273] Initializing built-in extension Generic Event Extension
[   488.273] Initializing built-in extension SHAPE
[   488.273] Initializing built-in extension MIT-SHM
[   488.273] Initializing built-in extension XInputExtension
[   488.273] Initializing built-in extension XTEST
[   488.273] Initializing built-in extension BIG-REQUESTS
[   488.273] Initializing built-in extension SYNC
[   488.273] Initializing built-in extension XKEYBOARD
[   488.273] Initializing built-in extension XC-MISC
[   488.273] Initializing built-in extension SECURITY
[   488.273] Initializing built-in extension XINERAMA
[   488.273] Initializing built-in extension XFIXES
[   488.273] Initializing built-in extension RENDER
[   488.274] Initializing built-in extension RANDR
[   488.274] Initializing built-in extension COMPOSITE
[   488.274] Initializing built-in extension DAMAGE
[   488.274] Initializing built-in extension MIT-SCREEN-SAVER
[   488.274] Initializing built-in extension DOUBLE-BUFFER
[   488.274] Initializing built-in extension RECORD
[   488.274] Initializing built-in extension DPMS
[   488.274] Initializing built-in extension X-Resource
[   488.274] Initializing built-in extension XVideo
[   488.274] Initializing built-in extension XVideo-MotionCompensation
[   488.274] Initializing built-in extension XFree86-VidModeExtension
[   488.274] Initializing built-in extension XFree86-DGA
[   488.274] Initializing built-in extension XFree86-DRI
[   488.274] Initializing built-in extension DRI2
[   488.274] (II) LoadModule: "glx"
[   488.274] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   488.285] (II) Module glx: vendor="NVIDIA Corporation"
[   488.285]     compiled for 4.0.2, module version = 1.0.0
[   488.285]     Module class: X.Org Server Extension
[   488.285] (II) NVIDIA GLX Module  310.32  Mon Jan 14 15:02:04 PST 2013
[   488.285] Loading extension GLX
[   488.285] (II) LoadModule: "nvidia"
[   488.285] (WW) Warning, couldn't open module nvidia
[   488.285] (II) UnloadModule: "nvidia"
[   488.285] (II) Unloading nvidia
[   488.285] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   488.285] (==) Matched nvidia as autoconfigured driver 0
[   488.285] (==) Matched nouveau as autoconfigured driver 1
[   488.285] (==) Matched nv as autoconfigured driver 2
[   488.285] (==) Matched vesa as autoconfigured driver 3
[   488.285] (==) Matched modesetting as autoconfigured driver 4
[   488.285] (==) Matched fbdev as autoconfigured driver 5
[   488.285] (==) Assigned the driver to the xf86ConfigLayout
[   488.285] (II) LoadModule: "nvidia"
[   488.286] (WW) Warning, couldn't open module nvidia
[   488.286] (II) UnloadModule: "nvidia"
[   488.286] (II) Unloading nvidia
[   488.286] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   488.286] (II) LoadModule: "nouveau"
[   488.286] (WW) Warning, couldn't open module nouveau
[   488.286] (II) UnloadModule: "nouveau"
[   488.286] (II) Unloading nouveau
[   488.286] (EE) Failed to load module "nouveau" (module does not exist, 0)
[   488.286] (II) LoadModule: "nv"
[   488.286] (WW) Warning, couldn't open module nv
[   488.286] (II) UnloadModule: "nv"
[   488.286] (II) Unloading nv
[   488.286] (EE) Failed to load module "nv" (module does not exist, 0)
[   488.286] (II) LoadModule: "vesa"
[   488.287] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   488.287] (II) Module vesa: vendor="X.Org Foundation"
[   488.287]     compiled for 1.12.99.902, module version = 2.3.2
[   488.287]     Module class: X.Org Video Driver
[   488.287]     ABI class: X.Org Video Driver, version 13.0
[   488.287] (II) LoadModule: "modesetting"
[   488.287] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   488.287] (II) Module modesetting: vendor="X.Org Foundation"
[   488.287]     compiled for 1.13.0, module version = 0.5.0
[   488.287]     Module class: X.Org Video Driver
[   488.287]     ABI class: X.Org Video Driver, version 13.0
[   488.287] (II) LoadModule: "fbdev"
[   488.287] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   488.287] (II) Module fbdev: vendor="X.Org Foundation"
[   488.287]     compiled for 1.12.99.902, module version = 0.4.3
[   488.287]     Module class: X.Org Video Driver
[   488.287]     ABI class: X.Org Video Driver, version 13.0
[   488.287] (II) LoadModule: "mouse"
[   488.287] (II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
[   488.295] (II) Module mouse: vendor="X.Org Foundation"
[   488.295]     compiled for 1.12.99.902, module version = 1.7.2
[   488.295]     Module class: X.Org XInput Driver
[   488.295]     ABI class: X.Org XInput driver, version 18.0
[   488.295] (II) LoadModule: "kbd"
[   488.296] (WW) Warning, couldn't open module kbd
[   488.296] (II) UnloadModule: "kbd"
[   488.296] (II) Unloading kbd
[   488.296] (EE) Failed to load module "kbd" (module does not exist, 0)
[   488.296] (II) VESA: driver for VESA chipsets: vesa
[   488.296] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   488.296] (II) FBDEV: driver for framebuffer: fbdev
[   488.296] (--) using VT number 7

[   488.297] vesa: Ignoring device with a bound kernel driver
[   488.297] (WW) Falling back to old probe method for vesa
[   488.297] (WW) Falling back to old probe method for modesetting
[   488.297] (II) modesetting(2): using default device
[   488.297] (II) Loading sub module "fbdevhw"
[   488.297] (II) LoadModule: "fbdevhw"
[   488.297] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   488.297] (II) Module fbdevhw: vendor="X.Org Foundation"
[   488.297]     compiled for 1.13.0, module version = 0.0.2
[   488.297]     ABI class: X.Org Video Driver, version 13.0
[   488.298] (**) FBDEV(3): claimed PCI slot 1@0:0:0
[   488.298] (II) FBDEV(3): using default device
[   488.298] (EE) Screen 0 deleted because of no matching config section.
[   488.298] (II) UnloadModule: "vesa"
[   488.298] (EE) Screen 0 deleted because of no matching config section.
[   488.298] (II) UnloadModule: "modesetting"
[   488.298] 
Fatal server error:
[   488.298] Cannot run in framebuffer mode. Please specify busIDs        for all framebuffer devices
[   488.298] 
[   488.298] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   488.298] (EE) Please also check the log file at "/var/log/Xorg.8.log" for additional information.
[   488.298] (EE) 
[   488.298] Server terminated with error (1). Closing log file.
```

---

### Post by howefield on 2013-02-23
Check that you have the kernel headers installed...

```
uname -a
```

to get the kernel version that you are using.

Then install the kernel headers matching that kernel.

You may need to do this every time you update the kernel.

---

### Post by fowlslegs on 2013-02-23
Here is my bumblebee.conf and the xorg.nvidia.conf that is in my /etc/bumblebee not my /etc/X11 folder.

# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=nvidia-current

## Client options. Will take effect on the next optirun executed.
[optirun]
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# [https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods](https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods)

Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-current
Module=nvidia
PMMethod=bbswitch
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if
# Driver=nouveau
# [driver-nouveau]
# KernelDriver=nouveau
# PMMethod=auto
# XorgConfFile=/etc/bumblebee/xorg.conf.nouveau



~~~~~~~AND~~~~~~~~~~


&#8234;Section "ServerLayout"
    Identifier "Layout0"
    Option "AutoAddDevices" "false"
EndSection

Section "Device"
    Identifier "GeForce GT 640M LE"
    Driver "nvidia-current"
    VendorName "NVIDIA Corporation"
    Option "NoLogo" "true"
    Option "UseEDID" "false"
    Option "ConnectedMonitor" "DFP"
EndSection

---

### Post by fowlslegs on 2013-02-23
Finally here is my xorg.conf that is in my /etc/X11 folder.

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 304.64  (buildmeister@swio-display-x86-rhel47-12)  Tue Oct 30 12:04:46 PDT 2012


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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
    Identifier     "GeForce GT 640M LE"
    Driver         "nvidia-current"
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

---

### Post by fowlslegs on 2013-02-23
> **howefield said:**
> Check that you have the kernel headers installed...

```
uname -a
```to get the kernel version that you are using.

Then install the kernel headers matching that kernel.

You may need to do this every time you update the kernel.

I made sure I had the latest headers for 3.7.0-7-generic then rebooted. It didn't change anything.

---

### Post by Yellow Pasque on 2013-02-23
The problem is that you keep trying to install the nvidia driver and bork the intel driver when you do that... (Don't do that).

---

### Post by fowlslegs on 2013-02-23
> **Temüjin said:**
> The problem is that you keep trying to install the nvidia driver and bork the intel driver when you do that... (Don't do that).

I ```
--purge removed
``` all nvidia and bumbleebee packages then reinstalled nouveau-firmware then reinstalled bumblebee using ```
sudo apt-get install --no-install-recommends bumblebee bbswritch-dkms linux-headers-generic
```. I then edited bumbleebee.conf and xorg.conf to reflect that I wanted to use the nouveau driver as instructed by these developers. Still my resolution is horrible and I am unable to change it under my system settings. Not sure how my battery is doing. Optirun firefox does something, but not anything good--just a mostly black screen and an extremely distorted part of a firefox window up top. I had to ctrl alt f1 and then ctrl alt f7 and everything was back to normal.

---

### Post by Yellow Pasque on 2013-02-23
> Still my resolution is horrible
Then you didn't completely uninstall the nvidia driver and the intel driver is borked.
Maybe you should try a fresh install and follow the Bumblebee instructions...

---

### Post by fowlslegs on 2013-02-23
Deleted xorg.conf and was able to adjust resolution. Tried ```
optirun firefox
``` and I had a similar error. Ctrl-alt-1 then ctrl-alt-7 and I was back to a normal looking screen. I saw that the terminal hadn't closed so I wondered if firefox was now being run with my dedicated gpu. I tried ```
sudo tee /proc/acpi/bbswitch <<<OFF
``` and firefox stayed open. Does this mean firefox wasn't running through my gpu or that it stopped at that instant or that an exception was made and it continued to run with my dedicated gpu? When I closed the terminal  tab running firefox I had to do a quick Ctrl-alt-1 then ctrl-alt-7 and things were again normalized.

Also is there no way to get NVidia working? My gpu is listed as compatible. I don't get it. Also is nouveau considered outdated and will take full advantage of my card/ it's 3D capabilities? If I want to use CUDA can I do that without an NVidia driver?

Thanks for all your help **Temüjin.**

---

### Post by Jedcurtis on 2013-02-24
Hello Fowlslegs,
(YES, Nouveau is VERY OUTDATED!!!)

After fighting with nvidia's ominous Optimus graphics for laptops (now installed in 90% of newly sold laptops) for over a year, I wrote my own How To [here]("http://vsido.org/index.php/topic,32.msg109.html#msg109").  This was written with my distribution in mind (VSIDO) but as it is a Debian based distro just like Ubuntu is, it should work for you.  A couple of points for you to be aware of with Bumblebee.
1.  It is mainly designed with the idea of 'Powersavings' related to battery life.
2.  The Hybrid/Optimus Graphics "share" a GPU.  Bumblebee doesn't turn one off, then activate the other...  (confusing I know!)
The x-swat repositories don't work for me and is the reason for me writing the How To which points to the (I think) official Debian supported repositories at [http://suwako.nomanga.net](http://suwako.nomanga.net).  
Like I said, try to follow the How To at the above link.  I'd appreciate any feedback you may have.  This just resulted in me getting my second newly purchased laptop (Feb. 21st 2013) up and fully functional.  It is an MSI GT60 with Nvidia's GTX 675M with 2Gb of GDDR5 ram.  The first laptop was a Dell XPS 15z with the GeForce 540M.  Both were able to be put in working order using the How To.
If you don't want to use the Suwako repo's, then feel free to continue with the Ubuntu xswat repo's but following the How To at the above link.
I have made this work with 2 separate Linux distributions now.  Ubuntu, and VSIDO my current Linux distro.
Again, the How To is here; [http://vsido.org/index.php/topic,32.msg109.html#msg109](http://vsido.org/index.php/topic,32.msg109.html#msg109)

You should "***_once again_***" uninstall all Bumblebee related software before trying this.  Hopefully this will end your Optimus nightmare!

If you have any questions, don't hesitate to ask!  I just wish someone had done this before me, so I wouldn't have had to go through this nightmare myself.

---

### Post by fowlslegs on 2013-02-24
> **Jedcurtis said:**
> Hello Fowlslegs,
(YES, Nouveau is VERY OUTDATED!!!)

After fighting with nvidia's ominous Optimus graphics for laptops (now installed in 90% of newly sold laptops) for over a year, I wrote my own How To [here]("http://vsido.org/index.php/topic,32.msg109.html#msg109").  This was written with my distribution in mind (VSIDO) but as it is a Debian based distro just like Ubuntu is, it should work for you.  A couple of points for you to be aware of with Bumblebee.
1.  It is mainly designed with the idea of 'Powersavings' related to battery life.
2.  The Hybrid/Optimus Graphics "share" a GPU.  Bumblebee doesn't turn one off, then activate the other...  (confusing I know!)
The x-swat repositories don't work for me and is the reason for me writing the How To which points to the (I think) official Debian supported repositories at [http://suwako.nomanga.net](http://suwako.nomanga.net).  
Like I said, try to follow the How To at the above link.  I'd appreciate any feedback you may have.  This just resulted in me getting my second newly purchased laptop (Feb. 21st 2013) up and fully functional.  It is an MSI GT60 with Nvidia's GTX 675M with 2Gb of GDDR5 ram.  The first laptop was a Dell XPS 15z with the GeForce 540M.  Both were able to be put in working order using the How To.
If you don't want to use the Suwako repo's, then feel free to continue with the Ubuntu xswat repo's but following the How To at the above link.
I have made this work with 2 separate Linux distributions now.  Ubuntu, and VSIDO my current Linux distro.
Again, the How To is here; [http://vsido.org/index.php/topic,32.msg109.html#msg109](http://vsido.org/index.php/topic,32.msg109.html#msg109)

You should "***_once again_***" uninstall all Bumblebee related software before trying this.  Hopefully this will end your Optimus nightmare!

If you have any questions, don't hesitate to ask!  I just wish someone had done this before me, so I wouldn't have had to go through this nightmare myself.

Thanks for the tutorial Jedcurtis, however, I ran into a couple difficulties which resulted in this error: ```
noah@noah-Aspire-M5-481TG:~$ optirun glxspheres
[  295.899476] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the

[  295.899520] [ERROR]Aborting because fallback start is disabled.
```.

To tell you how I got here. First I used ```
apt-get --purge remove bumblebee bbswitch-dkms
``` and ```
-apt-get --purge autoremove
```. I removed the xswat and bumblebee repositories and bumblebee authentication from synaptic. I tried to add a new authentication as suggest, but [HTML]http://suwako.nomanga.net/[/HTML] is down, so I just ran ```
add-apt-repository ppa:bumblebee/stable
``` again. I also tried to add these repositories to my /etc/apt/sources.list, but ```
apt-get update
``` told me they failed to load. I decided to add the xorg-edgers ppa instead. At this time I have the nouveau-firmware and not the nvidia-current package installed. I ran ```
apt-get install bbswitch-dkms bumblebee-nvidia
``` and it installed nvidia-current and nvidia-settings, among other packages, as dependencies. I was already added to the group then did the username add. Rebooted and what you see above is what happened. ```
glxspheres
``` worked fine at 60.721748 frames/sec - 53.986492 Mpixels/sec
but ```
optirun glxspheres
``` gave me the error above.

---

### Post by fowlslegs on 2013-02-24
Aaaaaand theeeeeen.... I followed the instructions at ```
https://github.com/Bumblebee-Project/Bumblebee/wiki/Configuration
``` to set up my bumblebee.conf. Then I also went over to my xorg.conf.nvidia files (in both /etc/X11 and /etc/bumblebee) and filled out them both out like so
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 304.64  (buildmeister@swio-display-x86-rhel47-12)  Tue Oct 30 12:04:46 PDT 2012


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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
    Identifier     "GeForce GT 640M LE"
    Driver         "nvidia-current"
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

Section "Module"
Load "glx"
EndSection
```
taking my cues from [HTML]ftp://download.nvidia.com/solaris/1.0-9629/README/chapter-02.html[/HTML].

I rebooted and now have a different error when I ```
optirun glxspheres
```:
```
gnoah@noah-Aspire-M5-481TG:~$ optirun glxspheres
[   66.369908] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) Failed to load module "nvidia-current" (module does not exist, 0)

[   66.369947] [ERROR]Aborting because fallback start is disabled.
```

---

### Post by fowlslegs on 2013-02-24
```
# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=

## Client options. Will take effect on the next optirun executed.
[optirun]
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods

## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia-current
Module=nvidia
PMMethod=bbswitch
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia
```

I have now tried the module and kerneldriver as both nvidia and nvidia current, but I am still getting the failed to load module error. It's now saying failed to load nvidia-current, even though I have it set to just nvidia. This shouldn't matter as "On Ubuntu and Mandriva, the value for KernelDriver is nvidia-current by default, not nvidia.  However, on Ubuntu you can also find nvidia-current-updates and nvidia,  so we added a patch that should auto-detect the correct one in case  it's not set" ([HTML]https://github.com/Bumblebee-Project/Bumblebee/wiki/Configuration[/HTML]).

---

### Post by fowlslegs on 2013-02-24
I'm continuing to work on this and giving updates, hoping some of this info may help someone help me as I can't interpret it one tenth as efficiently as most of you. Thanks for the comments this far everyone and for being part of an awesome community--some people pay for this kind of service! I'm sure we will figure this out soon!

Anyway
```

noah@noah-Aspire-M5-481TG:/etc/default$ modprobe nvidia-current
FATAL: Module nvidia_current not found.
```

```
gedit /var/log/kern.log
```=

```
Feb 24 13:30:24 noah-Aspire-M5-481TG kernel: [  477.433886] nvidia: module license 'NVIDIA' taints kernel.
Feb 24 13:30:24 noah-Aspire-M5-481TG kernel: [  477.439691] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
Feb 24 13:30:24 noah-Aspire-M5-481TG kernel: [  477.439783] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  310.32  Mon Jan 14 14:41:13 PST 2013
Feb 24 13:30:25 noah-Aspire-M5-481TG kernel: [  478.111154] NVRM: API mismatch: the client has the version 304.43, but
Feb 24 13:30:25 noah-Aspire-M5-481TG kernel: [  478.111154] NVRM: this kernel module has the version 310.32.  Please
Feb 24 13:30:25 noah-Aspire-M5-481TG kernel: [  478.111154] NVRM: make sure that this kernel module and all NVIDIA driver
Feb 24 13:30:25 noah-Aspire-M5-481TG kernel: [  478.111154] NVRM: components have the same version.
Feb 24 13:39:33 noah-Aspire-M5-481TG kernel: [ 1025.719296] NVRM: API mismatch: the client has the version 304.43, but
Feb 24 13:39:33 noah-Aspire-M5-481TG kernel: [ 1025.719296] NVRM: this kernel module has the version 310.32.  Please
Feb 24 13:39:33 noah-Aspire-M5-481TG kernel: [ 1025.719296] NVRM: make sure that this kernel module and all NVIDIA driver
Feb 24 13:39:33 noah-Aspire-M5-481TG kernel: [ 1025.719296] NVRM: components have the same version.

```

---

### Post by Yellow Pasque on 2013-02-24
My vote is still for a clean install. It looks like you never fully removed a previous install of the nvidia driver (the one you installed directly without using a .deb).

---

### Post by fowlslegs on 2013-02-24
> **Temüjin said:**
> My vote is still for a clean install. It looks like you never fully removed a previous install of the nvidia driver (the one you installed directly without using a .deb).

How can I be more complete than ```
apt-get --purge remove nvidia-common bbswitch-dkms bumblebee bumblebee-nvidia nvidia-current nvidia-settings && apt-get --purge autoremove
```? I also removed the bumblebee repositories and authentication.

---

### Post by fowlslegs on 2013-02-24
After making sure all files were backed up I took what to me seems like a "newb-ish" and risky move. I used a nautilus search and deleted everything nvidia and bumblebee. Now, do you think I should install Nvidia via the .run file then bumblebee or just follow the bumblebee directions that include getting/installing the nvidia.deb?

---

### Post by fowlslegs on 2013-02-24
> **fowlslegs said:**
> After making sure all files were backed up I took what to me seems like a "newb-ish" and risky move. I used a nautilus search and deleted everything nvidia and bumblebee. Now, do you think I should install Nvidia via the .run file then bumblebee or just follow the bumblebee directions that include getting/installing the nvidia.deb?

I'd like to add to the quoted post above that first I used the code in the post before that one. Anyway, I rebooted and I am still here. I can't imagine a cleaner uninstall. Now I'd like to ask Temujin and others EXACTLY what they think I should do. Note I do have nouveau-firmware, libdrm-nouveau2, libdrm-nouveau1a, libdrm-nouveau2-dbg, libdrm-nouveau1a-dbg, xserver-xorg-video-nouveau, and xserver-xorg-video-nouveau-dbg packages currently installed. If there is any code whatsoever I can run to give anyone any additional information they think might help them help me please let me know. For now I'm not touching anything.

---

### Post by Jedcurtis on 2013-02-24
> After making sure all files were backed up I took what to me seems like a  "newb-ish" and risky move. I used a nautilus search and deleted  everything nvidia and bumblebee
Actually I wouldn't call it "newb-ish" at all.  However, I'd never do it again!!!  I'm really surprised you got logged back into the system after that.  If you look through you system files, you'll find folders of all kinds that you didn't (think) install.
My on question on your removing things was you method using the --purge...
This is just telling 'purge' to be 'verbose' and tell you everything its doing.
This is what you did;
```
apt-get --purge remove bumblebee bbswitch-dkms
```
And this is how I'd have done it;
```
sudo apt-get remove bumblebee bbswitch-dkms
```
then;
```
sudo apt-get autoremove
```

I have never seen the suwako site down, but I'd try again.  That said, they are the repository for the base Debian OS.  I do not know and can not vouch for how they'll work with Ubuntu for you.  I did install using them when I was using Ubuntu, and I'm using them now on the Debian distro I use.

Temujin may have the best solution for you, though I'm sure that may be hard to swallow.  I hated re-installing, and would bang my head into the bricks till it bled before giving in.  I'm not necessarily smart, just stubborn!  I would encourage you to keep trying till you fix it or break it and "HAVE" to re-install!  It's the best way to learn about Linux!  Make sure before you go any further though, that you have everything of value to you backed up.

And for the record I'll post here a link you've probably been to or at least referred to a dozen times;
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
Temujin is right in that if you didn't 'completely' get rid of previous Bumblebee/Nvidia stuff, then your probably wasting your time trying to re-install Bumblebee at this point.  Which, of course, means a totally clean re-install of Ubuntu.  Isn't Optimus/hybrid graphics fun?  Grrr, what was or is Nvidia thinking?  Not about Linux users, thats for sure.

The link to my How To should get you through all this if you can get your system cleaned of the previous installs of Bumblebee.  As much work as your posts indicate you've done, I'll take it one step further and tell you another route.  irc.  If you can get an irc client installed, I'm usually around throughout the day/night at chat.freenode.net and the channel is #VSIDO.  It is sometimes easier to get things solved through irc than the forums.  A lesson I wish someone had told me a long time ago!!!

Good Luck...

---

### Post by Yellow Pasque on 2013-02-24
> **fowlslegs said:**
> How can I be more complete than ```
apt-get --purge remove nvidia-common bbswitch-dkms bumblebee bumblebee-nvidia nvidia-current nvidia-settings && apt-get --purge autoremove
```? I also removed the bumblebee repositories and authentication.
The problem is that you ran the nvidia driver install directly from a .run file (not using .deb packages). No amount of apt-get purging will make sure that whatever files the .run program littered your filesystem with are removed.

Nouveau packages can be installed; it doesn't matter (they don't interfere with other drivers).

---

### Post by fowlslegs on 2013-02-25
Reinstalled Ubuntu 12.10 studio. Followed bumblebee's wiki instructions exactly except used xorg-edgers instead of x-swat (all packages/ drivers in x-swat are also in xorg-edgers). 

```
noah@noah-Aspire-M5-481TG:~$ optirun glxspheres
[  621.630550] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0

[  621.630602] [ERROR]Aborting because fallback start is disabled.
```

```
noah@noah-Aspire-M5-481TG:~$ gedit /var/log/kern.log
``` =
```
Feb 25 00:13:33 noah-Aspire-M5-481TG kernel: [  619.091107] bbswitch: enabling discrete graphics
Feb 25 00:13:33 noah-Aspire-M5-481TG kernel: [  619.149698] pci 0000:01:00.0: power state changed by ACPI to D0
Feb 25 00:13:33 noah-Aspire-M5-481TG kernel: [  619.149719] pci 0000:01:00.0: power state changed by ACPI to D0
Feb 25 00:13:33 noah-Aspire-M5-481TG kernel: [  619.149832] pci 0000:01:00.0: power state changed by ACPI to D0
Feb 25 00:13:33 noah-Aspire-M5-481TG kernel: [  619.149841] pci 0000:01:00.0: power state changed by ACPI to D0
Feb 25 00:13:33 noah-Aspire-M5-481TG kernel: [  619.149850] pci 0000:01:00.0: enabling device (0006 -> 0007)
Feb 25 00:13:33 noah-Aspire-M5-481TG kernel: [  619.320568] nvidia: module license 'NVIDIA' taints kernel.
Feb 25 00:13:33 noah-Aspire-M5-481TG kernel: [  619.320574] Disabling lock debugging due to kernel taint
Feb 25 00:13:33 noah-Aspire-M5-481TG kernel: [  619.333195] nvidia 0000:01:00.0: power state changed by ACPI to D0
Feb 25 00:13:33 noah-Aspire-M5-481TG kernel: [  619.333203] nvidia 0000:01:00.0: power state changed by ACPI to D0
Feb 25 00:13:33 noah-Aspire-M5-481TG kernel: [  619.333209] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
Feb 25 00:13:33 noah-Aspire-M5-481TG kernel: [  619.333226] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
Feb 25 00:13:33 noah-Aspire-M5-481TG kernel: [  619.333379] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.64  Tue Oct 30 10:58:20 PDT 2012
```

---

### Post by fowlslegs on 2013-02-25
```
noah@noah-Aspire-M5-481TG:~$ dmesg | grep nvidia
[  619.320568] nvidia: module license 'NVIDIA' taints kernel.
[  619.333195] nvidia 0000:01:00.0: power state changed by ACPI to D0
[  619.333203] nvidia 0000:01:00.0: power state changed by ACPI to D0
[  619.333209] nvidia 0000:01:00.0: enabling device (0006 -> 0007)
```

---

### Post by fowlslegs on 2013-02-25
```
noah@noah-Aspire-M5-481TG:~$ lsmod | grep nvidia
nvidia              11284048  0 
```

and

```
noah@noah-Aspire-M5-481TG:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend, 
```.

---

### Post by fowlslegs on 2013-02-25
> **Jedcurtis said:**
> Actually I wouldn't call it "newb-ish" at all.  However, I'd never do it again!!!  I'm really surprised you got logged back into the system after that.  If you look through you system files, you'll find folders of all kinds that you didn't (think) install.
My on question on your removing things was you method using the --purge...
This is just telling 'purge' to be 'verbose' and tell you everything its doing.
This is what you did;
```
apt-get --purge remove bumblebee bbswitch-dkms
```And this is how I'd have done it;
```
sudo apt-get remove bumblebee bbswitch-dkms
```then;
```
sudo apt-get autoremove
```I have never seen the suwako site down, but I'd try again.  That said, they are the repository for the base Debian OS.  I do not know and can not vouch for how they'll work with Ubuntu for you.  I did install using them when I was using Ubuntu, and I'm using them now on the Debian distro I use.

Temujin may have the best solution for you, though I'm sure that may be hard to swallow.  I hated re-installing, and would bang my head into the bricks till it bled before giving in.  I'm not necessarily smart, just stubborn!  I would encourage you to keep trying till you fix it or break it and "HAVE" to re-install!  It's the best way to learn about Linux!  Make sure before you go any further though, that you have everything of value to you backed up.

And for the record I'll post here a link you've probably been to or at least referred to a dozen times;
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
Temujin is right in that if you didn't 'completely' get rid of previous Bumblebee/Nvidia stuff, then your probably wasting your time trying to re-install Bumblebee at this point.  Which, of course, means a totally clean re-install of Ubuntu.  Isn't Optimus/hybrid graphics fun?  Grrr, what was or is Nvidia thinking?  Not about Linux users, thats for sure.

The link to my How To should get you through all this if you can get your system cleaned of the previous installs of Bumblebee.  As much work as your posts indicate you've done, I'll take it one step further and tell you another route.  irc.  If you can get an irc client installed, I'm usually around throughout the day/night at chat.freenode.net and the channel is #VSIDO.  It is sometimes easier to get things solved through irc than the forums.  A lesson I wish someone had told me a long time ago!!!

Good Luck...

I also did autoremove as well, but thank you for the information. I will try to get in contact with you soon if I cannot figure this out and I really appreciate that offer.

---

### Post by fowlslegs on 2013-02-25
Could I need to blacklist my nvidia module? [HTML] https://wiki.archlinux.org/index.php/Blacklisting#Blacklisting[/HTML]

---

### Post by Yellow Pasque on 2013-02-25
[https://wiki.archlinux.org/index.php/Bumblebee#NVIDIA.280.29:_Failed_to_assign_any_connected_display_devices_to_X_screen_0](https://wiki.archlinux.org/index.php/Bumblebee#NVIDIA.280.29:_Failed_to_assign_any_connected_display_devices_to_X_screen_0)

---

### Post by fowlslegs on 2013-02-25
> **Temüjin said:**
> [https://wiki.archlinux.org/index.php/Bumblebee#NVIDIA.280.29:_Failed_to_assign_any_connected_display_devices_to_X_screen_0](https://wiki.archlinux.org/index.php/Bumblebee#NVIDIA.280.29:_Failed_to_assign_any_connected_display_devices_to_X_screen_0)


```
noah@noah-Aspire-M5-481TG:~$ optirun glxspheres
Polygons in scene: 62464
Visual ID of window: 0x20
Context is Direct
OpenGL Renderer: GeForce GT 640M LE/PCIe/SSE2
145.726134 frames/sec - 129.562191 Mpixels/sec
164.320099 frames/sec - 146.093714 Mpixels/sec
149.756779 frames/sec - 133.145757 Mpixels/sec
178.797599 frames/sec - 158.965369 Mpixels/sec
187.541933 frames/sec - 166.739782 Mpixels/sec
164.111603 frames/sec - 145.908344 Mpixels/sec
158.846902 frames/sec - 142.701164 Mpixels/sec
115.876935 frames/sec - 129.318659 Mpixels/sec
134.616768 frames/sec - 134.935523 Mpixels/sec
132.613854 frames/sec - 130.609528 Mpixels/sec
123.378469 frames/sec - 121.513727 Mpixels/sec
133.711651 frames/sec - 131.690733 Mpixels/sec
137.517216 frames/sec - 135.438781 Mpixels/sec
133.929484 frames/sec - 131.905274 Mpixels/sec
117.630182 frames/sec - 115.852319 Mpixels/sec
132.415881 frames/sec - 130.414547 Mpixels/sec
120.453735 frames/sec - 118.633197 Mpixels/sec
123.712038 frames/sec - 121.842254 Mpixels/sec
120.972009 frames/sec - 119.143638 Mpixels/sec
148.911455 frames/sec - 146.660807 Mpixels/sec
132.271679 frames/sec - 130.272525 Mpixels/sec
```

Success! Marry me Temujin! Thanks everyone! How can I close this thread?

---

### Post by Yellow Pasque on 2013-02-25
You're welcome. There's thread tools menu towards the top that says "mark solved"

---

