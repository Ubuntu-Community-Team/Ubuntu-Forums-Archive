---
title: "Screen brightness unable to be changed in 20.04, usual solutions don't work"
date: 2020-08-02
forum: Hardware
---

### Post by deerminer on 2020-08-02
I've got asus with nvidia graphics. Screen brightness is at maximum and wont budge. Installing brightness-controller, which worked for 16.04 on the same hardware, doesn't work now.  I've also tried, to no avail, the following:

[LIST]
[*]f.lux 
[*]redshift 
[*]Editing /etc/default/grub with multiple suggested configurations (with sudo update-grub and reboot after each modification). 
[*]Editing /usr/share/X11/xorg.conf.d/80-backlight.conf and /usr/share/X11/xorg.conf.d/20-intel.conf (with reboots afterwards) 
[*]Editing directly /sys/class/backlight/acpi_video0/brightness and /sys/class/backlight/acpi_video1/brightness (they take values from 1 to 10) 
[/LIST]
Some outputs:
```
$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
default connected primary 1920x1080+0+0 0mm x 0mm
   1920x1080     77.00*

$ xrandr --output default --brightness 0.8
xrandr: Gamma size is 0.
```
```
$ ls /sys/class/backlight/
acpi_video0  acpi_video1
```
```
$ cat /usr/share/X11/xorg.conf.d/20-intel.conf
Section "Device"
        Identifier  "card0"
        Driver      "nvidia"
        Option      "Backlight"  "acpi_video1"
        BusID       "PCI:0:2:0"
EndSection

```
```
$ cat /usr/share/X11/xorg.conf.d/80-backlight.conf 
Section "Device"
    Identifier  "Intel Graphics"
    Driver      "intel"
    Option      "AccelMethod"     "sna"
    Option      "Backlight"       "acpi_video0"
    BusID       "PCI:0:2:0"
EndSection
```
```
$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi_osi="
##GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=video1"
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
$ cat /usr/share/X11/xorg.conf.d/10-nvidia-brightness.conf 
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro K1000M"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection

```

Usage of the laptop keys changes */sys/class/backlight/acpi_video0/brightness*, but without apparent further effect.

---

### Post by deerminer on 2020-08-03
I've got a hunch the problem might be different than the more common ones. *sudo su -c "echo 7 >/sys/class/backlight/asus-nb-wmi/brightness"* does nothing (only asus-nb-wmi in backlight dir), neither does *xgamma -gamma 0.1*;

Are there any other potential causes? What is some good reference on backlight brightness in linux?

---

### Post by deerminer on 2020-08-15
Some more information: got Xubuntu 20.04.1 on a flash stick, boot with it, and the screen brightness could be controlled. I copied over the settings, which I suspect are relevant (GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" in /etc/default/grub and no files for backlight in /usr/share/X11/xorg.conf.d/), but alas, to no avail.
For the record, in my current setup ubuntu 20.04 uses X11.

What else could affect the screen brightness? What else could be worth looking at and comparing?

---

### Post by deerminer on 2020-08-20
The issue seems to be related to nvidia drivers and their settings. As it turns out, I've got bumblebee and the both nouveau and proprietary drivers, and the settings for both drivers are apparently modified. Could somebody lend me a hand in interpreting the sea of config options and their effects?

*cat /etc/bumblebee/bumblebee.conf*
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
# Directory with a dummy config file to pass as a -configdir to secondary X
XorgConfDir=/etc/bumblebee/xorg.conf.d
# Xorg binary to run
XorgBinary=/usr/lib/xorg/Xorg

## Client options. Will take effect on the next optirun executed.
[optirun]
# Acceleration/ rendering bridge, possible values are auto, virtualgl and
# primus.
Bridge=auto
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# List of paths which are searched for the primus libGL.so.1 when using
# the primus bridge
PrimusLibraryPath=/usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
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
KernelDriver=nvidia
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current:/usr/lib/x86_64-linux-gnu:/usr/lib/i386-linux-gnu
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia
# If set to true, will always unload the kernel module(s) even with
# PMMethod=none - useful for newer Optimus models on which the kernel power
# management works out of the box to power the card on/off without bbswitch.
AlwaysUnloadKernelDriver=false

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau
```

*cat /etc/bumblebee/xorg.conf.nvidia*
```
Section "ServerLayout"
    Identifier  "Layout0"
    Option      "AutoAddDevices" "false"
    Option      "AutoAddGPU" "false"
EndSection

Section "Device"
    Identifier  "DiscreteNvidia"
    Driver      "nvidia"
    VendorName  "NVIDIA Corporation"

#   If the X server does not automatically detect your VGA device,
#   you can manually set it here.
#   To get the BusID prop, run `lspci | egrep 'VGA|3D'` and input the data
#   as you see in the commented example.
#   This Setting may be needed in some platforms with more than one
#   nvidia card, which may confuse the proprietary driver (e.g.,
#   trying to take ownership of the wrong device). Also needed on Ubuntu 13.04.
    BusID "PCI:01:00:0"

#   Setting ProbeAllGpus to false prevents the new proprietary driver
#   instance spawned to try to control the integrated graphics card,
#   which is already being managed outside bumblebee.
#   This option doesn't hurt and it is required on platforms running
#   more than one nvidia graphics card with the proprietary driver.
#   (E.g. Macbook Pro pre-2010 with nVidia 9400M + 9600M GT).
#   If this option is not set, the new Xorg may blacken the screen and
#   render it unusable (unless you have some way to run killall Xorg).
    Option "ProbeAllGpus" "false"

    Option "NoLogo" "true"
    Option "UseEDID" "false"
    Option "UseDisplayDevice" "none"
EndSection

```

*cat /etc/bumblebee/xorg.conf.nouveau*
```
Section "ServerLayout"
    Identifier  "Layout0"
    Option      "AutoAddDevices" "false"
    Option      "AutoAddGPU" "false"
EndSection

Section "Device"
    Identifier  "DiscreteNvidia"
    Driver      "nouveau"

#   If the X server does not automatically detect your VGA device,
#   you can manually set it here.
#   To get the BusID prop, run `lspci | egrep 'VGA|3D'` and input the data
#   as you see in the commented example.
#   This Setting is needed on Ubuntu 13.04.
    BusID "PCI:01:00:0"

EndSection

```

---

### Post by danielserva on 2020-12-26
Did you find a solution for this issue?
I am having the same problem. The keys work but the brightness doesn't change.
My laptop has an NVIDIA GTX 1650 ti card.

---

