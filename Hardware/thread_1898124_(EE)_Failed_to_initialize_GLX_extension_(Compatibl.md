---
title: "(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)"
date: 2011-12-20
forum: Hardware
---

### Post by p4r4 on 2011-12-20
Hi,

I have had a great idea, but right now it seems to be a little more tricky than expected and I hope that you have the knowledge to be able to help me :)

I have a problem getting a NVIDIA-Card to work, xorg always throws me the error: 
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

I have tried different drivers. The ones from the *buntu repo and the ones from nvidia. Always the same error.

I am running this system as a guest on a ESXi 4.1u2 with all current updates (before this I tried ESXi 5, with the same failures) with PCIe passthrough enabled (the outpout of hwinfo says everything is forwarded ok!). I also have tried different *buntu flavors (Ubuntu, Xubuntu, Mint) in the current versions.

It seems to me that the problem is, that I am not able to set the nvidia card to be the primary video-card.

I already have searched nearly the whole www without any success. I hope someone can help me at this point, because I don't know what to do next :(

Here is some output that maybe helps you with the troubleshooting:

```
# lspci
00:0f.0 VGA compatible controller: VMware SVGA II Adapter
0b:00.0 VGA compatible controller: nVidia Corporation GF108 [GeForce GT 430] (rev a1)
0b:00.1 Audio device: nVidia Corporation GF108 High Definition Audio Controller (rev a1)
```
```
# hwinfo --gfxcard
> hal.1: read hal dataprocess 4597: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
16: PCI 0f.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  Unique ID: _+Pw.jBKePf3JQB5
  SysFS ID: /devices/pci0000:00/0000:00:0f.0
  SysFS BusID: 0000:00:0f.0
  Hardware Class: graphics card
  Model: "VMWare VMWARE0405"
  Vendor: pci 0x15ad "VMWare, Inc."
  Device: pci 0x0405 "VMWARE0405"
  SubVendor: pci 0x15ad "VMWare, Inc."
  SubDevice: pci 0x0405
  I/O Ports: 0x10d0-0x10df (rw)
  Memory Range: 0xc0000000-0xc3ffffff (rw,non-prefetchable)
  Memory Range: 0xc4000000-0xc47fffff (rw,non-prefetchable)
  Memory Range: 0xc4840000-0xc4847fff (ro,non-prefetchable,disabled)
  IRQ: 9 (no events)
  Module Alias: "pci:v000015ADd00000405sv000015ADsd00000405bc03sc00i00"
  Driver Info #0:
    XFree86 v4 Server Module: vmware
  Config Status: cfg=new, avail=yes, need=no, active=unknown

53: PCI b00.0: 0300 VGA compatible controller (VGA)
  [Created at pci.318]
  Unique ID: IluS.IpfMc9IqwEA
  Parent ID: WnlC.11lousfpsJ2
  SysFS ID: /devices/pci0000:00/0000:00:16.0/0000:0b:00.0
  SysFS BusID: 0000:0b:00.0
  Hardware Class: graphics card
  Model: "nVidia VGA compatible controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0de1
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x83b8
  Revision: 0xa1
  Driver: "nvidia"
  Driver Modules: "nvidia"
  Memory Range: 0xc6000000-0xc6ffffff (rw,non-prefetchable)
  Memory Range: 0xd0000000-0xd7ffffff (ro,non-prefetchable)
  Memory Range: 0xca000000-0xcbffffff (ro,non-prefetchable)
  I/O Ports: 0x5080-0x50ff (rw)
  IRQ: 19 (no events)
  Module Alias: "pci:v000010DEd00000DE1sv00001043sd000083B8bc03sc00i00"
  Driver Info #0:
    Driver Status: nvidiafb is active
    Driver Activation Cmd: "modprobe nvidiafb"
  Driver Info #1:
    Driver Status: nouveau is not active
    Driver Activation Cmd: "modprobe nouveau"
  Driver Info #2:
    Driver Status: nvidia_current_updates is not active
    Driver Activation Cmd: "modprobe nvidia_current_updates"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #27 (PCI bridge)

Primary display adapter: #16


``````
# cat /var/log/Xorg.0.log | grep NV
[  2131.959] (II) Module glx: vendor="NVIDIA Corporation"
[  2131.959] (II) NVIDIA GLX Module  280.13  Wed Jul 27 17:12:07 PDT 2011
[  2131.961] (II) Module nvidia: vendor="NVIDIA Corporation"
[  2131.961] (II) NVIDIA dlloader X Driver  280.13  Wed Jul 27 16:55:26 PDT 2011
[  2131.961] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[  2132.215] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[  2132.239] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event5)
[  2132.239] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event6)
[  2132.239] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event7)
[  2132.239] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event8)
```
```
# cat /var/log/Xorg.0.log | grep nv
[  2131.960] (II) LoadModule: "nvidia"
[  2131.960] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[  2131.961] (II) Module nvidia: vendor="NVIDIA Corporation"
[  2132.088] (II) UnloadModule: "nvidia"
[  2132.088] (II) Unloading nvidia
```Thanks in advance!


EDIT:
Here is the current xorg.conf with working vmware output, but with the same error as ususal:
```

 # cat /etc/X11/xorg.conf

Section "Monitor"
        Identifier   "vmware"
        VendorName   "VMware, Inc"
EndSection

Section "Monitor"
        Identifier     "Monitor1"
        VendorName     "Unknown"
        Option         "DPMS"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "VMware SVGA"
        Monitor    "vmware"
        DefaultDepth     24
EndSection

Section "Screen"
        Identifier     "Screen1"
        Device         "Device1"
        Monitor        "Monitor1"
        DefaultDepth    24
        SubSection "Display"
                Depth       24
        EndSubSection
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "ServerLayout"
        Identifier     "single head configuration"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" 0 0
        Option         "Clone" "on"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Device"
        Identifier  "VMware SVGA"
        Driver      "vmware"
        Option  "NoLogo"        "True"
EndSection

Section "Device"
        Identifier     "Device1"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "nVidia Corporation GF108 [GeForce GT 430] (rev a1)"
        Screen          1
        Option  "NoLogo"        "True"
EndSection

```


Regards,
p4r4

---

