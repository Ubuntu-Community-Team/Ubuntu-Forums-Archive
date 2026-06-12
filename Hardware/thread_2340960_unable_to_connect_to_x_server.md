---
title: "unable to connect to x server"
date: 2016-10-23
forum: Hardware
---

### Post by celicoo123 on 2016-10-23
I'm unable to connect to my ubuntu by the interface, only by the terminal. Yesterday i have installed the ubuntu 16.04.1 using a usb pen drive, and i'm unable to see the interface... i already installed the nvidia-370 package. I'm seeing this message "no screens found(EE)... so i searched and appears to be a problem with the x server.. so i did try to startx, but this is the output:




    ....
    xinit: giving up
    xinit: unable to connect to x server: connection refused
    xinit: server error


Machine specifications:


    NVIDIA GeForce GTX 1060 GPU (6GB dedicado)
    PROCESSADOR:
    Intel® Core™ i7 Skylake - 6700HQ 2.6 GHz, 6MB Cache (3.50 GHz with Max Turbo)
    MEMORY:
    32GB RAM DDR4 (2133 MHZ)
    HARD DISK (HDD), SSD OU SSHD:
    SSHD 1 TB with 8GB SSD
    SATAE M.2:
    SATAe M.2 - 480GB SATA III - 6Gb/s
    TELA (LCD):
    15.6" FullHD (1920 x 1080p) 16:9 LED-Backlit - (Matte)




ANY help will be very much appreciated!


Thanks.

---

### Post by Bashing-om on 2016-10-23
celicoo123; Hello;

Let's see what the system knows:
from the terminal post back the outputs - Between code tags - of terminal commands:
- As you are in a TTY if you have difficulties transferring the requested outputs and require some guidance in this regard we advise on a means to do so - 
```

lspci -vnn | grep -i VGA
sudo lshw -C display

```

and what does X report :
```

cat /var/log/Xorg.0.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


Be aware the command startx has limited applications today . Very possible depending on the DE the system will tell you to go pound sand when the startx command is invoked .
So what release is this and what is the DE we are working with ?
```

lsb_release -a
env | grep XDG_CURRENT_DESKTOP

``` and we come up with the proper command to start the GUI from terminal.

[INDENT][INDENT]let there be GUI
[/INDENT][/INDENT]

---

### Post by celicoo123 on 2016-10-23
Hei Bashing-om! Thank you!!! i really appreciate your help.


```

00:02.0 VGA compatible controller [0300]: Intel Corporation Skylake Integrated Graphics [8086:191b] (rev 06) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1c20] (rev a1) (prog-if 00 [VGA controller])  *-display
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:db000000-dbffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:e000(size=128) memory:dc000000-dc07ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: driver=i915_bpo latency=0
       resources: iomemory:2f0-2ef iomemory:2f0-2ef irq:132 memory:2ffe000000-2ffeffffff memory:2fa0000000-2fafffffff ioport:f000(size=64)
```

```

[     8.230] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[     8.230] X Protocol Version 11, Revision 0
[     8.230] Build Operating System: Linux 3.13.0-95-generic x86_64 Ubuntu
[     8.230] Current Operating System: Linux celicoo 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64
[     8.230] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-45-generic.efi.signed root=UUID=bf4ecadf-17c6-4d7d-90a2-0c8689bcac4c ro quiet splash vt.handoff=7
[     8.230] Build Date: 14 September 2016  03:33:24PM
[     8.230] xorg-server 2:1.18.4-0ubuntu0.1 (For technical support please see http://www.ubuntu.com/support) 
[     8.230] Current version of pixman: 0.33.6
[     8.230]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     8.230] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     8.230] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 23 22:34:44 2016
[     8.238] (==) Using config file: "/etc/X11/xorg.conf"
[     8.238] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     8.242] (==) ServerLayout "Layout0"
[     8.242] (**) |-->Screen "Screen0" (0)
[     8.242] (**) |   |-->Monitor "Monitor0"
[     8.244] (**) |   |-->Device "Device0"
[     8.244] (**) |-->Input Device "Keyboard0"
[     8.244] (**) |-->Input Device "Mouse0"
[     8.244] (==) Automatically adding devices
[     8.244] (==) Automatically enabling devices
[     8.244] (==) Automatically adding GPU devices
[     8.244] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     8.244] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     8.244]     Entry deleted from font path.
[     8.244] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     8.244]     Entry deleted from font path.
[     8.244] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     8.244]     Entry deleted from font path.
[     8.244] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     8.244]     Entry deleted from font path.
[     8.244] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     8.244]     Entry deleted from font path.
[     8.244] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     8.244] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     8.244] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[     8.244] (WW) Disabling Keyboard0
[     8.244] (WW) Disabling Mouse0
[     8.244] (II) Loader magic: 0x5568d2013dc0
[     8.244] (II) Module ABI versions:
[     8.244]     X.Org ANSI C Emulation: 0.4
[     8.244]     X.Org Video Driver: 20.0
[     8.244]     X.Org XInput driver : 22.1
[     8.244]     X.Org Server Extension : 9.0
[     8.245] (++) using VT number 7

