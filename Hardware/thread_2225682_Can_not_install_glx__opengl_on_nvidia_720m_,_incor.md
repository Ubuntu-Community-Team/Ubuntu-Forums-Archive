---
title: "Can not install glx / opengl on nvidia 720m , incorrect driver"
date: 2014-05-22
forum: Hardware
---

### Post by shiningstone on 2014-05-22
please help, my notebook cant install glx in ubuntu 12.04 i have tried using jockey-text / jocket-gtk

but it said that "no propietary driver found"

here is my lshw that pointing to Display Driver

```

*-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:e000(size=4096) memory:f6000000-f70fffff ioport:e0000000(size=301989888)
           *-display
                description: 3D controller
                product: GF117M [GeForce 610M/710M / GT 620M/625M/630M/720M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:16 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
        *-display
             description: VGA compatible controller
             product: 3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)

```

is there any driver that i can use to install GLX correctly in ubuntu 12.04

please help i have tried to install it in one week but i cant install it untill now

---

### Post by papibe on 2014-05-22
Hi shiningstone.

It looks like you have a machine with [Nvidia Optimus]("http://www.nvidia.com/object/optimus_technology.html").

Start reading the description [here]("http://askubuntu.com/questions/36930/is-a-nvidia-geforce-with-optimus-technology-supported-by-ubuntu"), and let us know if you need more help.
Regards.

---

### Post by shiningstone on 2014-05-24
thanks pap. it helping me.  i will try it first

---

### Post by shiningstone on 2014-05-24
it is failed. when i install bumblebee and execute 

optirun glxinfo 
it comes to blackscreen