[     8.245] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     8.245] (II) xfree86: Adding drm device (/dev/dri/card0)
[     9.950] (II) xfree86: Adding drm device (/dev/dri/card1)
[     9.951] (--) PCI: (0:0:2:0) 8086:191b:1558:6a01 rev 6, Mem @ 0x2ffe000000/16777216, 0x2fa0000000/268435456, I/O @ 0x0000f000/64
[     9.951] (--) PCI:*(0:1:0:0) 10de:1c20:1558:6a01 rev 161, Mem @ 0xdb000000/16777216, 0x90000000/268435456, 0xa0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     9.951] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     9.951] (II) "glx" will be loaded by default.
[     9.951] (II) LoadModule: "glx"
[     9.952] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    10.084] (II) Module glx: vendor="NVIDIA Corporation"
[    10.084]     compiled for 4.0.2, module version = 1.0.0
[    10.084]     Module class: X.Org Server Extension
[    10.085] (II) NVIDIA GLX Module  370.28  Thu Sep  1 19:14:30 PDT 2016
[    10.086] (II) LoadModule: "nvidia"
[    10.086] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    10.107] (II) Module nvidia: vendor="NVIDIA Corporation"
[    10.107]     compiled for 4.0.2, module version = 1.0.0
[    10.107]     Module class: X.Org Video Driver
[    10.108] (II) NVIDIA dlloader X Driver  370.28  Thu Sep  1 18:51:40 PDT 2016
[    10.108] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    10.112] (II) Loading sub module "fb"
[    10.112] (II) LoadModule: "fb"
[    10.112] (II) Loading /usr/lib/xorg/modules/libfb.so
[    10.114] (II) Module fb: vendor="X.Org Foundation"
[    10.114]     compiled for 1.18.4, module version = 1.0.0
[    10.114]     ABI class: X.Org ANSI C Emulation, version 0.4
[    10.114] (II) Loading sub module "wfb"
[    10.114] (II) LoadModule: "wfb"
[    10.115] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    10.117] (II) Module wfb: vendor="X.Org Foundation"
[    10.117]     compiled for 1.18.4, module version = 1.0.0
[    10.117]     ABI class: X.Org ANSI C Emulation, version 0.4
[    10.117] (II) Loading sub module "ramdac"
[    10.117] (II) LoadModule: "ramdac"
[    10.117] (II) Module "ramdac" already built-in
[    10.122] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    10.122] (==) NVIDIA(0): RGB weight 888
[    10.122] (==) NVIDIA(0): Default visual is TrueColor
[    10.122] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    10.127] (**) NVIDIA(0): Enabling 2D acceleration
[    10.669] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[    10.669] (--) NVIDIA(0):     DFP-0
[    10.669] (--) NVIDIA(0):     DFP-1
[    10.669] (--) NVIDIA(0):     DFP-2
[    10.669] (--) NVIDIA(0):     DFP-3
[    10.669] (--) NVIDIA(0):     DFP-4
[    10.669] (--) NVIDIA(0): DFP-0: disconnected
[    10.669] (--) NVIDIA(0): DFP-0: Internal TMDS
[    10.669] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    10.669] (--) NVIDIA(0): 
[    10.669] (--) NVIDIA(0): DFP-1: disconnected
[    10.669] (--) NVIDIA(0): DFP-1: Internal DisplayPort
[    10.669] (--) NVIDIA(0): DFP-1: 1440.0 MHz maximum pixel clock
[    10.669] (--) NVIDIA(0): 
[    10.670] (--) NVIDIA(0): DFP-2: disconnected
[    10.670] (--) NVIDIA(0): DFP-2: Internal TMDS
[    10.670] (--) NVIDIA(0): DFP-2: 330.0 MHz maximum pixel clock
[    10.670] (--) NVIDIA(0): 
[    10.670] (--) NVIDIA(0): DFP-3: disconnected
[    10.670] (--) NVIDIA(0): DFP-3: Internal DisplayPort
[    10.670] (--) NVIDIA(0): DFP-3: 1440.0 MHz maximum pixel clock
[    10.670] (--) NVIDIA(0): 
[    10.670] (--) NVIDIA(0): DFP-4: disconnected
[    10.670] (--) NVIDIA(0): DFP-4: Internal TMDS
[    10.670] (--) NVIDIA(0): DFP-4: 330.0 MHz maximum pixel clock
[    10.670] (--) NVIDIA(0): 
[    10.671] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 1060 (GP106-A) at PCI:1:0:0 (GPU-0)
[    10.671] (--) NVIDIA(0): Memory: 6291456 kBytes
[    10.671] (--) NVIDIA(0): VideoBIOS: 86.06.18.00.04
[    10.671] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    10.671] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0. 
[    10.671] (EE) NVIDIA(0):     Set AllowEmptyInitialConfiguration if you want the server
[    10.671] (EE) NVIDIA(0):     to start anyway
[    10.671] (EE) NVIDIA(0): Failing initialization of X screen 0
[    10.742] (II) UnloadModule: "nvidia"
[    10.742] (II) UnloadSubModule: "wfb"
[    10.742] (II) UnloadSubModule: "fb"
[    10.742] (EE) Screen(s) found, but none have a usable configuration.
[    10.742] (EE) 
Fatal server error:
[    10.742] (EE) no screens found(EE) 
[    10.742] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    10.742] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    10.742] (EE) 
[    10.745] (EE) Server terminated with error (1). Closing log file.
```

```

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial
```

The last command doesn't return anything.

What do you mean by "DE"?

Thank you again!!

---

### Post by Bashing-om on 2016-10-23
celicoo123; UnGood;

In that we have the system wanting to set up the nVidia card on one of the PCI busses:
> 
9.951] (--) PCI: (0:0:2:0) 8086:191b:1558:6a01 rev 6, Mem @ 0x2ffe000000/16777216, 0x2fa0000000/268435456, I/O @ 0x0000f000/64
[     9.951] (--) PCI:*(0:1:0:0) 10de:1c20:1558:6a01 rev 161, Mem @ 0xdb000000/16777216, 0x90000000/268435456, 0xa0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     9.951]

But but, but nVidia can not identify the display device:
> 
10.669] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
10.671] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0.
10.742] (EE) Screen(s) found, but none have a usable configuration.
10.742] (EE) no screens found(EE) 


So we have hybrid graphics .. the 1st set is Intel and the 2nd being nVidia GeForce GTX 1060 .
Now the question is :
Why is no screen found ?

show us now:
```

lspci -k|grep -iEA5 'vga|3d'
dpkg -l | grep -i nvidia

```
Because I want to see that the systems sees this additional Nvidia card and if drivers are installed.

And what monitor are you using and how is it connected ? We loosing contact because of an adapter ?

And is the control file in existence ?
what returns:
```

cat /etc/X11/Xorg.conf

```

--------------------
DE is the (D)esktop (E)environment .. maybe unity (??) if it is (u)buntu that is installed .

[INDENT][INDENT]gotta be a reason why not
[INDENT][INDENT][INDENT]we be look'n
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by celicoo123 on 2016-10-23
Output:

```


00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)
    Subsystem: CLEVO/KAPOK Computer Skylake Integrated Graphics
    Kernel driver in use: i915_bpo
    Kernel modules: i915_bpo
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
    Subsystem: CLEVO/KAPOK Computer Sunrise Point-H USB 3.0 xHCI Controller
--
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1c20 (rev a1)
    Subsystem: CLEVO/KAPOK Computer Device 6a01
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_370, nvidia_370_drm
6d:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)
    Subsystem: CLEVO/KAPOK Computer Device 6a01


ii  bbswitch-dkms                               0.8-3ubuntu1                                  amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-370                                370.28-0ubuntu0~gpu16.04.2                    amd64        NVIDIA CUDA runtime library
ii  nvidia-370                                  370.28-0ubuntu0~gpu16.04.2                    amd64        NVIDIA binary driver - version 370.28
ii  nvidia-opencl-icd-370                       370.28-0ubuntu0~gpu16.04.2                    amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.2                                         amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             370.28-0ubuntu0~gpu16.04.1                    amd64        Tool for configuring the NVIDIA graphics driver