here are the logs
```

[   27.563869] bbswitch: version 0.8
[   27.563879] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   27.563886] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[   27.564024] bbswitch: detected an Optimus _DSM function
[   27.564044] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is on
[   27.566603] bbswitch: disabling discrete graphics
[   27.670977] pci 0000:01:00.0: power state changed by ACPI to D3cold
[  313.488711] bbswitch: enabling discrete graphics
[  313.890664] pci 0000:01:00.0: power state changed by ACPI to D0
[  313.931371] bbswitch: disabling discrete graphics
[  313.998570] pci 0000:01:00.0: power state changed by ACPI to D3cold
[  315.277187] bbswitch: enabling discrete graphics
[  315.673953] pci 0000:01:00.0: power state changed by ACPI to D0
[  315.714641] bbswitch: disabling discrete graphics
[  315.781990] pci 0000:01:00.0: power state changed by ACPI to D3cold
[  332.108917] bbswitch: enabling discrete graphics
[  332.504627] pci 0000:01:00.0: power state changed by ACPI to D0
[  332.550613] MXM: GUID detected in BIOS
[  332.550707] ACPI Error: Needed [Buffer/String/Package], found [Integer] f6f54de0 (20121018/exresop-590)
[  332.550721] ACPI Exception: AE_AML_OPERAND_TYPE, While resolving operands for [OpcodeName unavailable] (20121018/dswexec-460)
[  332.550733] ACPI Error: Method parse/execution failed [\_SB_.PCI0.GFX0._DSM] (Node f6c2e648), AE_AML_OPERAND_TYPE (20121018/psparse-537)
[  332.550757] failed to evaluate _DSM: 12291
[  332.550931] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.GFX0 handle
[  332.551903] nouveau ![  DEVICE][0000:01:00.0] unknown Fermi chipset
[  332.551914] nouveau E[  DEVICE][0000:01:00.0] unknown chipset, 0x0d7000a2
[  332.551921] nouveau E[     DRM] failed to create 0x80000080, -22
[  332.553197] nouveau: probe of 0000:01:00.0 failed with error -22
[  333.570758] bbswitch: disabling discrete graphics
[  333.636283] pci 0000:01:00.0: power state changed by ACPI to D3cold
[  414.549585] usb 3-2: USB disconnect, device number 2
[  415.961821] usb 3-2: new low-speed USB device number 3 using xhci_hcd
[  415.983253] usb 3-2: New USB device found, idVendor=1c4f, idProduct=0003
[  415.983265] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  415.983271] usb 3-2: Product: Usb Mouse
[  415.983276] usb 3-2: Manufacturer: SIGMACHIP
[  415.983611] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[  415.986694] input: SIGMACHIP Usb Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input12
[  415.987194] hid-generic 0003:1C4F:0003.0002: input,hidraw0: USB HID v1.10 Mouse [SIGMACHIP Usb Mouse] on usb-0000:00:14.0-2/input0
[  584.242570] bbswitch: enabling discrete graphics
[  584.636428] pci 0000:01:00.0: power state changed by ACPI to D0
[  585.432672] bbswitch: disabling discrete graphics
[  585.500223] pci 0000:01:00.0: power state changed by ACPI to D3cold
[  597.799788] usb 3-2: USB disconnect, device number 3
[  599.211556] usb 3-2: new low-speed USB device number 4 using xhci_hcd
[  599.233004] usb 3-2: New USB device found, idVendor=1c4f, idProduct=0003
[  599.233017] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  599.233025] usb 3-2: Product: Usb Mouse
[  599.233031] usb 3-2: Manufacturer: SIGMACHIP
[  599.233297] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[  599.236535] input: SIGMACHIP Usb Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input13
[  599.236879] hid-generic 0003:1C4F:0003.0003: input,hidraw0: USB HID v1.10 Mouse [SIGMACHIP Usb Mouse] on usb-0000:00:14.0-2/input0
[  748.141217] bbswitch: enabling discrete graphics
[  748.536316] pci 0000:01:00.0: power state changed by ACPI to D0
[  749.375625] bbswitch: disabling discrete graphics
[  749.444069] pci 0000:01:00.0: power state changed by ACPI to D3cold
[  749.480092] bbswitch: enabling discrete graphics
[  749.879772] pci 0000:01:00.0: power state changed by ACPI to D0
[  750.686763] bbswitch: disabling discrete graphics
[  750.775596] pci 0000:01:00.0: power state changed by ACPI to D3cold
[  764.158235] usb 3-2: USB disconnect, device number 4
[  765.570650] usb 3-2: new low-speed USB device number 5 using xhci_hcd
[  765.592092] usb 3-2: New USB device found, idVendor=1c4f, idProduct=0003
[  765.592103] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  765.592110] usb 3-2: Product: Usb Mouse
[  765.592115] usb 3-2: Manufacturer: SIGMACHIP
[  765.592441] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes



```

here is my lspci

```
01:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M / GT 620M/625M/630M/720M] (rev ff)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
```

//etc/bumblebee/bumblebee.conf

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
KernelDriver=nvidia-331-updates
LibraryPath=/usr/lib/nvidia-331-updates:/usr/lib32/nvidia-331-updates/
XorgModulePath=/usr/lib/nvidia-331-updates/xorg,/usr/lib/xorg/modules
#######################
#
# Module name to load, defaults to Driver if empty or unset
##KernelDriver=nvidia-current
PMMethod=auto
# colon-separated path to the nvidia libraries
##LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
#XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia


## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau



```

//etc/bumblebee/xorg.conf.nvidia
```

Section "ServerLayout"
    Identifier  "Layout0"
    Option      "AutoAddDevices" "false"
    Option      "AutoAddGPU" "false"
EndSection


Section "Device"
    Identifier  "DiscreteNvidia"
    Driver      "nvidia"
    BusId       "PCI:1:0:0"
    VendorName  "NVIDIA Corporation"
EndSection

```

//etc/bumblebee/xorg.conf.noveau

```

Section "ServerLayout"
    Identifier  "Layout0"
    Option      "AutoAddDevices" "false"
    Option      "AutoAddGPU" "false"
EndSection


Section "Device"
    Identifier  "DiscreteNvidia"
    Driver      "nouveau"
    BusId       "PCI:1:0:0"
EndSection

```
i am using ubuntu 12.04 LTS.

anyone know how to solve this? please help 

:( :( :( :( :(

---