```

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 370.28  (buildmeister@swio-display-x64-rhel04-17)  Thu Sep  1 20:22:52 PDT 2016


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



```

Actually, the file here is xorg.config, not Xorg.config. Could be this messing things up?

I'm using a notebook :b.

Thanks!!!

---

### Post by Bashing-om on 2016-10-23
celicoo123; Ouch !

I sure do not like that xorg.conf file ! ..
However, I have not messed about with sytemd's requirements in 16.04.
I would expect something like:
> 
 Section "ServerLayout" ##should be as this 
    Identifier "layout" ##should be as this
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
EndSection


Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection


Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:8@0:0:0"
    Option "ConstrainCursor" "off"
EndSection


Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection

where your   BusID "PCIXXXXX" would be different.

Let's see what results if we have the system build a new config file.
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo nvidia-xconfig

```
Now restart so that the Nvidia driver can take effect.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by celicoo123 on 2016-10-23
I was able to generate the file, but i saw first:

```

Package xorg-server was not found in the pkg-config search path
Perhaps you should add the directory containing `xorg-server.pc`
No package 'xorg-server' found
New X configuration file written to '/etc/X11/xorg.conf'


```

And the new file:

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 370.28  (buildmeister@swio-display-x64-rhel04-17)  Thu Sep  1 20:22:52 PDT 2016

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



```


[COLOR=#212121][FONT=arial]I reboot ubuntu and unfortunately still can't access :/ .[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-10-23
celicoo123; Humm ..

still do not see Intel in that new config file .. as I expect it to be there and marked as "inactive" .. 
Do you have the Intel chip set disabled in bios ?? By some chance ?

and as to :
> 
Package xorg-server was not found in the pkg-config search path
Perhaps you should add the directory containing `xorg-server.pc`
No package 'xorg-server' found

I do not know what to make of that warning .. will have to expand my mind and see what I can learn .
Is this a development system ? As a quick look:
[http://packages.ubuntu.com/search?searchon=contents&keywords=xorg-server&mode=filename&suite=xenial&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=xorg-server&mode=filename&suite=xenial&arch=any)
indicates such .

And in the meantime .. I look and consider dkms .

///
and:
> 
unfortunately still can't access 

make sure that "you" are authorized to access the desktop.
what returns:
```

ls -al .ICEauthority .Xauthority

```

[INDENT]still, all we know to this time :
[INDENT][INDENT][INDENT]it's broke, Jim
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by celicoo123 on 2016-10-23
Hm let my check the BIOS. Meanwhile, this is the output from the last commands:

```

ls: cannot access '.ICEauthority': No such file or directory
-rw------- 1 celicoo celicoo 0 Out 23 20:41 .Xauthority

```

About the development system.. it isn't.. i download from [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop), 16.04.01 version.

---

### Post by celicoo123 on 2016-10-23
I see my Intel(R) Core(TM) I7-6700HQ CPU @ 2.60GHz enable in the BIOS.

---

### Post by Bashing-om on 2016-10-24
celicoo123; Welp !

I am not getting why the Nvidia installer wants the  xserver-xorg-dev package installed ..presently I am not in a position yet to make an advisement. 

Nor can I imagine why .ICEauthority would not be on your system :
> 
sysop@1404mini:~$ ls -al .ICEauthority .Xauthority
-rw------- 1 sysop sysop 1304 Oct 23 18:28 .ICEauthority
-rw------- 1 sysop sysop  209 Jul 28 15:28 .Xauthority
sysop@1404mini:~$


let's make up that file:
```

touch .ICEauthority # creates blank file with name .ICEauthority
chown celicoo:celicoo .ICEauthority # makes "YOU" owner of the file
chmod 600 .ICEauthority # sets permissions to "-rw-------" (read/write access to owner only)
You don't need to use sudo if you are in the recovery console or if you are logged in as kevin on a virtual terminal (Eg Ctrl+Alt+F1..F3).

```

check your home directory permissions/ownership;
```

ls -ld ../celicoo /home

```
should be :
> 
sysop@1404mini:~$ ls -ld ../sysop /home
drwxr-xr-x  4 root  root  4096 May 19  2013 /home
drwxr-xr-x 29 sysop sysop 4096 Oct 23 18:28 ../sysop
sysop@1404mini:~$

where I am sysop

and now reboot, can you now access the GUI ? 

[INDENT][INDENT]maybe a step forward
[/INDENT][/INDENT]

---

### Post by celicoo123 on 2016-10-24
[COLOR=#212121][FONT=arial]I created the file and the permissions, but it did not work :(.

Maybe my hardware is incompatible?[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-10-24
celicoo123; sad
that it "did not work" .

Just to cover the base; what returns:
```

sudo dkms status

```
to make sure the tools to build the nVidia driver are available.
I do not think it is incompatible hardware . unless this is real new .. skylake is now supported .

I am done for this session we will pick this back up in my morrow - we consider a way forward .


[INDENT][INDENT]got to be a reason why
[/INDENT][/INDENT]

---

### Post by celicoo123 on 2016-10-24
Hei!

This are the outputs:

```

bbwitch, 0.8, 4.4.0-45-generic, x86_64: installed
nvidia-370, 370.28, 4.4.0-45-generic, x86_64: installed

```

Thanks again!!

---

### Post by Bashing-om on 2016-10-24
celicoo123; Hummm ...

The package is present .. that is not the reason for nVida not discovering the screen.
I am, honestly, drawing a blank here as to what could have happened .
A bit of a grasp at straws, but verify the install medium  - as this is a fresh install ?

Boot the installer, and as soon as the bios screen clears depress and hold a shift key ( EFI system spam the escape key) -> language screen - escape key to accept the defaults -> boot options screen .
Here choose " check disk for defects " .
Do you eventually get no errors found or ??

[INDENT][INDENT]I just do not know
[/INDENT][/INDENT]

---

### Post by celicoo123 on 2016-10-24
Yes, this is a fresh install.

No, i didn't get any errors in the check for defects.

I'm starting to believe this is a hardware problem. My computer started having some reboot problems, and today I got in touch with the store I bought and tomorrow they will withdraw and give me a new one ... let's wait and try to install ubuntu in this new one.

---

### Post by Bashing-om on 2016-10-24
celicoo123; Kl

That is one technique on troubleshooting ....

[INDENT][INDENT][INDENT]swap out the hardware 
[/INDENT][/INDENT][/INDENT]

---

### Post by celicoo123 on 2016-10-26
Bashing-om, i'm back with the new machine... and still the same problem is happening. Also, i found some folks with the same problem: [http://askubuntu.com/questions/836239/ubuntu-16-04-doesnt-seem-to-see-my-gtx-1060-gpu](http://askubuntu.com/questions/836239/ubuntu-16-04-doesnt-seem-to-see-my-gtx-1060-gpu)

---

### Post by Bashing-om on 2016-10-26
celicoo123; Ouch !

Mind ya we are getting put of my depth here . A guru of the nVidia driver I am not, just one with a bit of knowledge .

Is the situation same same as before .,.in that the driver will not identify the display ?
show :
```

/var/log/Xorg.0.log
dpkg -l | grep -i nvidia

```

see what
[INDENT][INDENT][INDENT]tale now gets told
[/INDENT][/INDENT][/INDENT]

---

### Post by celicoo123 on 2016-10-26
Same output.I'm giving up... Unfortunately i'm going to use a virtual-box, instead... I'm going to wait 6 months, and then try again... I don't know if this problem will be solved until then... apparently problems like this are normal with NVIDIA :(.Thanks a LOT, anyway!!

---

### Post by Bashing-om on 2016-10-26
celicoo123; Welp;

Can not say I blame you , I wish I could help more .
If it is any consolation ,, I too an having my nVidia problems after switching from ATI .

I am sure the wrinkles will eventually iron out .

[INDENT][INDENT]I hate when this happens
[/INDENT][/INDENT]

---

