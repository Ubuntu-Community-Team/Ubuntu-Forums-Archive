---
title: "Nvidia GeForce GT840M driver issues"
date: 2015-01-27
forum: Hardware
---

### Post by zan-public on 2015-01-27
Hi, I have a brand new HP Envy 17t with a 2GB NVIDIA GeForce GT840M Graphics card. 
Here's the rub, I can't get the nvidia driver to take over. I have installed the nvidia-340 driver from both the ppa: xorg-edgers/ppa and ppa:mamarley/nvidia (separately, purging out the driver and ppa between attempts) but still I get no glory. If I run: 
```
nvidia-settings
``` 
I get: 
```
(nvidia-settings:3858): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no


ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       preopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.



```

I have searched this and the only advice I can find is to install one of those two PPAs, update apt, then install the package... yea, no.
Also, I looked up my card on the nvidia site and they are specifying the 346 driver for it... 

I am lost, confused, and quite frustrated. Can anyone explain what I am doing wrong?

Thank you.

= = = = = 
Also, I did have this working for a couple of days, but then lightdm  failed and wouldn't load, so I uninstalled lightdm, and switched to gdm,  and thought all was well, then I noticed I lost the use of my nvidia  higher functions... Can't seem to figure out what is going on.

---

### Post by startas on 2015-01-28
I have a laptop with same graphics(intel hd + nvidia 840m), some time ago i managed to install 343.xx drivers, but my problem was that nvidia didnt have any vsync, plus 3d stuff was broken, so it was useless. Now, when i tried to install 346.35 newest drivers, ubuntu doesnt even boot, it gets stuck at black screen - its a general linux problem right now, xorg server is broken, linux kernel some new versions are broken (tty doesnt work), plus some other stuff, so i will just leave linux for like another year, its a minimum amount of time required for linux to get at least some things to get moving. I would suggest to do the same, because right now one problem leads to another, and there is no solution, if you are lucky to get everything to work out of the box, then its ok, but if not, then there is nothing you can do.

---

### Post by zan-public on 2015-01-28
Update: A driver update for nvidia-340 came down the pipe on ppa:mamarley/nvidia today. This had no effect on the problem (Problem persists). Should I download the driver from nvidia, and install that? I really don't want to use non managed drivers...

---

### Post by Bashing-om on 2015-01-28
> **startas said:**
> I have a laptop with same graphics(intel hd + nvidia 840m), some time ago i managed to install 343.xx drivers, but my problem was that nvidia didnt have any vsync, plus 3d stuff was broken, so it was useless. Now, when i tried to install 346.35 newest drivers, ubuntu doesnt even boot, it gets stuck at black screen - its a general linux problem right now, xorg server is broken, linux kernel some new versions are broken (tty doesnt work), plus some other stuff, so i will just leave linux for like another year, its a minimum amount of time required for linux to get at least some things to get moving. I would suggest to do the same, because right now one problem leads to another, and there is no solution, if you are lucky to get everything to work out of the box, then its ok, but if not, then there is nothing you can do.

@startas;; Not, not and not.

If the manufactures do not provide code, then it is very demanding and difficult to reverse engineer the interfacing software. Recently Nvidia has provided assistance,

Install the required proprietary driver and then install 'nvidia-prime' to control the graphics sets.

[INDENT][INDENT]if you have the will
[INDENT][INDENT][INDENT]you can make a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aljosa2 on 2015-01-28
hi, combination NVIDIA 346.35 and kernel 3.17.7 is ok for me, with all newer kernels i have the same problem like you.
i still didn't try kernel 3.19-rc6, but here's some good news: "Kernel 3.19-rc6 – Good News for NVIDIA"
[http://rglinuxtech.com/?p=1284](http://rglinuxtech.com/?p=1284)

---

### Post by zan-public on 2015-01-28
> **Bashing-om said:**
> @startas;; Not, not and not.

If the manufactures do not provide code, then it is very demanding and difficult to reverse engineer the interfacing software. Recently Nvidia has provided assistance,

Install the required proprietary driver and then install 'nvidia-prime' to control the graphics sets.
[INDENT][INDENT]if you have the will[INDENT][INDENT][INDENT]you can make a way
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om,

I do have both of these installed and I still cannot get the nvidia driver to take over. Any thoughts?

---

### Post by Bashing-om on 2015-01-28
zan-public; Well ...

Let's see if you DO have the driver loaded .
```

sudo lshw -C display

```
the configuration line in that output will list the driver installed ( if any) .
and while we are at it, see what the hardware is:
```

lspci -nnk | grep -iA3 vga

```

back to the basics
[INDENT][INDENT][INDENT]look and see
[/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-28
> **Bashing-om said:**
> zan-public; Well ...

Let's see if you DO have the driver loaded .
```

sudo lshw -C display

```
the configuration line in that output will list the driver installed ( if any) .
and while we are at it, see what the hardware is:
```

lspci -nnk | grep -iA3 vga

```

back to the basics[INDENT][INDENT][INDENT]look and see
[/INDENT]
[/INDENT]
[/INDENT]


```
sudo lshw -C display
```
gives us:
```
  *-display                      description: 3D controller
       product: GM108M [GeForce 840M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:b5000000-b5ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:6000(size=128)
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:b7000000-b73fffff memory:c0000000-cfffffff ioport:8000(size=64)



```

```
lspci -nnk | grep -iA3 vga
```

Gives us:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:1968]
	Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)



```

---

### Post by Bashing-om on 2015-01-28
zan-public; Well ...

I am sorta at a loss as driver(s) are loaded . The way I read the 'lshw' output, should work .

What can you do in the Nvidia-settings tool ?

[INDENT][INDENT]sometime I do wonder
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-28
Bashing-om,

 I have the "Application Profiles" and "nvidia-settings Configuration" pages listed on the left. 

The big thing is that I do not have the Prime Page that lets me switch to the nvidia driver. 

Also, I noticed that when I run 
```
nvidia-settings
```
and I get:
```
(nvidia-settings:5512): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no


ERROR: nvidia-settings could not find the registry key file. This file should
       have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       preopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.



```

I noticed that the registry key is missing. I read that this might be an issue with the key not being included in the package? Not sure if that helps...

---

### Post by Bashing-om on 2015-01-28
zan-public; Maybe;

Think about reinstalling ? Maybe also a driver conflict ?
What is presently installed ?
```

dpkg -l  | grep nvidia

```

Gotta be a cause
[INDENT][INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-28
> **Bashing-om said:**
> zan-public; Maybe;

Think about reinstalling ? Maybe also a driver conflict ?
What is presently installed ?
```

dpkg -l  | grep nvidia

```

Gotta be a cause[INDENT][INDENT][INDENT]gotta be a reason
[/INDENT]
[/INDENT]
[/INDENT]


```
$ dpkg -l  | grep nvidia
ii  nvidia-340                                            340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-340                                 340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-340                                 340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       346.35-100ubuntu100~ppa0~trusty                        amd64        Tool for configuring the NVIDIA graphics driver



```

---

### Post by Bashing-om on 2015-01-28
zan-public; Hummm .....

From post #1:
> 
Also, I looked up my card on the nvidia site and they are specifying the 346 driver for it... 

As there looks to be a disparity between the 340 driver installed and nvidia-settings (   346.35-100ubuntu100~ppa0~trusty).
Purge the 340 driver and install from the PPA ?
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

[INDENT][INDENT]what I think
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-28
> **Bashing-om said:**
> zan-public; Hummm .....

From post #1:

As there looks to be a disparity between the 340 driver installed and nvidia-settings (   346.35-100ubuntu100~ppa0~trusty).
Purge the 340 driver and install from the PPA ?
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
[INDENT][INDENT]what I think
[/INDENT]
[/INDENT]


So purge out 340 and install 346 or 340 from ppa?

---

### Post by Bashing-om on 2015-01-28
zan-public; Hey;

As that is new hardware ,, I would say purge 340 and install 346 version.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-28
> **Bashing-om said:**
> zan-public; Hey;

As that is new hardware ,, I would say purge 340 and install 346 version.[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


Ok, So:

```

$ dpkg -l  | grep nvidia
ii  nvidia-346                                            346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-346                                 346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-346                                 346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       346.35-100ubuntu100~ppa0~trusty                        amd64        Tool for configuring the NVIDIA graphics driver


```

```

$ nvidia-settings 

(nvidia-settings:3417): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector
** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no


ERROR: nvidia-settings could not find the registry key file. This file should have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The application profiles will continue to work, but values cannot be preopulated or
       validated, and will not be listed in the help text. Please see the README for possible values and descriptions.



```

```

$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:1968]
    Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)



```

```

$ sudo lshw -C display
  *-display               
       description: 3D controller
       product: GM108M [GeForce 840M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:b5000000-b5ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:6000(size=128)
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:b7000000-b73fffff memory:c0000000-cfffffff ioport:8000(size=64)



```

(Still no glory)

---

### Post by Bashing-om on 2015-01-28
zan-public; Honestly, do not know.


But we have:
> 
$ nvidia-settings 

(nvidia-settings:3417): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector
** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no

As we know the driver is installed and it is supported !
maybe try and remove 'nvidia-prime' and re-install ?
```

sudo apt-get remove nvidia-prime
sudo apt-get install nvidia-prime

```

keeping an eye our for any errors the system will relay.

[INDENT][INDENT][INDENT]if at 1st you do not succeed 
[/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-28
> **Bashing-om said:**
> zan-public; Honestly, do not know.


But we have:

As we know the driver is installed and it is supported !
maybe try and remove 'nvidia-prime' and re-install ?
```

sudo apt-get remove nvidia-prime
sudo apt-get install nvidia-prime

```

keeping an eye our for any errors the system will relay.[INDENT][INDENT][INDENT]if at 1st you do not succeed 
[/INDENT]
[/INDENT]
[/INDENT]


```

$ sudo apt-get remove nvidia-prime Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-prime
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 88.1 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 285009 files and directories currently installed.)
Removing nvidia-prime (0.6.2) ...


$ sudo apt-get install nvidia-prime 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-prime
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/11.2 kB of archives.
After this operation, 88.1 kB of additional disk space will be used.
Selecting previously unselected package nvidia-prime.
(Reading database ... 284999 files and directories currently installed.)
Preparing to unpack .../nvidia-prime_0.6.2_amd64.deb ...
Unpacking nvidia-prime (0.6.2) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up nvidia-prime (0.6.2) ...
nvidia-prime start/running, process 4201

$ nvidia-settings 


(nvidia-settings:4293): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector
** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no


ERROR: nvidia-settings could not find the registry key file. This file should have been
       installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The application
       profiles will continue to work, but values cannot be preopulated or validated, and
       will not be listed in the help text. Please see the README for possible values and
       descriptions.




```

Gonna reboot and test. BRB...

---

### Post by zan-public on 2015-01-28
Yea, No change.

---

### Post by Bashing-om on 2015-01-28
zan-public; Yuk .

I am stuck, I do not know what else to advise, presently.

[INDENT][INDENT]I Hate when that happens
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-28
Thanks or trying Bashing-om...

Anyone else?

---

### Post by Bashing-om on 2015-01-28
zan-public; Hey !

No quit in my nature, just back up and regroup .
Make sure that the graphics card is not disabled in bios
And then let's read the log and see what it has to report :
```

cat /var/log/Xorg.0.log

``` Maybe then get a hint of what is not going on.

I am about done for this session, with a fresh mind I will look over the log .

[INDENT][INDENT]back up 3 yards and punt
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-28
> **Bashing-om said:**
> zan-public; Hey !

No quit in my nature, just back up and regroup .
Make sure that the graphics card is not disabled in bios
And then let's read the log and see what it has to report :
```

cat /var/log/Xorg.0.log

``` Maybe then get a hint of what is not going on.

I am about done for this session, with a fresh mind I will look over the log .
[INDENT][INDENT]back up 3 yards and punt
[/INDENT]
[/INDENT]


```
$ cat /var/log/Xorg.0.log[    27.546] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    27.546] X Protocol Version 11, Revision 0
[    27.546] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[    27.546] Current Operating System: Linux Odin 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64
[    27.546] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-44-generic.efi.signed root=UUID=f1544fc7-e2ba-4d6d-b3e4-451064c75b80 ro quiet splash vt.handoff=7
[    27.546] Build Date: 10 December 2014  06:15:52PM
[    27.546] xorg-server 2:1.15.1-0ubuntu2.6 (For technical support please see http://www.ubuntu.com/support) 
[    27.546] Current version of pixman: 0.30.2
[    27.546] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    27.546] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.546] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Jan 28 20:36:02 2015
[    27.676] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.744] (==) No Layout section.  Using the first Screen section.
[    27.744] (==) No screen section available. Using defaults.
[    27.744] (**) |-->Screen "Default Screen Section" (0)
[    27.744] (**) |   |-->Monitor "<default monitor>"
[    27.778] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    27.778] (==) Automatically adding devices
[    27.778] (==) Automatically enabling devices
[    27.778] (==) Automatically adding GPU devices
[    27.863] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.863] 	Entry deleted from font path.
[    27.863] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    27.863] 	Entry deleted from font path.
[    27.863] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    27.863] 	Entry deleted from font path.
[    27.863] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    27.863] 	Entry deleted from font path.
[    27.863] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    27.863] 	Entry deleted from font path.
[    27.863] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    27.863] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    27.863] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    27.863] (II) Loader magic: 0x7ff912281d40
[    27.863] (II) Module ABI versions:
[    27.863] 	X.Org ANSI C Emulation: 0.4
[    27.863] 	X.Org Video Driver: 15.0
[    27.863] 	X.Org XInput driver : 20.0
[    27.863] 	X.Org Server Extension : 8.0
[    27.864] (II) xfree86: Adding drm device (/dev/dri/card1)
[    27.864] (II) xfree86: Adding drm device (/dev/dri/card0)
[    27.865] (--) PCI:*(0:0:2:0) 8086:0416:103c:1968 rev 6, Mem @ 0xb7000000/4194304, 0xc0000000/268435456, I/O @ 0x00008000/64
[    27.865] (--) PCI: (0:7:0:0) 10de:1341:103c:21a1 rev 162, Mem @ 0xb5000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00006000/128
[    27.919] Initializing built-in extension Generic Event Extension
[    27.919] Initializing built-in extension SHAPE
[    27.919] Initializing built-in extension MIT-SHM
[    27.919] Initializing built-in extension XInputExtension
[    27.919] Initializing built-in extension XTEST
[    27.919] Initializing built-in extension BIG-REQUESTS
[    27.919] Initializing built-in extension SYNC
[    27.919] Initializing built-in extension XKEYBOARD
[    27.920] Initializing built-in extension XC-MISC
[    27.920] Initializing built-in extension SECURITY
[    27.920] Initializing built-in extension XINERAMA
[    27.920] Initializing built-in extension XFIXES
[    27.920] Initializing built-in extension RENDER
[    27.920] Initializing built-in extension RANDR
[    27.920] Initializing built-in extension COMPOSITE
[    27.920] Initializing built-in extension DAMAGE
[    27.920] Initializing built-in extension MIT-SCREEN-SAVER
[    27.920] Initializing built-in extension DOUBLE-BUFFER
[    27.920] Initializing built-in extension RECORD
[    27.920] Initializing built-in extension DPMS
[    27.920] Initializing built-in extension Present
[    27.920] Initializing built-in extension DRI3
[    27.920] Initializing built-in extension X-Resource
[    27.920] Initializing built-in extension XVideo
[    27.920] Initializing built-in extension XVideo-MotionCompensation
[    27.920] Initializing built-in extension SELinux
[    27.920] Initializing built-in extension XFree86-VidModeExtension
[    27.920] Initializing built-in extension XFree86-DGA
[    27.920] Initializing built-in extension XFree86-DRI
[    27.920] Initializing built-in extension DRI2
[    27.920] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    27.920] (II) "glx" will be loaded by default.
[    27.920] (WW) "xmir" is not to be loaded by default. Skipping.
[    27.920] (II) LoadModule: "glx"
[    28.382] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    29.104] (II) Module glx: vendor="X.Org Foundation"
[    29.104] 	compiled for 1.15.1, module version = 1.0.0
[    29.104] 	ABI class: X.Org Server Extension, version 8.0
[    29.104] (==) AIGLX enabled
[    29.104] Loading extension GLX
[    29.104] (==) Matched intel as autoconfigured driver 0
[    29.104] (==) Matched nvidia as autoconfigured driver 1
[    29.104] (==) Matched nouveau as autoconfigured driver 2
[    29.104] (==) Matched intel as autoconfigured driver 3
[    29.104] (==) Matched modesetting as autoconfigured driver 4
[    29.104] (==) Matched fbdev as autoconfigured driver 5
[    29.104] (==) Matched vesa as autoconfigured driver 6
[    29.104] (==) Assigned the driver to the xf86ConfigLayout
[    29.104] (II) LoadModule: "intel"
[    29.104] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    29.178] (II) Module intel: vendor="X.Org Foundation"
[    29.178] 	compiled for 1.15.1, module version = 2.99.917
[    29.178] 	Module class: X.Org Video Driver
[    29.178] 	ABI class: X.Org Video Driver, version 15.0
[    29.178] (II) LoadModule: "nvidia"
[    29.179] (WW) Warning, couldn't open module nvidia
[    29.179] (II) UnloadModule: "nvidia"
[    29.179] (II) Unloading nvidia
[    29.179] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    29.179] (II) LoadModule: "nouveau"
[    29.179] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    29.263] (II) Module nouveau: vendor="X.Org Foundation"
[    29.263] 	compiled for 1.15.1, module version = 1.0.11
[    29.263] 	Module class: X.Org Video Driver
[    29.263] 	ABI class: X.Org Video Driver, version 15.0
[    29.263] (II) LoadModule: "modesetting"
[    29.263] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    29.297] (II) Module modesetting: vendor="X.Org Foundation"
[    29.297] 	compiled for 1.15.0, module version = 0.8.1
[    29.297] 	Module class: X.Org Video Driver
[    29.297] 	ABI class: X.Org Video Driver, version 15.0
[    29.297] (II) LoadModule: "fbdev"
[    29.298] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.302] (II) Module fbdev: vendor="X.Org Foundation"
[    29.302] 	compiled for 1.15.0, module version = 0.4.4
[    29.302] 	Module class: X.Org Video Driver
[    29.302] 	ABI class: X.Org Video Driver, version 15.0
[    29.302] (II) LoadModule: "vesa"
[    29.303] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.313] (II) Module vesa: vendor="X.Org Foundation"
[    29.313] 	compiled for 1.15.0, module version = 2.3.3
[    29.313] 	Module class: X.Org Video Driver
[    29.313] 	ABI class: X.Org Video Driver, version 15.0
[    29.313] (==) Matched intel as autoconfigured driver 0
[    29.314] (==) Matched nvidia as autoconfigured driver 1
[    29.314] (==) Matched nouveau as autoconfigured driver 2
[    29.314] (==) Matched intel as autoconfigured driver 3
[    29.314] (==) Matched modesetting as autoconfigured driver 4
[    29.314] (==) Matched fbdev as autoconfigured driver 5
[    29.314] (==) Matched vesa as autoconfigured driver 6
[    29.314] (==) Assigned the driver to the xf86ConfigLayout
[    29.314] (II) LoadModule: "intel"
[    29.314] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    29.314] (II) Module intel: vendor="X.Org Foundation"
[    29.314] 	compiled for 1.15.1, module version = 2.99.917
[    29.314] 	Module class: X.Org Video Driver
[    29.314] 	ABI class: X.Org Video Driver, version 15.0
[    29.314] (II) UnloadModule: "intel"
[    29.314] (II) Unloading intel
[    29.314] (II) Failed to load module "intel" (already loaded, 32761)
[    29.314] (II) LoadModule: "nvidia"
[    29.314] (WW) Warning, couldn't open module nvidia
[    29.314] (II) UnloadModule: "nvidia"
[    29.314] (II) Unloading nvidia
[    29.314] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    29.314] (II) LoadModule: "nouveau"
[    29.314] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    29.314] (II) Module nouveau: vendor="X.Org Foundation"
[    29.314] 	compiled for 1.15.1, module version = 1.0.11
[    29.314] 	Module class: X.Org Video Driver
[    29.314] 	ABI class: X.Org Video Driver, version 15.0
[    29.314] (II) UnloadModule: "nouveau"
[    29.314] (II) Unloading nouveau
[    29.314] (II) Failed to load module "nouveau" (already loaded, 0)
[    29.314] (II) LoadModule: "modesetting"
[    29.314] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    29.314] (II) Module modesetting: vendor="X.Org Foundation"
[    29.314] 	compiled for 1.15.0, module version = 0.8.1
[    29.314] 	Module class: X.Org Video Driver
[    29.314] 	ABI class: X.Org Video Driver, version 15.0
[    29.314] (II) UnloadModule: "modesetting"
[    29.314] (II) Unloading modesetting
[    29.314] (II) Failed to load module "modesetting" (already loaded, 0)
[    29.314] (II) LoadModule: "fbdev"
[    29.314] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.314] (II) Module fbdev: vendor="X.Org Foundation"
[    29.314] 	compiled for 1.15.0, module version = 0.4.4
[    29.314] 	Module class: X.Org Video Driver
[    29.314] 	ABI class: X.Org Video Driver, version 15.0
[    29.315] (II) UnloadModule: "fbdev"
[    29.315] (II) Unloading fbdev
[    29.315] (II) Failed to load module "fbdev" (already loaded, 0)
[    29.315] (II) LoadModule: "vesa"
[    29.315] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.315] (II) Module vesa: vendor="X.Org Foundation"
[    29.315] 	compiled for 1.15.0, module version = 2.3.3
[    29.315] 	Module class: X.Org Video Driver
[    29.315] 	ABI class: X.Org Video Driver, version 15.0
[    29.315] (II) UnloadModule: "vesa"
[    29.315] (II) Unloading vesa
[    29.315] (II) Failed to load module "vesa" (already loaded, 0)
[    29.315] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    29.315] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    29.315] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    29.315] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    29.315] (II) NOUVEAU driver 
[    29.315] (II) NOUVEAU driver for NVIDIA chipset families :
[    29.315] 	RIVA TNT        (NV04)
[    29.315] 	RIVA TNT2       (NV05)
[    29.315] 	GeForce 256     (NV10)
[    29.315] 	GeForce 2       (NV11, NV15)
[    29.315] 	GeForce 4MX     (NV17, NV18)
[    29.315] 	GeForce 3       (NV20)
[    29.315] 	GeForce 4Ti     (NV25, NV28)
[    29.315] 	GeForce FX      (NV3x)
[    29.315] 	GeForce 6       (NV4x)
[    29.315] 	GeForce 7       (G7x)
[    29.315] 	GeForce 8       (G8x)
[    29.315] 	GeForce GTX 200 (NVA0)
[    29.315] 	GeForce GTX 400 (NVC0)
[    29.315] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    29.315] (II) FBDEV: driver for framebuffer: fbdev
[    29.315] (II) VESA: driver for VESA chipsets: vesa
[    29.315] (++) using VT number 7


[    29.361] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    29.361] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150127.4bbd1023-0ubuntu0sarvatt~trusty (Robert Hooker <sarvatt@ubuntu.com>)
[    29.361] (II) intel(0): SNA compiled for use with valgrind
[    29.370] (EE) [drm] KMS not enabled
[    29.370] (WW) Falling back to old probe method for modesetting
[    29.370] (WW) Falling back to old probe method for fbdev
[    29.370] (II) Loading sub module "fbdevhw"
[    29.370] (II) LoadModule: "fbdevhw"
[    29.370] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.391] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.391] 	compiled for 1.15.1, module version = 0.0.2
[    29.391] 	ABI class: X.Org Video Driver, version 15.0
[    29.391] (WW) Falling back to old probe method for vesa
[    29.438] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    29.438] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[    29.438] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    29.438] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    29.438] (==) intel(0): RGB weight 888
[    29.438] (==) intel(0): Default visual is TrueColor
[    29.438] (II) intel(0): Output eDP1 has no monitor section
[    29.438] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output eDP1
[    29.438] (II) intel(0): Enabled output eDP1
[    29.438] (II) intel(0): Output VGA1 has no monitor section
[    29.438] (II) intel(0): Enabled output VGA1
[    29.438] (II) intel(0): Output HDMI1 has no monitor section
[    29.438] (II) intel(0): Enabled output HDMI1
[    29.438] (--) intel(0): Using a maximum size of 64x64 for hardware cursors
[    29.438] (II) intel(0): Output VIRTUAL1 has no monitor section
[    29.438] (II) intel(0): Enabled output VIRTUAL1
[    29.438] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[    29.438] (==) intel(0): TearFree disabled
[    29.438] (==) intel(0): DPI set to (96, 96)
[    29.438] (II) Loading sub module "dri2"
[    29.438] (II) LoadModule: "dri2"
[    29.438] (II) Module "dri2" already built-in
[    29.438] (II) Loading sub module "present"
[    29.438] (II) LoadModule: "present"
[    29.439] (WW) Warning, couldn't open module present
[    29.439] (II) UnloadModule: "present"
[    29.439] (II) Unloading present
[    29.439] (EE) intel: Failed to load module "present" (module does not exist, 0)
[    29.440] (II) UnloadModule: "fbdev"
[    29.440] (II) Unloading fbdev
[    29.440] (II) UnloadSubModule: "fbdevhw"
[    29.440] (II) Unloading fbdevhw
[    29.440] (II) UnloadModule: "vesa"
[    29.440] (II) Unloading vesa
[    29.440] (==) Depth 24 pixmap format is 32 bpp
[    29.599] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    29.599] (==) intel(0): Backing store enabled
[    29.599] (==) intel(0): Silken mouse enabled
[    29.600] (II) intel(0): HW Cursor enabled
[    29.600] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    29.639] (==) intel(0): DPMS enabled
[    29.639] (==) intel(0): Display hotplug detection enabled
[    29.639] (II) intel(0): [DRI2] Setup complete
[    29.639] (II) intel(0): [DRI2]   DRI driver: i965
[    29.639] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    29.639] (II) intel(0): direct rendering: DRI2 enabled
[    29.639] (--) RandR disabled
[    29.645] (II) SELinux: Disabled on system
[    30.261] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    30.261] (II) AIGLX: enabled GLX_ARB_create_context
[    30.261] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    30.261] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    30.261] (II) AIGLX: enabled GLX_INTEL_swap_event
[    30.261] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    30.261] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    30.261] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    30.261] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    30.261] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    30.261] (II) AIGLX: Loaded and initialized i965
[    30.261] (II) GLX: Initialized DRI2 GL provider for screen 0
[    30.452] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    30.452] (II) intel(0): Setting screen physical size to 508 x 285
[    30.851] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.862] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    30.862] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.862] (II) LoadModule: "evdev"
[    30.862] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.947] (II) Module evdev: vendor="X.Org Foundation"
[    30.947] 	compiled for 1.15.0, module version = 2.8.2
[    30.947] 	Module class: X.Org XInput Driver
[    30.947] 	ABI class: X.Org XInput driver, version 20.0
[    30.947] (II) Using input driver 'evdev' for 'Power Button'
[    30.947] (**) Power Button: always reports core events
[    30.947] (**) evdev: Power Button: Device: "/dev/input/event2"
[    30.947] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.947] (--) evdev: Power Button: Found keys
[    30.947] (II) evdev: Power Button: Configuring as keyboard
[    30.947] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    30.947] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    30.947] (**) Option "xkb_rules" "evdev"
[    30.947] (**) Option "xkb_model" "pc105"
[    30.947] (**) Option "xkb_layout" "us"
[    30.948] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    30.948] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    30.948] (II) Using input driver 'evdev' for 'Video Bus'
[    30.948] (**) Video Bus: always reports core events
[    30.948] (**) evdev: Video Bus: Device: "/dev/input/event9"
[    30.948] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    30.948] (--) evdev: Video Bus: Found keys
[    30.948] (II) evdev: Video Bus: Configuring as keyboard
[    30.948] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input10/event9"
[    30.948] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    30.948] (**) Option "xkb_rules" "evdev"
[    30.948] (**) Option "xkb_model" "pc105"
[    30.948] (**) Option "xkb_layout" "us"
[    30.948] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    30.948] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    30.948] (II) Using input driver 'evdev' for 'Video Bus'
[    30.948] (**) Video Bus: always reports core events
[    30.948] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    30.948] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    30.948] (--) evdev: Video Bus: Found keys
[    30.948] (II) evdev: Video Bus: Configuring as keyboard
[    30.948] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:44/LNXVIDEO:00/input/input9/event8"
[    30.948] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    30.948] (**) Option "xkb_rules" "evdev"
[    30.948] (**) Option "xkb_model" "pc105"
[    30.948] (**) Option "xkb_layout" "us"
[    30.948] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    30.948] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.948] (II) Using input driver 'evdev' for 'Power Button'
[    30.948] (**) Power Button: always reports core events
[    30.948] (**) evdev: Power Button: Device: "/dev/input/event1"
[    30.948] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.948] (--) evdev: Power Button: Found keys
[    30.948] (II) evdev: Power Button: Configuring as keyboard
[    30.948] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    30.948] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    30.948] (**) Option "xkb_rules" "evdev"
[    30.948] (**) Option "xkb_model" "pc105"
[    30.948] (**) Option "xkb_layout" "us"
[    30.949] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    30.949] (II) No input driver specified, ignoring this device.
[    30.949] (II) This device may have been added with another device file.
[    30.949] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:01.1/0000:07:00.0/drm/card1
[    30.949] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[    30.949] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    30.949] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    30.949] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event12)
[    30.949] (II) No input driver specified, ignoring this device.
[    30.949] (II) This device may have been added with another device file.
[    30.949] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event11)
[    30.949] (II) No input driver specified, ignoring this device.
[    30.949] (II) This device may have been added with another device file.
[    30.949] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event10)
[    30.949] (II) No input driver specified, ignoring this device.
[    30.949] (II) This device may have been added with another device file.
[    30.949] (II) config/udev: Adding input device eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00 (/dev/input/event15)
[    30.949] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Applying InputClass "evdev touchscreen catchall"
[    30.949] (II) Using input driver 'evdev' for 'eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00'
[    30.949] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: always reports core events
[    30.949] (**) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Device: "/dev/input/event15"
[    30.949] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Using mtdev for this device
[    30.949] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Vendor 0xeef Product 0xa80f
[    30.949] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found absolute axes
[    30.949] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found absolute multitouch axes
[    30.949] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: No buttons found, faking one.
[    30.949] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found x and y absolute axes
[    30.949] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found absolute touchscreen
[    30.949] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Configuring as touchscreen
[    30.950] (**) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: YAxisMapping: buttons 4 and 5
[    30.950] (**) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    30.950] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-13/2-13:1.0/input/input16/event15"
[    30.950] (II) XINPUT: Adding extended input device "eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00" (type: TOUCHSCREEN, id 10)
[    30.950] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: initialized for absolute axes.
[    30.950] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) keeping acceleration scheme 1
[    30.950] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) acceleration profile 0
[    30.950] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) acceleration factor: 2.000
[    30.950] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) acceleration threshold: 4
[    30.950] (II) config/udev: Adding input device eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00 (/dev/input/mouse1)
[    30.950] (II) No input driver specified, ignoring this device.
[    30.950] (II) This device may have been added with another device file.
[    30.950] (II) config/udev: Adding input device HP Truevision HD (/dev/input/event16)
[    30.950] (**) HP Truevision HD: Applying InputClass "evdev keyboard catchall"
[    30.950] (II) Using input driver 'evdev' for 'HP Truevision HD'
[    30.950] (**) HP Truevision HD: always reports core events
[    30.950] (**) evdev: HP Truevision HD: Device: "/dev/input/event16"
[    30.950] (--) evdev: HP Truevision HD: Vendor 0x64e Product 0xc341
[    30.950] (--) evdev: HP Truevision HD: Found keys
[    30.950] (II) evdev: HP Truevision HD: Configuring as keyboard
[    30.950] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-7/2-7:1.0/input/input18/event16"
[    30.950] (II) XINPUT: Adding extended input device "HP Truevision HD" (type: KEYBOARD, id 11)
[    30.950] (**) Option "xkb_rules" "evdev"
[    30.950] (**) Option "xkb_model" "pc105"
[    30.950] (**) Option "xkb_layout" "us"
[    30.950] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event14)
[    30.950] (II) No input driver specified, ignoring this device.
[    30.950] (II) This device may have been added with another device file.
[    30.950] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event13)
[    30.950] (II) No input driver specified, ignoring this device.
[    30.950] (II) This device may have been added with another device file.
[    30.951] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    30.951] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    30.951] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    30.951] (**) AT Translated Set 2 keyboard: always reports core events
[    30.951] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    30.951] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    30.951] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    30.951] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    30.951] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    30.951] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    30.951] (**) Option "xkb_rules" "evdev"
[    30.951] (**) Option "xkb_model" "pc105"
[    30.951] (**) Option "xkb_layout" "us"
[    30.951] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[    30.951] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    30.951] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    30.951] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    30.951] (II) LoadModule: "synaptics"
[    30.951] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.974] (II) Module synaptics: vendor="X.Org Foundation"
[    30.974] 	compiled for 1.15.0, module version = 1.7.4
[    30.974] 	Module class: X.Org XInput Driver
[    30.974] 	ABI class: X.Org XInput driver, version 20.0
[    30.974] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    30.974] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    30.974] (**) Option "Device" "/dev/input/event4"
[    30.988] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    30.988] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5660 (res 41)
[    30.988] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4702 (res 56)
[    30.988] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    30.988] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    30.988] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    30.988] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    30.988] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    30.988] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    30.988] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    31.000] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[    31.000] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[    31.000] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    31.000] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    31.000] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[    31.000] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    31.000] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    31.000] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    31.000] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    31.000] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    31.000] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    31.000] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    31.000] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[    31.000] (II) No input driver specified, ignoring this device.
[    31.000] (II) This device may have been added with another device file.
[    31.000] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    31.000] (II) No input driver specified, ignoring this device.
[    31.000] (II) This device may have been added with another device file.
[    31.001] (II) config/udev: Adding input device HP Wireless hotkeys (/dev/input/event5)
[    31.001] (**) HP Wireless hotkeys: Applying InputClass "evdev keyboard catchall"
[    31.001] (II) Using input driver 'evdev' for 'HP Wireless hotkeys'
[    31.001] (**) HP Wireless hotkeys: always reports core events
[    31.001] (**) evdev: HP Wireless hotkeys: Device: "/dev/input/event5"
[    31.001] (--) evdev: HP Wireless hotkeys: Vendor 0 Product 0
[    31.001] (--) evdev: HP Wireless hotkeys: Found keys
[    31.001] (II) evdev: HP Wireless hotkeys: Configuring as keyboard
[    31.001] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event5"
[    31.001] (II) XINPUT: Adding extended input device "HP Wireless hotkeys" (type: KEYBOARD, id 14)
[    31.001] (**) Option "xkb_rules" "evdev"
[    31.001] (**) Option "xkb_model" "pc105"
[    31.001] (**) Option "xkb_layout" "us"
[    31.002] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[    31.002] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    31.002] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    31.002] (**) HP WMI hotkeys: always reports core events
[    31.002] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event7"
[    31.002] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    31.002] (--) evdev: HP WMI hotkeys: Found keys
[    31.002] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    31.002] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event7"
[    31.002] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 15)
[    31.002] (**) Option "xkb_rules" "evdev"
[    31.002] (**) Option "xkb_model" "pc105"
[    31.002] (**) Option "xkb_layout" "us"
[    34.829] (II) intel(0): EDID vendor "AUO", prod id 8605
[    34.829] (II) intel(0): Printing DDC gathered Modelines:
[    34.829] (II) intel(0): Modeline "1920x1080"x0.0  140.50  1920 1968 2068 2104  1080 1083 1089 1112 -hsync -vsync (66.8 kHz eP)
[    34.829] (II) intel(0): Modeline "1920x1080"x0.0   93.67  1920 1968 2068 2104  1080 1083 1089 1112 -hsync -vsync (44.5 kHz e)
[    38.492] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    39.080] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    39.082] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    39.083] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    40.268] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    40.498] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    41.988] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    41.991] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    41.994] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    42.015] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    49.189] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/mouse2)
[    49.189] (II) No input driver specified, ignoring this device.
[    49.189] (II) This device may have been added with another device file.
[    49.189] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/event17)
[    49.189] (**) Logitech Unifying Device. Wireless PID:101a: Applying InputClass "evdev pointer catchall"
[    49.189] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101a'
[    49.189] (**) Logitech Unifying Device. Wireless PID:101a: always reports core events
[    49.189] (**) evdev: Logitech Unifying Device. Wireless PID:101a: Device: "/dev/input/event17"
[    49.189] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Vendor 0x46d Product 0xc52b
[    49.189] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found 20 mouse buttons
[    49.189] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found scroll wheel(s)
[    49.189] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found relative axes
[    49.189] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found x and y relative axes
[    49.190] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Configuring as mouse
[    49.190] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Adding scrollwheel support
[    49.190] (**) evdev: Logitech Unifying Device. Wireless PID:101a: YAxisMapping: buttons 4 and 5
[    49.190] (**) evdev: Logitech Unifying Device. Wireless PID:101a: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    49.190] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.2/0003:046D:C52B.0003/input/input19/event17"
[    49.190] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101a" (type: MOUSE, id 16)
[    49.190] (II) evdev: Logitech Unifying Device. Wireless PID:101a: initialized for relative axes.
[    49.190] (**) Logitech Unifying Device. Wireless PID:101a: (accel) keeping acceleration scheme 1
[    49.190] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration profile 0
[    49.190] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration factor: 2.000
[    49.190] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration threshold: 4
[    50.936] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    58.224] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    60.633] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    60.639] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    70.946] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm



```

---

### Post by startas on 2015-01-29
Well, i will install ubuntu later, as i still need linux for some stuff, so i will try these repositories with 346 drivers as i have same hardware. Of course, i will install ubuntu 15.04.

---

### Post by SeijiSensei on 2015-01-29
Can you disable the Intel adapter entirely in the BIOS?  Some laptops like Lenovos also have a physical switch to force using the NVIDIA card.  Any such choices on your machine?

If you run "lsmod" do you see the i915 driver installed, or the nvidia one?

---

### Post by zan-public on 2015-01-29
There does not seem to be any bios controls for video cards on this machine.
```
$ lsmod | grep "i915"
i915                  784207  6 
drm_kms_helper         55071  1 i915
drm                   303102  6 i915,drm_kms_helper,nvidia
i2c_algo_bit           13413  1 i915
video                  19476  1 i915



```

---

### Post by Bashing-om on 2015-01-29
zan-public; More here (Xorg) than meets my eye.

@SeijiSensei; Glad ya joined the thread, I am stuck .

@startas; Great, let us know how it goes with you.

zan-public; From the log, here is what is blowing things away:

> 
Nvidia:
#The hardware is recognized. But then ->
# a driver is made available:
Matched nvidia as autoconfigured driver 1
29.179] (WW) Warning, couldn't open module nvidia
[    29.179] (II) UnloadModule: "nvidia"
[    29.179] (II) Unloading nvidia
29.179] (II) Unloading nvidia
#open source driver does not see the hardware :
(II) NOUVEAU driver for NVIDIA chipset families :
[    29.315] 	RIVA TNT        (NV04)
[    29.315] 	RIVA TNT2       (NV05)
[    29.315] 	GeForce 256     (NV10)
[    29.315] 	GeForce 2       (NV11, NV15)
[    29.315] 	GeForce 4MX     (NV17, NV18)
[    29.315] 	GeForce 3       (NV20)
[    29.315] 	GeForce 4Ti     (NV25, NV28)
[    29.315] 	GeForce FX      (NV3x)
[    29.315] 	GeForce 6       (NV4x)
[    29.315] 	GeForce 7       (G7x)
[    29.315] 	GeForce 8       (G8x)
[    29.315] 	GeForce GTX 200 (NVA0)
[    29.315] 	GeForce GTX 400 (NVC0)

Intel:
#The system advises using the i915 driver, But ;
(WW) Warning, couldn't open module present
[    29.439] (II) UnloadModule: "present"
[    29.439] (II) Unloading present
[    29.439] (EE) intel: Failed to load module "present" (module does not exist, 0)
29.639] (II) intel(0): [DRI2] Setup complete
[    29.639] (II) intel(0): [DRI2]   DRI driver: i965
[    29.639] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    29.639] (II) intel(0): direct rendering: DRI2 enabled


I fail to understand what is taking place here, or how these circumstances can come about.

Is the 'GT840M' Graphics set so new that even the PPA has not caught up ? Maybe we (ubuntu) do not have a driver in our tool box ?

As I scratch my head
[INDENT][INDENT][INDENT]what to do, Oh what to do
[/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-29
I am considering doing a wipe and re-install (I hate doing that) only because there has been so much going on with this that I am not even sure what all has been done now. Thoughts?

---

### Post by startas on 2015-01-29
Nope, nothing, just black screen, tried both drivers via ppa and via nvidia site.

---

### Post by Bashing-om on 2015-01-29
@zan-public; Welp;

If all that you have amiss is the graphics, I can not see how a (RE-)install will benefit us. I would expect the same situation to persist.
However, I could be in error - IF it is no big deal (" re-install (I hate doing that)" one can try and see if there is a better result. 
In the meantime I am doing a bit of homework/research see what I can find to answer my questions.

@startas ; Well ...

Have you tried booting up with the "nomodeset" boot parameter ? And once at the - degraded - GUI try and install a driver :
```

sudo apt-get update
sudo apt-get upgrade
sudo add-apt-repository ppa:mamarley/nvidia
sudo apt-get update
sudo apt-get install nvidia-346
sudo apt-get install nvidia-prime

```

This is assuming that you are running hybrid graphics Intel/Nvidia and the Nvidia card is latest -such that there is no driver available in the software repository - .

[INDENT][INDENT]quitters never win
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-29
> **Bashing-om said:**
> @zan-public; Welp;

If all that you have amiss is the graphics, I can not see how a (RE-)install will benefit us. I would expect the same situation to persist.
However, I could be in error - IF it is no big deal (" re-install (I hate doing that)" one can try and see if there is a better result. 
In the meantime I am doing a bit of homework/research see what I can find to answer my questions.[INDENT][INDENT]
[/INDENT]
[/INDENT]



@Bashing-om, I think you are likely right. I will hold off. In the mean time, I will load up a parallel distro of mint (I have projects that need to be worked on, and I need higher graphic power to get it done) and see if that works.

---

### Post by Bashing-om on 2015-01-29
zan-public; Hey ;

Sounds like a plan to me . ( I also multi boot, If I break one I have another to go to).
To aid my thought process do you have 'nvidia-settings' installed ( by default ?) ?
```

dpkg -l nvidia-settings

```

Edit: dkms ?
```

dpkg -l dkms

```

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-29
> **Bashing-om said:**
> zan-public; Hey ;

Sounds like a plan to me . ( I also multi boot, If I break one I have another to go to).
To aid my thought process do you have 'nvidia-settings' installed ( by default ?) ?
```

dpkg -l nvidia-settings

```

Edit: dkms ?
```

dpkg -l dkms

```[INDENT][INDENT]which way did he go, George
[/INDENT]
[/INDENT]


nvidia-settings is installed and comes in when the driver package is installed.
```
$ dpkg -l nvidia-settings
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version            Architecture       Description
+++-===========================-==================-==================-============================================================
ii  nvidia-settings             346.35-100ubuntu10 amd64              Tool for configuring the NVIDIA graphics driver
```

```
$ dpkg -l dkms
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version            Architecture       Description
+++-===========================-==================-==================-============================================================
ii  dkms                        2.2.0.3-1.1ubuntu5 all                Dynamic Kernel Module Support Framework



```

---

### Post by Bashing-om on 2015-01-29
zan-public; Shheessshh ;

All is in-place -> should workie, but does not !
I am at a loss here. I am going to ask a compatriot to join in here, see what he can come up with.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-29
@Bashing-om, WE HAVE MOVEMENT... but not quite there:

I remembered that when this did work, it was running with lightdm installed. I thought maybe if I could reinstall lightdm and have it work, maybe nvidia would come back... well, lightdm did not work, so left it installed and put gdm on point... Then something promising happened... the Prime tab in nvidia-settings came back up!... but when you try to select the nvidia card it gives you an error that just reads as: "ERROR: " So yea... no. But then I thought "Hey, I was running 340 when this last worked..." So I swapped out the 346 driver for the older 340 driver and... Nope, still no go. But hey, the Prime options weren't even there before, but now they are back... Does lightdm somehow play a major role in nvidia-prime? what am I not understanding?

---

### Post by Bashing-om on 2015-01-29
zan-public; Well, yeah .

lightdm and GDM are 'display managers' and so yes will have a lot to do with how the hardware and kernel interface.
What I am not is a proponent of mixing display managers - as we see here can lead to conflicts.
In a condition of conflict of the DM's I have yet to find a good way to resolve.

I have left a contact request with a compatriot, let's see what he has to advise.

When you do not know
Ask -> the great thing about ubuntu

---

### Post by startas on 2015-01-29
Its official - some new updates totaly broke nvidia graphics, because just 2 months ago nvidia drivers worked, it had many issues, bugs and so on, but at least it installed and ubuntu could start, and now ubuntu doesnt even start with nvidia.

---

### Post by Bashing-om on 2015-01-29
startas; Yep;

3rd party software is not under the auspices of ubuntu's software management system . It is outside and is the responsibility of the authors and YOU to maintain that software.

When an update to the system is done it often breaks what the 3rd party author "DID" then . What one has to do now is re-install the driver . Now maybe there is continued support ... but, maybe not ( in some rare cases). All you can do is re-install the driver and hope for the best.

[INDENT][INDENT]there are ways
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-29
Great, mint won't start on live, so I can't install it without getting all techie on it... If I was prepared to do that, I'd just use Arch... Guess I'll just have to wait...

---

### Post by Bashing-om on 2015-01-29
zan-public; Well !

Dual boot with Xubuntu 14.04 ? (different DM) .

[INDENT][INDENT]meanwhile back at the ranch
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-29
@Bashing-om, Great suggestion, I am up and running on Xubuntu and I have Nvidia 346 fully functional! I will work on here until we can sort this out. :-D

---

### Post by Bashing-om on 2015-01-29
zan-public; Hey hey !

Looks like we are on the right track .. and pointing to a DM issue .
In that light .. 
```

cat .xsession-errors

```

Maybe get a bit more info.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-29
> **Bashing-om said:**
> zan-public; Hey hey !

Looks like we are on the right track .. and pointing to a DM issue .
In that light .. 
```

cat .xsession-errors

```

Maybe get a bit more info.[INDENT][INDENT]inquiring minds want to know
[/INDENT]
[/INDENT]


```
$ cat .xsession-errors
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: unity-settings-daemon main process ended, respawning
init: hud main process (2242) terminated with status 1
init: gnome-session (Unity) main process (2248) terminated with status 1
init: unity-panel-service main process (2262) terminated with status 1
init: indicator-printers main process (2300) terminated with status 1
init: indicator-bluetooth main process (2288) killed by TERM signal
init: indicator-power main process (2290) killed by TERM signal
init: indicator-session main process (2313) killed by TERM signal
init: indicator-datetime main process (2295) killed by TERM signal
init: unity-settings-daemon main process (3702) terminated with status 1
init: indicator-application main process (2314) killed by TERM signal
init: Disconnected from notified D-Bus bus
Xsession: X session started for zanahade at Tue Jan 27 10:44:59 PST 2015
localuser:zanahade being added to access control list
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
x-session-manager[2148]: WARNING: Could not parse desktop file fingerprint-polkit-agent.desktop or it references a not found TryExec binary
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-mfg4Vx
SSH_AUTH_SOCK=/run/user/1000/keyring-mfg4Vx/ssh
GNOME_KEYRING_PID=2334
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-mfg4Vx
SSH_AUTH_SOCK=/run/user/1000/keyring-mfg4Vx/ssh
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-mfg4Vx
SSH_AUTH_SOCK=/run/user/1000/keyring-mfg4Vx/ssh
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-mfg4Vx
SSH_AUTH_SOCK=/run/user/1000/keyring-mfg4Vx/ssh
GPG_AGENT_INFO=/run/user/1000/keyring-mfg4Vx/gpg:0:1


(unity-settings-daemon:2337): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector
x-session-manager[2148]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector


(unity-settings-daemon:2337): color-plugin-WARNING **: no xrandr-AU Optronics device found: Failed to find output xrandr-AU Optronics
x-session-manager[2148]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector


(unity-settings-daemon:2337): color-plugin-WARNING **: failed to obtain org.freedesktop.color-manager.create-profile auth


(unity-settings-daemon:2337): AccountsService-WARNING **: SetInputSources call failed: GDBus.Error:org.freedesktop.Accounts.Error.PermissionDenied: Not authorized
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp


(nm-applet:2395): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector


(indicator-printers-service:2400): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector
initctl: UPSTART_SESSION isn't set in the environment. Unable to locate the Upstart instance.


(polkit-gnome-authentication-agent-1:2403): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector


** (process:2401): CRITICAL **: volume_control_set_volume_internal: assertion '_tmp1_ == PA_CONTEXT_READY' failed


** (process:2401): CRITICAL **: file /build/buildd/indicator-sound-12.10.2+14.04.20140401/obj-x86_64-linux-gnu/src/volume-control.c: line 1775: uncaught error: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: No such interface (g-dbus-error-quark, 16)


** (process:2461): WARNING **: killswitch.vala:103: Can't open /dev/rfkill for use as a killswitch backend: Permission denied
compiz (core) - Info: Loading plugin: composite


** (process:2461): CRITICAL **: bluez.vala:104: GDBus.Error:org.bluez.Error.NoSuchAdapter: No such adapter


(unity-fallback-mount-helper:2432): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl


(nvidia-settings:2460): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector
compiz (core) - Info: Starting plugin: opengl
Compiz (opengl) - Info: GLX_EXT_buffer_age is supported
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor


(nautilus:2413): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/zanahade/.compiz/session/1030b33b4e4058cda142238430720343000000021480001"
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (core) - Warn: Attempted to restack relative to 0x2600186 which is not a child of the root window or a window compiz owns


(gnome-user-share:2588): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector


(telepathy-indicator:2591): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector


(zeitgeist-datahub:2609): GLib-GObject-WARNING **: invalid (NULL) pointer instance


(zeitgeist-datahub:2609): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed


** (zeitgeist-datahub:2609): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/Downloads/raspberry_pi_nes_console_case.gcode" was not found, exec: python, mime_type: application/octet-stream


** (zeitgeist-datahub:2609): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/Downloads/raspberry_pi_nes_console_case.stl" was not found, exec: python, mime_type: application/octet-stream


** (zeitgeist-datahub:2609): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/Desktop/2014%201099G%20Detail.pdf" was not found, exec: google-chrome-stable, mime_type: application/pdf


** (zeitgeist-datahub:2609): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/Pictures/Restricted%20Freedom.jpg" was not found, exec: google-chrome-stable, mime_type: image/jpeg


** (zeitgeist-datahub:2609): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/VB%20Share/Drawings/V6-NOZZLE-175.pdf" was not found, exec: google-chrome-stable, mime_type: application/pdf


** (zeitgeist-datahub:2609): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/VB%20Share/Drawings/V6-BLOCK.pdf" was not found, exec: google-chrome-stable, mime_type: application/pdf


** (zeitgeist-datahub:2609): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/VB%20Share/Drawings/V6-175-BREAK.pdf" was not found, exec: google-chrome-stable, mime_type: application/pdf


** (zeitgeist-datahub:2609): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/VB%20Share/Drawings/V6-175-SINK.pdf" was not found, exec: google-chrome-stable, mime_type: application/pdf


(unity-settings-daemon:2337): media-keys-plugin-WARNING **: Unable to get default sink
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1"
      after 4692 requests (4692 known processed) with 0 events remaining.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.0.
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : Default
Xsession: X session started for zanahade at Tue Jan 27 11:06:36 PST 2015
localuser:zanahade being added to access control list
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
x-session-manager[2586]: WARNING: Could not parse desktop file fingerprint-polkit-agent.desktop or it references a not found TryExec binary
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-ioVmpt
SSH_AUTH_SOCK=/run/user/1000/keyring-ioVmpt/ssh
GNOME_KEYRING_PID=2717
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-ioVmpt
SSH_AUTH_SOCK=/run/user/1000/keyring-ioVmpt/ssh
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-ioVmpt
SSH_AUTH_SOCK=/run/user/1000/keyring-ioVmpt/ssh
GNOME_KEYRING_CONTROL=/run/user/1000/keyring-ioVmpt
SSH_AUTH_SOCK=/run/user/1000/keyring-ioVmpt/ssh
GPG_AGENT_INFO=/run/user/1000/keyring-ioVmpt/gpg:0:1


(unity-settings-daemon:2720): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector
x-session-manager[2586]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector
x-session-manager[2586]: Gtk-WARNING: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector


(unity-settings-daemon:2720): color-plugin-WARNING **: no xrandr-AU Optronics device found: Failed to find output xrandr-AU Optronics


(unity-settings-daemon:2720): AccountsService-WARNING **: SetInputSources call failed: GDBus.Error:org.freedesktop.Accounts.Error.PermissionDenied: Not authorized


(unity-settings-daemon:2720): color-plugin-WARNING **: failed to obtain org.freedesktop.color-manager.create-profile auth
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp


(nm-applet:2782): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector


(indicator-printers-service:2787): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector
initctl: UPSTART_SESSION isn't set in the environment. Unable to locate the Upstart instance.


(polkit-gnome-authentication-agent-1:2794): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector


** (process:2788): CRITICAL **: volume_control_set_volume_internal: assertion '_tmp1_ == PA_CONTEXT_READY' failed


** (process:2788): CRITICAL **: file /build/buildd/indicator-sound-12.10.2+14.04.20140401/obj-x86_64-linux-gnu/src/volume-control.c: line 1775: uncaught error: GDBus.Error:org.freedesktop.DBus.Error.InvalidArgs: No such interface (g-dbus-error-quark, 16)


** (process:2859): WARNING **: killswitch.vala:103: Can't open /dev/rfkill for use as a killswitch backend: Permission denied
compiz (core) - Info: Loading plugin: composite


** (process:2859): CRITICAL **: bluez.vala:104: GDBus.Error:org.bluez.Error.NoSuchAdapter: No such adapter


(unity-fallback-mount-helper:2824): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl


(nvidia-settings:2857): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector
compiz (core) - Info: Starting plugin: opengl
Compiz (opengl) - Info: GLX_EXT_buffer_age is supported
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor


(nautilus:2800): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/zanahade/.compiz/session/108967329161127269142238560016196200000025860001"
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (decor) - Warn: No default decoration found, placement will not be correct
compiz (core) - Warn: Attempted to restack relative to 0x2800186 which is not a child of the root window or a window compiz owns
compiz (decor) - Warn: No default decoration found, placement will not be correct


(gnome-user-share:2975): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector


(telepathy-indicator:2977): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector


(zeitgeist-datahub:2995): GLib-GObject-WARNING **: invalid (NULL) pointer instance


(zeitgeist-datahub:2995): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed


** (zeitgeist-datahub:2995): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/Downloads/raspberry_pi_nes_console_case.gcode" was not found, exec: python, mime_type: application/octet-stream


** (zeitgeist-datahub:2995): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/Downloads/raspberry_pi_nes_console_case.stl" was not found, exec: python, mime_type: application/octet-stream


** (zeitgeist-datahub:2995): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/Desktop/2014%201099G%20Detail.pdf" was not found, exec: google-chrome-stable, mime_type: application/pdf


** (zeitgeist-datahub:2995): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/Pictures/Restricted%20Freedom.jpg" was not found, exec: google-chrome-stable, mime_type: image/jpeg


** (zeitgeist-datahub:2995): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/VB%20Share/Drawings/V6-NOZZLE-175.pdf" was not found, exec: google-chrome-stable, mime_type: application/pdf


** (zeitgeist-datahub:2995): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/VB%20Share/Drawings/V6-BLOCK.pdf" was not found, exec: google-chrome-stable, mime_type: application/pdf


** (zeitgeist-datahub:2995): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/VB%20Share/Drawings/V6-175-BREAK.pdf" was not found, exec: google-chrome-stable, mime_type: application/pdf


** (zeitgeist-datahub:2995): WARNING **: recent-manager-provider.vala:132: Desktop file for "file:///home/zanahade/VB%20Share/Drawings/V6-175-SINK.pdf" was not found, exec: google-chrome-stable, mime_type: application/pdf


(update-notifier:3030): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:121:0: Expected a valid selector


(unity-settings-daemon:2720): media-keys-plugin-WARNING **: Unable to get default sink
XIO:  fatal IO error 4 (Interrupted system call) on X server ":1"
      after 5008 requests (5008 known processed) with 0 events remaining.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
Terminated
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : Default
Xsession: X session started for zanahade at Wed Jan 28 18:25:10 PST 2015
localuser:zanahade being added to access control list
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
Xlib:  extension "GLX" missing on display ":1".
Xlib:  extension "GLX" missing on display ":1".
Xlib:  extension "GLX" missing on display ":1".
gnome-session-is-accelerated: No hardware 3D support.
Xlib:  extension "GLX" missing on display ":1".
gnome-session-check-accelerated: Helper exited with code 256
Xlib:  extension "GLX" missing on display ":1".
Xlib:  extension "GLX" missing on display ":1".
Xlib:  extension "GLX" missing on display ":1".
gnome-session-is-accelerated: No hardware 3D support.
Xlib:  extension "GLX" missing on display ":1".
gnome-session-check-accelerated: Helper exited with code 256


** (process:1869): WARNING **: software acceleration check failed: Child process exited with code 1


** (x-session-manager:1869): CRITICAL **: We failed, but the fail whale is dead. Sorry....



```

Hey, at least it was polite... and apologized...

---

### Post by Bashing-om on 2015-01-30
zan-public; Morning .

Unity us not happy at all ..
My compatriot has directed my attention to:
[http://askubuntu.com/questions/477553/ubuntu-14-04-cant-get-nvidia-prime-working](http://askubuntu.com/questions/477553/ubuntu-14-04-cant-get-nvidia-prime-working)

Is libvdpau-va-gl1 installed ?
```

dpkg -l libvdpau-va-gl1

```
"Also, make sure libvdpau-va-gl1 is not enabled system-wide because it causes Nvidia Settings to crash on start - if it is, either disable it or simply remove the package:"
```

sudo apt-get purge libvdpau-va-gl1

```
(not installed on my system, but I do not run hybrid or Nvidia graphics)
And; what have we to work with in:
```

ls -al /etc/nvidia

```

For my thought process - for the way I think - is this GUI 'root' interface installed "
```

dpkg -l gksu

```

As we work to get
[INDENT][INDENT]to the bottom of things
[/INDENT][/INDENT]

---

### Post by MAFoElffen on 2015-01-30
Agreed with Bashing...

Could you please post your /var/log/Xorg.0.log and the results of
```

ls -l /etc/nvidia
ls -l /etc/alternatives | grep -i nvidia
dpkg -l | grep -i nvidia
tail -n 3 /etc/group

```
The Xorg.0.log will show us what it is trying to use as drivers, what hardware it is seeing, what is trying to load and what it is actually trying to do (with the errors).

The first command is looking for a directory to exist, which would be indicative by some of your errors you are getting when you try to use nvidia-setting, (from a current bug). The second looks for other things in that same bug, where some links may be missing, that would cause you not to get options in nividia-settings. The fourth command is looking to see which nvidia packages are installed, because that would vary what the instructions to you for that fix. The fourth command is to trace another current bug that might prevent you from not being able to save settings from nvidia-settings.

All those are just diagnostic and really make no changes to your system, but help us to be able to track down what might be going on and to be able to adapt a fix to you and your system...

---

### Post by zan-public on 2015-01-30
> **Bashing-om said:**
> zan-public; Morning .

Unity us not happy at all ..
My compatriot has directed my attention to:
[http://askubuntu.com/questions/477553/ubuntu-14-04-cant-get-nvidia-prime-working](http://askubuntu.com/questions/477553/ubuntu-14-04-cant-get-nvidia-prime-working)

Is libvdpau-va-gl1 installed ?
```

dpkg -l libvdpau-va-gl1

```
"Also, make sure libvdpau-va-gl1 is not enabled system-wide because it causes Nvidia Settings to crash on start - if it is, either disable it or simply remove the package:"
```

sudo apt-get purge libvdpau-va-gl1

```
(not installed on my system, but I do not run hybrid or Nvidia graphics)
And; what have we to work with in:
```

ls -al /etc/nvidia

```

For my thought process - for the way I think - is this GUI 'root' interface installed "
```

dpkg -l gksu

```

As we work to get[INDENT][INDENT]to the bottom of things
[/INDENT]
[/INDENT]


> **MAFoElffen said:**
> Agreed with Bashing...

Could you please post your /var/log/Xorg.0.log and the results of
```

ls -l /etc/nvidia
ls -l /etc/alternatives | grep -i nvidia
dpkg -l | grep -i nvidia
tail -n 3 /etc/group

```
The Xorg.0.log will show us what it is trying to use as drivers, what hardware it is seeing, what is trying to load and what it is actually trying to do (with the errors).

The first command is looking for a directory to exist, which would be indicative by some of your errors you are getting when you try to use nvidia-setting, (from a current bug). The second looks for other things in that same bug, where some links may be missing, that would cause you not to get options in nividia-settings. The fourth command is looking to see which nvidia packages are installed, because that would vary what the instructions to you for that fix. The fourth command is to trace another current bug that might prevent you from not being able to save settings from nvidia-settings.

All those are just diagnostic and really make no changes to your system, but help us to be able to track down what might be going on and to be able to adapt a fix to you and your system...

```
$ dpkg -l libvdpau-va-gl1
dpkg-query: no packages found matching libvdpau-va-gl1
```


```
$ ls -al /etc/nvidia
total 16
drwxr-xr-x   2 root root  4096 Jan 22 06:47 .
drwxr-xr-x 150 root root 12288 Jan 30 09:01 ..



```

```
$ dpkg -l gksu
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  gksu           2.0.2-6ubunt amd64        graphical frontend to su



```

```
$ cat /var/log/Xorg.0.log
[    20.102] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    20.102] X Protocol Version 11, Revision 0
[    20.102] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[    20.102] Current Operating System: Linux Odin 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64
[    20.102] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-44-generic.efi.signed root=UUID=f1544fc7-e2ba-4d6d-b3e4-451064c75b80 ro quiet splash
[    20.102] Build Date: 10 December 2014  06:15:52PM
[    20.102] xorg-server 2:1.15.1-0ubuntu2.6 (For technical support please see http://www.ubuntu.com/support) 
[    20.102] Current version of pixman: 0.30.2
[    20.102]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.102] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.102] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 30 09:00:29 2015
[    20.464] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.550] (==) No Layout section.  Using the first Screen section.
[    20.550] (==) No screen section available. Using defaults.
[    20.550] (**) |-->Screen "Default Screen Section" (0)
[    20.550] (**) |   |-->Monitor "<default monitor>"
[    20.550] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    20.550] (==) Automatically adding devices
[    20.550] (==) Automatically enabling devices
[    20.550] (==) Automatically adding GPU devices
[    20.550] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.550]     Entry deleted from font path.
[    20.550] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.550]     Entry deleted from font path.
[    20.550] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.550]     Entry deleted from font path.
[    20.550] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.550]     Entry deleted from font path.
[    20.550] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.550]     Entry deleted from font path.
[    20.550] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    20.550] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.550] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.550] (II) Loader magic: 0x7f9a5676dd40
[    20.550] (II) Module ABI versions:
[    20.550]     X.Org ANSI C Emulation: 0.4
[    20.550]     X.Org Video Driver: 15.0
[    20.550]     X.Org XInput driver : 20.0
[    20.550]     X.Org Server Extension : 8.0
[    20.550] (II) xfree86: Adding drm device (/dev/dri/card0)
[    20.551] (II) xfree86: Adding drm device (/dev/dri/card1)
[    20.552] (--) PCI:*(0:0:2:0) 8086:0416:103c:1968 rev 6, Mem @ 0xb7000000/4194304, 0xc0000000/268435456, I/O @ 0x00008000/64
[    20.552] (--) PCI: (0:7:0:0) 10de:1341:103c:21a1 rev 162, Mem @ 0xb5000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00006000/128
[    20.552] Initializing built-in extension Generic Event Extension
[    20.552] Initializing built-in extension SHAPE
[    20.552] Initializing built-in extension MIT-SHM
[    20.552] Initializing built-in extension XInputExtension
[    20.552] Initializing built-in extension XTEST
[    20.552] Initializing built-in extension BIG-REQUESTS
[    20.552] Initializing built-in extension SYNC
[    20.552] Initializing built-in extension XKEYBOARD
[    20.552] Initializing built-in extension XC-MISC
[    20.552] Initializing built-in extension SECURITY
[    20.552] Initializing built-in extension XINERAMA
[    20.552] Initializing built-in extension XFIXES
[    20.552] Initializing built-in extension RENDER
[    20.552] Initializing built-in extension RANDR
[    20.552] Initializing built-in extension COMPOSITE
[    20.552] Initializing built-in extension DAMAGE
[    20.552] Initializing built-in extension MIT-SCREEN-SAVER
[    20.552] Initializing built-in extension DOUBLE-BUFFER
[    20.552] Initializing built-in extension RECORD
[    20.552] Initializing built-in extension DPMS
[    20.552] Initializing built-in extension Present
[    20.552] Initializing built-in extension DRI3
[    20.552] Initializing built-in extension X-Resource
[    20.552] Initializing built-in extension XVideo
[    20.552] Initializing built-in extension XVideo-MotionCompensation
[    20.552] Initializing built-in extension SELinux
[    20.552] Initializing built-in extension XFree86-VidModeExtension
[    20.552] Initializing built-in extension XFree86-DGA
[    20.552] Initializing built-in extension XFree86-DRI
[    20.552] Initializing built-in extension DRI2
[    20.552] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    20.552] (II) "glx" will be loaded by default.
[    20.552] (WW) "xmir" is not to be loaded by default. Skipping.
[    20.552] (II) LoadModule: "glx"
[    20.681] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.370] (II) Module glx: vendor="X.Org Foundation"
[    21.370]     compiled for 1.15.1, module version = 1.0.0
[    21.370]     ABI class: X.Org Server Extension, version 8.0
[    21.370] (==) AIGLX enabled
[    21.370] Loading extension GLX
[    21.370] (==) Matched intel as autoconfigured driver 0
[    21.370] (==) Matched nvidia as autoconfigured driver 1
[    21.370] (==) Matched nouveau as autoconfigured driver 2
[    21.370] (==) Matched intel as autoconfigured driver 3
[    21.370] (==) Matched modesetting as autoconfigured driver 4
[    21.370] (==) Matched fbdev as autoconfigured driver 5
[    21.370] (==) Matched vesa as autoconfigured driver 6
[    21.370] (==) Assigned the driver to the xf86ConfigLayout
[    21.370] (II) LoadModule: "intel"
[    21.370] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.383] (II) Module intel: vendor="X.Org Foundation"
[    21.384]     compiled for 1.15.1, module version = 2.99.917
[    21.384]     Module class: X.Org Video Driver
[    21.384]     ABI class: X.Org Video Driver, version 15.0
[    21.384] (II) LoadModule: "nvidia"
[    21.384] (WW) Warning, couldn't open module nvidia
[    21.384] (II) UnloadModule: "nvidia"
[    21.384] (II) Unloading nvidia
[    21.384] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    21.384] (II) LoadModule: "nouveau"
[    21.384] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    21.903] (II) Module nouveau: vendor="X.Org Foundation"
[    21.903]     compiled for 1.15.1, module version = 1.0.11
[    21.903]     Module class: X.Org Video Driver
[    21.903]     ABI class: X.Org Video Driver, version 15.0
[    21.903] (II) LoadModule: "modesetting"
[    21.903] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    21.903] (II) Module modesetting: vendor="X.Org Foundation"
[    21.903]     compiled for 1.15.0, module version = 0.8.1
[    21.903]     Module class: X.Org Video Driver
[    21.903]     ABI class: X.Org Video Driver, version 15.0
[    21.903] (II) LoadModule: "fbdev"
[    21.904] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.904] (II) Module fbdev: vendor="X.Org Foundation"
[    21.904]     compiled for 1.15.0, module version = 0.4.4
[    21.904]     Module class: X.Org Video Driver
[    21.904]     ABI class: X.Org Video Driver, version 15.0
[    21.904] (II) LoadModule: "vesa"
[    21.904] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.904] (II) Module vesa: vendor="X.Org Foundation"
[    21.904]     compiled for 1.15.0, module version = 2.3.3
[    21.904]     Module class: X.Org Video Driver
[    21.904]     ABI class: X.Org Video Driver, version 15.0
[    21.904] (==) Matched intel as autoconfigured driver 0
[    21.904] (==) Matched nvidia as autoconfigured driver 1
[    21.904] (==) Matched nouveau as autoconfigured driver 2
[    21.904] (==) Matched intel as autoconfigured driver 3
[    21.904] (==) Matched modesetting as autoconfigured driver 4
[    21.904] (==) Matched fbdev as autoconfigured driver 5
[    21.904] (==) Matched vesa as autoconfigured driver 6
[    21.904] (==) Assigned the driver to the xf86ConfigLayout
[    21.904] (II) LoadModule: "intel"
[    21.904] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.904] (II) Module intel: vendor="X.Org Foundation"
[    21.904]     compiled for 1.15.1, module version = 2.99.917
[    21.904]     Module class: X.Org Video Driver
[    21.904]     ABI class: X.Org Video Driver, version 15.0
[    21.904] (II) UnloadModule: "intel"
[    21.904] (II) Unloading intel
[    21.904] (II) Failed to load module "intel" (already loaded, 32666)
[    21.904] (II) LoadModule: "nvidia"
[    21.904] (WW) Warning, couldn't open module nvidia
[    21.904] (II) UnloadModule: "nvidia"
[    21.904] (II) Unloading nvidia
[    21.904] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    21.904] (II) LoadModule: "nouveau"
[    21.904] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    21.904] (II) Module nouveau: vendor="X.Org Foundation"
[    21.904]     compiled for 1.15.1, module version = 1.0.11
[    21.904]     Module class: X.Org Video Driver
[    21.904]     ABI class: X.Org Video Driver, version 15.0
[    21.904] (II) UnloadModule: "nouveau"
[    21.904] (II) Unloading nouveau
[    21.904] (II) Failed to load module "nouveau" (already loaded, 0)
[    21.904] (II) LoadModule: "modesetting"
[    21.905] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    21.905] (II) Module modesetting: vendor="X.Org Foundation"
[    21.905]     compiled for 1.15.0, module version = 0.8.1
[    21.905]     Module class: X.Org Video Driver
[    21.905]     ABI class: X.Org Video Driver, version 15.0
[    21.905] (II) UnloadModule: "modesetting"
[    21.905] (II) Unloading modesetting
[    21.905] (II) Failed to load module "modesetting" (already loaded, 0)
[    21.905] (II) LoadModule: "fbdev"
[    21.905] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.905] (II) Module fbdev: vendor="X.Org Foundation"
[    21.905]     compiled for 1.15.0, module version = 0.4.4
[    21.905]     Module class: X.Org Video Driver
[    21.905]     ABI class: X.Org Video Driver, version 15.0
[    21.905] (II) UnloadModule: "fbdev"
[    21.905] (II) Unloading fbdev
[    21.905] (II) Failed to load module "fbdev" (already loaded, 0)
[    21.905] (II) LoadModule: "vesa"
[    21.905] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.905] (II) Module vesa: vendor="X.Org Foundation"
[    21.905]     compiled for 1.15.0, module version = 2.3.3
[    21.905]     Module class: X.Org Video Driver
[    21.905]     ABI class: X.Org Video Driver, version 15.0
[    21.905] (II) UnloadModule: "vesa"
[    21.905] (II) Unloading vesa
[    21.905] (II) Failed to load module "vesa" (already loaded, 0)
[    21.905] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    21.905] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    21.905] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    21.905] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    21.905] (II) NOUVEAU driver 
[    21.905] (II) NOUVEAU driver for NVIDIA chipset families :
[    21.905]     RIVA TNT        (NV04)
[    21.905]     RIVA TNT2       (NV05)
[    21.905]     GeForce 256     (NV10)
[    21.905]     GeForce 2       (NV11, NV15)
[    21.905]     GeForce 4MX     (NV17, NV18)
[    21.905]     GeForce 3       (NV20)
[    21.905]     GeForce 4Ti     (NV25, NV28)
[    21.905]     GeForce FX      (NV3x)
[    21.905]     GeForce 6       (NV4x)
[    21.905]     GeForce 7       (G7x)
[    21.905]     GeForce 8       (G8x)
[    21.905]     GeForce GTX 200 (NVA0)
[    21.905]     GeForce GTX 400 (NVC0)
[    21.905] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    21.905] (II) FBDEV: driver for framebuffer: fbdev
[    21.905] (II) VESA: driver for VESA chipsets: vesa
[    21.905] (++) using VT number 7


[    21.905] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    21.905] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150127.4bbd1023-0ubuntu0sarvatt~trusty (Robert Hooker <sarvatt@ubuntu.com>)
[    21.905] (II) intel(0): SNA compiled for use with valgrind
[    21.906] (EE) [drm] KMS not enabled
[    21.906] (WW) Falling back to old probe method for modesetting
[    21.906] (WW) Falling back to old probe method for fbdev
[    21.906] (II) Loading sub module "fbdevhw"
[    21.906] (II) LoadModule: "fbdevhw"
[    21.906] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.906] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.906]     compiled for 1.15.1, module version = 0.0.2
[    21.906]     ABI class: X.Org Video Driver, version 15.0
[    21.906] (WW) Falling back to old probe method for vesa
[    21.906] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    21.906] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[    21.906] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    21.906] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    21.906] (==) intel(0): RGB weight 888
[    21.906] (==) intel(0): Default visual is TrueColor
[    21.906] (II) intel(0): Output eDP1 has no monitor section
[    21.906] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output eDP1
[    21.906] (II) intel(0): Enabled output eDP1
[    21.906] (II) intel(0): Output VGA1 has no monitor section
[    21.906] (II) intel(0): Enabled output VGA1
[    21.906] (II) intel(0): Output HDMI1 has no monitor section
[    21.906] (II) intel(0): Enabled output HDMI1
[    21.906] (--) intel(0): Using a maximum size of 64x64 for hardware cursors
[    21.906] (II) intel(0): Output VIRTUAL1 has no monitor section
[    21.906] (II) intel(0): Enabled output VIRTUAL1
[    21.906] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[    21.906] (==) intel(0): TearFree disabled
[    21.906] (==) intel(0): DPI set to (96, 96)
[    21.906] (II) Loading sub module "dri2"
[    21.906] (II) LoadModule: "dri2"
[    21.906] (II) Module "dri2" already built-in
[    21.906] (II) Loading sub module "present"
[    21.906] (II) LoadModule: "present"
[    21.907] (WW) Warning, couldn't open module present
[    21.907] (II) UnloadModule: "present"
[    21.907] (II) Unloading present
[    21.907] (EE) intel: Failed to load module "present" (module does not exist, 0)
[    21.909] (II) UnloadModule: "fbdev"
[    21.909] (II) Unloading fbdev
[    21.909] (II) UnloadSubModule: "fbdevhw"
[    21.909] (II) Unloading fbdevhw
[    21.909] (II) UnloadModule: "vesa"
[    21.909] (II) Unloading vesa
[    21.909] (==) Depth 24 pixmap format is 32 bpp
[    21.909] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    21.909] (==) intel(0): Backing store enabled
[    21.909] (==) intel(0): Silken mouse enabled
[    21.909] (II) intel(0): HW Cursor enabled
[    21.909] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.909] (==) intel(0): DPMS enabled
[    21.909] (==) intel(0): Display hotplug detection enabled
[    21.909] (II) intel(0): [DRI2] Setup complete
[    21.909] (II) intel(0): [DRI2]   DRI driver: i965
[    21.909] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    21.909] (II) intel(0): direct rendering: DRI2 enabled
[    21.909] (--) RandR disabled
[    21.913] (II) SELinux: Disabled on system
[    21.950] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    21.950] (II) AIGLX: enabled GLX_ARB_create_context
[    21.950] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    21.950] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    21.950] (II) AIGLX: enabled GLX_INTEL_swap_event
[    21.950] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    21.950] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    21.950] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    21.950] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    21.950] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    21.950] (II) AIGLX: Loaded and initialized i965
[    21.950] (II) GLX: Initialized DRI2 GL provider for screen 0
[    21.952] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    21.952] (II) intel(0): Setting screen physical size to 508 x 285
[    21.957] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.959] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    21.959] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.959] (II) LoadModule: "evdev"
[    21.959] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.023] (II) Module evdev: vendor="X.Org Foundation"
[    22.023]     compiled for 1.15.0, module version = 2.8.2
[    22.023]     Module class: X.Org XInput Driver
[    22.023]     ABI class: X.Org XInput driver, version 20.0
[    22.023] (II) Using input driver 'evdev' for 'Power Button'
[    22.023] (**) Power Button: always reports core events
[    22.024] (**) evdev: Power Button: Device: "/dev/input/event2"
[    22.024] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.024] (--) evdev: Power Button: Found keys
[    22.024] (II) evdev: Power Button: Configuring as keyboard
[    22.024] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    22.024] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    22.024] (**) Option "xkb_rules" "evdev"
[    22.024] (**) Option "xkb_model" "pc105"
[    22.024] (**) Option "xkb_layout" "us"
[    22.024] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[    22.024] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    22.024] (II) Using input driver 'evdev' for 'Video Bus'
[    22.024] (**) Video Bus: always reports core events
[    22.024] (**) evdev: Video Bus: Device: "/dev/input/event11"
[    22.024] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    22.024] (--) evdev: Video Bus: Found keys
[    22.024] (II) evdev: Video Bus: Configuring as keyboard
[    22.024] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input13/event11"
[    22.024] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    22.024] (**) Option "xkb_rules" "evdev"
[    22.024] (**) Option "xkb_model" "pc105"
[    22.024] (**) Option "xkb_layout" "us"
[    22.024] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    22.024] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    22.024] (II) Using input driver 'evdev' for 'Video Bus'
[    22.024] (**) Video Bus: always reports core events
[    22.024] (**) evdev: Video Bus: Device: "/dev/input/event10"
[    22.024] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    22.024] (--) evdev: Video Bus: Found keys
[    22.024] (II) evdev: Video Bus: Configuring as keyboard
[    22.024] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:44/LNXVIDEO:00/input/input12/event10"
[    22.024] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    22.024] (**) Option "xkb_rules" "evdev"
[    22.025] (**) Option "xkb_model" "pc105"
[    22.025] (**) Option "xkb_layout" "us"
[    22.025] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.025] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.025] (II) Using input driver 'evdev' for 'Power Button'
[    22.025] (**) Power Button: always reports core events
[    22.025] (**) evdev: Power Button: Device: "/dev/input/event1"
[    22.025] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.025] (--) evdev: Power Button: Found keys
[    22.025] (II) evdev: Power Button: Configuring as keyboard
[    22.025] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    22.025] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    22.025] (**) Option "xkb_rules" "evdev"
[    22.025] (**) Option "xkb_model" "pc105"
[    22.025] (**) Option "xkb_layout" "us"
[    22.025] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    22.025] (II) No input driver specified, ignoring this device.
[    22.025] (II) This device may have been added with another device file.
[    22.025] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.1/0000:07:00.0/drm/card0
[    22.025] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    22.025] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:02.0/drm/card1
[    22.025] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[    22.025] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event14)
[    22.025] (II) No input driver specified, ignoring this device.
[    22.025] (II) This device may have been added with another device file.
[    22.025] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event13)
[    22.025] (II) No input driver specified, ignoring this device.
[    22.025] (II) This device may have been added with another device file.
[    22.025] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event12)
[    22.025] (II) No input driver specified, ignoring this device.
[    22.025] (II) This device may have been added with another device file.
[    22.026] (II) config/udev: Adding input device eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00 (/dev/input/event8)
[    22.026] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Applying InputClass "evdev touchscreen catchall"
[    22.026] (II) Using input driver 'evdev' for 'eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00'
[    22.026] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: always reports core events
[    22.026] (**) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Device: "/dev/input/event8"
[    22.026] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Using mtdev for this device
[    22.026] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Vendor 0xeef Product 0xa80f
[    22.026] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found absolute axes
[    22.026] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found absolute multitouch axes
[    22.026] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: No buttons found, faking one.
[    22.026] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found x and y absolute axes
[    22.026] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found absolute touchscreen
[    22.026] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Configuring as touchscreen
[    22.026] (**) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: YAxisMapping: buttons 4 and 5
[    22.026] (**) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.026] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-13/2-13:1.0/input/input9/event8"
[    22.026] (II) XINPUT: Adding extended input device "eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00" (type: TOUCHSCREEN, id 10)
[    22.026] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: initialized for absolute axes.
[    22.026] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) keeping acceleration scheme 1
[    22.026] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) acceleration profile 0
[    22.026] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) acceleration factor: 2.000
[    22.026] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) acceleration threshold: 4
[    22.026] (II) config/udev: Adding input device eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00 (/dev/input/mouse1)
[    22.026] (II) No input driver specified, ignoring this device.
[    22.026] (II) This device may have been added with another device file.
[    22.026] (II) config/udev: Adding input device HP Truevision HD (/dev/input/event9)
[    22.026] (**) HP Truevision HD: Applying InputClass "evdev keyboard catchall"
[    22.026] (II) Using input driver 'evdev' for 'HP Truevision HD'
[    22.026] (**) HP Truevision HD: always reports core events
[    22.026] (**) evdev: HP Truevision HD: Device: "/dev/input/event9"
[    22.026] (--) evdev: HP Truevision HD: Vendor 0x64e Product 0xc341
[    22.026] (--) evdev: HP Truevision HD: Found keys
[    22.026] (II) evdev: HP Truevision HD: Configuring as keyboard
[    22.026] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-7/2-7:1.0/input/input11/event9"
[    22.026] (II) XINPUT: Adding extended input device "HP Truevision HD" (type: KEYBOARD, id 11)
[    22.026] (**) Option "xkb_rules" "evdev"
[    22.026] (**) Option "xkb_model" "pc105"
[    22.026] (**) Option "xkb_layout" "us"
[    22.026] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event16)
[    22.026] (II) No input driver specified, ignoring this device.
[    22.026] (II) This device may have been added with another device file.
[    22.027] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event15)
[    22.027] (II) No input driver specified, ignoring this device.
[    22.027] (II) This device may have been added with another device file.
[    22.027] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    22.027] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    22.027] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    22.027] (**) AT Translated Set 2 keyboard: always reports core events
[    22.027] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    22.027] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    22.027] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    22.027] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    22.027] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    22.027] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    22.027] (**) Option "xkb_rules" "evdev"
[    22.027] (**) Option "xkb_model" "pc105"
[    22.027] (**) Option "xkb_layout" "us"
[    22.027] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[    22.027] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    22.027] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    22.027] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    22.027] (II) LoadModule: "synaptics"
[    22.027] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    22.027] (II) Module synaptics: vendor="X.Org Foundation"
[    22.027]     compiled for 1.15.0, module version = 1.7.4
[    22.027]     Module class: X.Org XInput Driver
[    22.027]     ABI class: X.Org XInput driver, version 20.0
[    22.027] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    22.027] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    22.027] (**) Option "Device" "/dev/input/event4"
[    22.044] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    22.044] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5660 (res 41)
[    22.044] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4702 (res 56)
[    22.044] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    22.044] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    22.044] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    22.044] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    22.044] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    22.044] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    22.044] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    22.056] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[    22.056] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[    22.056] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    22.056] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    22.056] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[    22.056] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    22.056] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    22.056] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    22.056] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    22.056] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    22.056] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    22.056] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    22.056] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[    22.056] (II) No input driver specified, ignoring this device.
[    22.056] (II) This device may have been added with another device file.
[    22.056] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    22.056] (II) No input driver specified, ignoring this device.
[    22.056] (II) This device may have been added with another device file.
[    22.057] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[    22.057] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    22.057] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    22.057] (**) HP WMI hotkeys: always reports core events
[    22.057] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event7"
[    22.057] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    22.057] (--) evdev: HP WMI hotkeys: Found keys
[    22.057] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    22.057] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event7"
[    22.057] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 14)
[    22.057] (**) Option "xkb_rules" "evdev"
[    22.057] (**) Option "xkb_model" "pc105"
[    22.057] (**) Option "xkb_layout" "us"
[    22.057] (II) config/udev: Adding input device HP Wireless hotkeys (/dev/input/event5)
[    22.057] (**) HP Wireless hotkeys: Applying InputClass "evdev keyboard catchall"
[    22.057] (II) Using input driver 'evdev' for 'HP Wireless hotkeys'
[    22.057] (**) HP Wireless hotkeys: always reports core events
[    22.057] (**) evdev: HP Wireless hotkeys: Device: "/dev/input/event5"
[    22.057] (--) evdev: HP Wireless hotkeys: Vendor 0 Product 0
[    22.057] (--) evdev: HP Wireless hotkeys: Found keys
[    22.057] (II) evdev: HP Wireless hotkeys: Configuring as keyboard
[    22.057] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event5"
[    22.057] (II) XINPUT: Adding extended input device "HP Wireless hotkeys" (type: KEYBOARD, id 15)
[    22.057] (**) Option "xkb_rules" "evdev"
[    22.057] (**) Option "xkb_model" "pc105"
[    22.057] (**) Option "xkb_layout" "us"
[    24.216] (II) intel(0): EDID vendor "AUO", prod id 8605
[    24.216] (II) intel(0): Printing DDC gathered Modelines:
[    24.216] (II) intel(0): Modeline "1920x1080"x0.0  140.50  1920 1968 2068 2104  1080 1083 1089 1112 -hsync -vsync (66.8 kHz eP)
[    24.216] (II) intel(0): Modeline "1920x1080"x0.0   93.67  1920 1968 2068 2104  1080 1083 1089 1112 -hsync -vsync (44.5 kHz e)
[    25.102] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.142] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.144] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.145] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.378] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.719] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    57.622] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/mouse2)
[    57.622] (II) No input driver specified, ignoring this device.
[    57.622] (II) This device may have been added with another device file.
[    57.622] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/event17)
[    57.622] (**) Logitech Unifying Device. Wireless PID:101a: Applying InputClass "evdev pointer catchall"
[    57.622] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101a'
[    57.622] (**) Logitech Unifying Device. Wireless PID:101a: always reports core events
[    57.622] (**) evdev: Logitech Unifying Device. Wireless PID:101a: Device: "/dev/input/event17"
[    57.622] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Vendor 0x46d Product 0xc52b
[    57.622] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found 20 mouse buttons
[    57.622] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found scroll wheel(s)
[    57.622] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found relative axes
[    57.622] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found x and y relative axes
[    57.622] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Configuring as mouse
[    57.623] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Adding scrollwheel support
[    57.623] (**) evdev: Logitech Unifying Device. Wireless PID:101a: YAxisMapping: buttons 4 and 5
[    57.623] (**) evdev: Logitech Unifying Device. Wireless PID:101a: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    57.623] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.2/0003:046D:C52B.0003/input/input19/event17"
[    57.623] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101a" (type: MOUSE, id 16)
[    57.623] (II) evdev: Logitech Unifying Device. Wireless PID:101a: initialized for relative axes.
[    57.623] (**) Logitech Unifying Device. Wireless PID:101a: (accel) keeping acceleration scheme 1
[    57.623] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration profile 0
[    57.623] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration factor: 2.000
[    57.623] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration threshold: 4
[    74.106] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    78.623] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    78.713] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    78.719] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    82.897] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm



```

```
$ ls -l /etc/nvidia
total 0



```

```
$ ls -l /etc/alternatives | grep -i nvidia
lrwxrwxrwx 1 root root  33 Jan 29 11:34 glamor_conf -> /usr/share/nvidia-340/glamor.conf
lrwxrwxrwx 1 root root  34 Jan 29 11:34 i386-linux-gnu_gl_conf -> /usr/lib/nvidia-340/alt_ld.so.conf



```

```
$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                         0.7-2ubuntu1                                           amd64        Interface for toggling the power on nVidia Optimus video cards
rc  libcuda1-304                                          304.125-0ubuntu0.0.1                                   amd64        NVIDIA CUDA runtime library
ii  libcuda1-340                                          340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA CUDA runtime library
rc  libcuda1-346                                          346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA CUDA runtime library
ii  nvidia-340                                            340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-346                                            346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-340                                 340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-libopencl1-346                                 346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-340                                 340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-346                                 346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       346.35-100ubuntu100~ppa0~trusty                        amd64        Tool for configuring the NVIDIA graphics driver



```

```
$ tail -n 3 /etc/group
geoclue:x:128:
gdm:x:129:
nvidia-persistenced:x:126:



```

So... how hosed am I?

---

### Post by lotus49 on 2015-01-30
I am having the same problem with my Acer laptop, which also has a GeForce 840M.  This was working fine with the xorg-edgers nvidia-340 package then an update to another package (don't recall what) broke it.

If I purge the nvidia* packages, I can use my laptop with the Intel graphics card but I bought this laptop partly to play Minecraft on and the frame rate using the Intel card is half that of the 840M.

If Xubuntu works, presumably this is some interaction between the display manager and the driver.  Which display manager does Xubuntu use these days?  That might work as a short-termi workaround.

---

### Post by zan-public on 2015-01-30
@Lotus49, Hi fellow tree puncher! Yes, Xubuntu will most likely work (that's what I am using to get my Nvidia card running in the interim.) I can confirm that minecraft does run in that environment. I needed it more for my Virtual Box with all my CAD tools on it, but when I want to unwind... I too, indulge in the art of tree punching. 

But to be serious, I do not know what the display manager is, but I can say that it does work... for me at least.

Ok, this is weird, but everything I read says that Xubuntu 14.04 is running LightDM... so... yea, I'm confused.

---

### Post by lotus49 on 2015-01-30
Greetings to you, fellow tree puncher.

Can you see whether lightdm is running ($ ps aux|grep lightdm)?

Fortunately I still get 60 fps running Minecraft on the Intel graphics so I can finish off building my witch farm but I would like to get back to doing that rather than faffing around with Nvidia drivers.

---

### Post by Bashing-om on 2015-01-30
zan-public; Still floundering !

Hardware is identified:
(--) PCI:*(0:0:2:0) 8086:0416:103c:1968 rev 6, Mem @ 0xb7000000/4194304, 0xc0000000/268435456, I/O @ 0x00008000/64 ## bus info: pci@0000:00:02.0 product: 4th Gen Core Processor Integrated Graphics Controller ##
(--) PCI: (0:7:0:0) 10de:1341:103c:21a1 rev 162, Mem @ 0xb5000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00006000/128 ##  bus info: pci@0000:07:00.0  product: GM108M [GeForce 840M]

drivers are loaded:
configuration: driver=nvidia ==> (==) Matched nvidia as autoconfigured driver 1
[color=red]configuration: driver=i915[/color] ==> (==) Matched intel as autoconfigured driver 0

How and where ? as Xorg screams and hollers:
> 
(II) LoadModule: "nvidia"
[    21.384] (WW) Warning, couldn't open module nvidia
[    21.384] (II) UnloadModule: "nvidia"
[    21.384] (II) Unloading nvidia
[    21.384] (EE) Failed to load module "nvidia" (module does not exist, 0)

NOW the i915 mudule is built:
 21.905] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
But, HUH ?
21.909] (II) intel(0): [DRI2]   DRI driver: i965

Should not the i965 driver be loaded ?

And lastly but not least is:
> 
21.906] (II) Loading sub module "present"
[    21.906] (II) LoadModule: "present"
[    21.907] (WW) Warning, couldn't open module present
[    21.907] (II) UnloadModule: "present"
[    21.907] (II) Unloading present
[    21.907] (EE) intel: Failed to load module "present" (module does not exist, 0) 

"The DRI3 Present extension is about swapping screen contents in a more synchronized manner." 
So does it fail due to the Nvidia module not building ? (but a nvidia driver is loaded per 'lshw')

I am still trying to see a means to discover what is taking place .

[INDENT][INDENT]sometimes I just do not know
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-30
> **lotus49 said:**
> Greetings to you, fellow tree puncher.

Can you see whether lightdm is running ($ ps aux|grep lightdm)?

Fortunately I still get 60 fps running Minecraft on the Intel graphics so I can finish off building my witch farm but I would like to get back to doing that rather than faffing around with Nvidia drivers.

```
$ ps aux|grep lightdm
root      1282  0.0  0.0 277888  5840 ?        SLsl 10:48   0:00 lightdm
root      1293  0.9  0.4 262936 74796 tty7     Ssl+ 10:48   0:12 /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
root      1615  0.0  0.0 170496  3752 ?        Sl   10:48   0:00 lightdm --session-child 12 19
zanahade  2992  0.0  0.0  18936   928 pts/0    S+   11:10   0:00 grep --color=auto lightdm



```

---

### Post by Bashing-om on 2015-01-30
zan-public; Hey :

Nother thought. I am seeing several threads in respect to kernel upgrades breaking the hybrid graphics. Maybe a bug in the new kernel ?

Can you boot up and old kernel and see if the Nvidia driver will then build in that old kernel environment ?
Purge and install the 346 driver .

[INDENT][INDENT]maybe yes 
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-30
> **Bashing-om said:**
> zan-public; Hey :

Nother thought. I am seeing several threads in respect to kernel upgrades breaking the hybrid graphics. Maybe a bug in the new kernel ?

Can you boot up and old kernel and see if the Nvidia driver will then build in that old kernel environment ?
Purge and install the 346 driver .
[INDENT][INDENT]maybe yes 
[/INDENT]
[/INDENT]


Ok, I have purged the 340 driver, booted into the last kernel before the current one, installed the 346 driver, rebooted into the previous kernel, ran nvidia-seetings, no change. Is there a specific log, or command I can post for you?

So tell me if I am wrong, but I thought Xubuntu and Ubuntu would have been running the same kernels, and since they both appear to run Lightdm but it is broken in Ubuntu, can that be the cause? I would reinstate lightdm, but if I do, it won't even make it to the login screen. Also, if it is not lightdm but something else that is breaking lightdm (since lightdm is working on my Xubuntu side) what would be different between them that would cause nvidia to die so horribly, and cause the login to die as well?

Just trying to understand...

---

### Post by Bashing-om on 2015-01-30
zan-public; Yuk ( or great ).

"Just trying to understand..." -> Me too !

Well it was a thought that the new kernel had issues ... gone now.

"I thought Xubuntu and Ubuntu would have been running the same kernels" -> yes, same same kernel ( I had expected different DM)

"would reinstate lightdm, but if I do, it won't even make it to the login screen" -> Did you not also install GDM ? Maybe consider removing GDM and rebuild lightdm (unity) .

"Also, if it is not lightdm but something else that is breaking lightdm (since lightdm is working on my Xubuntu side) what would be different between them that would cause nvidia to die so horribly, and cause the login to die as well? " I am behind the times as I 'thought' Xubuntu used xfce (hence the x in Xubuntu). Will do some checking and confirm what DM Xubuntu does use. ===>>
Xubuntu 11.10 and LightDM was introduced as the log-in manager.
Xubuntu 13.10 This release also included new wallpaper, new GTK themes, with Gtk3.10 support and the LightDM greeter.

OK, I honestly do not know how lightdm, as the Display manager, intercedes with xfce, the Desktop Environment. I **do** use xfce as my DE and my DM is Xfwm4,  nor do I use a login manager. -boot to terminal, and then whatever .


Back to think'n what could be taking place, and for me it is
[INDENT][INDENT][INDENT]seek and ye shall find
[/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-01-30
> **Bashing-om said:**
> zan-public; Yuk ( or great ).

"Just trying to understand..." -> Me too !

Well it was a thought that the new kernel had issues ... gone now.

"I thought Xubuntu and Ubuntu would have been running the same kernels" -> yes, same same kernel ( I had expected different DM)

"would reinstate lightdm, but if I do, it won't even make it to the login screen" -> Did you not also install GDM ? Maybe consider removing GDM and rebuild lightdm (unity) .

"Also, if it is not lightdm but something else that is breaking lightdm (since lightdm is working on my Xubuntu side) what would be different between them that would cause nvidia to die so horribly, and cause the login to die as well? " I am behind the times as I 'thought' Xubuntu used xfce (hence the x in Xubuntu). Will do some checking and confirm what DM Xubuntu does use. ===>>
Xubuntu 11.10 and LightDM was introduced as the log-in manager.
Xubuntu 13.10 This release also included new wallpaper, new GTK themes, with Gtk3.10 support and the LightDM greeter.

OK, I honestly do not know how lightdm, as the Display manager, intercedes with xfce, the Desktop Environment. I **do** use xfce as my DE and my DM is Xfwm4,  nor do I use a login manager. -boot to terminal, and then whatever .


Back to think'n what could be taking place, and for me it is[INDENT][INDENT][INDENT]seek and ye shall find
[/INDENT]
[/INDENT]
[/INDENT]


Another step in the right direction!!! I removed GDM and LightDM, reinstalled LightDM and guess what? It loaded, and logged in perfectly... but no nvidia as of yet... Is there a log or command that I should check now that we are passed that issue?

---

### Post by Bashing-om on 2015-01-30
zan-public; Well, Glory be !

Ok, can you activate 'nvidia-settings' ? Any options available to change the graphics set ?
And yeah, there is a terminal way, at the moment the command escapes me.

But there is light on the subject.

---

### Post by zan-public on 2015-01-30
Yes, the Prime page is there, but when I try to switch to nvidia, I get "Error:" With nothing after it.

---

### Post by MAFoElffen on 2015-01-30
NVidia is trying to load but fails. I'm assuming that is because  there are multiple versions of nVidia packages installed "over" each other. That is not always a good idea. The binary nvidia driver nvidia-installer from NVidia, removes previous versions that are present before installing anything new. "jockey" (the alternate driver installer) is supposed to work this way. That is how the install scripts inside Ubuntu's nvidia driver deb packages are supposed to work also, but doesn't always catch those. The problem with that, is when the newer package installs, it doesn't always see the pieces as part of another version, or see's a piece so doesn't know it needs to install a newer piece in place of the older, so skips installing the newer, so ends of with a mix-match of pieces that don't work together, because they are different versions of code.

That is why nVidia's logic to get around that is to remove everything first, and just start fresh. Simplicity.

So using that same logic, what I would recommend is doing a remove/purge for each of those packages (to make sure there is nothing left), then start a driver install cleanly.

After installing fresh, then run those diagnostic commands again to make sure everything went kosher with the install. 

Since that is a major stumbling block, there is no sense in doing anything else until that is straightened out. Not correcting that now is not going to let any other fix be effective. 

Will check back later.

---

### Post by zan-public on 2015-01-30
We have actually done this each step of the way. When the ppa nvidia packages wouldn't work, I purged them out. When the nvidia driver binary that I downloaded from nvidia didn't work, I ran it again with the remove option. Every time I go in another direction, I clean out what ever is in place first. Right now, we have nothing but the 346 ppa driver installed. That's it. Where do you see the multiple version of nvidia installed over each other? Was it in a command that I posted?

---

### Post by MAFoElffen on 2015-01-31
I response to me, you had posted:
```
$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                         0.7-2ubuntu1                                           amd64        Interface for toggling the power on nVidia Optimus video cards
[COLOR=#ff8c00]rc  libcuda1-304                                          304.125-0ubuntu0.0.1                                   amd64        NVIDIA CUDA runtime library
ii  libcuda1-340                                          340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA CUDA runtime library
rc  libcuda1-346                                          346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA CUDA runtime library
[/COLOR][COLOR=#008000]ii  nvidia-340                                            340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-346                                            346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
[/COLOR][COLOR=#ff0000]ii  nvidia-libopencl1-340                                 340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-libopencl1-346                                 346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL Driver and ICD Loader library
[/COLOR][COLOR=#40e0d0]ii  nvidia-opencl-icd-340                                 340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-346                                 346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL ICD
[/COLOR]ii  nvidia-prime                                          0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       346.35-100ubuntu100~ppa0~trusty                        amd64        Tool for configuring the NVIDIA graphics driver

```
A little confusion there, Look at the first field of output about, then decode it with the key below:

First letter -> desired package state ("selection state"):
i ... install
r ... remove/deinstall


Second letter -> current package state:
i ... installed
c ... config-files (only the config files are installed)

If there was a third letter there, that would mean it had an error state:
r ... reinst-required (package broken, reinstallation required)

If you look at that, what is installed is cuda v340, nvidia v340 & opencli v340... but you have config files for newer v346.

Looking at my NVidia Boxes here... mine show rc on the older packages, where just the config files remain, and ii on all the newest of the packages. That sort of gives me the impression that your driver version 346 didn't go right...

---

### Post by zan-public on 2015-01-31
> **MAFoElffen said:**
> I response to me, you had posted:
```
$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                         0.7-2ubuntu1                                           amd64        Interface for toggling the power on nVidia Optimus video cards
[COLOR=#ff8c00]rc  libcuda1-304                                          304.125-0ubuntu0.0.1                                   amd64        NVIDIA CUDA runtime library
ii  libcuda1-340                                          340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA CUDA runtime library
rc  libcuda1-346                                          346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA CUDA runtime library
[/COLOR][COLOR=#008000]ii  nvidia-340                                            340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-346                                            346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
[/COLOR][COLOR=#ff0000]ii  nvidia-libopencl1-340                                 340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-libopencl1-346                                 346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL Driver and ICD Loader library
[/COLOR][COLOR=#40e0d0]ii  nvidia-opencl-icd-340                                 340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-346                                 346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL ICD
[/COLOR]ii  nvidia-prime                                          0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       346.35-100ubuntu100~ppa0~trusty                        amd64        Tool for configuring the NVIDIA graphics driver

```
A little confusion there, Look at the first field of output about, then decode it with the key below:

First letter -> desired package state ("selection state"):
i ... install
r ... remove/deinstall


Second letter -> current package state:
i ... installed
c ... config-files (only the config files are installed)

If there was a third letter there, that would mean it had an error state:
r ... reinst-required (package broken, reinstallation required)

If you look at that, what is installed is cuda v340, nvidia v340 & opencli v340... but you have config files for newer v346.

Looking at my NVidia Boxes here... mine show rc on the older packages, where just the config files remain, and ii on all the newest of the packages. That sort of gives me the impression that your driver version 346 didn't go right...

I SEE!!! Ok, I ran that command again, and this is what it gives me...

```
$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                         0.7-2ubuntu1                                           amd64        Interface for toggling the power on nVidia Optimus video cards
rc  libcuda1-304                                          304.125-0ubuntu0.0.1                                   amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                          340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA CUDA runtime library
ii  libcuda1-346                                          346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA CUDA runtime library
ii  nvidia-346                                            346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-libopencl1-340                                 340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-libopencl1-346                                 346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-opencl-icd-340                                 340.76-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-346                                 346.35-100ubuntu100~ppa0~trusty                        amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings
```

So It looks like 346 is the only one installed at this point, (thank you so much for explaining the ii/rc codes) and while it looks like I had a 340+346 before (Not sure how I did that?) I think all that is corrected now. 

Is there an easy way to scrap the config files and all other traces of the stuff I do not want so that it does not show or effect anything, and if so, is that even advisable?

---

### Post by startas on 2015-01-31
Ok, so i managed to get bumblebee to work with nvidia 346 drivers on ubuntu 15.04, but should work on any other version, run commands in this order :
Reboot into kernel you want to use - i used kernel 3.19 rc6.
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo add-apt-repository ppa:mamarley/nvidia
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia primus
sudo apt-get install nvidia-346 nvidia-settings
```

```
sudo gedit /etc/bumblebee/bumblebee.conf
```
change lines with these numbers to look like this :
line 22 - Driver=nvidia 
line 55 - KernelDriver=nvidia-346 
line 58 - LibraryPath=/usr/lib/nvidia-346:/usr/lib32/nvidia-346 
line 61 - XorgModulePath=/usr/lib/nvidia-346/xorg,/usr/lib/xorg/modules
save file, exit it.

```
sudo apt-get install --reinstall bbswitch-dkms
sudo /etc/init.d/bumblebeed stop
sudo /etc/init.d/bumblebeed start
```
restart pc.

I found these instructions for ubuntu 13.10 and nvidia 331 drivers, but it worked for me on 15.04 with nvidia 346.35 too :
```
primusrun glxinfo
```
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 840M/PCIe/SSE2
OpenGL core profile version string: 4.4.0 NVIDIA 346.35
OpenGL core profile shading language version string: 4.40 NVIDIA via Cg compiler
OpenGL version string: 4.5.0 NVIDIA 346.35
OpenGL shading language version string: 4.50 NVIDIA

---

### Post by Bashing-om on 2015-02-01
zan-public; Moving on along;
Yes:
> 
Is there an easy way to scrap the config files and all other traces of the stuff I do not want so that it does not show or effect anything, and if so, is that even advisable?

While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package; The state is rc, the package is removed, but the config files are not removed.
To remove all the packages marked as 'rc' execute the following command.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

Let's get a new look at Xorg, see what it has to relate as to the Nvidia driver:
```

cat /var/log/Xorg.0.log

```

Did it build ?
-----------------------------------
@startas; Great !

Good to know that BumbleBee is still supported .
Just goes to confirm -> where there is a will there is a way.
-------------------------------

[INDENT][INDENT]if at 1st you do not succeed 
[INDENT][INDENT][INDENT]try try again (sky diving excepted)
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-01
> **Bashing-om said:**
> zan-public; Moving on along;
Yes:

While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package; The state is rc, the package is removed, but the config files are not removed.
To remove all the packages marked as 'rc' execute the following command.
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

Let's get a new look at Xorg, see what it has to relate as to the Nvidia driver:
```

cat /var/log/Xorg.0.log

```

Did it build ?
-----------------------------------
@startas; Great !

Good to know that BumbleBee is still supported .
Just goes to confirm -> where there is a will there is a way.
-------------------------------[INDENT][INDENT]if at 1st you do not succeed[INDENT][INDENT][INDENT]try try again (sky diving excepted)
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



```
$ cat /var/log/Xorg.0.log
[    20.459] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    20.459] X Protocol Version 11, Revision 0
[    20.459] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[    20.459] Current Operating System: Linux Odin 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64
[    20.459] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-44-generic.efi.signed root=UUID=f1544fc7-e2ba-4d6d-b3e4-451064c75b80 ro quiet splash vt.handoff=7
[    20.459] Build Date: 10 December 2014  06:15:52PM
[    20.459] xorg-server 2:1.15.1-0ubuntu2.6 (For technical support please see http://www.ubuntu.com/support) 
[    20.459] Current version of pixman: 0.30.2
[    20.459]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.459] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.459] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb  1 13:51:31 2015
[    20.545] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.577] (==) No Layout section.  Using the first Screen section.
[    20.577] (==) No screen section available. Using defaults.
[    20.577] (**) |-->Screen "Default Screen Section" (0)
[    20.577] (**) |   |-->Monitor "<default monitor>"
[    20.577] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    20.577] (==) Automatically adding devices
[    20.577] (==) Automatically enabling devices
[    20.577] (==) Automatically adding GPU devices
[    20.577] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.577]     Entry deleted from font path.
[    20.577] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.577]     Entry deleted from font path.
[    20.577] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.577]     Entry deleted from font path.
[    20.577] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.577]     Entry deleted from font path.
[    20.577] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.577]     Entry deleted from font path.
[    20.577] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    20.577] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.577] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.577] (II) Loader magic: 0x7f8dd052ed40
[    20.577] (II) Module ABI versions:
[    20.577]     X.Org ANSI C Emulation: 0.4
[    20.577]     X.Org Video Driver: 15.0
[    20.577]     X.Org XInput driver : 20.0
[    20.577]     X.Org Server Extension : 8.0
[    20.577] (II) xfree86: Adding drm device (/dev/dri/card0)
[    20.577] (II) xfree86: Adding drm device (/dev/dri/card1)
[    20.579] (--) PCI:*(0:0:2:0) 8086:0416:103c:1968 rev 6, Mem @ 0xb7000000/4194304, 0xc0000000/268435456, I/O @ 0x00008000/64
[    20.579] (--) PCI: (0:7:0:0) 10de:1341:103c:21a1 rev 162, Mem @ 0xb5000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00006000/128
[    20.579] Initializing built-in extension Generic Event Extension
[    20.579] Initializing built-in extension SHAPE
[    20.579] Initializing built-in extension MIT-SHM
[    20.579] Initializing built-in extension XInputExtension
[    20.579] Initializing built-in extension XTEST
[    20.579] Initializing built-in extension BIG-REQUESTS
[    20.579] Initializing built-in extension SYNC
[    20.579] Initializing built-in extension XKEYBOARD
[    20.579] Initializing built-in extension XC-MISC
[    20.579] Initializing built-in extension SECURITY
[    20.579] Initializing built-in extension XINERAMA
[    20.579] Initializing built-in extension XFIXES
[    20.579] Initializing built-in extension RENDER
[    20.579] Initializing built-in extension RANDR
[    20.579] Initializing built-in extension COMPOSITE
[    20.579] Initializing built-in extension DAMAGE
[    20.579] Initializing built-in extension MIT-SCREEN-SAVER
[    20.579] Initializing built-in extension DOUBLE-BUFFER
[    20.579] Initializing built-in extension RECORD
[    20.579] Initializing built-in extension DPMS
[    20.579] Initializing built-in extension Present
[    20.579] Initializing built-in extension DRI3
[    20.579] Initializing built-in extension X-Resource
[    20.579] Initializing built-in extension XVideo
[    20.579] Initializing built-in extension XVideo-MotionCompensation
[    20.579] Initializing built-in extension SELinux
[    20.579] Initializing built-in extension XFree86-VidModeExtension
[    20.579] Initializing built-in extension XFree86-DGA
[    20.579] Initializing built-in extension XFree86-DRI
[    20.579] Initializing built-in extension DRI2
[    20.579] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    20.579] (II) "glx" will be loaded by default.
[    20.579] (WW) "xmir" is not to be loaded by default. Skipping.
[    20.579] (II) LoadModule: "glx"
[    20.617] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.217] (II) Module glx: vendor="X.Org Foundation"
[    21.217]     compiled for 1.15.1, module version = 1.0.0
[    21.217]     ABI class: X.Org Server Extension, version 8.0
[    21.217] (==) AIGLX enabled
[    21.217] Loading extension GLX
[    21.217] (==) Matched intel as autoconfigured driver 0
[    21.217] (==) Matched nvidia as autoconfigured driver 1
[    21.217] (==) Matched nouveau as autoconfigured driver 2
[    21.217] (==) Matched intel as autoconfigured driver 3
[    21.217] (==) Matched modesetting as autoconfigured driver 4
[    21.217] (==) Matched fbdev as autoconfigured driver 5
[    21.217] (==) Matched vesa as autoconfigured driver 6
[    21.217] (==) Assigned the driver to the xf86ConfigLayout
[    21.217] (II) LoadModule: "intel"
[    21.218] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.331] (II) Module intel: vendor="X.Org Foundation"
[    21.331]     compiled for 1.15.1, module version = 2.99.917
[    21.331]     Module class: X.Org Video Driver
[    21.331]     ABI class: X.Org Video Driver, version 15.0
[    21.331] (II) LoadModule: "nvidia"
[    21.331] (WW) Warning, couldn't open module nvidia
[    21.331] (II) UnloadModule: "nvidia"
[    21.331] (II) Unloading nvidia
[    21.331] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    21.331] (II) LoadModule: "nouveau"
[    21.331] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    21.384] (II) Module nouveau: vendor="X.Org Foundation"
[    21.384]     compiled for 1.15.1, module version = 1.0.11
[    21.384]     Module class: X.Org Video Driver
[    21.384]     ABI class: X.Org Video Driver, version 15.0
[    21.384] (II) LoadModule: "modesetting"
[    21.384] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    21.384] (II) Module modesetting: vendor="X.Org Foundation"
[    21.384]     compiled for 1.15.0, module version = 0.8.1
[    21.384]     Module class: X.Org Video Driver
[    21.384]     ABI class: X.Org Video Driver, version 15.0
[    21.384] (II) LoadModule: "fbdev"
[    21.384] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.384] (II) Module fbdev: vendor="X.Org Foundation"
[    21.384]     compiled for 1.15.0, module version = 0.4.4
[    21.384]     Module class: X.Org Video Driver
[    21.384]     ABI class: X.Org Video Driver, version 15.0
[    21.384] (II) LoadModule: "vesa"
[    21.384] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.384] (II) Module vesa: vendor="X.Org Foundation"
[    21.384]     compiled for 1.15.0, module version = 2.3.3
[    21.384]     Module class: X.Org Video Driver
[    21.384]     ABI class: X.Org Video Driver, version 15.0
[    21.384] (==) Matched intel as autoconfigured driver 0
[    21.384] (==) Matched nvidia as autoconfigured driver 1
[    21.384] (==) Matched nouveau as autoconfigured driver 2
[    21.384] (==) Matched intel as autoconfigured driver 3
[    21.384] (==) Matched modesetting as autoconfigured driver 4
[    21.384] (==) Matched fbdev as autoconfigured driver 5
[    21.384] (==) Matched vesa as autoconfigured driver 6
[    21.384] (==) Assigned the driver to the xf86ConfigLayout
[    21.384] (II) LoadModule: "intel"
[    21.384] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.384] (II) Module intel: vendor="X.Org Foundation"
[    21.384]     compiled for 1.15.1, module version = 2.99.917
[    21.384]     Module class: X.Org Video Driver
[    21.384]     ABI class: X.Org Video Driver, version 15.0
[    21.384] (II) UnloadModule: "intel"
[    21.384] (II) Unloading intel
[    21.385] (II) Failed to load module "intel" (already loaded, 32653)
[    21.385] (II) LoadModule: "nvidia"
[    21.385] (WW) Warning, couldn't open module nvidia
[    21.385] (II) UnloadModule: "nvidia"
[    21.385] (II) Unloading nvidia
[    21.385] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    21.385] (II) LoadModule: "nouveau"
[    21.385] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    21.385] (II) Module nouveau: vendor="X.Org Foundation"
[    21.385]     compiled for 1.15.1, module version = 1.0.11
[    21.385]     Module class: X.Org Video Driver
[    21.385]     ABI class: X.Org Video Driver, version 15.0
[    21.385] (II) UnloadModule: "nouveau"
[    21.385] (II) Unloading nouveau
[    21.385] (II) Failed to load module "nouveau" (already loaded, 0)
[    21.385] (II) LoadModule: "modesetting"
[    21.385] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    21.385] (II) Module modesetting: vendor="X.Org Foundation"
[    21.385]     compiled for 1.15.0, module version = 0.8.1
[    21.385]     Module class: X.Org Video Driver
[    21.385]     ABI class: X.Org Video Driver, version 15.0
[    21.385] (II) UnloadModule: "modesetting"
[    21.385] (II) Unloading modesetting
[    21.385] (II) Failed to load module "modesetting" (already loaded, 0)
[    21.385] (II) LoadModule: "fbdev"
[    21.385] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.385] (II) Module fbdev: vendor="X.Org Foundation"
[    21.385]     compiled for 1.15.0, module version = 0.4.4
[    21.385]     Module class: X.Org Video Driver
[    21.385]     ABI class: X.Org Video Driver, version 15.0
[    21.385] (II) UnloadModule: "fbdev"
[    21.385] (II) Unloading fbdev
[    21.385] (II) Failed to load module "fbdev" (already loaded, 0)
[    21.385] (II) LoadModule: "vesa"
[    21.385] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.385] (II) Module vesa: vendor="X.Org Foundation"
[    21.385]     compiled for 1.15.0, module version = 2.3.3
[    21.385]     Module class: X.Org Video Driver
[    21.385]     ABI class: X.Org Video Driver, version 15.0
[    21.385] (II) UnloadModule: "vesa"
[    21.385] (II) Unloading vesa
[    21.385] (II) Failed to load module "vesa" (already loaded, 0)
[    21.385] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    21.385] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    21.385] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    21.385] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    21.385] (II) NOUVEAU driver 
[    21.385] (II) NOUVEAU driver for NVIDIA chipset families :
[    21.385]     RIVA TNT        (NV04)
[    21.385]     RIVA TNT2       (NV05)
[    21.385]     GeForce 256     (NV10)
[    21.385]     GeForce 2       (NV11, NV15)
[    21.385]     GeForce 4MX     (NV17, NV18)
[    21.385]     GeForce 3       (NV20)
[    21.385]     GeForce 4Ti     (NV25, NV28)
[    21.386]     GeForce FX      (NV3x)
[    21.386]     GeForce 6       (NV4x)
[    21.386]     GeForce 7       (G7x)
[    21.386]     GeForce 8       (G8x)
[    21.386]     GeForce GTX 200 (NVA0)
[    21.386]     GeForce GTX 400 (NVC0)
[    21.386] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    21.386] (II) FBDEV: driver for framebuffer: fbdev
[    21.386] (II) VESA: driver for VESA chipsets: vesa
[    21.386] (++) using VT number 7


[    21.386] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    21.386] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150127.4bbd1023-0ubuntu0sarvatt~trusty (Robert Hooker <sarvatt@ubuntu.com>)
[    21.386] (II) intel(0): SNA compiled for use with valgrind
[    21.386] (EE) [drm] KMS not enabled
[    21.386] (WW) Falling back to old probe method for modesetting
[    21.386] (WW) Falling back to old probe method for fbdev
[    21.386] (II) Loading sub module "fbdevhw"
[    21.386] (II) LoadModule: "fbdevhw"
[    21.386] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.386] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.386]     compiled for 1.15.1, module version = 0.0.2
[    21.386]     ABI class: X.Org Video Driver, version 15.0
[    21.386] (WW) Falling back to old probe method for vesa
[    21.386] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    21.386] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[    21.386] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    21.386] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    21.386] (==) intel(0): RGB weight 888
[    21.386] (==) intel(0): Default visual is TrueColor
[    21.387] (II) intel(0): Output eDP1 has no monitor section
[    21.387] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output eDP1
[    21.387] (II) intel(0): Enabled output eDP1
[    21.387] (II) intel(0): Output VGA1 has no monitor section
[    21.387] (II) intel(0): Enabled output VGA1
[    21.387] (II) intel(0): Output HDMI1 has no monitor section
[    21.387] (II) intel(0): Enabled output HDMI1
[    21.387] (--) intel(0): Using a maximum size of 64x64 for hardware cursors
[    21.387] (II) intel(0): Output VIRTUAL1 has no monitor section
[    21.387] (II) intel(0): Enabled output VIRTUAL1
[    21.387] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[    21.387] (==) intel(0): TearFree disabled
[    21.387] (==) intel(0): DPI set to (96, 96)
[    21.387] (II) Loading sub module "dri2"
[    21.387] (II) LoadModule: "dri2"
[    21.387] (II) Module "dri2" already built-in
[    21.387] (II) Loading sub module "present"
[    21.387] (II) LoadModule: "present"
[    21.387] (WW) Warning, couldn't open module present
[    21.387] (II) UnloadModule: "present"
[    21.387] (II) Unloading present
[    21.387] (EE) intel: Failed to load module "present" (module does not exist, 0)
[    21.389] (II) UnloadModule: "fbdev"
[    21.389] (II) Unloading fbdev
[    21.389] (II) UnloadSubModule: "fbdevhw"
[    21.389] (II) Unloading fbdevhw
[    21.389] (II) UnloadModule: "vesa"
[    21.389] (II) Unloading vesa
[    21.389] (==) Depth 24 pixmap format is 32 bpp
[    21.389] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    21.389] (==) intel(0): Backing store enabled
[    21.389] (==) intel(0): Silken mouse enabled
[    21.389] (II) intel(0): HW Cursor enabled
[    21.389] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.389] (==) intel(0): DPMS enabled
[    21.389] (==) intel(0): Display hotplug detection enabled
[    21.389] (II) intel(0): [DRI2] Setup complete
[    21.389] (II) intel(0): [DRI2]   DRI driver: i965
[    21.389] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    21.389] (II) intel(0): direct rendering: DRI2 enabled
[    21.389] (--) RandR disabled
[    21.392] (II) SELinux: Disabled on system
[    21.471] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    21.471] (II) AIGLX: enabled GLX_ARB_create_context
[    21.471] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    21.471] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    21.471] (II) AIGLX: enabled GLX_INTEL_swap_event
[    21.471] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    21.471] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    21.471] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    21.471] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    21.471] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    21.471] (II) AIGLX: Loaded and initialized i965
[    21.471] (II) GLX: Initialized DRI2 GL provider for screen 0
[    21.473] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    21.473] (II) intel(0): Setting screen physical size to 508 x 285
[    21.478] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.479] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    21.479] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.479] (II) LoadModule: "evdev"
[    21.479] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.493] (II) Module evdev: vendor="X.Org Foundation"
[    21.493]     compiled for 1.15.0, module version = 2.8.2
[    21.493]     Module class: X.Org XInput Driver
[    21.493]     ABI class: X.Org XInput driver, version 20.0
[    21.493] (II) Using input driver 'evdev' for 'Power Button'
[    21.493] (**) Power Button: always reports core events
[    21.493] (**) evdev: Power Button: Device: "/dev/input/event2"
[    21.493] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.493] (--) evdev: Power Button: Found keys
[    21.493] (II) evdev: Power Button: Configuring as keyboard
[    21.493] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    21.493] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    21.493] (**) Option "xkb_rules" "evdev"
[    21.493] (**) Option "xkb_model" "pc105"
[    21.493] (**) Option "xkb_layout" "us"
[    21.493] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[    21.493] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    21.493] (II) Using input driver 'evdev' for 'Video Bus'
[    21.493] (**) Video Bus: always reports core events
[    21.493] (**) evdev: Video Bus: Device: "/dev/input/event11"
[    21.493] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    21.493] (--) evdev: Video Bus: Found keys
[    21.493] (II) evdev: Video Bus: Configuring as keyboard
[    21.493] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input13/event11"
[    21.493] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    21.493] (**) Option "xkb_rules" "evdev"
[    21.493] (**) Option "xkb_model" "pc105"
[    21.494] (**) Option "xkb_layout" "us"
[    21.494] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    21.494] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    21.494] (II) Using input driver 'evdev' for 'Video Bus'
[    21.494] (**) Video Bus: always reports core events
[    21.494] (**) evdev: Video Bus: Device: "/dev/input/event10"
[    21.494] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    21.494] (--) evdev: Video Bus: Found keys
[    21.494] (II) evdev: Video Bus: Configuring as keyboard
[    21.494] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:44/LNXVIDEO:00/input/input12/event10"
[    21.494] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    21.494] (**) Option "xkb_rules" "evdev"
[    21.494] (**) Option "xkb_model" "pc105"
[    21.494] (**) Option "xkb_layout" "us"
[    21.494] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    21.494] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.494] (II) Using input driver 'evdev' for 'Power Button'
[    21.494] (**) Power Button: always reports core events
[    21.494] (**) evdev: Power Button: Device: "/dev/input/event1"
[    21.494] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.494] (--) evdev: Power Button: Found keys
[    21.494] (II) evdev: Power Button: Configuring as keyboard
[    21.494] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    21.494] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    21.494] (**) Option "xkb_rules" "evdev"
[    21.494] (**) Option "xkb_model" "pc105"
[    21.494] (**) Option "xkb_layout" "us"
[    21.494] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    21.494] (II) No input driver specified, ignoring this device.
[    21.494] (II) This device may have been added with another device file.
[    21.494] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.1/0000:07:00.0/drm/card0
[    21.494] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    21.495] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:02.0/drm/card1
[    21.495] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[    21.495] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event14)
[    21.495] (II) No input driver specified, ignoring this device.
[    21.495] (II) This device may have been added with another device file.
[    21.495] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event13)
[    21.495] (II) No input driver specified, ignoring this device.
[    21.495] (II) This device may have been added with another device file.
[    21.495] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event12)
[    21.495] (II) No input driver specified, ignoring this device.
[    21.495] (II) This device may have been added with another device file.
[    21.495] (II) config/udev: Adding input device eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00 (/dev/input/event8)
[    21.495] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Applying InputClass "evdev touchscreen catchall"
[    21.495] (II) Using input driver 'evdev' for 'eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00'
[    21.495] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: always reports core events
[    21.495] (**) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Device: "/dev/input/event8"
[    21.495] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Using mtdev for this device
[    21.495] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Vendor 0xeef Product 0xa80f
[    21.495] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found absolute axes
[    21.495] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found absolute multitouch axes
[    21.495] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: No buttons found, faking one.
[    21.495] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found x and y absolute axes
[    21.495] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found absolute touchscreen
[    21.495] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Configuring as touchscreen
[    21.495] (**) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: YAxisMapping: buttons 4 and 5
[    21.495] (**) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    21.495] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-13/2-13:1.0/input/input9/event8"
[    21.495] (II) XINPUT: Adding extended input device "eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00" (type: TOUCHSCREEN, id 10)
[    21.495] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: initialized for absolute axes.
[    21.495] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) keeping acceleration scheme 1
[    21.495] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) acceleration profile 0
[    21.495] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) acceleration factor: 2.000
[    21.495] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) acceleration threshold: 4
[    21.495] (II) config/udev: Adding input device eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00 (/dev/input/mouse1)
[    21.495] (II) No input driver specified, ignoring this device.
[    21.495] (II) This device may have been added with another device file.
[    21.496] (II) config/udev: Adding input device HP Truevision HD (/dev/input/event9)
[    21.496] (**) HP Truevision HD: Applying InputClass "evdev keyboard catchall"
[    21.496] (II) Using input driver 'evdev' for 'HP Truevision HD'
[    21.496] (**) HP Truevision HD: always reports core events
[    21.496] (**) evdev: HP Truevision HD: Device: "/dev/input/event9"
[    21.496] (--) evdev: HP Truevision HD: Vendor 0x64e Product 0xc341
[    21.496] (--) evdev: HP Truevision HD: Found keys
[    21.496] (II) evdev: HP Truevision HD: Configuring as keyboard
[    21.496] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-7/2-7:1.0/input/input11/event9"
[    21.496] (II) XINPUT: Adding extended input device "HP Truevision HD" (type: KEYBOARD, id 11)
[    21.496] (**) Option "xkb_rules" "evdev"
[    21.496] (**) Option "xkb_model" "pc105"
[    21.496] (**) Option "xkb_layout" "us"
[    21.496] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event16)
[    21.496] (II) No input driver specified, ignoring this device.
[    21.496] (II) This device may have been added with another device file.
[    21.496] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event15)
[    21.496] (II) No input driver specified, ignoring this device.
[    21.496] (II) This device may have been added with another device file.
[    21.496] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    21.496] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    21.496] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    21.496] (**) AT Translated Set 2 keyboard: always reports core events
[    21.496] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    21.496] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    21.496] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    21.496] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    21.496] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    21.496] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    21.496] (**) Option "xkb_rules" "evdev"
[    21.496] (**) Option "xkb_model" "pc105"
[    21.496] (**) Option "xkb_layout" "us"
[    21.496] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[    21.496] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    21.496] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    21.496] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    21.496] (II) LoadModule: "synaptics"
[    21.496] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    21.497] (II) Module synaptics: vendor="X.Org Foundation"
[    21.497]     compiled for 1.15.0, module version = 1.7.4
[    21.497]     Module class: X.Org XInput Driver
[    21.497]     ABI class: X.Org XInput driver, version 20.0
[    21.497] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    21.497] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    21.497] (**) Option "Device" "/dev/input/event4"
[    21.516] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    21.516] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5660 (res 41)
[    21.516] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4702 (res 56)
[    21.516] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    21.516] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    21.516] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    21.516] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    21.516] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    21.516] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    21.516] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    21.528] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[    21.528] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[    21.528] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    21.528] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    21.528] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[    21.528] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    21.528] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    21.528] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    21.528] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    21.528] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    21.528] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    21.528] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    21.528] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[    21.528] (II) No input driver specified, ignoring this device.
[    21.528] (II) This device may have been added with another device file.
[    21.528] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    21.529] (II) No input driver specified, ignoring this device.
[    21.529] (II) This device may have been added with another device file.
[    21.529] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[    21.529] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    21.529] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    21.529] (**) HP WMI hotkeys: always reports core events
[    21.529] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event7"
[    21.529] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    21.529] (--) evdev: HP WMI hotkeys: Found keys
[    21.529] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    21.529] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event7"
[    21.529] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 14)
[    21.529] (**) Option "xkb_rules" "evdev"
[    21.529] (**) Option "xkb_model" "pc105"
[    21.529] (**) Option "xkb_layout" "us"
[    21.530] (II) config/udev: Adding input device HP Wireless hotkeys (/dev/input/event5)
[    21.530] (**) HP Wireless hotkeys: Applying InputClass "evdev keyboard catchall"
[    21.530] (II) Using input driver 'evdev' for 'HP Wireless hotkeys'
[    21.530] (**) HP Wireless hotkeys: always reports core events
[    21.530] (**) evdev: HP Wireless hotkeys: Device: "/dev/input/event5"
[    21.530] (--) evdev: HP Wireless hotkeys: Vendor 0 Product 0
[    21.530] (--) evdev: HP Wireless hotkeys: Found keys
[    21.530] (II) evdev: HP Wireless hotkeys: Configuring as keyboard
[    21.530] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event5"
[    21.530] (II) XINPUT: Adding extended input device "HP Wireless hotkeys" (type: KEYBOARD, id 15)
[    21.530] (**) Option "xkb_rules" "evdev"
[    21.530] (**) Option "xkb_model" "pc105"
[    21.530] (**) Option "xkb_layout" "us"
[    21.584] (II) intel(0): EDID vendor "AUO", prod id 8605
[    21.584] (II) intel(0): Printing DDC gathered Modelines:
[    21.584] (II) intel(0): Modeline "1920x1080"x0.0  140.50  1920 1968 2068 2104  1080 1083 1089 1112 -hsync -vsync (66.8 kHz eP)
[    21.584] (II) intel(0): Modeline "1920x1080"x0.0   93.67  1920 1968 2068 2104  1080 1083 1089 1112 -hsync -vsync (44.5 kHz e)
[    22.864] (II) intel(0): resizing framebuffer to 8x8
[    23.084] (II) intel(0): resizing framebuffer to 1920x1080
[    23.084] (II) intel(0): switch to mode 1920x1080@60.1 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    48.665] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.827] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    48.896] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    51.996] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/mouse2)
[    51.996] (II) No input driver specified, ignoring this device.
[    51.996] (II) This device may have been added with another device file.
[    51.996] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/event17)
[    51.996] (**) Logitech Unifying Device. Wireless PID:101a: Applying InputClass "evdev pointer catchall"
[    51.996] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101a'
[    51.996] (**) Logitech Unifying Device. Wireless PID:101a: always reports core events
[    51.996] (**) evdev: Logitech Unifying Device. Wireless PID:101a: Device: "/dev/input/event17"
[    51.996] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Vendor 0x46d Product 0xc52b
[    51.996] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found 20 mouse buttons
[    51.996] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found scroll wheel(s)
[    51.996] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found relative axes
[    51.996] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found x and y relative axes
[    51.996] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Configuring as mouse
[    51.996] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Adding scrollwheel support
[    51.996] (**) evdev: Logitech Unifying Device. Wireless PID:101a: YAxisMapping: buttons 4 and 5
[    51.996] (**) evdev: Logitech Unifying Device. Wireless PID:101a: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    51.996] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-3/2-3:1.2/0003:046D:C52B.0003/input/input19/event17"
[    51.996] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101a" (type: MOUSE, id 16)
[    51.996] (II) evdev: Logitech Unifying Device. Wireless PID:101a: initialized for relative axes.
[    51.996] (**) Logitech Unifying Device. Wireless PID:101a: (accel) keeping acceleration scheme 1
[    51.996] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration profile 0
[    51.996] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration factor: 2.000
[    51.996] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration threshold: 4
[    54.907] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm



```
So... I am not sure that is going on in this log... but I hope you can make heads or tails of it.

---

### Post by Bashing-om on 2015-02-01
zan-public; Still afloundering.


As I so not see Nvidia build:
> 
21.331] (II) LoadModule: "nvidia"
[    21.331] (WW) Warning, couldn't open module nvidia
[    21.331] (II) UnloadModule: "nvidia"
[    21.331] (II) Unloading nvidia
[    21.331] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    21.331] (II) LoadModule: "nouveau"


So, the system loads "nouveau" to drive the Nvidia card
> 
21.331] (II) LoadModule: "nouveau"
[    21.331] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    21.384] (II) Module nouveau: vendor="X.Org Foundation"
[    21.384]     compiled for 1.15.1, module version = 1.0.11
[    21.384]     Module class: X.Org Video Driver
[    21.384]     ABI class: X.Org Video Driver, version 15.0

HUH ?
But where/how is this coming about ?
> 
[    21.384] (==) Matched nvidia as autoconfigured driver 1


And to compound what I do not understand, Intel :
> 
21.389] (II) intel(0): [DRI2] Setup complete
[    21.389] (II) intel(0): [DRI2]   DRI driver: i965
[ 21.471] (II) AIGLX: Loaded and initialized i965


HUH ? and then we have:
> 
[    21.386] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730


----------------------------
So, what does the system see ? post back the output of:
```

sudo lshw -C display

```

Depending on that output; it is really going to make me wonder what 'nvidia-prime' is doing, and what is more, how to tell ?
What tools are at our disposal to look at nvidia-prime ?

So I be alook'n to see what I can learn about nvidia-prime.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by MAFoElffen on 2015-02-01
Not sure on hybrids, but I thought even on hybrids, that they had to switch BIOS from the HW intel to NVidia for it to use NVidia. The uses 2 xorg.conf files... one pointing to the intel GPU HW address and intel driver, and the other for the NVidia GPU HW address, and the NVidia driver. Bumblebee does the BIOS calls for the hardware switch and then copies over the appropraite xorg.conf file, so that only one is being used at a time to the one display...

Thinking that the newer NVidia Prime should be doing the same logic... But with this OP's is not. I don't see an xorg.conf file being used (in the Xorg.0.log)... so it is seeing both GPU's and trying to load both. Since it see's the Intel GPU, the BIOS must be switched right now to Intel... So that would be logical that the NVidia is failing to load. But nouveau still loads. It is seeing both GPU's as active (on) at the same time? So it's trying to load all drivers at the same time? But since they both are connected to the same display, that's not going to work...

Please post
```

cat /etc/X11/xorg.conf
ls /etc/X11/
xrandr --listproviders
glxinfo | grep "OpenGL renderer"

```

It looks like it is implemented differently, as is has the NVidia driver active all the time and uses the Intel GPU as a sink... but does use one Xorg.conf file:
```

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    Option "NoLogo" "true"
    Option "DPI" "96 x 96"
    # Specify Nvidia PCI device
    BusID "PCI:1:0:0"
    # Make sure X starts also when no outputs are connected to the Nvidia chip
    Option "AllowEmptyInitialConfiguration"
EndSection
 
# Slave device
Section "Device"
    Identifier "intel"
    # Simple output, no full Intel driver
    Driver "modesetting"
    # BusID "PCI:0:2:0"
EndSection
 
Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection
 
Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
EndSection
 
# Make sure the Nvidia device is the first in the server
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

```

---

### Post by lotus49 on 2015-02-02
> **MAFoElffen said:**
> Not sure on hybrids, but I thought even on hybrids, that they had to switch BIOS from the HW intel to NVidia for it to use NVidia.
My laptop is a hybrid and until very recently, the xedgers nvidia-340 drivers worked well enough.  I have never touched the BIOS settings on my laptop apart from to change the boot order.  I certainly never disabled the Intel graphics.

---

### Post by zan-public on 2015-02-02
```
$ sudo lshw -C display
[sudo] password for zanahade: 
  *-display               
       description: 3D controller
       product: GM108M [GeForce 840M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:b5000000-b5ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:6000(size=128)
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:b7000000-b73fffff memory:c0000000-cfffffff ioport:8000(size=64)



```

```
$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory



```

```
$ ls /etc/X11/
app-defaults                      xorg.conf.01292015
core                              xorg.conf-backup-150110214450
cursors                           xorg.conf-backup-150110215230
default-display-manager           xorg.conf-backup-150110215743
default-display-manager.dpkg-tmp  xorg.conf.failsafe
fonts                             Xreset
rgb.txt                           Xreset.d
X                                 Xresources
xinit                             Xsession
xkb                               Xsession.d
xorg.conf.01142015                Xsession.options
xorg.conf.01222015                xsm
xorg.conf.01272015                Xwrapper.config
xorg.conf.01282015



```

```
$ xrandr --listproviders
Providers: number : 1
Provider 0: id: 0x47 cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 4 associated providers: 0 name:Intel



```

```
 $ glxinfo | grep "OpenGL renderer"
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile



```

---

### Post by Bashing-om on 2015-02-02
zan-public; Humm ...

Odd that there is no current /etc/X11/xorg.conf file.

Let's wait for MAFoElffen comment before we generate one.
Other than that I am still at a loss as to what is going on, and still seeking a means to find out.
The Nvidia driver obviously builds in the Xubuntu dual boot install. I sure do want to know why it will not build in this install.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-03
Boing!

---

### Post by Bashing-om on 2015-02-04
zan-public; OK, moving on .....

As advised, I do not have the skill sets to determine what is not taking place. All I do know is that the drivers are not being built. I do have a couple of ideas to 'try' that might "fix" or at last lead to additional info to point us in a resolution direction.

Generate the required xconf file:
```

sudo nvidia-xconfig

```
Did the file get generated ?
```

cat /etc/X11/xorg.conf

```

reboot to propagate the change in the operating system.

Make sure 'lightdm' is the controlling authority:
```

sudo dpkg-reconfigure lightdm

```

Now let's make sure xorg is in a happy state:
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
the-phigh flag, Using that forces it to autodetect.

I think at this point we should reboot and IF it comes up all rosy and 'nvidia-settings' is functional, we should re-write the image:
```

sudo update-initramfs -u

```

See what happens. too soon else to say what we might do If no driver(s) are in the Xorg.0.log .

When it is failing ->
[INDENT][INDENT]do something, right wrong, or otherwise -> do something
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-04
Ok... so, I ran some updates earlier, and now lightdm is broken again... (black screen) Ideas?

---

### Post by Bashing-om on 2015-02-04
> **zan-public said:**
> Ok... so, I ran some updates earlier, and now lightdm is broken again... (black screen) Ideas?


Graphics driver ? proprietary driver broke in the system upgrades - 
What results if you boot with the boot parameter "nomodeset" ('e' key to edit the boot parameters )
OR
boot "recovery" mode from grubs advanced options menu.

If you boot to the GUI we can surmise it is graphics driver related .

The never ending
[INDENT][INDENT][INDENT]why, OH why 
[/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-04
Ok, so... weirdness... I waited it out, did a ctrl+alt+f1 to go in and shut down, but when I did, the login screen flashed. So I ctrl+alt+f7 to get back and what do you know? I was able to login to the gui... That's not the weird part. Nvidia WAS WORKING! I was all "YAAAAAAY!!!" but then I rebooted to see if all was well... and... no. Not at all. I am back to a blank screen. Thoughts?

---

### Post by Bashing-om on 2015-02-04
zan-public; Your GUI does not like you ??

Seriuosly though, we know that the drivers did not build, maybe now they have ?

What results if you do:
```

sudo dpkg-reconfigure lightdm

```

[INDENT][INDENT]theys a rat about. somewhere
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-04
I did a purge of 346, installed 340... didn't work, so I purged 340, re-installed 346... and was back to pre-nvidia condition. Then the update, Lightdm failed and... you know the rest. I will try the command you listed, and let you know...

Yea, that got me nowhere. Still hung up on a blank screen. I obviously changed something in everything that happened today. I did have full nvidia for 1 whole boot cycle... So... if we can get lightdm to work, (crossing fingers) We SHOULD be all set...

Are there any tests I can run to help figure out the lightdm issue?

---

### Post by Bashing-om on 2015-02-04
zan-public; Hummm ..

Try:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall ubuntu-desktop

```
See what the system reports. What is really hurting us in trouble shooting is that with new hardware, we have no support for open source drivers. We have only the proprietary drivers and nothing to trade off too.

Boot up with nomodeset, do you have a GUI ?

I think I go see what I can find for drivers for this card ... maybe we can come up with an alternate (??).

Keeping in mind this is hybrid graphics and optimus technology -

[INDENT][INDENT]I do be think'n
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-05
Interesting, my system in the gui, says that the nvidia driver is open... so yea, I think it is lying to me. Anyway, I will be traveling quite a bit for work today, so I will have to do the -reinstall when I get home tonight... I'll let you know.

Ok, that's no good. Still black screen. Didn't get any errors in the process... I don't know what to further. Any ideas?

---

### Post by Bashing-om on 2015-02-06
zan-public; Yuk ...

As you have the 346 driver installed in the Xubuntu install, we know the driver is compatible with the hardware and the kernel.
We conclude there is something amiss with the ubuntu desktop that prevents the building of the drivers.

you did the commands in post # 77 and came up with a black screen - no driver at all loaded ... 
a) What graphics set is the system booting on ? Will the log files tell us anything ?
```

cat /var/log/Xorg.0.log
cat ~/.xsession-errors

```

b) I had expected the high level --reinstall of 'ubuntu-desktop' to have had some effect !

so let's see if 'compiz' is at fault :
```

sudo apt-get install --reinstall compiz ubuntu-desktop

```
Failing this, perhaps focus our attention directly on unity ?

I do not know enough about the unity desk top, perhaps we can both learn something here. All I presently know is that the graphics module is not building, and it is something to do with the desktop. I am thrashing my brain to come up with a means to see where the fault lies . 

[INDENT][INDENT]find the fault
[INDENT][INDENT][INDENT]we can fix the error
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-06
```
$[COLOR=#000000][FONT=Ubuntu Mono]cat /var/log/Xorg.0.log
[/FONT][/COLOR][    19.498] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    19.498] X Protocol Version 11, Revision 0
[    19.498] Build Operating System: Linux 3.2.0-70-generic x86_64 Ubuntu
[    19.498] Current Operating System: Linux Odin 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64
[    19.498] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-45-generic.efi.signed root=UUID=f1544fc7-e2ba-4d6d-b3e4-451064c75b80 ro quiet splash vt.handoff=7
[    19.498] Build Date: 10 December 2014  06:15:52PM
[    19.498] xorg-server 2:1.15.1-0ubuntu2.6 (For technical support please see http://www.ubuntu.com/support) 
[    19.498] Current version of pixman: 0.30.2
[    19.498] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    19.498] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    19.498] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb  6 12:10:12 2015
[    19.554] (==) Using config file: "/etc/X11/xorg.conf"
[    19.554] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    19.605] (==) ServerLayout "layout"
[    19.605] (**) |-->Screen "nvidia" (0)
[    19.605] (**) |   |-->Monitor "<default monitor>"
[    19.605] (**) |   |-->Device "nvidia"
[    19.605] (==) No monitor specified for screen "nvidia".
	Using a default monitor configuration.
[    19.605] (**) |-->Inactive Device "intel"
[    19.605] (==) Automatically adding devices
[    19.605] (==) Automatically enabling devices
[    19.605] (==) Automatically adding GPU devices
[    19.605] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    19.605] 	Entry deleted from font path.
[    19.605] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    19.605] 	Entry deleted from font path.
[    19.605] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    19.605] 	Entry deleted from font path.
[    19.605] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    19.605] 	Entry deleted from font path.
[    19.605] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    19.605] 	Entry deleted from font path.
[    19.605] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    19.605] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    19.605] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    19.605] (II) Loader magic: 0x7f66a76e3d40
[    19.605] (II) Module ABI versions:
[    19.605] 	X.Org ANSI C Emulation: 0.4
[    19.605] 	X.Org Video Driver: 15.0
[    19.605] 	X.Org XInput driver : 20.0
[    19.605] 	X.Org Server Extension : 8.0
[    19.605] (II) xfree86: Adding drm device (/dev/dri/card0)
[    19.606] (II) xfree86: Adding drm device (/dev/dri/card1)
[    19.607] (--) PCI:*(0:0:2:0) 8086:0416:103c:1968 rev 6, Mem @ 0xb7000000/4194304, 0xc0000000/268435456, I/O @ 0x00008000/64
[    19.607] (--) PCI: (0:7:0:0) 10de:1341:103c:21a1 rev 162, Mem @ 0xb5000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00006000/128
[    19.607] Initializing built-in extension Generic Event Extension
[    19.607] Initializing built-in extension SHAPE
[    19.607] Initializing built-in extension MIT-SHM
[    19.607] Initializing built-in extension XInputExtension
[    19.607] Initializing built-in extension XTEST
[    19.607] Initializing built-in extension BIG-REQUESTS
[    19.607] Initializing built-in extension SYNC
[    19.607] Initializing built-in extension XKEYBOARD
[    19.607] Initializing built-in extension XC-MISC
[    19.607] Initializing built-in extension SECURITY
[    19.607] Initializing built-in extension XINERAMA
[    19.607] Initializing built-in extension XFIXES
[    19.607] Initializing built-in extension RENDER
[    19.607] Initializing built-in extension RANDR
[    19.607] Initializing built-in extension COMPOSITE
[    19.607] Initializing built-in extension DAMAGE
[    19.607] Initializing built-in extension MIT-SCREEN-SAVER
[    19.607] Initializing built-in extension DOUBLE-BUFFER
[    19.607] Initializing built-in extension RECORD
[    19.607] Initializing built-in extension DPMS
[    19.607] Initializing built-in extension Present
[    19.607] Initializing built-in extension DRI3
[    19.607] Initializing built-in extension X-Resource
[    19.607] Initializing built-in extension XVideo
[    19.607] Initializing built-in extension XVideo-MotionCompensation
[    19.607] Initializing built-in extension SELinux
[    19.607] Initializing built-in extension XFree86-VidModeExtension
[    19.607] Initializing built-in extension XFree86-DGA
[    19.607] Initializing built-in extension XFree86-DRI
[    19.607] Initializing built-in extension DRI2
[    19.607] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    19.607] (II) "glx" will be loaded by default.
[    19.607] (WW) "xmir" is not to be loaded by default. Skipping.
[    19.607] (II) LoadModule: "glx"
[    19.607] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    19.614] (II) Module glx: vendor="NVIDIA Corporation"
[    19.614] 	compiled for 4.0.2, module version = 1.0.0
[    19.614] 	Module class: X.Org Server Extension
[    19.614] (II) NVIDIA GLX Module  346.35  Sat Jan 10 20:53:39 PST 2015
[    19.614] Loading extension GLX
[    19.615] (II) LoadModule: "nvidia"
[    19.615] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    19.615] (II) Module nvidia: vendor="NVIDIA Corporation"
[    19.615] 	compiled for 4.0.2, module version = 1.0.0
[    19.615] 	Module class: X.Org Video Driver
[    19.615] (II) LoadModule: "intel"
[    19.632] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    19.824] (II) Module intel: vendor="X.Org Foundation"
[    19.824] 	compiled for 1.15.1, module version = 2.99.917
[    19.824] 	Module class: X.Org Video Driver
[    19.824] 	ABI class: X.Org Video Driver, version 15.0
[    19.824] (II) NVIDIA dlloader X Driver  346.35  Sat Jan 10 20:32:18 PST 2015
[    19.824] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    19.825] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    19.825] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    19.825] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    19.825] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    19.825] (++) using VT number 7


[    19.825] (II) Loading sub module "fb"
[    19.825] (II) LoadModule: "fb"
[    19.825] (II) Loading /usr/lib/xorg/modules/libfb.so
[    19.825] (II) Module fb: vendor="X.Org Foundation"
[    19.825] 	compiled for 1.15.1, module version = 1.0.0
[    19.825] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.825] (II) Loading sub module "wfb"
[    19.825] (II) LoadModule: "wfb"
[    19.825] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    19.825] (II) Module wfb: vendor="X.Org Foundation"
[    19.825] 	compiled for 1.15.1, module version = 1.0.0
[    19.825] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    19.825] (II) Loading sub module "ramdac"
[    19.825] (II) LoadModule: "ramdac"
[    19.825] (II) Module "ramdac" already built-in
[    19.826] (II) intel(G0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    19.826] (II) intel(G0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150127.4bbd1023-0ubuntu0sarvatt~trusty (Robert Hooker <sarvatt@ubuntu.com>)
[    19.826] (II) intel(G0): SNA compiled for use with valgrind
[    19.826] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"nvidia" for depth/fbbpp 24/32
[    19.826] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    19.826] (==) NVIDIA(0): RGB weight 888
[    19.826] (==) NVIDIA(0): Default visual is TrueColor
[    19.826] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    19.826] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    19.826] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    19.826] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    19.826] (**) NVIDIA(0): Enabling 2D acceleration
[    21.461] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
[    21.462] (II) NVIDIA(0): NVIDIA GPU GeForce 840M (GM108-A) at PCI:7:0:0 (GPU-0)
[    21.462] (--) NVIDIA(0): Memory: 2097152 kBytes
[    21.462] (--) NVIDIA(0): VideoBIOS: 82.08.14.00.0e
[    21.462] (II) NVIDIA(0): Detected PCI Express Link width: 4X
[    21.462] (--) NVIDIA(0): Valid display device(s) on GeForce 840M at PCI:7:0:0
[    21.462] (--) NVIDIA(0):     none
[    21.462] (II) NVIDIA(0): Validated MetaModes:
[    21.462] (II) NVIDIA(0):     "NULL"
[    21.462] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    21.462] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    21.462] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    21.462] (--) intel(G0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    21.462] (--) intel(G0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[    21.462] (==) intel(G0): Depth 24, (--) framebuffer bpp 32
[    21.462] (==) intel(G0): RGB weight 888
[    21.462] (==) intel(G0): Default visual is TrueColor
[    21.462] (**) intel(G0): Option "AccelMethod" "SNA"
[    21.462] (II) intel(G0): Output eDP1 has no monitor section
[    21.462] (--) intel(G0): Found backlight control interface acpi_video0 (type 'firmware') for output eDP1
[    21.462] (II) intel(G0): Enabled output eDP1
[    21.463] (II) intel(G0): Output VGA1 has no monitor section
[    21.463] (II) intel(G0): Enabled output VGA1
[    21.463] (II) intel(G0): Output HDMI1 has no monitor section
[    21.463] (II) intel(G0): Enabled output HDMI1
[    21.463] (--) intel(G0): Using a maximum size of 64x64 for hardware cursors
[    21.463] (II) intel(G0): Output VIRTUAL1 has no monitor section
[    21.463] (II) intel(G0): Enabled output VIRTUAL1
[    21.464] (==) intel(G0): TearFree disabled
[    21.464] (==) intel(G0): DPI set to (96, 96)
[    21.464] (II) Loading sub module "dri2"
[    21.464] (II) LoadModule: "dri2"
[    21.464] (II) Module "dri2" already built-in
[    21.464] (II) Loading sub module "present"
[    21.464] (II) LoadModule: "present"
[    21.544] (WW) Warning, couldn't open module present
[    21.544] (II) UnloadModule: "present"
[    21.544] (II) Unloading present
[    21.544] (EE) intel: Failed to load module "present" (module does not exist, 0)
[    21.545] (--) Depth 24 pixmap format is 32 bpp
[    21.546] (II) intel(G0): SNA initialized with Haswell (gen7.5, gt2) backend
[    21.546] (==) intel(G0): Backing store enabled
[    21.546] (==) intel(G0): Silken mouse enabled
[    21.546] (II) intel(G0): HW Cursor enabled
[    21.546] (II) intel(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.546] (==) intel(G0): DPMS enabled
[    21.546] (==) intel(G0): Display hotplug detection enabled
[    21.546] (II) intel(G0): [DRI2] Setup complete
[    21.546] (II) intel(G0): [DRI2]   DRI driver: i965
[    21.546] (II) intel(G0): [DRI2]   VDPAU driver: va_gl
[    21.546] (II) intel(G0): direct rendering: DRI2 enabled
[    21.546] (WW) intel(G0): Option "AllowEmptyInitialConfiguration" is not used
[    21.546] (WW) intel(G0): Option "IgnoreDisplayDevices" is not used
[    21.546] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    21.546] (II) NVIDIA:     access.
[    21.551] (II) NVIDIA(0): Setting mode "NULL"
[    21.564] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[    21.564] Loading extension NV-GLX
[    21.569] (==) NVIDIA(0): Disabling shared memory pixmaps
[    21.569] (==) NVIDIA(0): Backing store enabled
[    21.569] (==) NVIDIA(0): Silken mouse enabled
[    21.569] (==) NVIDIA(0): DPMS enabled
[    21.586] Loading extension NV-CONTROL
[    21.587] (II) Loading sub module "dri2"
[    21.587] (II) LoadModule: "dri2"
[    21.587] (II) Module "dri2" already built-in
[    21.587] (II) NVIDIA(0): [DRI2] Setup complete
[    21.587] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    21.587] (--) RandR disabled
[    21.590] (II) SELinux: Disabled on system
[    21.591] (II) Initializing extension GLX
[    22.645] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.647] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    22.647] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.647] (II) LoadModule: "evdev"
[    22.647] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.698] (II) Module evdev: vendor="X.Org Foundation"
[    22.698] 	compiled for 1.15.0, module version = 2.8.2
[    22.698] 	Module class: X.Org XInput Driver
[    22.698] 	ABI class: X.Org XInput driver, version 20.0
[    22.698] (II) Using input driver 'evdev' for 'Power Button'
[    22.698] (**) Power Button: always reports core events
[    22.698] (**) evdev: Power Button: Device: "/dev/input/event2"
[    22.698] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.698] (--) evdev: Power Button: Found keys
[    22.698] (II) evdev: Power Button: Configuring as keyboard
[    22.698] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    22.698] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    22.698] (**) Option "xkb_rules" "evdev"
[    22.698] (**) Option "xkb_model" "pc105"
[    22.698] (**) Option "xkb_layout" "us"
[    22.698] (II) config/udev: Adding input device Video Bus (/dev/input/event11)
[    22.698] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    22.698] (II) Using input driver 'evdev' for 'Video Bus'
[    22.698] (**) Video Bus: always reports core events
[    22.698] (**) evdev: Video Bus: Device: "/dev/input/event11"
[    22.698] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    22.698] (--) evdev: Video Bus: Found keys
[    22.698] (II) evdev: Video Bus: Configuring as keyboard
[    22.698] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input13/event11"
[    22.698] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    22.698] (**) Option "xkb_rules" "evdev"
[    22.698] (**) Option "xkb_model" "pc105"
[    22.698] (**) Option "xkb_layout" "us"
[    22.698] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[    22.698] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    22.698] (II) Using input driver 'evdev' for 'Video Bus'
[    22.698] (**) Video Bus: always reports core events
[    22.699] (**) evdev: Video Bus: Device: "/dev/input/event10"
[    22.699] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    22.699] (--) evdev: Video Bus: Found keys
[    22.699] (II) evdev: Video Bus: Configuring as keyboard
[    22.699] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:44/LNXVIDEO:00/input/input12/event10"
[    22.699] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    22.699] (**) Option "xkb_rules" "evdev"
[    22.699] (**) Option "xkb_model" "pc105"
[    22.699] (**) Option "xkb_layout" "us"
[    22.699] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.699] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.699] (II) Using input driver 'evdev' for 'Power Button'
[    22.699] (**) Power Button: always reports core events
[    22.699] (**) evdev: Power Button: Device: "/dev/input/event1"
[    22.699] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.699] (--) evdev: Power Button: Found keys
[    22.699] (II) evdev: Power Button: Configuring as keyboard
[    22.699] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    22.699] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    22.699] (**) Option "xkb_rules" "evdev"
[    22.699] (**) Option "xkb_model" "pc105"
[    22.699] (**) Option "xkb_layout" "us"
[    22.699] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    22.699] (II) No input driver specified, ignoring this device.
[    22.699] (II) This device may have been added with another device file.
[    22.699] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.1/0000:07:00.0/drm/card0
[    22.699] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    22.699] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:02.0/drm/card1
[    22.699] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[    22.699] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event14)
[    22.699] (II) No input driver specified, ignoring this device.
[    22.699] (II) This device may have been added with another device file.
[    22.699] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event13)
[    22.699] (II) No input driver specified, ignoring this device.
[    22.699] (II) This device may have been added with another device file.
[    22.700] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event12)
[    22.700] (II) No input driver specified, ignoring this device.
[    22.700] (II) This device may have been added with another device file.
[    22.700] (II) config/udev: Adding input device eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00 (/dev/input/event8)
[    22.700] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Applying InputClass "evdev touchscreen catchall"
[    22.700] (II) Using input driver 'evdev' for 'eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00'
[    22.700] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: always reports core events
[    22.700] (**) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Device: "/dev/input/event8"
[    22.700] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Using mtdev for this device
[    22.700] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Vendor 0xeef Product 0xa80f
[    22.700] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found absolute axes
[    22.700] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found absolute multitouch axes
[    22.700] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: No buttons found, faking one.
[    22.700] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found x and y absolute axes
[    22.700] (--) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Found absolute touchscreen
[    22.700] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: Configuring as touchscreen
[    22.700] (**) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: YAxisMapping: buttons 4 and 5
[    22.700] (**) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.700] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-13/2-13:1.0/input/input9/event8"
[    22.700] (II) XINPUT: Adding extended input device "eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00" (type: TOUCHSCREEN, id 10)
[    22.700] (II) evdev: eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: initialized for absolute axes.
[    22.700] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) keeping acceleration scheme 1
[    22.700] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) acceleration profile 0
[    22.700] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) acceleration factor: 2.000
[    22.700] (**) eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00: (accel) acceleration threshold: 4
[    22.700] (II) config/udev: Adding input device eGalax Inc. eGalaxTouch EXC7920-2027-46.00.00 (/dev/input/mouse1)
[    22.700] (II) No input driver specified, ignoring this device.
[    22.700] (II) This device may have been added with another device file.
[    22.700] (II) config/udev: Adding input device HP Truevision HD (/dev/input/event9)
[    22.700] (**) HP Truevision HD: Applying InputClass "evdev keyboard catchall"
[    22.700] (II) Using input driver 'evdev' for 'HP Truevision HD'
[    22.700] (**) HP Truevision HD: always reports core events
[    22.700] (**) evdev: HP Truevision HD: Device: "/dev/input/event9"
[    22.700] (--) evdev: HP Truevision HD: Vendor 0x64e Product 0xc341
[    22.700] (--) evdev: HP Truevision HD: Found keys
[    22.700] (II) evdev: HP Truevision HD: Configuring as keyboard
[    22.700] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-7/2-7:1.0/input/input11/event9"
[    22.700] (II) XINPUT: Adding extended input device "HP Truevision HD" (type: KEYBOARD, id 11)
[    22.700] (**) Option "xkb_rules" "evdev"
[    22.700] (**) Option "xkb_model" "pc105"
[    22.700] (**) Option "xkb_layout" "us"
[    22.701] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event16)
[    22.701] (II) No input driver specified, ignoring this device.
[    22.701] (II) This device may have been added with another device file.
[    22.701] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event15)
[    22.701] (II) No input driver specified, ignoring this device.
[    22.701] (II) This device may have been added with another device file.
[    22.701] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    22.701] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    22.701] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    22.701] (**) AT Translated Set 2 keyboard: always reports core events
[    22.701] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    22.701] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    22.701] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    22.701] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    22.701] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    22.701] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    22.701] (**) Option "xkb_rules" "evdev"
[    22.701] (**) Option "xkb_model" "pc105"
[    22.701] (**) Option "xkb_layout" "us"
[    22.701] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[    22.701] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    22.701] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    22.701] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    22.701] (II) LoadModule: "synaptics"
[    22.701] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    22.701] (II) Module synaptics: vendor="X.Org Foundation"
[    22.701] 	compiled for 1.15.0, module version = 1.7.4
[    22.701] 	Module class: X.Org XInput Driver
[    22.701] 	ABI class: X.Org XInput driver, version 20.0
[    22.701] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    22.701] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    22.701] (**) Option "Device" "/dev/input/event4"
[    22.740] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    22.740] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5660 (res 41)
[    22.740] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4702 (res 56)
[    22.740] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    22.740] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    22.740] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    22.740] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    22.740] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    22.740] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    22.740] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    22.756] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[    22.756] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[    22.756] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    22.756] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    22.756] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[    22.756] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    22.756] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    22.756] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    22.756] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    22.756] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    22.756] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    22.756] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    22.756] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[    22.756] (II) No input driver specified, ignoring this device.
[    22.756] (II) This device may have been added with another device file.
[    22.756] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    22.756] (II) No input driver specified, ignoring this device.
[    22.756] (II) This device may have been added with another device file.
[    22.757] (II) config/udev: Adding input device HP Wireless hotkeys (/dev/input/event5)
[    22.757] (**) HP Wireless hotkeys: Applying InputClass "evdev keyboard catchall"
[    22.757] (II) Using input driver 'evdev' for 'HP Wireless hotkeys'
[    22.757] (**) HP Wireless hotkeys: always reports core events
[    22.757] (**) evdev: HP Wireless hotkeys: Device: "/dev/input/event5"
[    22.757] (--) evdev: HP Wireless hotkeys: Vendor 0 Product 0
[    22.757] (--) evdev: HP Wireless hotkeys: Found keys
[    22.757] (II) evdev: HP Wireless hotkeys: Configuring as keyboard
[    22.757] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event5"
[    22.757] (II) XINPUT: Adding extended input device "HP Wireless hotkeys" (type: KEYBOARD, id 14)
[    22.757] (**) Option "xkb_rules" "evdev"
[    22.757] (**) Option "xkb_model" "pc105"
[    22.757] (**) Option "xkb_layout" "us"
[    22.758] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[    22.758] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    22.758] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    22.758] (**) HP WMI hotkeys: always reports core events
[    22.758] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event7"
[    22.758] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    22.758] (--) evdev: HP WMI hotkeys: Found keys
[    22.758] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    22.758] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[    22.758] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 15)
[    22.758] (**) Option "xkb_rules" "evdev"
[    22.758] (**) Option "xkb_model" "pc105"
[    22.758] (**) Option "xkb_layout" "us"
[    23.045] (II) intel(G0): EDID vendor "AUO", prod id 8605
[    23.045] (II) intel(G0): Printing DDC gathered Modelines:
[    23.045] (II) intel(G0): Modeline "1920x1080"x0.0  140.50  1920 1968 2068 2104  1080 1083 1089 1112 -hsync -vsync (66.8 kHz eP)
[    23.045] (II) intel(G0): Modeline "1920x1080"x0.0   93.67  1920 1968 2068 2104  1080 1083 1089 1112 -hsync -vsync (44.5 kHz e)
[    23.060] reporting 4 4 17 141
[    23.080] have a master to look out for
[    23.080] adjust shatters 0 1920
[    23.083] need to create shared pixmap 1(II) intel(G0): switch to mode 1920x1080@60.1 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    23.100] reporting 4 4 17 141
[    23.120] reporting 4 4 17 141
[    23.120] have a master to look out for
[    23.121] need to create shared pixmap 1reporting 4 4 17 141
[    23.175] have a master to look out for
[    23.175] adjust shatters 0 1920
[    23.178] need to create shared pixmap 1(II) intel(G0): switch to mode 1920x1080@60.1 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    24.157] reporting 4 4 17 141
[    25.566] reporting 4 4 17 141
[    26.021] reporting 4 4 17 141
[    26.143] reporting 4 4 17 141
[    27.128] reporting 4 4 17 141
[    27.133] reporting 4 4 17 141
[    27.269] reporting 4 4 17 141
[    27.269] reporting 4 4 17 141
[    27.288] reporting 4 4 17 141
[    27.304] reporting 4 4 17 141
[    27.320] reporting 4 4 17 141
[    27.672] reporting 4 4 17 141
[    27.798] reporting 4 4 17 141
[    27.816] reporting 4 4 17 141
[    27.832] reporting 4 4 17 141
[    27.848] reporting 4 4 17 141
[    27.848] reporting 4 4 17 141
[    27.848] reporting 4 4 17 141
[    28.012] reporting 4 4 17 141

```

```
$[COLOR=#000000][FONT=Ubuntu Mono]cat ~/.xsession-errors
[/FONT][/COLOR]Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd main process ended, respawning
init: at-spi2-registryd respawning too fast, stopped
init: unity-settings-daemon main process (2195) terminated with status 1
init: hud main process (2199) terminated with status 1
init: gnome-session (Unity) main process (2211) terminated with status 1
init: unity-panel-service main process (2214) terminated with status 1
init: upstart-dbus-session-bridge main process (2159) terminated with status 1
init: indicator-bluetooth main process (2342) killed by TERM signal
init: indicator-power main process (2344) killed by TERM signal
init: indicator-datetime main process (2345) killed by TERM signal
init: indicator-sound main process (2355) killed by TERM signal
init: indicator-printers main process (2356) terminated with status 1
init: indicator-session main process (2378) killed by TERM signal
init: indicator-application main process (2428) killed by TERM signal
init: Disconnected from notified D-Bus bus

```

ALSO, I noticed this file, and wondered if it could tell you anything...

```
$cat ~/.nvidia-settings-rc
#
# /home/zanahade/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Wed Feb  4 15:32:38 2015
#


# ConfigProperties:


RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
UpdateRulesOnProfileNameChange = Yes
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = Memory_Used_(GPU_0),Yes,3000


# Attributes:


0/LogAniso=0
0/FSAA=0
0/TextureSharpen=0
0/TextureClamping=1
0/FXAA=0
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/OpenGLImageSettings=1
0/FSAAAppEnhanced=0



```

---

### Post by Bashing-om on 2015-02-06
zan-public; Wow !

The Nvidia driver did build this time:
> 
19.607] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    19.614] (II) Module glx: vendor="NVIDIA Corporation"
[    19.614] 	compiled for 4.0.2, module version = 1.0.0
[    19.614] 	Module class: X.Org Server Extension
[    19.614] (II) NVIDIA GLX Module  346.35  Sat Jan 10 20:53:39 PST 2015
[    19.614] Loading extension GLX
[    19.615] (II) LoadModule: "nvidia"

19.824] (II) NVIDIA dlloader X Driver  346.35  Sat Jan 10 20:32:18 PST 2015
[    19.824] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs

 21.462] (II) NVIDIA(0): NVIDIA GPU GeForce 840M (GM108-A) at PCI:7:0:0 (GPU-0)

 21.586] Loading extension NV-CONTROL 21.586] Loading extension NV-CONTROL



And Intel also looks in a happy state.

So what is the deal ? Can you boot to the GUI now ?
Else let's boot to terminal (TTY1) and from there start the GUI - see what errors are reported back to the terminal .
```

sudo service lightdm start

```
will start the GUI, key combo ctl+alt+F7 to get the GUI login screen. Can you log into the GUI ?
key combo ctl+alt+F1 to return to terminal TTY1.

[INDENT][INDENT]surprise, surprise, surprise
 [/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-07
Yea, I have done
```

sudo service lightdm stop
sudo service lightdm start
sudo service lightdm restart

```.

With no changes...
Something that I find interesting, is that if I ctrl+alt+f1 to a command line, and then ctrl+alt_f7 to gui, the command line doesn't disappear, the cursor just stops flashing... so, yea, that means something significant... I just don't know what.

---

### Post by Bashing-om on 2015-02-07
zan-public; curious and curiouser ...

Can we get any info as to what is going on when we attempt to start the GUI from terminal ?

Boot to the grub boot menu, 'e' key for edit mode -> boot parameters screen;
Arrow down to the line starting with 'linux' and arrow across to "quiet splash" , replace these terms with the term "text" - with out the quotes.
key combo ctl+x to continue the boot process to TTY1.
Log in here with username and password - no response to the screen, enter password blindly and hit the enter key.
NOW to start the GUI, what results and what errors are passed back ?
```

sudo service lightdm start

```
As we seek to know why the desktop is not happy .


[INDENT][INDENT]gotta be a reason
[INDENT][INDENT][INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-07
Ok, I did this to the letter, Once I was logged in, I did
```

sudo service lightdm start

```

Which resulted in the screen switching to black, and nothing happening, beyond that. I returned to f1 and all that was shown on the screen was the job number that was assigned to the lightdm service. After that it had just returned to the $ prompt.

---

### Post by Bashing-om on 2015-02-07
zan-public; Sheesshh ..

An exercise in futility, as we got NO info to point us to where the problem lies .

As lightdm will not start, let's consider removing it, and (RE-)installing lightdm.
Let's see what it is going to do IF we remove 'lightdm' .
```

sudo apt-get purge -s lightdm

``` where the -s flag is "simulate" which tells us what the package manager would do .
If we are going to destroy the operating system, be nice to know how and have some indications of what it will take to put it back together.

Problems with the graphics modules building
Problems with the GUI starting
[INDENT][INDENT]just do not think that it is a coincidence
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-07
SO, the modified command:
```

sudo apt-get purge -s lightdm > ldmpurge.txt

```

rendered this output:
```

Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0
  gir1.2-nmgtk-1.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs
  gnome-shell gnome-themes-standard gnome-themes-standard-data
  libcaribou-common libcaribou0 libgdm1 libgjs0e libmozjs-24-0 libmutter0c
  mutter-common
The following packages will be REMOVED:
  lightdm*
The following NEW packages will be installed:
  gdm gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdm-1.0 gir1.2-gkbd-3.0 gir1.2-json-1.0 gir1.2-mutter-3.0
  gir1.2-nmgtk-1.0 gir1.2-polkit-1.0 gir1.2-telepathyglib-0.12
  gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs
  gnome-shell gnome-themes-standard gnome-themes-standard-data
  libcaribou-common libcaribou0 libgdm1 libgjs0e libmozjs-24-0 libmutter0c
  mutter-common
0 upgraded, 29 newly installed, 1 to remove and 0 not upgraded.
Inst libgdm1 (3.10.0.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-gdm-1.0 (3.10.0.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-cogl-1.0 (1.16.2-1 Ubuntu:14.04/trusty [amd64])
Inst gir1.2-coglpango-1.0 (1.16.2-1 Ubuntu:14.04/trusty [amd64])
Inst gir1.2-json-1.0 (0.16.2-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst gir1.2-clutter-1.0 (1.16.4-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst mutter-common (3.10.4-0ubuntu2.1 Ubuntu:14.04/trusty-updates [all])
Inst libmutter0c (3.10.4-0ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-mutter-3.0 (3.10.4-0ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-telepathyglib-0.12 (0.22.1-1ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst libmozjs-24-0 (24.2.0-1 Ubuntu:14.04/trusty [amd64])
Inst libgjs0e (1.40.1-0ubuntu0.3 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-accountsservice-1.0 (0.6.35-0ubuntu7.1 Ubuntu:14.04/trusty-updates [amd64])
Inst libcaribou-common (0.4.13-0ubuntu1 Ubuntu:14.04/trusty [all])
Inst libcaribou0 (0.4.13-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst gir1.2-caribou-1.0 (0.4.13-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst gir1.2-gck-1 (3.10.1-1 Ubuntu:14.04/trusty [amd64])
Inst gir1.2-gcr-3 (3.10.1-1 Ubuntu:14.04/trusty [amd64])
Inst gir1.2-xkl-1.0 (5.4-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst gir1.2-gkbd-3.0 (3.6.0-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst gir1.2-nmgtk-1.0 (0.9.8.8-0ubuntu4.3 Ubuntu:14.04/trusty-updates [amd64])
Inst gir1.2-polkit-1.0 (0.105-4ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst gir1.2-telepathylogger-0.2 (0.8.0-3 Ubuntu:14.04/trusty [amd64])
Inst gir1.2-upowerglib-1.0 (0.9.23-2ubuntu1 Ubuntu:14.04/trusty [amd64])
Inst gjs (1.40.1-0ubuntu0.3 Ubuntu:14.04/trusty-updates [amd64])
Inst gnome-themes-standard-data (3.10.0-1ubuntu2 Ubuntu:14.04/trusty [all])
Inst gnome-themes-standard (3.10.0-1ubuntu2 Ubuntu:14.04/trusty [amd64])
Inst gnome-shell (3.10.4-0ubuntu5.2 Ubuntu:14.04/trusty-updates [amd64])
Inst gdm (3.10.0.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Purg lightdm [1.10.3-0ubuntu2]
Conf libgdm1 (3.10.0.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-gdm-1.0 (3.10.0.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-cogl-1.0 (1.16.2-1 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-coglpango-1.0 (1.16.2-1 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-json-1.0 (0.16.2-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-clutter-1.0 (1.16.4-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf mutter-common (3.10.4-0ubuntu2.1 Ubuntu:14.04/trusty-updates [all])
Conf libmutter0c (3.10.4-0ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-mutter-3.0 (3.10.4-0ubuntu2.1 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-telepathyglib-0.12 (0.22.1-1ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf libmozjs-24-0 (24.2.0-1 Ubuntu:14.04/trusty [amd64])
Conf libgjs0e (1.40.1-0ubuntu0.3 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-accountsservice-1.0 (0.6.35-0ubuntu7.1 Ubuntu:14.04/trusty-updates [amd64])
Conf libcaribou-common (0.4.13-0ubuntu1 Ubuntu:14.04/trusty [all])
Conf libcaribou0 (0.4.13-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-caribou-1.0 (0.4.13-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-gck-1 (3.10.1-1 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-gcr-3 (3.10.1-1 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-xkl-1.0 (5.4-0ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-gkbd-3.0 (3.6.0-0ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-nmgtk-1.0 (0.9.8.8-0ubuntu4.3 Ubuntu:14.04/trusty-updates [amd64])
Conf gir1.2-polkit-1.0 (0.105-4ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-telepathylogger-0.2 (0.8.0-3 Ubuntu:14.04/trusty [amd64])
Conf gir1.2-upowerglib-1.0 (0.9.23-2ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf gjs (1.40.1-0ubuntu0.3 Ubuntu:14.04/trusty-updates [amd64])
Conf gnome-themes-standard-data (3.10.0-1ubuntu2 Ubuntu:14.04/trusty [all])
Conf gnome-themes-standard (3.10.0-1ubuntu2 Ubuntu:14.04/trusty [amd64])
Conf gnome-shell (3.10.4-0ubuntu5.2 Ubuntu:14.04/trusty-updates [amd64])
Conf gdm (3.10.0.1-0ubuntu3.1 Ubuntu:14.04/trusty-updates [amd64])

```

Does that help?

---

### Post by Bashing-om on 2015-02-07
zan-public; Surprise surprise,

Some good, some UnGood.
29 to be installed !
nothing else to be removed

But, but but .. how does 
> 
The following extra packages will be installed:
 gdm, gnome-shell gnome-themes-standard gnome-themes-standard-data

play into this ? A conflict of interest, still ? Is GDM still fighting with lightdm as the Display Environment ?

Lemme have a bit to do some cross checking. I do not have lightdm or gdm installed on my system so it makes things a bit challenging to check/test to see what is and what should be. 

clean up can be a messy affair

---

### Post by Bashing-om on 2015-02-07
zan-public; UUHH Boy.

Yeah it is a mess:
My results from a clean 14.04 ubuntu install:
```

sysop3@14:~$ sudo apt-get purge -s lightdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  lightdm* ubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Purg ubuntu-desktop [1.325]
Purg lightdm [1.10.3-0ubuntu2]
sysop3@14:~$

```
When one does the checks on your install:
```

apt-cahe show lightdm
apt-cache depends lightdm
apt-cache rdepends lightm

```
and the reverse also for the 'gdm' packages ->
one sees that there is no relation lightdm to gdm.

To me that confirms that what you have there is a conflict of interest in who controls that desk top .
I think it best to purge the gdm stuff and then (re-)install lightdm and ubuntu desktop.

It will not hurt my feeling one bit if we await a 2nd opinion on purging, and what might result - looks like it will get real messy. I do not presently see how it can hurt and we are going to reinstall the desktop any way. Just finding all the stuff we need to have replaced that was removed in that purge process .

[INDENT][INDENT][INDENT]messy messy messy
[/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-08
Ok, I did all of what you asked, here is what I found:
lightdm and gdm have nothing in the way of dependency with each other...
gdm was not installed...
and last but not least, I am lost.

What I noticed though, If I remove/purge Lightdm, gdm is installed automatically to replace it. If I remove the one, the other takes it's place. Also, sometimes a purple screen appears asking me to choose my dm from a short list (Lightdm, gdm) but it doesn't appear every time. Can I call up that screen manually some how?

Furthermore, I have noticed that if I purge out lightdm, install gdm, my system boots to gdm login... but nvidia doesn't build... I would settle for gdm, if we could get nvidia working on it...

---

### Post by zan-public on 2015-02-08
Ok, new information:
I ran 
```
$ sudo apt-get install --reinstall lightdm* ubuntu-desktop*
```

And that returned a list of packages to be re-installed and then this

```

Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 mbuntu-y-lightdm-v4 : Conflicts: mbuntu-lightdm-v3 but 3.10~trusty~NoobsLab.com is to be installed
E: Unable to correct problems, you have held broken packages.


```

Does that help our cause?

---

### Post by Bashing-om on 2015-02-08
zan-public; Hey, hey;

Yeah, that helps !
I do think we should concentrate on getting the native 'lightdm' functioning.
A)
> 
Conflicts: mbuntu-lightdm-v3 but 3.10~trusty~NoobsLab.com is to be installed

so let's get the source list(s) straightened up:
```

cat /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

b)With the end goal to remove 'gdm' completely, install lightdm and ubuntu-desktop and then 
c) purge all nvidia drivers and reinstall the Nvidia drivers;
By the way .. I find:
[http://www.nvidia.com/download/driverresults.aspx/74888/en-us](http://www.nvidia.com/download/driverresults.aspx/74888/en-us)
which indicates the 337 driver as proper (??) Does Xubuntu with the 346 driver perform as expected in all respects ? 
-------------------------

That is my thoughts, I am more than willing to follow what ever you want to try to resolve this; after all, it is your system, your time and your effort.
Presently we know that the package management system is messed up;
the desk top is messed up;
the graphics divers are messed up.

Everything begins with a solid package manager.

[INDENT][INDENT]but hey, it is all do-able
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-08
Ok, So I did a purge on the nvidia-346 and gdm; reinstalled lightdm and ubuntu desktop, and when I booted up, I got to a login, mind you, it was not the lightdm login that I am used to... looked more like the gdm one... but whatever. Now I am logged in, but I have no nvidia (no surprise since I purged it). Now, I do not seem to have the nvidia 337 in my PPAs so I am not sure how I could test that, but here is were I go the idea to use the 346 driver:
[http://www.nvidia.com/download/driverResults.aspx/81252/en-us](http://www.nvidia.com/download/driverResults.aspx/81252/en-us)

```

cat /etc/apt/sources.list
tail -v 0n +1 /etc/apt sources.list.d/*

```

rendered:

```

# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

```

and 

```

==> /etc/apt/sources.list.d/adabbas-1stppa-trusty.list <==
deb [http://ppa.launchpad.net/adabbas/1stppa/ubuntu](http://ppa.launchpad.net/adabbas/1stppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/adabbas/1stppa/ubuntu](http://ppa.launchpad.net/adabbas/1stppa/ubuntu) trusty main


==> /etc/apt/sources.list.d/fingerprint-fingerprint-gui-trusty.list <==


==> /etc/apt/sources.list.d/fingerprint-fingerprint-gui-trusty.list.save <==


==> /etc/apt/sources.list.d/getdeb.list <==
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) trusty-getdeb apps


==> /etc/apt/sources.list.d/getdeb.list.save <==
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) trusty-getdeb apps


==> /etc/apt/sources.list.d/gnome3-team-gnome3-trusty.list <==
deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main


==> /etc/apt/sources.list.d/gnome3-team-gnome3-trusty.list.save <==
deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/libdvdcss.list <==
deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
deb-src [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /


==> /etc/apt/sources.list.d/libdvdcss.list.save <==
deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
deb-src [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /


==> /etc/apt/sources.list.d/mamarley-nvidia-trusty.list <==
deb [http://ppa.launchpad.net/mamarley/nvidia/ubuntu](http://ppa.launchpad.net/mamarley/nvidia/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/mamarley/nvidia/ubuntu](http://ppa.launchpad.net/mamarley/nvidia/ubuntu) trusty main


==> /etc/apt/sources.list.d/mamarley-nvidia-trusty.list.save <==
deb [http://ppa.launchpad.net/mamarley/nvidia/ubuntu](http://ppa.launchpad.net/mamarley/nvidia/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/mamarley/nvidia/ubuntu](http://ppa.launchpad.net/mamarley/nvidia/ubuntu) trusty main


==> /etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list <==
deb [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) trusty main


==> /etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list.save <==
deb [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) trusty main


==> /etc/apt/sources.list.d/noobslab-icons-trusty.list <==
deb [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) trusty main


==> /etc/apt/sources.list.d/noobslab-icons-trusty.list.save <==
deb [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) trusty main


==> /etc/apt/sources.list.d/noobslab-themes-trusty.list <==
deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main


==> /etc/apt/sources.list.d/noobslab-themes-trusty.list.save <==
deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main


==> /etc/apt/sources.list.d/otto-kesselgulasch-gimp-trusty.list <==
deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) trusty main


==> /etc/apt/sources.list.d/otto-kesselgulasch-gimp-trusty.list.save <==
deb [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) trusty main


==> /etc/apt/sources.list.d/playdeb.list <==
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) trusty-getdeb games


==> /etc/apt/sources.list.d/playdeb.list.save <==
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) trusty-getdeb games


==> /etc/apt/sources.list.d/stebbins-handbrake-releases-trusty.list <==
deb [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) trusty main


==> /etc/apt/sources.list.d/stebbins-handbrake-releases-trusty.list.save <==
deb [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) trusty main


==> /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-trusty.list <==


==> /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-trusty.list.save <==


==> /etc/apt/sources.list.d/webupd8team-java-trusty.list <==
deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main


==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.save <==
deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main


==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list <==
deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) trusty main


==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list.save <==
deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) trusty main


==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list <==


==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list.save <==

```

respectively.

---

### Post by Bashing-om on 2015-02-08
zan-public; OK !

1) Gnome3 problems:
> 
==> /etc/apt/sources.list.d/gnome3-team-gnome3-trusty.list <==
deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main

A 3rd party ppa, and every time you remove 'gdm' it get reinstalled.
PPA purge time

2)Mixing debian source with ubuntu, do you really need/want to do this ?
> 
==> /etc/apt/sources.list.d/libdvdcss.list.save <==
deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
deb-src [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /


3) Bad URL:
> 
 
==> /etc/apt/sources.list.d/stebbins-handbrake-releases-trusty.list <==
deb [http://ppa.launchpad.net/stebbins/ha...eleases/ubuntu](http://ppa.launchpad.net/stebbins/ha...eleases/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/stebbins/ha...eleases/ubuntu](http://ppa.launchpad.net/stebbins/ha...eleases/ubuntu) trusty main


==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list <==
deb [http://ppa.launchpad.net/webupd8team...manager/ubuntu](http://ppa.launchpad.net/webupd8team...manager/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/webupd8team...manager/ubuntu](http://ppa.launchpad.net/webupd8team...manager/ubuntu) trusty main


will not resolve, needs correcting " /ha...eleases/ " ; webupd8team...manager

4) Not supported in 14.04 ?? As I get a 404
> 
==> /etc/apt/sources.list.d/getdeb.list.save <==
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) trusty-getdeb apps


get these issues under control.

And see now what the package manager relates:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg -C

```

We get the package manager happy
we get the desktop happy

Then we install the Nvidia driver .

[INDENT][INDENT][INDENT]what say you ?
[INDENT][INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-09
Ok, I purged out the PPAs that were troublesome, Then I ran the list of apt-get and dpkg commands you listed (in order), then installed the nvidia driver, rebooted and... got a black screen. I uninstalled the nvidia driver, rebooted, and now I am back, but with basic graphics... I am starting to loose my patience with this... I am very frustrated.

Well I guess we'll see what tomorrow brings...

---

### Post by Bashing-om on 2015-02-09
zan-public; Welp;

We are making some progress and some headway. If and when your frustration level is exceeded, there is always the nuclear option - back up and (RE-)install.
If I do not "see" errors, then i "assume" all is OK .
Presently:
'apt-get -f install' -> returns:
```

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
``` ??
AND
'dpkg -C' returns to prompt with no output ?

GDM has been removed ?
```

dpkg -l gdm
apt-cache policy gdm

```

then we can proceed to make sure 'lightdm' , 'compiz', and 'ubuntu-desktop' are properly installed.

[INDENT][INDENT][INDENT]all we want to do is
[INDENT][INDENT][INDENT]install a graphics driver 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-09
```

$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

dpkg -C returns to a blank command prompt.

```

$ dpkg -l gdm
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  gdm            <none>       <none>       (no description available)

```

```

$ apt-cache policy gdm

gdm:
  Installed: (none)
  Candidate: 3.10.0.1-0ubuntu3.1
  Version table:
     3.10.0.1-0ubuntu3.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
     3.10.0.1-0ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```

So now, I should reinstall lightdm, compiz, and ubuntu-desktop?

---

### Post by Bashing-om on 2015-02-09
zan-public; Hey;

Agreed, that do look promising.

And yes, I think trying to re-install these is the better course, rather than purging - tearing the GUI down . I could be wrong !
```

sudo service lightdm stop
sudo apt-get install --reinstall compiz unity-greeter unity ubuntu-desktop

```
In stages here, 
Paying attention to see any errors that the system may report .

Might be a good idea to insure that 'lightdm' is set as the default display manager:
```

sudo dpkg-reconfigure lightdm
sudo dpkg-reconfigure unity-greeter

```

Now will the GUI start ?
```

sudo service lightdm start

```

[INDENT][INDENT]fingers crossed
[/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-09
Each step of the way, everything looks good, but in the end, black screen. Ideas?

---

### Post by Bashing-om on 2015-02-09
zan-public; Sheeeshh ..

> **zan-public said:**
> Each step of the way, everything looks good, but in the end, black screen. Ideas?

Nope, I am about at the end of my rope.
A desperation move, just cause I know nothing better.
```

sudo service lightdm stop
sudo apt-get purge lightdm
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install lightdm
sudo apt-get install ubuntu-desktop

```

Then maybe try and purge Nvidia and RE-install 346 ( because we know it does work -xubuntu );
Now look in the /var/log/Xorg.0.log file and see if the Nvidia driver built .

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]I hope yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-09
Maybe... no. I am not sure what is up, but I do know this: IF the nvidia driver is not installed, lightdm is good. IF the nvidia driver is installed, blank screen (lightdm doesn't seem to be working.)  During this last exercise I forgot to install nvidia-prime and it booted to the login, I checked nvidia was not functional, so I dpkg -l nvidia-* and saw that prime was not installed, so I installed it and BLACK SCREEN OF DOOM!

---

### Post by Bashing-om on 2015-02-09
zan-public; Cogitating ...

Nvidia346 does not like unity ???

What do the log files relate ?

[INDENT][INDENT]Newer hardware, new driver
[INDENT][INDENT][INDENT]and I be short on experience
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by zan-public on 2015-02-09
> **Bashing-om said:**
> 
What do the log files relate ?


```

$ cat /var/log/Xorg.0.log | grep "nvidia"
[    29.360] (**) |-->Screen "nvidia" (0)
[    29.420] (**) |   |-->Device "nvidia"
[    29.420] (==) No monitor specified for screen "nvidia".
[    30.702] (II) LoadModule: "nvidia"
[    30.702] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    30.818] (II) Module nvidia: vendor="NVIDIA Corporation"
	"nvidia" for depth/fbbpp 24/32
[    31.645] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
[    31.950] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia

```

So it looks like nvidia is not the problem at this point...

---

### Post by zan-public on 2015-02-09
Ok, I don't know exactly what WAS wrong... but... I pulled the pin on a twenty megaton data bomb. After reinstall of ubuntu, I set up the PPA and installed nvidia-340 (it is listed as one of the drivers by nvidia that supports this card, they list 340 and 346 from what I have read) Anyway It works! I think something must have been fouled up bit wise with the original install, though I have NO clue what. This time I did a md5 check on the download, and then ran the integrity check before installing. Thank you for all you help and hard work @Bashing-om! Let me know if you're ever in Portland, OR. I'll buy ya a beer. (provided it is legal to do so.)

---

### Post by lotus49 on 2015-02-10
> **zan-public said:**
> Ok, I don't know exactly what WAS wrong... but... I pulled the pin on a twenty megaton data bomb. After reinstall of ubuntu...
I have been following this thread with interest as I have exactly the same problem and am also completely baffled.  

Am I right in thinking that you just did a comlete reinstall and now it works with the xorg-edgers nvidia-340 package?  I have installed Ubuntu so many times that I can almost do it in my sleep so a full install isn't that big a deal.  I'm fed up of using my slow Intel graphics card for Minecraft as it isn't really up to the job in full screen mode.  If a reinstall will do the trick, it's a small amount of pain that will be well worth it.

---

### Post by zan-public on 2015-02-10
> **lotus49 said:**
> I have been following this thread with interest as I have exactly the same problem and am also completely baffled.  

Am I right in thinking that you just did a comlete reinstall and now it works with the xorg-edgers nvidia-340 package?  I have installed Ubuntu so many times that I can almost do it in my sleep so a full install isn't that big a deal.  I'm fed up of using my slow Intel graphics card for Minecraft as it isn't really up to the job in full screen mode.  If a reinstall will do the trick, it's a small amount of pain that will be well worth it.

You are correct except for the ppa. The ppa I used was
```
ppa:mamarley/nvidia
```
As soon as the install was complete (redownload fresh, and check your md5 checksum, and/or do an integrity check befor you install.) Then run all updates. Then install the ppa. Then install nvidia driver. Reboot. That's how I did it anyway. I hope that if you are at the end of your rope, this helps. And remember to back up all your data first!

---

### Post by Bashing-om on 2015-02-10
zan-public; Outstanding !

Pleased to no end that you are up and running; Regretful that it took a (re-)install to make it so. All I can surmise is as originally guesstimated that there was a conflict between the DM's . We do see often times that in the process of removing one DM, the other is borked and not able to find the cause. ( I do feel a failure on my part)

As this matter is now concluded, 
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

@lotus49; Hello; happy to help.
IF you do NOT do a fresh clean install; prior to installing the proprietary Nvidia driver DO purge all other drivers from the system.
As you have opted into this thread, please let us know how it goes.

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

### Post by lotus49 on 2015-02-10
> **zan-public said:**
> You are correct except for the ppa. The ppa I used was
```
ppa:mamarley/nvidia
```
As soon as the install was complete (redownload fresh, and check your md5 checksum, and/or do an integrity check befor you install.) Then run all updates. Then install the ppa. Then install nvidia driver. Reboot. That's how I did it anyway. I hope that if you are at the end of your rope, this helps. And remember to back up all your data first!

Thanks for the reply.  I rather lost track of what you tried in the course of the thread so I shall try this PPA (which I haven't tried so far) first.  If that doesn't work, I shall try a full reinstall.

---

### Post by miixxii on 2015-02-13
Hello,

I'm following this tread because I have same issue with my Nvidia 840m on my asus ux303. I did even fresh installation of ubuntu 14.10 and ppa:mamarley/nvidia to repository and installed nvidia-340. In my case the problem still persist. After reboot black screen when lightdm is loaded. 

here is output from Xorg.0.log:

```
[     6.165] (**) |-->Screen "nvidia" (0)[     6.166] (**) |   |-->Device "nvidia"
[     6.333] (II) Module glx: vendor="NVIDIA Corporation"
[     6.333] (II) NVIDIA GLX Module  340.76  Thu Jan 22 11:24:42 PST 2015
[     6.333] (II) LoadModule: "nvidia"
[     6.333] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     6.333] (II) Module nvidia: vendor="NVIDIA Corporation"
[     6.336] (II) NVIDIA dlloader X Driver  340.76  Thu Jan 22 11:03:05 PST 2015
[     6.336] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     6.337] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[     6.337] (==) NVIDIA(0): RGB weight 888
[     6.337] (==) NVIDIA(0): Default visual is TrueColor
[     6.337] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     6.337] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[     6.337] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[     6.337] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[     6.337] (**) NVIDIA(0): Enabling 2D acceleration
[     7.274] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[     7.275] (II) NVIDIA(0): NVIDIA GPU GeForce 840M (GM108-A) at PCI:3:0:0 (GPU-0)
[     7.275] (--) NVIDIA(0): Memory: 2097152 kBytes
[     7.275] (--) NVIDIA(0): VideoBIOS: 82.08.14.00.31
[     7.275] (II) NVIDIA(0): Detected PCI Express Link width: 4X
[     7.275] (--) NVIDIA(0): Valid display device(s) on GeForce 840M at PCI:3:0:0
[     7.275] (--) NVIDIA(0):     none
[     7.275] (II) NVIDIA(0): Validated MetaModes:
[     7.275] (II) NVIDIA(0):     "NULL"
[     7.275] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[     7.275] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[     7.275] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[     7.282] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[     7.282] (II) NVIDIA:     access.
[     7.285] (II) NVIDIA(0): Setting mode "NULL"
[     7.285] (EE) NVIDIA(0): Failed to initiate mode change.
[     7.285] (EE) NVIDIA(0): Failed to complete mode change
[     7.294] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[     7.298] (==) NVIDIA(0): Disabling shared memory pixmaps
[     7.299] (==) NVIDIA(0): Backing store enabled
[     7.299] (==) NVIDIA(0): Silken mouse enabled
[     7.299] (**) NVIDIA(0): DPMS enabled
[     7.300] (II) NVIDIA(0): [DRI2] Setup complete
[     7.300] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
```

and here is bug nvidia-bug-report [ATTACH=CONFIG]259959[/ATTACH]
If somebody can help

---

### Post by zan-public on 2015-02-13
> **tomas-simik said:**
> I did even fresh installation of ubuntu 14.10 and ppa:mamarley/nvidia

Did you make sure to download it fresh, or at least validate with md5 checksum, or the built in validation tool that comes up when you first boot up on the ISO image? This is actually very important, because everything could seem fine, but that one thing (who knows what) could just not work properly, and you might have no idea why...

---

### Post by miixxii on 2015-02-14
> **zan-public said:**
> Did you make sure to download it fresh, or at least validate with md5 checksum, or the built in validation tool that comes up when you first boot up on the ISO image? This is actually very important, because everything could seem fine, but that one thing (who knows what) could just not work properly, and you might have no idea why...

Yes, fresh download 2 days ago md5 check went fine and also installation without errors or warnings.

###

I've solved the issue by following this: [http://askubuntu.com/questions/518985/ubuntu-14-04-and-nvidia-geforce-840m-compatability-on-64-bit-laptop](http://askubuntu.com/questions/518985/ubuntu-14-04-and-nvidia-geforce-840m-compatability-on-64-bit-laptop)

---

### Post by Bashing-om on 2015-02-14
zan-public; Hi !

> **zan-public said:**
> Did you make sure to download it fresh, or at least validate with md5 checksum, or the built in validation tool that comes up when you first boot up on the ISO image? This is actually very important, because everything could seem fine, but that one thing (who knows what) could just not work properly, and you might have no idea why...

:) You do good work. Keep on, good help is hard to come by.

[INDENT][INDENT]open source
[INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregor-skrt on 2015-02-16
Just to let you know I had the same problem on my lenovo y50-70. I was trying to install from edgers (black screen of death) except once after clean install of ubuntu 14.04. Later I tried proposed ppa but still I had problems switching to nvidia with prime-select. I had to update alternatives: sudo update-alternatives --config x86_64-linux-gnu_gl_conf and now it works (fingers crossed).

---

### Post by Bashing-om on 2015-02-16
gregor-skrt; Hi ;

Good to know;
Thanks for the sharing !

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lotus49 on 2015-02-19
In the end I just purged the xorg-edgers ppa (using ppa-purge) and also removed it using apt-add-repository -r xorg-edgers.  I also deleted the xorg-edgers files from /etc/apt/sources.list.d (I'm not sure why the first two steps hadn't already done this).  Then I installed the mamarley ppa and installed nvidia-346 and everything worked at last.

---

### Post by Bashing-om on 2015-02-19
lotus49; Great !
> 
Then I installed the mamarley ppa and installed nvidia-346 and everything worked at last


Thanks for sharing that solution.
Yeah, clean can work a treat.

[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-06
OK, So I know that this thread is solved, but I have a VERY similar issue, except that I am using UbuntuGnome 14.10 and my card is 860M on my Lenovo Y50 4K. Been frustrated with the black screen of death for a few months now. And I want to use my nvidia for full screen minecraft.

Let me know if I should start a new thread.

I have tried everything short of the mamarley ppa. This is my daily use workstation from work so I cannot just wipe and restart without a day of reinstalling and reconfiguring everything. 

I'm wondering if anyone has gotten this to work with gdm and gnome3. I have a lot of work to do to clean things up as you can see from the details below. But I have removed xorg-edgers and enabled mamarler ppa. Any other tips on what I should do before I attempt this. I followed along in this thread as best I could, but it looks like the successes came with lightdm and I want to know if gdm is going to work with this or the fixes on the link below.

[http://askubuntu.com/questions/518985/ubuntu-14-04-and-nvidia-geforce-840m-compatability-on-64-bit-laptop](http://askubuntu.com/questions/518985/ubuntu-14-04-and-nvidia-geforce-840m-compatability-on-64-bit-laptop)

A little basic details from my machine from the questions that were asked previously in this thread.

```

 &#10140; sudo lshw -C display                                                      ~ 
  *-display UNCLAIMED     
       description: 3D controller
       product: GM107M [GeForce GTX 860M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:d0000000-d0ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:b2000000-b207ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:d1000000-d13fffff memory:c0000000-cfffffff ioport:5000(size=64)



 &#10140; lspci -nnk | grep -iA3 vga                                                ~ 
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)
        Subsystem: Lenovo Device [17aa:3978]
        Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)




```

How is this for a mess? I'm just not sure what I can remove without breaking what currently has me not getting a black screen even though my nvidia is gather dust.
```

 &#10140; sudo dpkg -l | grep nvidia                                                ~ 
rc  nvidia-340                                  340.65-0ubuntu1~xedgers14.10.1                         amd64        NVIDIA binary driver - version 340.65
rc  nvidia-346                                  346.35-0ubuntu1~xedgers14.10.1                         amd64        NVIDIA binary driver - version 346.35
ii  nvidia-opencl-icd-331                       331.113-0ubuntu1~xedgers14.10.1                        amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-346                       346.35-0ubuntu1~xedgers14.10.1                         amd64        NVIDIA OpenCL ICD
rc  nvidia-prime                                0.6.7                                                  amd64        Tools to enable NVIDIA's Prime
rc  nvidia-settings                             346.35-0ubuntu1~xedgers14.10.1                         amd64        Tool for configuring the NVIDIA graphics driver

```

---

### Post by Bashing-om on 2015-03-06
JDAIII; Sure;

Your query is related in this thread, we can continue here ( will get a broader audience with a new thread, but ).

OK, your output shows no driver available for the Nvidia chip set and as well some old residual files.
For instance:
> 
ii  nvidia-opencl-icd-331
 that needs to be gone !

Let's see what we are working with, to get an idea of what has to be cleaned up and a method to do that cleanup in order to properly install a proprietary driver.
What results :
```

find / -name "NVIDIA-Linux-*"
cat ~/.nvidia-settings-rc
dpkg -l | grep -i nvidia
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

Clean up
wipe the sweat off
[INDENT][INDENT]install from PPA afresh
[/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-06
Good times. I swear that you said 'clean up, wipe the seat off' no comment. For translation, I changed the profile for my zsh shell so it is left justified  &#10140; and my path is right justified so I was in ~

```

 &#10140; sudo find / -name "NVIDIA-Linux-*"                                        ~ 
 &#10140; cat ~/.nvidia-settings-rc                                                 ~ 
cat: /home/jd/.nvidia-settings-rc: No such file or directory
 &#10140; dpkg -l | grep -i nvidia                                                  ~ 
rc  libcuda1-331                                331.113-0ubuntu0.1                                     amd64        NVIDIA CUDA runtime library
rc  libcuda1-340                                340.65-0ubuntu1~xedgers14.10.1                         amd64        NVIDIA CUDA runtime library
rc  libcuda1-346                                346.35-0ubuntu1~xedgers14.10.1                         amd64        NVIDIA CUDA runtime library
rc  nvidia-340                                  340.65-0ubuntu1~xedgers14.10.1                         amd64        NVIDIA binary driver - version 340.65
rc  nvidia-346                                  346.35-0ubuntu1~xedgers14.10.1                         amd64        NVIDIA binary driver - version 346.35
ii  nvidia-opencl-icd-331                       331.113-0ubuntu1~xedgers14.10.1                        amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-346                       346.35-0ubuntu1~xedgers14.10.1                         amd64        NVIDIA OpenCL ICD
rc  nvidia-prime                                0.6.7                                                  amd64        Tools to enable NVIDIA's Prime
rc  nvidia-settings                             346.35-0ubuntu1~xedgers14.10.1                         amd64        Tool for configuring the NVIDIA graphics driver
 &#10140; cat -n /etc/apt/sources.list                                              ~ 
     1  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     2  # newer versions of the distribution.
     3  deb http://us.archive.ubuntu.com/ubuntu/ utopic main restricted
     4  deb-src http://us.archive.ubuntu.com/ubuntu/ utopic main restricted
     5  ## Major bug fix updates produced after the final release of the
     6  ## distribution.
     7  deb http://us.archive.ubuntu.com/ubuntu/ utopic-updates main restricted
     8  deb-src http://us.archive.ubuntu.com/ubuntu/ utopic-updates main restricted
     9
    10  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    11  ## team. Also, please note that software in universe WILL NOT receive any
    12  ## review or updates from the Ubuntu security team.
    13  deb http://us.archive.ubuntu.com/ubuntu/ utopic universe
    14  deb-src http://us.archive.ubuntu.com/ubuntu/ utopic universe
    15  deb http://us.archive.ubuntu.com/ubuntu/ utopic-updates universe
    16  deb-src http://us.archive.ubuntu.com/ubuntu/ utopic-updates universe
    17
    18  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    19  ## team, and may not be under a free licence. Please satisfy yourself as to 
    20  ## your rights to use the software. Also, please note that software in 
    21  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    22  ## security team.
    23  deb http://us.archive.ubuntu.com/ubuntu/ utopic multiverse
    24  deb-src http://us.archive.ubuntu.com/ubuntu/ utopic multiverse
    25  deb http://us.archive.ubuntu.com/ubuntu/ utopic-updates multiverse
    26  deb-src http://us.archive.ubuntu.com/ubuntu/ utopic-updates multiverse
    27
    28  ## N.B. software from this repository may not have been tested as
    29  ## extensively as that contained in the main release, although it includes
    30  ## newer versions of some applications which may provide useful features.
    31  ## Also, please note that software in backports WILL NOT receive any review
    32  ## or updates from the Ubuntu security team.
    33  deb http://us.archive.ubuntu.com/ubuntu/ utopic-backports main restricted universe multiverse
    34  deb-src http://us.archive.ubuntu.com/ubuntu/ utopic-backports main restricted universe multiverse
    35
    36  deb http://security.ubuntu.com/ubuntu utopic-security main restricted
    37  deb-src http://security.ubuntu.com/ubuntu utopic-security main restricted
    38  deb http://security.ubuntu.com/ubuntu utopic-security universe
    39  deb-src http://security.ubuntu.com/ubuntu utopic-security universe
    40  deb http://security.ubuntu.com/ubuntu utopic-security multiverse
    41  deb-src http://security.ubuntu.com/ubuntu utopic-security multiverse
    42
    43  ## Uncomment the following two lines to add software from Canonical's
    44  ## 'partner' repository.
    45  ## This software is not part of Ubuntu, but is offered by Canonical and the
    46  ## respective vendors as a service to Ubuntu users.
    47  # deb http://archive.canonical.com/ubuntu trusty partner
    48  # deb-src http://archive.canonical.com/ubuntu trusty partner
    49
    50  ## This software is not part of Ubuntu, but is offered by third-party
    51  ## developers who want to ship their latest software.
    52  deb http://extras.ubuntu.com/ubuntu utopic main
    53  deb-src http://extras.ubuntu.com/ubuntu utopic main
    54  deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 contrib
 &#10140; tail -v -n +1 /etc/apt/sources.list.d/*                                   ~ 
==> /etc/apt/sources.list.d/enlightenment-git-ppa-trusty.list <==
# deb http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu trusty main
==> /etc/apt/sources.list.d/enlightenment-git-ppa-trusty.list.distUpgrade <==
deb http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu trusty main
==> /etc/apt/sources.list.d/enlightenment-git-ppa-trusty.list.save <==
# deb http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/enlightenment-git/ppa/ubuntu trusty main
==> /etc/apt/sources.list.d/gnome3-team-ubuntu-gnome3-staging-utopic.list <==
deb http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu utopic main
# deb-src http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu utopic main
==> /etc/apt/sources.list.d/gnome3-team-ubuntu-gnome3-staging-utopic.list.save <==
deb http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu utopic main
# deb-src http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu utopic main
==> /etc/apt/sources.list.d/gnome3-team-ubuntu-gnome3-utopic.list <==
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu utopic main
# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu utopic main
# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu utopic main
==> /etc/apt/sources.list.d/gnome3-team-ubuntu-gnome3-utopic.list.save <==
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu utopic main
# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu utopic main
# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu utopic main
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
==> /etc/apt/sources.list.d/google-talkplugin.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main
==> /etc/apt/sources.list.d/google-talkplugin.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main
==> /etc/apt/sources.list.d/libreoffice-ubuntu-libreoffice-4-2-utopic.list <==
deb http://ppa.launchpad.net/libreoffice/libreoffice-4-2/ubuntu utopic main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-2/ubuntu utopic main
==> /etc/apt/sources.list.d/libreoffice-ubuntu-libreoffice-4-2-utopic.list.save <==
deb http://ppa.launchpad.net/libreoffice/libreoffice-4-2/ubuntu utopic main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-2/ubuntu utopic main
==> /etc/apt/sources.list.d/maarten-baert-ubuntu-simplescreenrecorder-utopic.list <==
deb http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu utopic main
# deb-src http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu utopic main
==> /etc/apt/sources.list.d/maarten-baert-ubuntu-simplescreenrecorder-utopic.list.save <==
deb http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu utopic main
# deb-src http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu utopic main
==> /etc/apt/sources.list.d/mamarley-ubuntu-nvidia-utopic.list <==
deb http://ppa.launchpad.net/mamarley/nvidia/ubuntu utopic main
# deb-src http://ppa.launchpad.net/mamarley/nvidia/ubuntu utopic main
==> /etc/apt/sources.list.d/mamarley-ubuntu-nvidia-utopic.list.save <==
deb http://ppa.launchpad.net/mamarley/nvidia/ubuntu utopic main
# deb-src http://ppa.launchpad.net/mamarley/nvidia/ubuntu utopic main
==> /etc/apt/sources.list.d/pmjdebruijn-ubuntu-darktable-release-utopic.list <==
deb http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu utopic main
# deb-src http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu utopic main
==> /etc/apt/sources.list.d/pmjdebruijn-ubuntu-darktable-release-utopic.list.save <==
deb http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu utopic main
# deb-src http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu utopic main
==> /etc/apt/sources.list.d/webupd8team-java-trusty.list <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.distUpgrade <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.save <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-nemo-trusty.list <==
# deb http://ppa.launchpad.net/webupd8team/nemo/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/webupd8team/nemo/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-nemo-trusty.list.distUpgrade <==
deb http://ppa.launchpad.net/webupd8team/nemo/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/nemo/ubuntu trusty main


==> /etc/apt/sources.list.d/webupd8team-nemo-trusty.list.save <==
# deb http://ppa.launchpad.net/webupd8team/nemo/ubuntu utopic main # disabled on upgrade to utopic
# deb-src http://ppa.launchpad.net/webupd8team/nemo/ubuntu trusty main



```

---

### Post by Bashing-om on 2015-03-06
JDAIII; Well, well ....


Sources.lists looks good to me .. I do not know why the mamarley PPA is ineffective. We will see about that.
No --uninstall file for any OEM installed driver ... moving on along
There is " ii  nvidia-opencl-icd-331 " to be removed... and as well all those 'rc' marked files - ( (R)emoved but (C)onfig files remain -> next !

Let's do this number:
```

sudo apt-get remove --purge nvidia-opencl-icd-331
sudo apt-get remove --purge nvidia*
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
which should clean all up;
Now let's see what results in attempting to install the driver from the mamarley PPA .
```

sudo apt-get update
sudo apt-get install nvidia-346

```
as the 346 version is what Nvida recommends for the 860m .
Did the installer also install ' nvidia-settings and Nvidia-prime ?
```

dpkg -l nvidia-prime
dpkg -l nvidia-settings

```
else IF the driver is installed but these are not for some reason... IF the driver is installed then install:
```

sudo apt-get install nvidia-prime
sudo apt-get install nvidia-settings

```

Reboot at this time and let's take a look.
Did the driver build ?
```

cat /var/log/Xorg.0.log

```
to see
and did it install ?
```

sudo lshw -C display

```
to see.
Could be all that is required .....

[INDENT][INDENT]maybe YES
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-06
I started on the steps, but it looks like it just purged a lot of stuff that I wasn't planning to delete. It even removed mysql which I can reinstall since I was going to dump the only DBs that I still have on there but I'm going to go through the list and reinstall some of these things that I need for work. I will continue the steps this evbening so I have the rest of the weekend to fix anything that goes wrong.

```
 &#10140; sudo apt-get remove --purge nvidia-opencl-icd-331                         ~ Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-opencl-icd-331*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 27.1 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 259858 files and directories currently installed.)
Removing nvidia-opencl-icd-331 (331.113-0ubuntu1~xedgers14.10.1) ...
Purging configuration files for nvidia-opencl-icd-331 (331.113-0ubuntu1~xedgers14.10.1) ...
Processing triggers for libc-bin (2.19-10ubuntu2.3) ...
 &#10140; sudo apt-get remove --purge nvidia*                                       ~ 
zsh: no matches found: nvidia*
 &#10140; dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge       ~ 
(Reading database ... 259849 files and directories currently installed.)
Removing foomatic-filters (4.0.17-4) ...
Purging configuration files for foomatic-filters (4.0.17-4) ...
Removing hplip (3.14.6-1ubuntu1) ...
Purging configuration files for hplip (3.14.6-1ubuntu1) ...
Removing lib32gcc1 (1:4.9.1-16ubuntu6) ...
Purging configuration files for lib32gcc1 (1:4.9.1-16ubuntu6) ...
Removing libass4:amd64 (0.10.1-3ubuntu1) ...
Purging configuration files for libass4:amd64 (0.10.1-3ubuntu1) ...
Removing libavahi-ui-gtk3-0:amd64 (0.6.31-4ubuntu1) ...
Purging configuration files for libavahi-ui-gtk3-0:amd64 (0.6.31-4ubuntu1) ...
Removing libavcodec54:amd64 (6:9.16-0ubuntu0.14.04.1) ...
Purging configuration files for libavcodec54:amd64 (6:9.16-0ubuntu0.14.04.1) ...
Removing libavformat54:amd64 (6:9.16-0ubuntu0.14.04.1) ...
Purging configuration files for libavformat54:amd64 (6:9.16-0ubuntu0.14.04.1) ...
Removing libavutil52:amd64 (6:9.16-0ubuntu0.14.04.1) ...
Purging configuration files for libavutil52:amd64 (6:9.16-0ubuntu0.14.04.1) ...
Removing libbonobo2-0:amd64 (2.32.1-3) ...
Purging configuration files for libbonobo2-0:amd64 (2.32.1-3) ...
Removing libbonobo2-common (2.32.1-3) ...
Purging configuration files for libbonobo2-common (2.32.1-3) ...
Removing libbonoboui2-0:amd64 (2.24.5-0ubuntu3) ...
Purging configuration files for libbonoboui2-0:amd64 (2.24.5-0ubuntu3) ...
Removing libboost-iostreams1.54.0:amd64 (1.54.0-5) ...
Purging configuration files for libboost-iostreams1.54.0:amd64 (1.54.0-5) ...
Removing libboost-program-options1.54.0:amd64 (1.54.0-5) ...
Purging configuration files for libboost-program-options1.54.0:amd64 (1.54.0-5) ...
Removing libboost-python1.54.0 (1.54.0-5) ...
Purging configuration files for libboost-python1.54.0 (1.54.0-5) ...
Removing libcamel-1.2-45 (3.10.4-0ubuntu1.5) ...
Purging configuration files for libcamel-1.2-45 (3.10.4-0ubuntu1.5) ...
Removing libcdr-0.0-0 (0.0.15-1ubuntu1) ...
Purging configuration files for libcdr-0.0-0 (0.0.15-1ubuntu1) ...
Removing libcogl-pango15:amd64 (1.16.2-1) ...
Purging configuration files for libcogl-pango15:amd64 (1.16.2-1) ...
Removing libcogl15:amd64 (1.16.2-1) ...
Purging configuration files for libcogl15:amd64 (1.16.2-1) ...
Removing libcolord1:amd64 (1.0.6-1) ...
Purging configuration files for libcolord1:amd64 (1.0.6-1) ...
Removing libcolorhug1:amd64 (1.0.6-1) ...
Purging configuration files for libcolorhug1:amd64 (1.0.6-1) ...
Removing libcuda1-331 (331.113-0ubuntu0.1) ...
Purging configuration files for libcuda1-331 (331.113-0ubuntu0.1) ...
Removing libcuda1-340 (340.65-0ubuntu1~xedgers14.10.1) ...
Purging configuration files for libcuda1-340 (340.65-0ubuntu1~xedgers14.10.1) ...
Removing libcuda1-346 (346.35-0ubuntu1~xedgers14.10.1) ...
Purging configuration files for libcuda1-346 (346.35-0ubuntu1~xedgers14.10.1) ...
Removing libdvbpsi8:amd64 (1.0.0-3) ...
Purging configuration files for libdvbpsi8:amd64 (1.0.0-3) ...
Removing libept1.4.12:amd64 (1.0.12) ...
Purging configuration files for libept1.4.12:amd64 (1.0.12) ...
Removing libexiv2-12 (0.23-1ubuntu2) ...
Purging configuration files for libexiv2-12 (0.23-1ubuntu2) ...
Removing libgdata13 (0.14.1-1) ...
Purging configuration files for libgdata13 (0.14.1-1) ...
Removing libglamor0:amd64 (0.6.0-0ubuntu4) ...
Purging configuration files for libglamor0:amd64 (0.6.0-0ubuntu4) ...
Removing libgnome2-0:amd64 (2.32.1-4ubuntu1) ...
Purging configuration files for libgnome2-0:amd64 (2.32.1-4ubuntu1) ...
Removing libgnome2-common (2.32.1-4ubuntu1) ...
Purging configuration files for libgnome2-common (2.32.1-4ubuntu1) ...
Removing libgnomecanvas2-0:amd64 (2.30.3-2) ...
Purging configuration files for libgnomecanvas2-0:amd64 (2.30.3-2) ...
Removing libgnomeui-0:amd64 (2.24.5-3) ...
Purging configuration files for libgnomeui-0:amd64 (2.24.5-3) ...
Removing libgnomevfs2-0:amd64 (1:2.24.4-6ubuntu1) ...
Purging configuration files for libgnomevfs2-0:amd64 (1:2.24.4-6ubuntu1) ...
Removing libgnomevfs2-common (1:2.24.4-6ubuntu1) ...
Purging configuration files for libgnomevfs2-common (1:2.24.4-6ubuntu1) ...
Removing libgnutls28:amd64 (3.2.11-2ubuntu1) ...
Purging configuration files for libgnutls28:amd64 (3.2.11-2ubuntu1) ...
Removing libgsoap4:amd64 (2.8.16-2) ...
Purging configuration files for libgsoap4:amd64 (2.8.16-2) ...
Removing libgtksourceview2.0-0 (2.10.5-1ubuntu2) ...
Purging configuration files for libgtksourceview2.0-0 (2.10.5-1ubuntu2) ...
Removing libgtop2-7 (2.28.5-2) ...
Purging configuration files for libgtop2-7 (2.28.5-2) ...
Removing libidl0:amd64 (0.8.14-0.4) ...
Purging configuration files for libidl0:amd64 (0.8.14-0.4) ...
Removing libinput0:amd64 (0.2.0-2) ...
Purging configuration files for libinput0:amd64 (0.2.0-2) ...
Removing libllvm3.5:amd64 (1:3.5-4ubuntu2) ...
Purging configuration files for libllvm3.5:amd64 (1:3.5-4ubuntu2) ...
Removing libmspub-0.0-0 (0.0.6-1ubuntu2) ...
Purging configuration files for libmspub-0.0-0 (0.0.6-1ubuntu2) ...
Removing libmutter0c (3.10.4-0ubuntu2.1) ...
Purging configuration files for libmutter0c (3.10.4-0ubuntu2.1) ...
Removing libmutter0d (3.12.2-1ubuntu2) ...
Purging configuration files for libmutter0d (3.12.2-1ubuntu2) ...
Removing liboil0.3:amd64 (0.3.17-2ubuntu4) ...
Purging configuration files for liboil0.3:amd64 (0.3.17-2ubuntu4) ...
Removing libopenjpeg2:amd64 (1.3+dfsg-4.7ubuntu1) ...
Purging configuration files for libopenjpeg2:amd64 (1.3+dfsg-4.7ubuntu1) ...
Removing liborbit-2-0:amd64 (1:2.14.19-0.3) ...
Purging configuration files for liborbit-2-0:amd64 (1:2.14.19-0.3) ...
Removing liborbit2:amd64 (1:2.14.19-0.3) ...
Purging configuration files for liborbit2:amd64 (1:2.14.19-0.3) ...
Removing liborcus-0.6-0 (0.5.1-7) ...
Purging configuration files for liborcus-0.6-0 (0.5.1-7) ...
Removing libparted0debian1:amd64 (2.3-19ubuntu1) ...
Purging configuration files for libparted0debian1:amd64 (2.3-19ubuntu1) ...
Removing libplist1:amd64 (1.10-1) ...
Purging configuration files for libplist1:amd64 (1.10-1) ...
Removing libplymouth2:amd64 (0.8.8-0ubuntu17.1) ...
Purging configuration files for libplymouth2:amd64 (0.8.8-0ubuntu17.1) ...
Removing libpoppler44:amd64 (0.24.5-2ubuntu4.1) ...
Purging configuration files for libpoppler44:amd64 (0.24.5-2ubuntu4.1) ...
Removing libqmi-glib0:amd64 (1.4.0-1) ...
Purging configuration files for libqmi-glib0:amd64 (1.4.0-1) ...
Removing libraw9:amd64 (0.15.4-1) ...
Purging configuration files for libraw9:amd64 (0.15.4-1) ...
Removing librtmp0:amd64 (2.4+20121230.gitdf6c518-1) ...
Purging configuration files for librtmp0:amd64 (2.4+20121230.gitdf6c518-1) ...
Removing libssh2-1:amd64 (1.4.3-3) ...
Purging configuration files for libssh2-1:amd64 (1.4.3-3) ...
Removing libswscale2:amd64 (6:9.16-0ubuntu0.14.04.1) ...
Purging configuration files for libswscale2:amd64 (6:9.16-0ubuntu0.14.04.1) ...
Removing libt1-5 (5.1.2-3.6ubuntu1) ...
Purging configuration files for libt1-5 (5.1.2-3.6ubuntu1) ...
Removing libtar0 (1.2.20-4) ...
Purging configuration files for libtar0 (1.2.20-4) ...
Removing libtracker-extract-0.16-0 (0.16.5-0ubuntu0.1) ...
Purging configuration files for libtracker-extract-0.16-0 (0.16.5-0ubuntu0.1) ...
Removing libtracker-miner-0.16-0 (0.16.5-0ubuntu0.1) ...
Purging configuration files for libtracker-miner-0.16-0 (0.16.5-0ubuntu0.1) ...
Removing libtracker-sparql-0.16-0 (0.16.5-0ubuntu0.1) ...
Purging configuration files for libtracker-sparql-0.16-0 (0.16.5-0ubuntu0.1) ...
Removing libvisio-0.0-0 (0.0.31-1ubuntu2) ...
Purging configuration files for libvisio-0.0-0 (0.0.31-1ubuntu2) ...
Removing libvlccore7 (2.1.4-0ubuntu14.04.1) ...
Purging configuration files for libvlccore7 (2.1.4-0ubuntu14.04.1) ...
Removing libwpd-0.9-9 (0.9.9-1) ...
Purging configuration files for libwpd-0.9-9 (0.9.9-1) ...
Removing libwpg-0.2-2 (0.2.2-1ubuntu1) ...
Purging configuration files for libwpg-0.2-2 (0.2.2-1ubuntu1) ...
Removing libwps-0.2-2 (0.2.9-2ubuntu1) ...
Purging configuration files for libwps-0.2-2 (0.2.9-2ubuntu1) ...
Removing libwxbase2.8-0:amd64 (2.8.12.1+dfsg2-2ubuntu1) ...
Purging configuration files for libwxbase2.8-0:amd64 (2.8.12.1+dfsg2-2ubuntu1) ...
Removing libwxgtk2.8-0:amd64 (2.8.12.1+dfsg2-2ubuntu1) ...
Purging configuration files for libwxgtk2.8-0:amd64 (2.8.12.1+dfsg2-2ubuntu1) ...
Removing linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Purging configuration files for linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Removing linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Purging configuration files for linux-image-3.13.0-43-generic (3.13.0-43.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-43-generic /boot/vmlinuz-3.13.0-43-generic
Removing linux-image-3.16.0-28-generic (3.16.0-28.38) ...
Purging configuration files for linux-image-3.16.0-28-generic (3.16.0-28.38) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-28-generic /boot/vmlinuz-3.16.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-28-generic /boot/vmlinuz-3.16.0-28-generic
Removing linux-image-extra-3.13.0-32-generic (3.13.0-32.57) ...
Purging configuration files for linux-image-extra-3.13.0-32-generic (3.13.0-32.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Removing linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
Purging configuration files for linux-image-extra-3.13.0-43-generic (3.13.0-43.72) ...
Removing linux-image-extra-3.16.0-28-generic (3.16.0-28.38) ...
Purging configuration files for linux-image-extra-3.16.0-28-generic (3.16.0-28.38) ...
Removing linux-signed-image-3.13.0-43-generic (3.13.0-43.72) ...
Purging configuration files for linux-signed-image-3.13.0-43-generic (3.13.0-43.72) ...
Removing mysql-server-5.5 (5.5.41-0ubuntu0.14.10.1) ...
Purging configuration files for mysql-server-5.5 (5.5.41-0ubuntu0.14.10.1) ...
Removing nvidia-340 (340.65-0ubuntu1~xedgers14.10.1) ...
Purging configuration files for nvidia-340 (340.65-0ubuntu1~xedgers14.10.1) ...
update-initramfs: deferring update (trigger activated)
Removing nvidia-346 (346.35-0ubuntu1~xedgers14.10.1) ...
Purging configuration files for nvidia-346 (346.35-0ubuntu1~xedgers14.10.1) ...
update-initramfs: deferring update (trigger activated)
Removing nvidia-opencl-icd-346 (346.35-0ubuntu1~xedgers14.10.1) ...
Purging configuration files for nvidia-opencl-icd-346 (346.35-0ubuntu1~xedgers14.10.1) ...
Removing nvidia-prime (0.6.7) ...
Purging configuration files for nvidia-prime (0.6.7) ...
Removing nvidia-settings (346.35-0ubuntu1~xedgers14.10.1) ...
Purging configuration files for nvidia-settings (346.35-0ubuntu1~xedgers14.10.1) ...
Removing openprinting-gutenprint (5.2.7-1lsb3.2) ...
Purging configuration files for openprinting-gutenprint (5.2.7-1lsb3.2) ...
cups stop/waiting
cups start/running, process 15242
Removing powertop (2.5-1ubuntu1) ...
Purging configuration files for powertop (2.5-1ubuntu1) ...
Removing printer-driver-pnm2ppa (1.13+nondbs-0ubuntu5) ...
Purging configuration files for printer-driver-pnm2ppa (1.13+nondbs-0ubuntu5) ...
Removing python-cupshelpers (1.4.3+20140219-0ubuntu2.2) ...
Purging configuration files for python-cupshelpers (1.4.3+20140219-0ubuntu2.2) ...
Removing screen-resolution-extra (0.17.1) ...
Purging configuration files for screen-resolution-extra (0.17.1) ...
Removing systemd-services (204-5ubuntu20.9) ...
Purging configuration files for systemd-services (204-5ubuntu20.9) ...
Removing vinagre (3.10.2-0ubuntu1) ...
Purging configuration files for vinagre (3.10.2-0ubuntu1) ...
Removing xscreensaver (5.26-1ubuntu3) ...
Purging configuration files for xscreensaver (5.26-1ubuntu3) ...
Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-31-generic



```

---

### Post by Bashing-om on 2015-03-06
JDAIII; YUK !

I do not know what could have happened to have that turn of events:

That command sequence:
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package with the following command.
As it should purge all [color=red]removed[/color] but not yet purged packages only removing all the packages marked as rc.

I have run that sequence numerous times and have never had a adverse effect !

With that said, I t should not even " It even removed mysql " have touched any installed application.
see:
source:[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)
for info. Those docs are out-of date now as their example 
```

dpkg -l | grep '^rc' | awk '{print $2}' | xargs dpkg --purge

```
" if you are using awk then it is rare to need grep, too. Awk has most of the same capabilities. " this is depreciated.
to -> 
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

``` as indicated in my instruction.

May I suggest that you make sure that mysql has been adversely effected ? I just do not understand the how it could have.

---

### Post by JDAIII on 2015-03-06
No worries about mysql. I have to reinstall a piece of software that works best if it installs mysql itself.

So, good news/bad news.

Good news first, I am posting so I was able to uninstall nvidia-346 and didn't have to reformat and reinstall ubuntu. yippee for me.

Bad news, this will be a long post with logs and what not as I got the black screen of death upon installing nvidia-346. BSOD should work for black and not just blue.

Begin terminal output:


Install nvidia-346

```
 &#10140; sudo apt-get update                                                       ~ Ign http://www.openprinting.org lsb3.2 InRelease                               
Ign http://dl.google.com stable InRelease                                      
Ign http://us.archive.ubuntu.com utopic InRelease                              
Ign http://extras.ubuntu.com utopic InRelease                                  
Hit http://www.openprinting.org lsb3.2 Release.gpg                             
Ign http://ppa.launchpad.net utopic InRelease                                  
Ign http://security.ubuntu.com utopic-security InRelease                       
Hit http://www.openprinting.org lsb3.2 Release                                 
Ign http://dl.google.com stable InRelease                                      
Ign http://us.archive.ubuntu.com utopic-updates InRelease                      
Ign http://ppa.launchpad.net utopic InRelease                                  
Hit http://extras.ubuntu.com utopic Release.gpg                                
Get:1 http://security.ubuntu.com utopic-security Release.gpg [933 B]           
Hit http://www.openprinting.org lsb3.2/contrib amd64 Packages                  
Hit http://dl.google.com stable Release.gpg                                    
Ign http://us.archive.ubuntu.com utopic-backports InRelease                    
Hit http://extras.ubuntu.com utopic Release                                    
Ign http://ppa.launchpad.net utopic InRelease                                  
Get:2 http://security.ubuntu.com utopic-security Release [62.0 kB]             
Hit http://www.openprinting.org lsb3.2/contrib i386 Packages                   
Hit http://dl.google.com stable Release.gpg                                    
Hit http://us.archive.ubuntu.com utopic Release.gpg                            
Hit http://extras.ubuntu.com utopic/main Sources                               
Ign http://ppa.launchpad.net utopic InRelease                                  
Hit http://dl.google.com stable Release                                        
Get:3 http://us.archive.ubuntu.com utopic-updates Release.gpg [933 B]          
Ign http://ppa.launchpad.net utopic InRelease                                  
Hit http://extras.ubuntu.com utopic/main amd64 Packages                        
Hit http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com utopic-backports Release.gpg                  
Ign http://ppa.launchpad.net utopic InRelease                                  
Hit http://extras.ubuntu.com utopic/main i386 Packages                         
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://us.archive.ubuntu.com utopic Release                                
Hit http://ppa.launchpad.net utopic Release.gpg                                
Hit http://ppa.launchpad.net utopic Release.gpg                                
Get:4 http://security.ubuntu.com utopic-security/main Sources [41.9 kB]        
Get:5 http://us.archive.ubuntu.com utopic-updates Release [62.0 kB]            
Hit http://ppa.launchpad.net utopic Release.gpg                                
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://ppa.launchpad.net utopic Release.gpg                                
Get:6 http://security.ubuntu.com utopic-security/restricted Sources [2,107 B]  
Hit http://us.archive.ubuntu.com utopic-backports Release                      
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net utopic Release.gpg                                
Hit http://us.archive.ubuntu.com utopic/main Sources                           
Hit http://dl.google.com stable/main i386 Packages                             
Get:7 http://security.ubuntu.com utopic-security/universe Sources [8,059 B]    
Hit http://ppa.launchpad.net utopic Release.gpg                                
Hit http://us.archive.ubuntu.com utopic/restricted Sources                     
Hit http://ppa.launchpad.net utopic Release                                    
Get:8 http://security.ubuntu.com utopic-security/multiverse Sources [1,947 B]  
Hit http://us.archive.ubuntu.com utopic/universe Sources                       
Hit http://us.archive.ubuntu.com utopic/multiverse Sources                     
Hit http://ppa.launchpad.net utopic Release                                    
Get:9 http://security.ubuntu.com utopic-security/main amd64 Packages [124 kB]  
Hit http://us.archive.ubuntu.com utopic/main amd64 Packages                    
Hit http://ppa.launchpad.net utopic Release                                    
Ign http://extras.ubuntu.com utopic/main Translation-en_US                     
Hit http://us.archive.ubuntu.com utopic/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com utopic/universe amd64 Packages                
Hit http://ppa.launchpad.net utopic Release                                    
Ign http://extras.ubuntu.com utopic/main Translation-en                        
Hit http://us.archive.ubuntu.com utopic/multiverse amd64 Packages              
Hit http://ppa.launchpad.net utopic Release                                    
Ign http://www.openprinting.org lsb3.2/contrib Translation-en_US               
Hit http://us.archive.ubuntu.com utopic/main i386 Packages                     
Hit http://ppa.launchpad.net utopic Release                                    
Hit http://us.archive.ubuntu.com utopic/restricted i386 Packages               
Hit http://www.openprinting.org lsb3.2/contrib Translation-en                  
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com utopic/universe i386 Packages                 
Hit http://ppa.launchpad.net utopic/main amd64 Packages                        
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com utopic/multiverse i386 Packages               
Hit http://ppa.launchpad.net utopic/main i386 Packages                         
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com utopic/main Translation-en                    
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com utopic/multiverse Translation-en              
Hit http://ppa.launchpad.net utopic/main Translation-en                        
Get:10 http://security.ubuntu.com utopic-security/restricted amd64 Packages [8,496 B]
Hit http://us.archive.ubuntu.com utopic/restricted Translation-en              
Hit http://ppa.launchpad.net utopic/main amd64 Packages                        
Hit http://us.archive.ubuntu.com utopic/universe Translation-en                
Get:11 http://us.archive.ubuntu.com utopic-updates/main Sources [76.3 kB]      
Hit http://ppa.launchpad.net utopic/main i386 Packages                         
Get:12 http://security.ubuntu.com utopic-security/universe amd64 Packages [51.9 kB]
Hit http://ppa.launchpad.net utopic/main Translation-en                        
Hit http://ppa.launchpad.net utopic/main amd64 Packages                        
Hit http://ppa.launchpad.net utopic/main i386 Packages                         
Hit http://ppa.launchpad.net utopic/main Translation-en                        
Get:13 http://us.archive.ubuntu.com utopic-updates/restricted Sources [2,107 B]
Get:14 http://security.ubuntu.com utopic-security/multiverse amd64 Packages [4,133 B]
Hit http://ppa.launchpad.net utopic/main amd64 Packages                        
Get:15 http://us.archive.ubuntu.com utopic-updates/universe Sources [19.4 kB]  
Hit http://ppa.launchpad.net utopic/main i386 Packages                         
Get:16 http://security.ubuntu.com utopic-security/main i386 Packages [123 kB]  
Hit http://ppa.launchpad.net utopic/main Translation-en                        
Get:17 http://us.archive.ubuntu.com utopic-updates/multiverse Sources [1,947 B]
Get:18 http://us.archive.ubuntu.com utopic-updates/main amd64 Packages [199 kB]
Hit http://ppa.launchpad.net utopic/main amd64 Packages                        
Hit http://ppa.launchpad.net utopic/main i386 Packages                         
Hit http://ppa.launchpad.net utopic/main Translation-en                        
Hit http://ppa.launchpad.net utopic/main amd64 Packages                        
Get:19 http://security.ubuntu.com utopic-security/restricted i386 Packages [8,438 B]
Hit http://ppa.launchpad.net utopic/main i386 Packages                         
Get:20 http://security.ubuntu.com utopic-security/universe i386 Packages [51.8 kB]
Hit http://ppa.launchpad.net utopic/main Translation-en                        
Get:21 http://security.ubuntu.com utopic-security/multiverse i386 Packages [4,320 B]
Get:22 http://us.archive.ubuntu.com utopic-updates/restricted amd64 Packages [8,496 B]
Get:23 http://us.archive.ubuntu.com utopic-updates/universe amd64 Packages [77.9 kB]
Hit http://security.ubuntu.com utopic-security/main Translation-en             
Hit http://security.ubuntu.com utopic-security/multiverse Translation-en       
Hit http://security.ubuntu.com utopic-security/restricted Translation-en       
Get:24 http://us.archive.ubuntu.com utopic-updates/multiverse amd64 Packages [4,133 B]
Get:25 http://us.archive.ubuntu.com utopic-updates/main i386 Packages [198 kB] 
Hit http://security.ubuntu.com utopic-security/universe Translation-en         
Get:26 http://us.archive.ubuntu.com utopic-updates/restricted i386 Packages [8,438 B]
Get:27 http://us.archive.ubuntu.com utopic-updates/universe i386 Packages [77.8 kB]
Get:28 http://us.archive.ubuntu.com utopic-updates/multiverse i386 Packages [4,320 B]
Hit http://us.archive.ubuntu.com utopic-updates/main Translation-en            
Hit http://us.archive.ubuntu.com utopic-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com utopic-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com utopic-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com utopic-backports/main Sources                 
Hit http://us.archive.ubuntu.com utopic-backports/restricted Sources           
Hit http://us.archive.ubuntu.com utopic-backports/universe Sources             
Hit http://us.archive.ubuntu.com utopic-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com utopic-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com utopic-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com utopic-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com utopic-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com utopic-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com utopic-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com utopic-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com utopic-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com utopic-backports/main Translation-en          
Hit http://us.archive.ubuntu.com utopic-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com utopic-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com utopic-backports/universe Translation-en      
Fetched 1,234 kB in 25s (48.1 kB/s)                                            
Reading package lists... Done
 &#10140; sudo apt-get install nvidia-346                                           ~ 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bbswitch-dkms lib32gcc1 libc6-i386 libcuda1-346 nvidia-libopencl1-346
  nvidia-opencl-icd-346 nvidia-prime nvidia-settings screen-resolution-extra
Suggested packages:
  bumblebee nvidia-346-uvm
The following packages will be REMOVED:
  ocl-icd-libopencl1
The following NEW packages will be installed:
  bbswitch-dkms lib32gcc1 libc6-i386 libcuda1-346 nvidia-346
  nvidia-libopencl1-346 nvidia-opencl-icd-346 nvidia-prime nvidia-settings
  screen-resolution-extra
0 upgraded, 10 newly installed, 1 to remove and 0 not upgraded.
Need to get 70.2 MB of archives.
After this operation, 314 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libc6-i386 amd64 2.19-10ubuntu2.3 [2,214 kB]
Get:2 http://ppa.launchpad.net/mamarley/nvidia/ubuntu/ utopic/main libcuda1-346 amd64 346.47-100ubuntu100~ppa0~utopic [7,738 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ utopic-updates/main libc6-i386 amd64 2.19-10ubuntu2.3 [2,214 kB]
Get:4 http://ppa.launchpad.net/mamarley/nvidia/ubuntu/ utopic/main libcuda1-346 amd64 346.47-100ubuntu100~ppa0~utopic [7,738 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ utopic/main lib32gcc1 amd64 1:4.9.1-16ubuntu6 [48.0 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ utopic/main bbswitch-dkms amd64 0.7-2ubuntu1 [10.9 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ utopic/main nvidia-prime amd64 0.6.7 [11.4 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ utopic/main screen-resolution-extra all 0.17.1 [11.4 kB]
Get:9 http://ppa.launchpad.net/mamarley/nvidia/ubuntu/ utopic/main nvidia-346 amd64 346.47-100ubuntu100~ppa0~utopic [51.4 MB]
Get:10 http://ppa.launchpad.net/mamarley/nvidia/ubuntu/ utopic/main nvidia-libopencl1-346 amd64 346.47-100ubuntu100~ppa0~utopic [18.2 kB]
Get:11 http://ppa.launchpad.net/mamarley/nvidia/ubuntu/ utopic/main nvidia-opencl-icd-346 amd64 346.47-100ubuntu100~ppa0~utopic [7,831 kB]
Get:12 http://ppa.launchpad.net/mamarley/nvidia/ubuntu/ utopic/main nvidia-settings amd64 346.47-100ubuntu100~ppa0~utopic [943 kB]
Fetched 69.4 MB in 2min 55s (397 kB/s)                                         
(Reading database ... 259817 files and directories currently installed.)
Removing ocl-icd-libopencl1:amd64 (2.1.3-5) ...
Processing triggers for man-db (2.7.0.2-2) ...
Processing triggers for libc-bin (2.19-10ubuntu2.3) ...
Selecting previously unselected package libc6-i386.
(Reading database ... 259803 files and directories currently installed.)
Preparing to unpack .../libc6-i386_2.19-10ubuntu2.3_amd64.deb ...
Unpacking libc6-i386 (2.19-10ubuntu2.3) ...
Selecting previously unselected package libcuda1-346.
Preparing to unpack .../libcuda1-346_346.47-100ubuntu100~ppa0~utopic_amd64.deb ...
Unpacking libcuda1-346 (346.47-100ubuntu100~ppa0~utopic) ...
Selecting previously unselected package lib32gcc1.
Preparing to unpack .../lib32gcc1_1%3a4.9.1-16ubuntu6_amd64.deb ...
Unpacking lib32gcc1 (1:4.9.1-16ubuntu6) ...
Selecting previously unselected package nvidia-346.
Preparing to unpack .../nvidia-346_346.47-100ubuntu100~ppa0~utopic_amd64.deb ...
Unpacking nvidia-346 (346.47-100ubuntu100~ppa0~utopic) ...
Selecting previously unselected package nvidia-libopencl1-346.
Preparing to unpack .../nvidia-libopencl1-346_346.47-100ubuntu100~ppa0~utopic_amd64.deb ...
Unpacking nvidia-libopencl1-346 (346.47-100ubuntu100~ppa0~utopic) ...
Selecting previously unselected package nvidia-opencl-icd-346.
Preparing to unpack .../nvidia-opencl-icd-346_346.47-100ubuntu100~ppa0~utopic_amd64.deb ...
Unpacking nvidia-opencl-icd-346 (346.47-100ubuntu100~ppa0~utopic) ...
Selecting previously unselected package bbswitch-dkms.
Preparing to unpack .../bbswitch-dkms_0.7-2ubuntu1_amd64.deb ...
Unpacking bbswitch-dkms (0.7-2ubuntu1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.6.7_amd64.deb ...
Unpacking nvidia-prime (0.6.7) ...
Selecting previously unselected package screen-resolution-extra.
Preparing to unpack .../screen-resolution-extra_0.17.1_all.deb ...
Unpacking screen-resolution-extra (0.17.1) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_346.47-100ubuntu100~ppa0~utopic_amd64.deb ...
Unpacking nvidia-settings (346.47-100ubuntu100~ppa0~utopic) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.7.0.2-2) ...
Processing triggers for dbus (1.8.8-1ubuntu2.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
Processing triggers for mime-support (3.55ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Setting up libc6-i386 (2.19-10ubuntu2.3) ...
Setting up libcuda1-346 (346.47-100ubuntu100~ppa0~utopic) ...
Setting up lib32gcc1 (1:4.9.1-16ubuntu6) ...
Setting up nvidia-346 (346.47-100ubuntu100~ppa0~utopic) ...
update-alternatives: using /usr/lib/nvidia-346/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-346/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-346/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-346
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Adding system user `nvidia-persistenced' (UID 119) ...
Adding new group `nvidia-persistenced' (GID 130) ...
Adding new user `nvidia-persistenced' (UID 119) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-346-346.47 DKMS files...
First Installation: checking all kernels...
Building only for 3.16.0-31-generic
Building for architecture x86_64
Building initial module for 3.16.0-31-generic
Done.
nvidia_346:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.16.0-31-generic/updates/dkms/
depmod....
DKMS: install completed.
Setting up nvidia-libopencl1-346 (346.47-100ubuntu100~ppa0~utopic) ...
Setting up nvidia-opencl-icd-346 (346.47-100ubuntu100~ppa0~utopic) ...
Setting up bbswitch-dkms (0.7-2ubuntu1) ...
Loading new bbswitch-0.7 DKMS files...
First Installation: checking all kernels...
Building only for 3.16.0-31-generic
Building initial module for 3.16.0-31-generic
Done.


bbswitch:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.16.0-31-generic/updates/dkms/


depmod....


DKMS: install completed.
Setting up nvidia-prime (0.6.7) ...
nvidia-prime start/running, process 9553
Setting up screen-resolution-extra (0.17.1) ...
Processing triggers for dbus (1.8.8-1ubuntu2.1) ...
Setting up nvidia-settings (346.47-100ubuntu100~ppa0~utopic) ...
Processing triggers for libc-bin (2.19-10ubuntu2.3) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-31-generic



```

Veriofy nvidia install
```
 &#10140; dpkg -l nvidia-prime                                                      ~ Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  nvidia-prime   0.6.7        amd64        Tools to enable NVIDIA's Prime
 &#10140; dpkg -l nvidia-settings                                                   ~ 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  nvidia-setting 346.47-100ub amd64        Tool for configuring the NVIDIA g
 &#10140;         
```

verify xorg since nvidia-prime and nvidia-settings were both installed correctly

```
 &#10140; cat /var/log/Xorg.0.log                                                   ~ [     9.507] 
X.Org X Server 1.16.1.901 (1.16.2 RC 1)
Release Date: 2014-11-02
[     9.507] X Protocol Version 11, Revision 0
[     9.507] Build Operating System: Linux 3.13.0-39-generic x86_64 Ubuntu
[     9.507] Current Operating System: Linux jd-laptop 3.16.0-31-generic #41-Ubuntu SMP Tue Feb 10 15:24:04 UTC 2015 x86_64
[     9.507] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-31-generic root=UUID=9ba789c0-7d71-4b8e-b093-51d9db78b777 ro quiet splash vt.handoff=7
[     9.507] Build Date: 20 November 2014  09:55:19PM
[     9.507] xorg-server 2:1.16.1.901-1ubuntu1~utopic1 (For technical support please see http://www.ubuntu.com/support) 
[     9.507] Current version of pixman: 0.32.4
[     9.507]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[     9.507] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.507] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  6 13:57:44 2015
[     9.507] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.507] (==) No Layout section.  Using the first Screen section.
[     9.507] (==) No screen section available. Using defaults.
[     9.507] (**) |-->Screen "Default Screen Section" (0)
[     9.507] (**) |   |-->Monitor "<default monitor>"
[     9.508] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[     9.508] (==) Automatically adding devices
[     9.508] (==) Automatically enabling devices
[     9.508] (==) Automatically adding GPU devices
[     9.508] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.508]    Entry deleted from font path.
[     9.508] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.508]    Entry deleted from font path.
[     9.508] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.508]    Entry deleted from font path.
[     9.508] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.508]    Entry deleted from font path.
[     9.508] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.508]    Entry deleted from font path.
[     9.508] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[     9.508] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     9.508] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.508] (II) Loader magic: 0x7fccdf702d80
[     9.508] (II) Module ABI versions:
[     9.508]    X.Org ANSI C Emulation: 0.4
[     9.508]    X.Org Video Driver: 18.0
[     9.508]    X.Org XInput driver : 21.0
[     9.508]    X.Org Server Extension : 8.0
[     9.508] (II) xfree86: Adding drm device (/dev/dri/card0)
[     9.509] (--) PCI:*(0:0:2:0) 8086:0416:17aa:3978 rev 6, Mem @ 0xd1000000/4194304, 0xc0000000/268435456, I/O @ 0x00005000/64
[     9.509] (--) PCI: (0:1:0:0) 10de:1392:17aa:3978 rev 162, Mem @ 0xd0000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[     9.510] (II) LoadModule: "glx"
[     9.510] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     9.516] (II) Module glx: vendor="X.Org Foundation"
[     9.516]    compiled for 1.16.1.901, module version = 1.0.0
[     9.516]    ABI class: X.Org Server Extension, version 8.0
[     9.516] (==) AIGLX enabled
[     9.516] (==) Matched intel as autoconfigured driver 0
[     9.516] (==) Matched intel as autoconfigured driver 1
[     9.516] (==) Matched modesetting as autoconfigured driver 2
[     9.516] (==) Matched fbdev as autoconfigured driver 3
[     9.516] (==) Matched vesa as autoconfigured driver 4
[     9.516] (==) Assigned the driver to the xf86ConfigLayout
[     9.516] (II) LoadModule: "intel"
[     9.516] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     9.517] (II) Module intel: vendor="X.Org Foundation"
[     9.517]    compiled for 1.16.1.901, module version = 2.99.917
[     9.517]    Module class: X.Org Video Driver
[     9.517]    ABI class: X.Org Video Driver, version 18.0
[     9.517] (II) LoadModule: "modesetting"
[     9.517] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     9.517] (II) Module modesetting: vendor="X.Org Foundation"
[     9.517]    compiled for 1.16.0, module version = 0.9.0
[     9.517]    Module class: X.Org Video Driver
[     9.517]    ABI class: X.Org Video Driver, version 18.0
[     9.517] (II) LoadModule: "fbdev"
[     9.517] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     9.517] (II) Module fbdev: vendor="X.Org Foundation"
[     9.517]    compiled for 1.16.0, module version = 0.4.4
[     9.517]    Module class: X.Org Video Driver
[     9.517]    ABI class: X.Org Video Driver, version 18.0
[     9.517] (II) LoadModule: "vesa"
[     9.518] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     9.518] (II) Module vesa: vendor="X.Org Foundation"
[     9.518]    compiled for 1.16.0, module version = 2.3.3
[     9.518]    Module class: X.Org Video Driver
[     9.518]    ABI class: X.Org Video Driver, version 18.0
[     9.518] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[     9.518] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[     9.518] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[     9.518] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[     9.518] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     9.518] (II) FBDEV: driver for framebuffer: fbdev
[     9.518] (II) VESA: driver for VESA chipsets: vesa
[     9.518] (++) using VT number 7
[     9.518] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[     9.518] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150304.88e61542-0ubuntu0sarvatt~utopic (Robert Hooker <sarvatt@ubuntu.com>)
[     9.518] (II) intel(0): SNA compiled for use with valgrind
[     9.518] (WW) Falling back to old probe method for modesetting
[     9.518] (WW) Falling back to old probe method for fbdev
[     9.518] (II) Loading sub module "fbdevhw"
[     9.518] (II) LoadModule: "fbdevhw"
[     9.518] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     9.519] (II) Module fbdevhw: vendor="X.Org Foundation"
[     9.519]    compiled for 1.16.1.901, module version = 0.0.2
[     9.519]    ABI class: X.Org Video Driver, version 18.0
[     9.519] (WW) Falling back to old probe method for vesa
[     9.519] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[     9.519] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[     9.519] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[     9.519] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     9.519] (==) intel(0): RGB weight 888
[     9.519] (==) intel(0): Default visual is TrueColor
[     9.519] (II) intel(0): Output eDP1 has no monitor section
[     9.519] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[     9.519] (II) intel(0): Enabled output eDP1
[     9.519] (II) intel(0): Output VGA1 has no monitor section
[     9.519] (II) intel(0): Enabled output VGA1
[     9.519] (II) intel(0): Output HDMI1 has no monitor section
[     9.519] (II) intel(0): Enabled output HDMI1
[     9.519] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[     9.519] (II) intel(0): Output VIRTUAL1 has no monitor section
[     9.519] (II) intel(0): Enabled output VIRTUAL1
[     9.519] (--) intel(0): Output eDP1 using initial mode 3840x2160 on pipe 0
[     9.519] (==) intel(0): TearFree disabled
[     9.519] (==) intel(0): DPI set to (96, 96)
[     9.519] (II) Loading sub module "dri2"
[     9.519] (II) LoadModule: "dri2"
[     9.519] (II) Module "dri2" already built-in
[     9.519] (II) Loading sub module "present"
[     9.519] (II) LoadModule: "present"
[     9.519] (II) Module "present" already built-in
[     9.519] (II) UnloadModule: "modesetting"
[     9.519] (II) Unloading modesetting
[     9.519] (II) UnloadModule: "fbdev"
[     9.519] (II) Unloading fbdev
[     9.519] (II) UnloadSubModule: "fbdevhw"
[     9.519] (II) Unloading fbdevhw
[     9.519] (II) UnloadModule: "vesa"
[     9.519] (II) Unloading vesa
[     9.519] (==) Depth 24 pixmap format is 32 bpp
[     9.521] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[     9.521] (==) intel(0): Backing store enabled
[     9.521] (==) intel(0): Silken mouse enabled
[     9.521] (II) intel(0): HW Cursor enabled
[     9.521] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     9.522] (==) intel(0): DPMS enabled
[     9.522] (==) intel(0): Display hotplug detection enabled
[     9.522] (II) intel(0): [DRI2] Setup complete
[     9.522] (II) intel(0): [DRI2]   DRI driver: i965
[     9.522] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[     9.522] (II) intel(0): direct rendering: DRI2 enabled
[     9.522] (II) intel(0): hardware support for Present enabled
[     9.522] (--) RandR disabled
[     9.526] (II) SELinux: Disabled on system
[     9.550] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     9.550] (II) AIGLX: enabled GLX_ARB_create_context
[     9.550] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     9.550] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     9.550] (II) AIGLX: enabled GLX_INTEL_swap_event
[     9.550] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     9.550] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     9.550] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     9.550] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     9.550] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[     9.550] (II) AIGLX: Loaded and initialized i965
[     9.550] (II) GLX: Initialized DRI2 GL provider for screen 0
[     9.555] (II) intel(0): switch to mode 3840x2160@48.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[     9.556] (II) intel(0): Setting screen physical size to 1016 x 571
[     9.562] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     9.564] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[     9.564] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     9.564] (II) LoadModule: "evdev"
[     9.564] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     9.566] (II) Module evdev: vendor="X.Org Foundation"
[     9.566]    compiled for 1.16.0, module version = 2.9.0
[     9.566]    Module class: X.Org XInput Driver
[     9.566]    ABI class: X.Org XInput driver, version 21.0
[     9.566] (II) Using input driver 'evdev' for 'Power Button'
[     9.566] (**) Power Button: always reports core events
[     9.566] (**) evdev: Power Button: Device: "/dev/input/event3"
[     9.566] (--) evdev: Power Button: Vendor 0 Product 0x1
[     9.566] (--) evdev: Power Button: Found keys
[     9.566] (II) evdev: Power Button: Configuring as keyboard
[     9.566] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[     9.566] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     9.566] (**) Option "xkb_rules" "evdev"
[     9.566] (**) Option "xkb_model" "pc105"
[     9.566] (**) Option "xkb_layout" "us"
[     9.566] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[     9.566] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     9.566] (II) Using input driver 'evdev' for 'Video Bus'
[     9.566] (**) Video Bus: always reports core events
[     9.566] (**) evdev: Video Bus: Device: "/dev/input/event6"
[     9.566] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     9.566] (--) evdev: Video Bus: Found keys
[     9.566] (II) evdev: Video Bus: Configuring as keyboard
[     9.566] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8/event6"
[     9.566] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     9.566] (**) Option "xkb_rules" "evdev"
[     9.566] (**) Option "xkb_model" "pc105"
[     9.566] (**) Option "xkb_layout" "us"
[     9.566] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     9.566] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     9.567] (II) Using input driver 'evdev' for 'Power Button'
[     9.567] (**) Power Button: always reports core events
[     9.567] (**) evdev: Power Button: Device: "/dev/input/event0"
[     9.567] (--) evdev: Power Button: Vendor 0 Product 0x1
[     9.567] (--) evdev: Power Button: Found keys
[     9.567] (II) evdev: Power Button: Configuring as keyboard
[     9.567] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[     9.567] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     9.567] (**) Option "xkb_rules" "evdev"
[     9.567] (**) Option "xkb_model" "pc105"
[     9.567] (**) Option "xkb_layout" "us"
[     9.567] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[     9.567] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     9.567] (II) Using input driver 'evdev' for 'Sleep Button'
[     9.567] (**) Sleep Button: always reports core events
[     9.567] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[     9.567] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[     9.567] (--) evdev: Sleep Button: Found keys
[     9.567] (II) evdev: Sleep Button: Configuring as keyboard
[     9.567] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input1/event1"
[     9.567] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[     9.567] (**) Option "xkb_rules" "evdev"
[     9.567] (**) Option "xkb_model" "pc105"
[     9.567] (**) Option "xkb_layout" "us"
[     9.567] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[     9.567] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     9.567] (II) Using input driver 'evdev' for 'Video Bus'
[     9.567] (**) Video Bus: always reports core events
[     9.567] (**) evdev: Video Bus: Device: "/dev/input/event5"
[     9.567] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     9.567] (--) evdev: Video Bus: Found keys
[     9.567] (II) evdev: Video Bus: Configuring as keyboard
[     9.567] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:43/LNXVIDEO:00/input/input7/event5"
[     9.567] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 10)
[     9.567] (**) Option "xkb_rules" "evdev"
[     9.567] (**) Option "xkb_model" "pc105"
[     9.567] (**) Option "xkb_layout" "us"
[     9.568] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[     9.568] (II) No input driver specified, ignoring this device.
[     9.568] (II) This device may have been added with another device file.
[     9.568] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event14)
[     9.568] (II) No input driver specified, ignoring this device.
[     9.568] (II) This device may have been added with another device file.
[     9.568] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event15)
[     9.568] (II) No input driver specified, ignoring this device.
[     9.568] (II) This device may have been added with another device file.
[     9.568] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event16)
[     9.568] (II) No input driver specified, ignoring this device.
[     9.568] (II) This device may have been added with another device file.
[     9.568] (II) config/udev: Adding input device Logitech Logitech USB Headset (/dev/input/event17)
[     9.568] (**) Logitech Logitech USB Headset: Applying InputClass "evdev keyboard catchall"
[     9.568] (II) Using input driver 'evdev' for 'Logitech Logitech USB Headset'
[     9.568] (**) Logitech Logitech USB Headset: always reports core events
[     9.568] (**) evdev: Logitech Logitech USB Headset: Device: "/dev/input/event17"
[     9.568] (--) evdev: Logitech Logitech USB Headset: Vendor 0x46d Product 0xa44
[     9.568] (--) evdev: Logitech Logitech USB Headset: Found keys
[     9.568] (II) evdev: Logitech Logitech USB Headset: Configuring as keyboard
[     9.568] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2.1/3-2.1.1/3-2.1.1:1.3/0003:046D:0A44.0003/input/input18/event17"
[     9.568] (II) XINPUT: Adding extended input device "Logitech Logitech USB Headset" (type: KEYBOARD, id 11)
[     9.568] (**) Option "xkb_rules" "evdev"
[     9.568] (**) Option "xkb_model" "pc105"
[     9.568] (**) Option "xkb_layout" "us"
[     9.569] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:4024 (/dev/input/event18)
[     9.569] (**) Logitech Unifying Device. Wireless PID:4024: Applying InputClass "evdev pointer catchall"
[     9.569] (**) Logitech Unifying Device. Wireless PID:4024: Applying InputClass "evdev keyboard catchall"
[     9.569] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:4024'
[     9.569] (**) Logitech Unifying Device. Wireless PID:4024: always reports core events
[     9.569] (**) evdev: Logitech Unifying Device. Wireless PID:4024: Device: "/dev/input/event18"
[     9.569] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Vendor 0x46d Product 0xc52b
[     9.569] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found 20 mouse buttons
[     9.569] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found scroll wheel(s)
[     9.569] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found relative axes
[     9.569] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found x and y relative axes
[     9.569] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found absolute axes
[     9.569] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Forcing absolute x/y axes to exist.
[     9.569] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found keys
[     9.569] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Configuring as mouse
[     9.569] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Configuring as keyboard
[     9.569] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Adding scrollwheel support
[     9.569] (**) evdev: Logitech Unifying Device. Wireless PID:4024: YAxisMapping: buttons 4 and 5
[     9.569] (**) evdev: Logitech Unifying Device. Wireless PID:4024: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     9.569] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2.1/3-2.1.2/3-2.1.2:1.2/0003:046D:C52B.0006/0003:046D:C52B.0007/input/input19/event18"
[     9.569] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:4024" (type: KEYBOARD, id 12)
[     9.569] (**) Option "xkb_rules" "evdev"
[     9.569] (**) Option "xkb_model" "pc105"
[     9.569] (**) Option "xkb_layout" "us"
[     9.569] (II) evdev: Logitech Unifying Device. Wireless PID:4024: initialized for relative axes.
[     9.569] (WW) evdev: Logitech Unifying Device. Wireless PID:4024: ignoring absolute axes.
[     9.569] (**) Logitech Unifying Device. Wireless PID:4024: (accel) keeping acceleration scheme 1
[     9.569] (**) Logitech Unifying Device. Wireless PID:4024: (accel) acceleration profile 0
[     9.569] (**) Logitech Unifying Device. Wireless PID:4024: (accel) acceleration factor: 2.000
[     9.569] (**) Logitech Unifying Device. Wireless PID:4024: (accel) acceleration threshold: 4
[     9.569] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:4024 (/dev/input/mouse2)
[     9.569] (II) No input driver specified, ignoring this device.
[     9.569] (II) This device may have been added with another device file.
[     9.570] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:4024 (/dev/input/event19)
[     9.570] (**) Logitech Unifying Device. Wireless PID:4024: Applying InputClass "evdev pointer catchall"
[     9.570] (**) Logitech Unifying Device. Wireless PID:4024: Applying InputClass "evdev keyboard catchall"
[     9.570] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:4024'
[     9.570] (**) Logitech Unifying Device. Wireless PID:4024: always reports core events
[     9.570] (**) evdev: Logitech Unifying Device. Wireless PID:4024: Device: "/dev/input/event19"
[     9.570] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Vendor 0x46d Product 0xc52b
[     9.570] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found 20 mouse buttons
[     9.570] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found scroll wheel(s)
[     9.570] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found relative axes
[     9.570] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found x and y relative axes
[     9.570] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found absolute axes
[     9.570] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Forcing absolute x/y axes to exist.
[     9.570] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found keys
[     9.570] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Configuring as mouse
[     9.570] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Configuring as keyboard
[     9.570] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Adding scrollwheel support
[     9.570] (**) evdev: Logitech Unifying Device. Wireless PID:4024: YAxisMapping: buttons 4 and 5
[     9.570] (**) evdev: Logitech Unifying Device. Wireless PID:4024: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     9.570] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2.1/3-2.1.2/3-2.1.2:1.2/0003:046D:C52B.0006/0003:046D:C52B.0008/input/input20/event19"
[     9.570] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:4024" (type: KEYBOARD, id 13)
[     9.570] (**) Option "xkb_rules" "evdev"
[     9.570] (**) Option "xkb_model" "pc105"
[     9.570] (**) Option "xkb_layout" "us"
[     9.570] (II) evdev: Logitech Unifying Device. Wireless PID:4024: initialized for relative axes.
[     9.570] (WW) evdev: Logitech Unifying Device. Wireless PID:4024: ignoring absolute axes.
[     9.570] (**) Logitech Unifying Device. Wireless PID:4024: (accel) keeping acceleration scheme 1
[     9.570] (**) Logitech Unifying Device. Wireless PID:4024: (accel) acceleration profile 0
[     9.570] (**) Logitech Unifying Device. Wireless PID:4024: (accel) acceleration factor: 2.000
[     9.570] (**) Logitech Unifying Device. Wireless PID:4024: (accel) acceleration threshold: 4
[     9.570] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:4024 (/dev/input/mouse3)
[     9.570] (II) No input driver specified, ignoring this device.
[     9.570] (II) This device may have been added with another device file.
[     9.570] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event9)
[     9.570] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[     9.570] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[     9.570] (**) Logitech USB Receiver: always reports core events
[     9.570] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event9"
[     9.570] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc51a
[     9.570] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[     9.570] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[     9.570] (--) evdev: Logitech USB Receiver: Found relative axes
[     9.570] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[     9.570] (II) evdev: Logitech USB Receiver: Configuring as mouse
[     9.570] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[     9.570] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[     9.570] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     9.570] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2.4/3-2.4:1.0/0003:046D:C51A.0001/input/input10/event9"
[     9.570] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 14)
[     9.570] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[     9.571] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[     9.571] (**) Logitech USB Receiver: (accel) acceleration profile 0
[     9.571] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[     9.571] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[     9.571] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[     9.571] (II) No input driver specified, ignoring this device.
[     9.571] (II) This device may have been added with another device file.
[     9.571] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event10)
[     9.571] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[     9.571] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[     9.571] (**) Logitech USB Receiver: always reports core events
[     9.571] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event10"
[     9.571] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc51a
[     9.571] (--) evdev: Logitech USB Receiver: Found 1 mouse buttons
[     9.571] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[     9.571] (--) evdev: Logitech USB Receiver: Found relative axes
[     9.571] (II) evdev: Logitech USB Receiver: Forcing relative x/y axes to exist.
[     9.571] (--) evdev: Logitech USB Receiver: Found absolute axes
[     9.571] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[     9.571] (--) evdev: Logitech USB Receiver: Found keys
[     9.571] (II) evdev: Logitech USB Receiver: Configuring as mouse
[     9.571] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[     9.571] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[     9.571] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[     9.571] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     9.571] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2.4/3-2.4:1.1/0003:046D:C51A.0002/input/input11/event10"
[     9.571] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 15)
[     9.571] (**) Option "xkb_rules" "evdev"
[     9.571] (**) Option "xkb_model" "pc105"
[     9.571] (**) Option "xkb_layout" "us"
[     9.571] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[     9.571] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[     9.571] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[     9.571] (**) Logitech USB Receiver: (accel) acceleration profile 0
[     9.571] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[     9.571] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[     9.571] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event13)
[     9.571] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[     9.571] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[     9.571] (**) Lenovo EasyCamera: always reports core events
[     9.571] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event13"
[     9.571] (--) evdev: Lenovo EasyCamera: Vendor 0x5986 Product 0x55e
[     9.571] (--) evdev: Lenovo EasyCamera: Found keys
[     9.571] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[     9.571] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0/input/input14/event13"
[     9.571] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 16)
[     9.571] (**) Option "xkb_rules" "evdev"
[     9.571] (**) Option "xkb_model" "pc105"
[     9.572] (**) Option "xkb_layout" "us"
[     9.572] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event11)
[     9.572] (II) No input driver specified, ignoring this device.
[     9.572] (II) This device may have been added with another device file.
[     9.572] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event12)
[     9.572] (II) No input driver specified, ignoring this device.
[     9.572] (II) This device may have been added with another device file.
[     9.572] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event8)
[     9.572] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[     9.572] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[     9.572] (**) Ideapad extra buttons: always reports core events
[     9.572] (**) evdev: Ideapad extra buttons: Device: "/dev/input/event8"
[     9.572] (--) evdev: Ideapad extra buttons: Vendor 0 Product 0
[     9.572] (--) evdev: Ideapad extra buttons: Found keys
[     9.572] (II) evdev: Ideapad extra buttons: Configuring as keyboard
[     9.572] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input9/event8"
[     9.572] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 17)
[     9.572] (**) Option "xkb_rules" "evdev"
[     9.572] (**) Option "xkb_model" "pc105"
[     9.572] (**) Option "xkb_layout" "us"
[     9.572] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[     9.572] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     9.572] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     9.572] (**) AT Translated Set 2 keyboard: always reports core events
[     9.572] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[     9.572] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     9.572] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     9.572] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     9.572] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[     9.572] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 18)
[     9.572] (**) Option "xkb_rules" "evdev"
[     9.572] (**) Option "xkb_model" "pc105"
[     9.572] (**) Option "xkb_layout" "us"
[     9.573] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[     9.573] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     9.573] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     9.573] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     9.573] (II) LoadModule: "synaptics"
[     9.573] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     9.573] (II) Module synaptics: vendor="X.Org Foundation"
[     9.573]    compiled for 1.16.0, module version = 1.8.99
[     9.573]    Module class: X.Org XInput Driver
[     9.573]    ABI class: X.Org XInput driver, version 21.0
[     9.573] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     9.573] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     9.573] (**) Option "Device" "/dev/input/event7"
[     9.620] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[     9.620] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5664 (res 42)
[     9.620] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4678 (res 51)
[     9.620] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     9.620] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     9.620] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[     9.620] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     9.620] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[     9.620] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     9.620] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     9.676] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event7"
[     9.676] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 19)
[     9.676] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     9.676] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     9.676] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[     9.676] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     9.676] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     9.676] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     9.676] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     9.676] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     9.676] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[     9.676] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    10.250] (II) intel(0): EDID vendor "SDC", prod id 18514
[    10.250] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    10.250] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    10.250] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    10.250] (II) intel(0): Printing DDC gathered Modelines:
[    10.250] (II) intel(0): Modeline "3840x2160"x0.0  421.55  3840 3888 3920 3956  2160 2162 2167 2220 -hsync -vsync (106.6 kHz eP)
[    10.344] (II) intel(0): resizing framebuffer to 5760x2160
[    10.376] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 0, position (3840, 0), rotation normal, reflection none
[    10.646] (II) intel(0): switch to mode 3840x2160@48.0 on eDP1 using pipe 1, position (0, 0), rotation normal, reflection none
[    12.133] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    13.204] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    19.665] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.804] (II) intel(0): switch to mode 1920x1080@59.9 on HDMI1 using pipe 1, position (3840, 0), rotation normal, reflection none
[    20.090] (II) intel(0): switch to mode 3840x2160@48.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    21.339] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    23.094] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm



```


Verify lshw not so good, same as before I started on here.

```
 &#10140; sudo lshw -C display                                                      ~   *-display UNCLAIMED     
       description: 3D controller
       product: GM107M [GeForce GTX 860M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:d0000000-d0ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:b2000000-b207ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:d1000000-d13fffff memory:c0000000-cfffffff ioport:5000(size=64)



```


I love working in Linux on a daily basis, but little things like this make me contemplate self harm.

---

### Post by Bashing-om on 2015-03-06
JDAIII; Whewh .. back to work.

OK; alarm condition 14 called off.. mysql alive and well.

This from the output::
> 
Building only for 3.16.0-31-generic

WHY such an old kernel ?
Not updated system ? What do we have installed for kernels ?
```

dpkg -l | grep linux-
ls -al /boot

```

In the meantime, I be reading the Xorg log file see if I can make out the why a driver for Nvidia does not install !

[INDENT][INDENT]gotta be a cause
[INDENT][INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-06
So this is where you get frustrated. I just started using Linux in general in September of 2014. My boss said that we needed a linux expert and I've been teaching myself. I got one of those silly certifications (which our annual raises are based on) and I have to get 2-3 more this year.

In short, I've never upgraded my kernel and I will research now, but weary of upgrading something that can break everything on my machine.


```
 &#10140; dpkg -l | grep linux-                                                     ~ ii  linux-firmware                              1.138.1                                                all          Firmware for Linux kernel drivers
ii  linux-generic                               3.16.0.31.32                                           amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.16.0-29                     3.16.0-29.39                                           all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-29-generic             3.16.0-29.39                                           amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-30                     3.16.0-30.40                                           all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-30-generic             3.16.0-30.40                                           amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-31                     3.16.0-31.41                                           all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-31-generic             3.16.0-31.41                                           amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-generic                       3.16.0.31.32                                           amd64        Generic Linux kernel headers
ii  linux-image-3.16.0-29-generic               3.16.0-29.39                                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-30-generic               3.16.0-30.40                                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-31-generic               3.16.0-31.41                                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-29-generic         3.16.0-29.39                                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-30-generic         3.16.0-30.40                                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-31-generic         3.16.0-31.41                                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-generic                         3.16.0.31.32                                           amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                        3.16.0-31.41                                           amd64        Linux Kernel Headers for development
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu4                                   all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:6.03~pre18+dfsg-1ubuntu1                             all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu5                                   amd64        Bootloader for Linux/i386 using MS-DOS floppies
 &#10140; ls -al /boot                                                              ~ 
total 118876
drwxr-xr-x  3 root root     4096 Mar  6 14:09 .
drwxr-xr-x 24 root root     4096 Mar  6 14:01 ..
-rw-r--r--  1 root root  1207195 Dec 15 15:27 abi-3.16.0-29-generic
-rw-r--r--  1 root root  1207386 Jan 12 15:06 abi-3.16.0-30-generic
-rw-r--r--  1 root root  1207327 Feb 10 08:25 abi-3.16.0-31-generic
-rw-r--r--  1 root root   171760 Dec 15 15:27 config-3.16.0-29-generic
-rw-r--r--  1 root root   171760 Jan 12 15:06 config-3.16.0-30-generic
-rw-r--r--  1 root root   171794 Feb 10 08:25 config-3.16.0-31-generic
drwxr-xr-x  5 root root     4096 Mar  6 14:09 grub
-rw-r--r--  1 root root 29090352 Jan 29 13:35 initrd.img-3.16.0-29-generic
-rw-r--r--  1 root root 29094265 Feb 12 14:11 initrd.img-3.16.0-30-generic
-rw-r--r--  1 root root 29101786 Mar  6 14:09 initrd.img-3.16.0-31-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3500984 Dec 15 15:27 System.map-3.16.0-29-generic
-rw-------  1 root root  3501168 Jan 12 15:06 System.map-3.16.0-30-generic
-rw-------  1 root root  3501573 Feb 10 08:25 System.map-3.16.0-31-generic
-rw-------  1 root root  6408320 Dec 15 15:27 vmlinuz-3.16.0-29-generic
-rw-------  1 root root  6409808 Jan 12 15:06 vmlinuz-3.16.0-30-generic
-rw-------  1 root root  6410624 Feb 10 08:25 vmlinuz-3.16.0-31-generic



```

---

### Post by JDAIII on 2015-03-06
Update:

So I think that I have successfully upgraded to 3.18.3 kernel. I rebooted nad not dead.

```
 &#10140; dpkg -l | grep linux-                                                     ~ ii  linux-firmware                              1.138.1                                                all          Firmware for Linux kernel drivers
ii  linux-generic                               3.16.0.31.32                                           amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.16.0-29                     3.16.0-29.39                                           all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-29-generic             3.16.0-29.39                                           amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-30                     3.16.0-30.40                                           all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-30-generic             3.16.0-30.40                                           amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-31                     3.16.0-31.41                                           all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-31-generic             3.16.0-31.41                                           amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.18.3-031803                 3.18.3-031803.201501161810                             all          Header files related to Linux kernel version 3.18.3
ii  linux-headers-3.18.3-031803-generic         3.18.3-031803.201501161810                             amd64        Linux kernel headers for version 3.18.3 on 64 bit x86 SMP
ii  linux-headers-generic                       3.16.0.31.32                                           amd64        Generic Linux kernel headers
ii  linux-image-3.16.0-29-generic               3.16.0-29.39                                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-30-generic               3.16.0-30.40                                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-31-generic               3.16.0-31.41                                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.18.3-031803-generic           3.18.3-031803.201501161810                             amd64        Linux kernel image for version 3.18.3 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-29-generic         3.16.0-29.39                                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-30-generic         3.16.0-30.40                                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-31-generic         3.16.0-31.41                                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-generic                         3.16.0.31.32                                           amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                        3.16.0-31.41                                           amd64        Linux Kernel Headers for development
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu4                                   all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:6.03~pre18+dfsg-1ubuntu1                             all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu5                                   amd64        Bootloader for Linux/i386 using MS-DOS floppies
 &#10140; ls -al /boot                                                              ~ 
total 158984
drwxr-xr-x  3 root root     4096 Mar  6 14:52 .
drwxr-xr-x 24 root root     4096 Mar  6 14:51 ..
-rw-r--r--  1 root root  1207195 Dec 15 15:27 abi-3.16.0-29-generic
-rw-r--r--  1 root root  1207386 Jan 12 15:06 abi-3.16.0-30-generic
-rw-r--r--  1 root root  1207327 Feb 10 08:25 abi-3.16.0-31-generic
-rw-r--r--  1 root root  1220925 Jan 16 10:23 abi-3.18.3-031803-generic
-rw-r--r--  1 root root   171760 Dec 15 15:27 config-3.16.0-29-generic
-rw-r--r--  1 root root   171760 Jan 12 15:06 config-3.16.0-30-generic
-rw-r--r--  1 root root   171794 Feb 10 08:25 config-3.16.0-31-generic
-rw-r--r--  1 root root   174713 Jan 16 10:23 config-3.18.3-031803-generic
drwxr-xr-x  5 root root     4096 Mar  6 14:52 grub
-rw-r--r--  1 root root 29090352 Jan 29 13:35 initrd.img-3.16.0-29-generic
-rw-r--r--  1 root root 29094265 Feb 12 14:11 initrd.img-3.16.0-30-generic
-rw-r--r--  1 root root 29101786 Mar  6 14:09 initrd.img-3.16.0-31-generic
-rw-r--r--  1 root root 29433883 Mar  6 14:52 initrd.img-3.18.3-031803-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  3500984 Dec 15 15:27 System.map-3.16.0-29-generic
-rw-------  1 root root  3501168 Jan 12 15:06 System.map-3.16.0-30-generic
-rw-------  1 root root  3501573 Feb 10 08:25 System.map-3.16.0-31-generic
-rw-------  1 root root  3700902 Jan 16 10:23 System.map-3.18.3-031803-generic
-rw-------  1 root root  6408320 Dec 15 15:27 vmlinuz-3.16.0-29-generic
-rw-------  1 root root  6409808 Jan 12 15:06 vmlinuz-3.16.0-30-generic
-rw-------  1 root root  6410624 Feb 10 08:25 vmlinuz-3.16.0-31-generic
-rw-------  1 root root  6528080 Jan 16 10:23 vmlinuz-3.18.3-031803-generic



```





Should I remove all of the 3.16 files since I upgraded to 3.18?

I'm afraid to since I see this, shouldn't it be using 3.18? 
[COLOR=#000000][FONT=Ubuntu Mono]ii  linux-image-generic                         3.16.0.31.32                                           amd64        Generic Linux kernel image[/FONT][/COLOR]

---

### Post by Bashing-om on 2015-03-06
JDAIII; Small things can

Make mountain out of mole hill.

Let me tell you my story, I have been messing with computers since before they were, and I have some small degree of experience with a number of operating systems. This one - In My humblest Opinion - is the best thing since sliced bread. The infra structure and support make it so.

Now as to this situation:
The nvidia card is seen:
> 
(--) PCI: (0:1:0:0) 10de:1392:17aa:3978 rev 162, Mem @ 0xd0000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288

 I do expect that the Nvidia graphics set to be the primary as it is 1st on the buss ( PCI: (0:1:0:0). But the driver is never built, there is no further mention of Nvidia in the log file, instead Intel is built and installed. HUH ??
So I have to ask is the Nvidia card enabled in bios ?
speaking of which, is this a bios based system or the newer UEFI ?

I am all for getting this system updated prior to attempting anything else. To do so run terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
(dist-upgrade DOES NOT release upgrade to the next release, it does install the new kernel - apt-get install WILL NOT install anything new)
I am concerned that the 3.18 kernel is not booted, let's see what results after updated and all and take another look at the kernel/booting issue. Maybe that is the hold on the driver building ? ?? 

Right now I am stumped as to why the Nvidia driver does not build. But together we will figure it out.

[INDENT][INDENT]it's buntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-06
ok, so I ran 

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

I am now having fun times. The first time that it rebooted, black screen except for 15 pixel artifacts on my laptop screen and after two more restarts, it works, but the HDMI external monitor is not being recognized by gnome3 or xrandr. And it looks like I'm still using the 3.16 kernel even though I selected 3.18.3 in the boot menu after first reboot.

```

 &#10140; dpkg -l | grep linux-                                                     ~ 
ii  linux-firmware                              1.138.1                                                all          Firmware for Linux kernel drivers
ii  linux-generic                               3.16.0.31.32                                           amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.16.0-29                     3.16.0-29.39                                           all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-29-generic             3.16.0-29.39                                           amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-30                     3.16.0-30.40                                           all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-30-generic             3.16.0-30.40                                           amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-31                     3.16.0-31.41                                           all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-31-generic             3.16.0-31.41                                           amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.18.3-031803                 3.18.3-031803.201501161810                             all          Header files related to Linux kernel version 3.18.3
ii  linux-headers-3.18.3-031803-generic         3.18.3-031803.201501161810                             amd64        Linux kernel headers for version 3.18.3 on 64 bit x86 SMP
ii  linux-headers-generic                       3.16.0.31.32                                           amd64        Generic Linux kernel headers
ii  linux-image-3.16.0-29-generic               3.16.0-29.39                                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-30-generic               3.16.0-30.40                                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-31-generic               3.16.0-31.41                                           amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.18.3-031803-generic           3.18.3-031803.201501161810                             amd64        Linux kernel image for version 3.18.3 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-29-generic         3.16.0-29.39                                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-30-generic         3.16.0-30.40                                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-31-generic         3.16.0-31.41                                           amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-generic                         3.16.0.31.32                                           amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                        3.16.0-31.41                                           amd64        Linux Kernel Headers for development
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu4                                   all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:6.03~pre18+dfsg-1ubuntu1                             all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu5                                   amd64        Bootloader for Linux/i386 using MS-DOS floppies

```


Rebooted so that I could check the BIOS settings, they were already set to switchable which is what we want. See pic attached.
Booted into Gnome and now my external monitor works.
Let's hope it's ok to add external links on here to images: [[IMG]http://i31.photobucket.com/albums/c355/cheshireccat/IMG_20150306_153747.jpg[/IMG]](http://s31.photobucket.com/user/cheshireccat/media/IMG_20150306_153747.jpg.html)

---

### Post by Bashing-om on 2015-03-06
JDAIII; OK ! (NOT)

Any errors reported in that update process ?
What we appear to have here is a kernel issue.
How did you install the 3.18 kernel ?

and show us the background:
what are we working with ?
```

lsb_release -a
cat /etc/issue
uname -a
ls -al /
hwe-support-status --verbose
ls -al /usr/bin/hwe-support-status

``` we see where we go from here .


[INDENT][INDENT]I betcha
[/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-06
The one time that I did not record the terminal output. dammit. So Here is the site that I used for the steps to upgrade the kernel. I used the 64bit steps:
[http://www.linux.com/community/blogs/133-general-linux/803937-installupgrade-linux-kernel-to-3183-stable-in-ubuntulinux-mintpeppermint](http://www.linux.com/community/blogs/133-general-linux/803937-installupgrade-linux-kernel-to-3183-stable-in-ubuntulinux-mintpeppermint)

As for the answers to your questions, here they are:

I can feel your brow furrowing on that last part of the code below.

```

 &#10140; lsb_release -a                                                            ~ 
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.10
Release:        14.10
Codename:       utopic
 &#10140; cat /etc/issue                                                            ~ 
Ubuntu 14.10 \n \l
 &#10140; ls -al /                                                                  ~ 
total 104
drwxr-xr-x  23 root root  4096 Mar  6 15:21 .
drwxr-xr-x  23 root root  4096 Mar  6 15:21 ..
drwxr-xr-x   2 root root  4096 Feb 27 11:21 bin
drwxr-xr-x   3 root root  4096 Mar  6 14:52 boot
drwxrwxr-x   2 root root  4096 Jan  6 19:46 cdrom
drwxr-xr-x  18 root root  4320 Mar  6 15:44 dev
drwxr-xr-x 155 root root 12288 Mar  6 15:38 etc
drwxr-xr-x   4 root root  4096 Jan  6 19:48 home
lrwxrwxrwx   1 root root    37 Mar  6 14:51 initrd.img -> boot/initrd.img-3.18.3-031803-generic
lrwxrwxrwx   1 root root    33 Mar  2 08:18 initrd.img.old -> boot/initrd.img-3.16.0-31-generic
drwxr-xr-x  28 root root  4096 Mar  6 15:21 lib
drwxr-xr-x   2 root root  4096 Mar  2 08:18 lib64
drwx------   2 root root 16384 Jan  6 19:42 lost+found
drwxr-xr-x  10 root root  4096 Jan 16 14:12 media
drwxr-xr-x   2 root root  4096 Apr 10  2014 mnt
drwxr-xr-x   9 root root  4096 Feb 27 14:29 opt
dr-xr-xr-x 287 root root     0 Mar  6 15:38 proc
drwx------  12 root root  4096 Mar  4 14:52 root
drwxr-xr-x  28 root root   900 Mar  6 15:38 run
drwxr-xr-x   2 root root 12288 Mar  6 15:21 sbin
drwxr-xr-x   2 root root  4096 Jul 22  2014 srv
dr-xr-xr-x  13 root root     0 Mar  6 15:51 sys
drwxrwxrwt  10 root root  4096 Mar  6 15:42 tmp
drwxr-xr-x  10 root root  4096 Mar  6 15:21 usr
drwxr-xr-x  13 root root  4096 Jul 22  2014 var
lrwxrwxrwx   1 root root    34 Mar  6 14:51 vmlinuz -> boot/vmlinuz-3.18.3-031803-generic
lrwxrwxrwx   1 root root    30 Mar  2 08:18 vmlinuz.old -> boot/vmlinuz-3.16.0-31-generic
 &#10140; hwe-support-status --verbose                                              ~ 
zsh: command not found: hwe-support-status
 &#10140; ls -al /usr/bin/hwe-support-status                                        ~ 
ls: cannot access /usr/bin/hwe-support-status: No such file or directory
 &#10140; uname -r                                                                  ~ 
3.18.3-031803-generic




```

Would it be a good idea to just uninstall 3.18.3 with the line below and just try upgrading with dist-upgrade? I'm not doing that without input so don't worry.
```
sudo apt-get remove 'linux-headers-3.18.3*' 'linux-image-3.18.3*' 
```

---

### Post by Bashing-om on 2015-03-06
JDAIII; Humm ..,,

Gimme some time to digest this, on the surface I see no fault .
> 
lrwxrwxrwx   1 root root    37 Mar  6 14:51 initrd.img -> boot/initrd.img-3.18.3-031803-generic

says you are in fact booting the 3.18 kernel as is confirmed:
> 
 &#10140; uname -r                                                                  ~ 
3.18.3-031803-generic

so begs the question why from that old Xorg file :
> 
[     9.507] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-31-generic root=UUID=9ba789c0-7d71-4b8e-b093-51d9db78b777 ro quiet splash

bk

Building only for 3.16.0-31-generic

bk bk

update-initramfs: Generating /boot/initrd.img-3.16.0-31-generic


Why is not the 3.18 kernel seen and picked up ???
---------------
And no, to soon to remove that 3.18 kernel. My concern is that it might cause more harm .
Out of curiousity what does result booting the 3.16.0-31 kernel ? Is switchable graphics workable there by some chance ?

OH; That "hwe-support-status " stuff was just to see where the 3.18 kernel did not come from. Was not surprised either way. Just wanted to be sure.

More questions than answers, and presently I do not know how to proceed -> doing homework !

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-06
No rush here, I've had this issue for a few months. Now that I'm actually doing something about it, I have no problem waiting for a reply. I have removed anything with nvidia after my latest attempt.

so I checked xorg again and now is says 3.18

```
 &#10140; cat /var/log/Xorg.0.log                                                   ~ [    16.860] 
X.Org X Server 1.16.1.901 (1.16.2 RC 1)
Release Date: 2014-11-02
[    16.860] X Protocol Version 11, Revision 0
[    16.860] Build Operating System: Linux 3.13.0-39-generic x86_64 Ubuntu
[    16.860] Current Operating System: Linux jd-laptop 3.18.3-031803-generic #201501161810 SMP Fri Jan 16 18:12:22 UTC 2015 x86_64
[    16.860] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.18.3-031803-generic root=UUID=9ba789c0-7d71-4b8e-b093-51d9db78b777 ro quiet splash vt.handoff=7
[    16.860] Build Date: 20 November 2014  09:55:19PM
[    16.860] xorg-server 2:1.16.1.901-1ubuntu1~utopic1 (For technical support please see http://www.ubuntu.com/support) 
[    16.860] Current version of pixman: 0.32.4
[    16.860]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    16.860] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.860] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  6 16:50:16 2015
[    16.861] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.862] (==) No Layout section.  Using the first Screen section.
[    16.862] (==) No screen section available. Using defaults.
[    16.862] (**) |-->Screen "Default Screen Section" (0)
[    16.862] (**) |   |-->Monitor "<default monitor>"
[    16.863] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    16.863] (==) Automatically adding devices
[    16.863] (==) Automatically enabling devices
[    16.863] (==) Automatically adding GPU devices
[    16.874] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.874]    Entry deleted from font path.
[    16.874] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.874]    Entry deleted from font path.
[    16.874] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.874]    Entry deleted from font path.
[    16.874] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.874]    Entry deleted from font path.
[    16.874] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.874]    Entry deleted from font path.
[    16.874] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    16.874] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.874] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.874] (II) Loader magic: 0x7fde0d845d80
[    16.874] (II) Module ABI versions:
[    16.874]    X.Org ANSI C Emulation: 0.4
[    16.874]    X.Org Video Driver: 18.0
[    16.874]    X.Org XInput driver : 21.0
[    16.874]    X.Org Server Extension : 8.0
[    16.875] (II) xfree86: Adding drm device (/dev/dri/card0)
[    16.876] (--) PCI:*(0:0:2:0) 8086:0416:17aa:3978 rev 6, Mem @ 0xd1000000/4194304, 0xc0000000/268435456, I/O @ 0x00005000/64
[    16.876] (--) PCI: (0:1:0:0) 10de:1392:17aa:3978 rev 162, Mem @ 0xd0000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[    16.876] (II) LoadModule: "glx"
[    16.877] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.884] (II) Module glx: vendor="X.Org Foundation"
[    16.884]    compiled for 1.16.1.901, module version = 1.0.0
[    16.884]    ABI class: X.Org Server Extension, version 8.0
[    16.884] (==) AIGLX enabled
[    16.885] (==) Matched intel as autoconfigured driver 0
[    16.885] (==) Matched intel as autoconfigured driver 1
[    16.885] (==) Matched modesetting as autoconfigured driver 2
[    16.885] (==) Matched fbdev as autoconfigured driver 3
[    16.885] (==) Matched vesa as autoconfigured driver 4
[    16.885] (==) Assigned the driver to the xf86ConfigLayout
[    16.885] (II) LoadModule: "intel"
[    16.886] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    16.888] (II) Module intel: vendor="X.Org Foundation"
[    16.889]    compiled for 1.16.1.901, module version = 2.99.917
[    16.889]    Module class: X.Org Video Driver
[    16.889]    ABI class: X.Org Video Driver, version 18.0
[    16.889] (II) LoadModule: "modesetting"
[    16.889] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    16.889] (II) Module modesetting: vendor="X.Org Foundation"
[    16.889]    compiled for 1.16.0, module version = 0.9.0
[    16.889]    Module class: X.Org Video Driver
[    16.889]    ABI class: X.Org Video Driver, version 18.0
[    16.889] (II) LoadModule: "fbdev"
[    16.890] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.890] (II) Module fbdev: vendor="X.Org Foundation"
[    16.890]    compiled for 1.16.0, module version = 0.4.4
[    16.890]    Module class: X.Org Video Driver
[    16.890]    ABI class: X.Org Video Driver, version 18.0
[    16.890] (II) LoadModule: "vesa"
[    16.890] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.891] (II) Module vesa: vendor="X.Org Foundation"
[    16.891]    compiled for 1.16.0, module version = 2.3.3
[    16.891]    Module class: X.Org Video Driver
[    16.891]    ABI class: X.Org Video Driver, version 18.0
[    16.891] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    16.891] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    16.891] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    16.891] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    16.891] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    16.891] (II) FBDEV: driver for framebuffer: fbdev
[    16.891] (II) VESA: driver for VESA chipsets: vesa
[    16.891] (++) using VT number 7
[    16.892] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20140905
[    16.892] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150304.88e61542-0ubuntu0sarvatt~utopic (Robert Hooker <sarvatt@ubuntu.com>)
[    16.892] (II) intel(0): SNA compiled for use with valgrind
[    16.893] (WW) Falling back to old probe method for modesetting
[    16.893] (WW) Falling back to old probe method for fbdev
[    16.893] (II) Loading sub module "fbdevhw"
[    16.893] (II) LoadModule: "fbdevhw"
[    16.893] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.893] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.893]    compiled for 1.16.1.901, module version = 0.0.2
[    16.893]    ABI class: X.Org Video Driver, version 18.0
[    16.893] (WW) Falling back to old probe method for vesa
[    16.894] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    16.894] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[    16.894] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    16.894] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    16.894] (==) intel(0): RGB weight 888
[    16.894] (==) intel(0): Default visual is TrueColor
[    16.894] (II) intel(0): Output eDP1 has no monitor section
[    16.894] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[    16.894] (II) intel(0): Enabled output eDP1
[    16.894] (II) intel(0): Output VGA1 has no monitor section
[    16.894] (II) intel(0): Enabled output VGA1
[    16.894] (II) intel(0): Output HDMI1 has no monitor section
[    16.894] (II) intel(0): Enabled output HDMI1
[    16.894] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    16.895] (II) intel(0): Output VIRTUAL1 has no monitor section
[    16.895] (II) intel(0): Enabled output VIRTUAL1
[    16.895] (--) intel(0): Output eDP1 using initial mode 3840x2160 on pipe 0
[    16.895] (--) intel(0): Output HDMI1 using initial mode 1920x1080 on pipe 1
[    16.895] (==) intel(0): TearFree disabled
[    16.895] (==) intel(0): DPI set to (96, 96)
[    16.895] (II) Loading sub module "dri2"
[    16.895] (II) LoadModule: "dri2"
[    16.895] (II) Module "dri2" already built-in
[    16.895] (II) Loading sub module "present"
[    16.895] (II) LoadModule: "present"
[    16.895] (II) Module "present" already built-in
[    16.895] (II) UnloadModule: "modesetting"
[    16.895] (II) Unloading modesetting
[    16.895] (II) UnloadModule: "fbdev"
[    16.895] (II) Unloading fbdev
[    16.895] (II) UnloadSubModule: "fbdevhw"
[    16.895] (II) Unloading fbdevhw
[    16.895] (II) UnloadModule: "vesa"
[    16.895] (II) Unloading vesa
[    16.895] (==) Depth 24 pixmap format is 32 bpp
[    16.898] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    16.898] (==) intel(0): Backing store enabled
[    16.898] (==) intel(0): Silken mouse enabled
[    16.898] (II) intel(0): HW Cursor enabled
[    16.899] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    16.899] (==) intel(0): DPMS enabled
[    16.899] (==) intel(0): Display hotplug detection enabled
[    16.899] (II) intel(0): [DRI2] Setup complete
[    16.899] (II) intel(0): [DRI2]   DRI driver: i965
[    16.899] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    16.899] (II) intel(0): direct rendering: DRI2 enabled
[    16.899] (II) intel(0): hardware support for Present enabled
[    16.899] (--) RandR disabled
[    16.904] (II) SELinux: Disabled on system
[    16.936] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    16.936] (II) AIGLX: enabled GLX_ARB_create_context
[    16.936] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    16.936] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    16.936] (II) AIGLX: enabled GLX_INTEL_swap_event
[    16.936] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    16.936] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    16.936] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    16.936] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    16.936] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    16.936] (II) AIGLX: Loaded and initialized i965
[    16.936] (II) GLX: Initialized DRI2 GL provider for screen 0
[    16.947] (II) intel(0): switch to mode 3840x2160@48.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    16.947] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 1, position (0, 0), rotation normal, reflection none
[    16.947] (II) intel(0): Setting screen physical size to 1016 x 571
[    16.958] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.960] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    16.960] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.960] (II) LoadModule: "evdev"
[    16.960] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.962] (II) Module evdev: vendor="X.Org Foundation"
[    16.962]    compiled for 1.16.0, module version = 2.9.0
[    16.962]    Module class: X.Org XInput Driver
[    16.962]    ABI class: X.Org XInput driver, version 21.0
[    16.962] (II) Using input driver 'evdev' for 'Power Button'
[    16.962] (**) Power Button: always reports core events
[    16.962] (**) evdev: Power Button: Device: "/dev/input/event3"
[    16.962] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.962] (--) evdev: Power Button: Found keys
[    16.962] (II) evdev: Power Button: Configuring as keyboard
[    16.962] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    16.962] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    16.962] (**) Option "xkb_rules" "evdev"
[    16.962] (**) Option "xkb_model" "pc105"
[    16.962] (**) Option "xkb_layout" "us"
[    16.962] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    16.962] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.962] (II) Using input driver 'evdev' for 'Video Bus'
[    16.962] (**) Video Bus: always reports core events
[    16.962] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    16.962] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    16.963] (--) evdev: Video Bus: Found keys
[    16.963] (II) evdev: Video Bus: Configuring as keyboard
[    16.963] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8/event6"
[    16.963] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    16.963] (**) Option "xkb_rules" "evdev"
[    16.963] (**) Option "xkb_model" "pc105"
[    16.963] (**) Option "xkb_layout" "us"
[    16.963] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.963] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.963] (II) Using input driver 'evdev' for 'Power Button'
[    16.963] (**) Power Button: always reports core events
[    16.963] (**) evdev: Power Button: Device: "/dev/input/event0"
[    16.963] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.963] (--) evdev: Power Button: Found keys
[    16.963] (II) evdev: Power Button: Configuring as keyboard
[    16.963] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    16.963] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    16.963] (**) Option "xkb_rules" "evdev"
[    16.963] (**) Option "xkb_model" "pc105"
[    16.963] (**) Option "xkb_layout" "us"
[    16.963] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    16.963] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    16.963] (II) Using input driver 'evdev' for 'Sleep Button'
[    16.963] (**) Sleep Button: always reports core events
[    16.963] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    16.963] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    16.963] (--) evdev: Sleep Button: Found keys
[    16.963] (II) evdev: Sleep Button: Configuring as keyboard
[    16.963] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input1/event1"
[    16.963] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    16.963] (**) Option "xkb_rules" "evdev"
[    16.963] (**) Option "xkb_model" "pc105"
[    16.964] (**) Option "xkb_layout" "us"
[    16.964] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    16.964] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.964] (II) Using input driver 'evdev' for 'Video Bus'
[    16.964] (**) Video Bus: always reports core events
[    16.964] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    16.964] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    16.964] (--) evdev: Video Bus: Found keys
[    16.964] (II) evdev: Video Bus: Configuring as keyboard
[    16.964] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:43/LNXVIDEO:00/input/input7/event5"
[    16.964] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 10)
[    16.964] (**) Option "xkb_rules" "evdev"
[    16.964] (**) Option "xkb_model" "pc105"
[    16.964] (**) Option "xkb_layout" "us"
[    16.964] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    16.964] (II) No input driver specified, ignoring this device.
[    16.964] (II) This device may have been added with another device file.
[    16.964] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event15)
[    16.964] (II) No input driver specified, ignoring this device.
[    16.964] (II) This device may have been added with another device file.
[    16.965] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event16)
[    16.965] (II) No input driver specified, ignoring this device.
[    16.965] (II) This device may have been added with another device file.
[    16.965] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event17)
[    16.965] (II) No input driver specified, ignoring this device.
[    16.965] (II) This device may have been added with another device file.
[    16.965] (II) config/udev: Adding input device Logitech Logitech USB Headset (/dev/input/event10)
[    16.965] (**) Logitech Logitech USB Headset: Applying InputClass "evdev keyboard catchall"
[    16.965] (II) Using input driver 'evdev' for 'Logitech Logitech USB Headset'
[    16.965] (**) Logitech Logitech USB Headset: always reports core events
[    16.965] (**) evdev: Logitech Logitech USB Headset: Device: "/dev/input/event10"
[    16.965] (--) evdev: Logitech Logitech USB Headset: Vendor 0x46d Product 0xa44
[    16.965] (--) evdev: Logitech Logitech USB Headset: Found keys
[    16.965] (II) evdev: Logitech Logitech USB Headset: Configuring as keyboard
[    16.965] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.1/1-2.1.1/1-2.1.1:1.3/0003:046D:0A44.0003/input/input11/event10"
[    16.965] (II) XINPUT: Adding extended input device "Logitech Logitech USB Headset" (type: KEYBOARD, id 11)
[    16.965] (**) Option "xkb_rules" "evdev"
[    16.965] (**) Option "xkb_model" "pc105"
[    16.965] (**) Option "xkb_layout" "us"
[    16.965] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:4024 (/dev/input/event11)
[    16.965] (**) Logitech Unifying Device. Wireless PID:4024: Applying InputClass "evdev pointer catchall"
[    16.965] (**) Logitech Unifying Device. Wireless PID:4024: Applying InputClass "evdev keyboard catchall"
[    16.965] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:4024'
[    16.965] (**) Logitech Unifying Device. Wireless PID:4024: always reports core events
[    16.965] (**) evdev: Logitech Unifying Device. Wireless PID:4024: Device: "/dev/input/event11"
[    16.965] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Vendor 0x46d Product 0xc52b
[    16.965] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found 20 mouse buttons
[    16.965] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found scroll wheel(s)
[    16.965] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found relative axes
[    16.965] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found x and y relative axes
[    16.965] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found absolute axes
[    16.965] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Forcing absolute x/y axes to exist.
[    16.966] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found keys
[    16.966] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Configuring as mouse
[    16.966] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Configuring as keyboard
[    16.966] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Adding scrollwheel support
[    16.966] (**) evdev: Logitech Unifying Device. Wireless PID:4024: YAxisMapping: buttons 4 and 5
[    16.966] (**) evdev: Logitech Unifying Device. Wireless PID:4024: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.966] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.1/1-2.1.2/1-2.1.2:1.2/0003:046D:C52B.0006/0003:046D:C52B.0007/input/input12/event11"
[    16.966] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:4024" (type: KEYBOARD, id 12)
[    16.966] (**) Option "xkb_rules" "evdev"
[    16.966] (**) Option "xkb_model" "pc105"
[    16.966] (**) Option "xkb_layout" "us"
[    16.966] (II) evdev: Logitech Unifying Device. Wireless PID:4024: initialized for relative axes.
[    16.966] (WW) evdev: Logitech Unifying Device. Wireless PID:4024: ignoring absolute axes.
[    16.966] (**) Logitech Unifying Device. Wireless PID:4024: (accel) keeping acceleration scheme 1
[    16.966] (**) Logitech Unifying Device. Wireless PID:4024: (accel) acceleration profile 0
[    16.966] (**) Logitech Unifying Device. Wireless PID:4024: (accel) acceleration factor: 2.000
[    16.966] (**) Logitech Unifying Device. Wireless PID:4024: (accel) acceleration threshold: 4
[    16.966] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:4024 (/dev/input/mouse2)
[    16.966] (II) No input driver specified, ignoring this device.
[    16.966] (II) This device may have been added with another device file.
[    16.966] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:4024 (/dev/input/event12)
[    16.966] (**) Logitech Unifying Device. Wireless PID:4024: Applying InputClass "evdev pointer catchall"
[    16.966] (**) Logitech Unifying Device. Wireless PID:4024: Applying InputClass "evdev keyboard catchall"
[    16.966] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:4024'
[    16.966] (**) Logitech Unifying Device. Wireless PID:4024: always reports core events
[    16.966] (**) evdev: Logitech Unifying Device. Wireless PID:4024: Device: "/dev/input/event12"
[    16.966] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Vendor 0x46d Product 0xc52b
[    16.966] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found 20 mouse buttons
[    16.966] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found scroll wheel(s)
[    16.966] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found relative axes
[    16.966] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found x and y relative axes
[    16.966] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found absolute axes
[    16.966] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Forcing absolute x/y axes to exist.
[    16.966] (--) evdev: Logitech Unifying Device. Wireless PID:4024: Found keys
[    16.966] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Configuring as mouse
[    16.966] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Configuring as keyboard
[    16.966] (II) evdev: Logitech Unifying Device. Wireless PID:4024: Adding scrollwheel support
[    16.966] (**) evdev: Logitech Unifying Device. Wireless PID:4024: YAxisMapping: buttons 4 and 5
[    16.966] (**) evdev: Logitech Unifying Device. Wireless PID:4024: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.966] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.1/1-2.1.2/1-2.1.2:1.2/0003:046D:C52B.0006/0003:046D:C52B.0008/input/input13/event12"
[    16.966] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:4024" (type: KEYBOARD, id 13)
[    16.966] (**) Option "xkb_rules" "evdev"
[    16.966] (**) Option "xkb_model" "pc105"
[    16.966] (**) Option "xkb_layout" "us"
[    16.967] (II) evdev: Logitech Unifying Device. Wireless PID:4024: initialized for relative axes.
[    16.967] (WW) evdev: Logitech Unifying Device. Wireless PID:4024: ignoring absolute axes.
[    16.967] (**) Logitech Unifying Device. Wireless PID:4024: (accel) keeping acceleration scheme 1
[    16.967] (**) Logitech Unifying Device. Wireless PID:4024: (accel) acceleration profile 0
[    16.967] (**) Logitech Unifying Device. Wireless PID:4024: (accel) acceleration factor: 2.000
[    16.967] (**) Logitech Unifying Device. Wireless PID:4024: (accel) acceleration threshold: 4
[    16.967] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:4024 (/dev/input/mouse3)
[    16.967] (II) No input driver specified, ignoring this device.
[    16.967] (II) This device may have been added with another device file.
[    16.967] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event8)
[    16.967] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    16.967] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    16.967] (**) Logitech USB Receiver: always reports core events
[    16.967] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event8"
[    16.967] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc51a
[    16.967] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[    16.967] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    16.967] (--) evdev: Logitech USB Receiver: Found relative axes
[    16.967] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    16.967] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    16.967] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    16.967] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    16.967] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.967] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.4/1-2.4:1.0/0003:046D:C51A.0001/input/input9/event8"
[    16.967] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 14)
[    16.967] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    16.967] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    16.967] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    16.967] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    16.967] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    16.967] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[    16.967] (II) No input driver specified, ignoring this device.
[    16.967] (II) This device may have been added with another device file.
[    16.968] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event9)
[    16.968] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    16.968] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    16.968] (**) Logitech USB Receiver: always reports core events
[    16.968] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event9"
[    16.968] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc51a
[    16.968] (--) evdev: Logitech USB Receiver: Found 1 mouse buttons
[    16.968] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    16.968] (--) evdev: Logitech USB Receiver: Found relative axes
[    16.968] (II) evdev: Logitech USB Receiver: Forcing relative x/y axes to exist.
[    16.968] (--) evdev: Logitech USB Receiver: Found absolute axes
[    16.968] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[    16.968] (--) evdev: Logitech USB Receiver: Found keys
[    16.968] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    16.968] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    16.968] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    16.968] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    16.968] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.968] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.4/1-2.4:1.1/0003:046D:C51A.0002/input/input10/event9"
[    16.968] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 15)
[    16.968] (**) Option "xkb_rules" "evdev"
[    16.968] (**) Option "xkb_model" "pc105"
[    16.968] (**) Option "xkb_layout" "us"
[    16.968] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    16.968] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[    16.968] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    16.968] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    16.968] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    16.968] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    16.968] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event14)
[    16.968] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[    16.968] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[    16.968] (**) Lenovo EasyCamera: always reports core events
[    16.968] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event14"
[    16.968] (--) evdev: Lenovo EasyCamera: Vendor 0x5986 Product 0x55e
[    16.968] (--) evdev: Lenovo EasyCamera: Found keys
[    16.968] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[    16.968] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/input/input15/event14"
[    16.968] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 16)
[    16.968] (**) Option "xkb_rules" "evdev"
[    16.968] (**) Option "xkb_model" "pc105"
[    16.968] (**) Option "xkb_layout" "us"
[    16.969] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event18)
[    16.969] (II) No input driver specified, ignoring this device.
[    16.969] (II) This device may have been added with another device file.
[    16.969] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event19)
[    16.969] (II) No input driver specified, ignoring this device.
[    16.969] (II) This device may have been added with another device file.
[    16.969] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event13)
[    16.969] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[    16.969] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[    16.969] (**) Ideapad extra buttons: always reports core events
[    16.969] (**) evdev: Ideapad extra buttons: Device: "/dev/input/event13"
[    16.969] (--) evdev: Ideapad extra buttons: Vendor 0 Product 0
[    16.969] (--) evdev: Ideapad extra buttons: Found keys
[    16.969] (II) evdev: Ideapad extra buttons: Configuring as keyboard
[    16.969] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input14/event13"
[    16.969] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 17)
[    16.969] (**) Option "xkb_rules" "evdev"
[    16.969] (**) Option "xkb_model" "pc105"
[    16.969] (**) Option "xkb_layout" "us"
[    16.969] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    16.969] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    16.969] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    16.969] (**) AT Translated Set 2 keyboard: always reports core events
[    16.969] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    16.969] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    16.969] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    16.969] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    16.969] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    16.969] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 18)
[    16.969] (**) Option "xkb_rules" "evdev"
[    16.969] (**) Option "xkb_model" "pc105"
[    16.969] (**) Option "xkb_layout" "us"
[    16.970] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    16.970] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    16.970] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    16.970] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    16.970] (II) LoadModule: "synaptics"
[    16.970] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    16.971] (II) Module synaptics: vendor="X.Org Foundation"
[    16.971]    compiled for 1.16.0, module version = 1.8.99
[    16.971]    Module class: X.Org XInput Driver
[    16.971]    ABI class: X.Org XInput driver, version 21.0
[    16.971] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    16.971] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.971] (**) Option "Device" "/dev/input/event7"
[    17.020] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    17.020] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5664 (res 42)
[    17.020] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4678 (res 51)
[    17.020] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    17.020] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    17.020] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    17.020] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    17.020] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    17.020] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    17.020] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    17.056] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event7"
[    17.056] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 19)
[    17.056] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    17.056] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    17.056] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[    17.056] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    17.056] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    17.056] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    17.056] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    17.056] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    17.056] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    17.056] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    17.887] (II) intel(0): resizing framebuffer to 5760x2160
[    17.924] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 0, position (3840, 0), rotation normal, reflection none
[    18.437] (II) intel(0): switch to mode 3840x2160@48.0 on eDP1 using pipe 1, position (0, 0), rotation normal, reflection none
[    20.051] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    21.266] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    52.807] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    52.987] (II) intel(0): switch to mode 1920x1080@59.9 on HDMI1 using pipe 1, position (3840, 0), rotation normal, reflection none
[    53.482] (II) intel(0): switch to mode 3840x2160@48.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    54.753] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    80.488] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm



```

What puzzled me was the 'ii  linux-image-generic                         3.16.0.31.32                                           amd64        Generic Linux kernel image' from a &#10140; dpkg -l | grep linux-


Now with the 3.18.3 Kernel in place, I did try installing nvidia-346 and it gave me the black screen of death again. So I uninstalled that and it reboots fine.

---

### Post by wwwebdevil on 2015-03-06
Hi!
I have the same computer Lenovo Y50. I managed to get the nvidia drivers working. I was trying to do this for 1-2 months. So, I am not sure what causes the problem (probably the kernel) but what I did is, I installed ubuntu clean and did not upgrade it. Installed the nvidia-346 drivers from mamarley ppa and it worked. Multiscreen does not work with nvidia drivers properly. You should use intel.

Edit: Kernel version of mine is 3.16.0-31

Thanks.

---

### Post by JDAIII on 2015-03-06
Well that adds a wrinkle to the plan. If I have a choice, I have to have multiple monitors. I'll still try since you are on an older kernel and it may work with 3.18. May being the word of the day here.

---

### Post by Bashing-om on 2015-03-06
JDAIII; Yep,

Getting curious and curiouser, as now the file does show booting the 3.18 kernel.
But but, But ....
> 
16.876] (--) PCI:*(0:0:2:0) 8086:0416:17aa:3978 rev 6, Mem @ 0xd1000000/4194304, 0xc0000000/268435456, I/O @ 0x00005000/64
[    16.876] (--) PCI: (0:1:0:0) 10de:1392:17aa:3978 rev 162, Mem @ 0xd0000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[    16.876] (II) LoadModule: "glx"
[    16.877] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.884] (II) Module glx: vendor="X.Org Foundation"
[    16.884]    compiled for 1.16.1.901, module version = 1.0.0
[    16.884]    ABI class: X.Org Server Extension, version 8.0
[    16.884] (==) AIGLX enabled
[    16.885] (==) Matched intel as autoconfigured driver 0
[    16.885] (==) Matched intel as autoconfigured driver 1
[    16.885] (==) Matched modesetting as autoconfigured driver 2
[    16.885] (==) Matched fbdev as autoconfigured driver 3
[    16.885] (==) Matched vesa as autoconfigured driver 4
[    16.885] (==) Assigned the driver to the xf86ConfigLayout
[    16.885] (II) LoadModule: "intel"

the Nvidia card is identified ( PCI: (0:1:0:0) )) BUT, no attempt is even made to build the module for Nvidia ! Is this output with the Nvidia 346 driver UN-Installed ?

Maybe try and install the 340 driver, see if that one will build ?
--------------------
> 
What puzzled me was the 'ii linux-image-generic 3.16.0.31.32 amd64 Generic Linux kernel image' from a &#10140; dpkg -l | grep linux-
 that dpkg command shows all kernels installed. To soon to address it, but at some later point will have to remove the old no-longer-needed kernels.

[INDENT][INDENT]it is a process in learning
[/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-06
This is the xorg after I install nvidia-346. I will reboot and update this with the xorg from then. I will also try 340 and update the post again.

```
 &#10140; cat /var/log/Xorg.0.log                                                   ~ [    16.104] 
X.Org X Server 1.16.1.901 (1.16.2 RC 1)
Release Date: 2014-11-02
[    16.104] X Protocol Version 11, Revision 0
[    16.104] Build Operating System: Linux 3.13.0-39-generic x86_64 Ubuntu
[    16.104] Current Operating System: Linux jd-laptop 3.18.3-031803-generic #201501161810 SMP Fri Jan 16 18:12:22 UTC 2015 x86_64
[    16.104] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.18.3-031803-generic root=UUID=9ba789c0-7d71-4b8e-b093-51d9db78b777 ro quiet splash vt.handoff=7
[    16.104] Build Date: 20 November 2014  09:55:19PM
[    16.104] xorg-server 2:1.16.1.901-1ubuntu1~utopic1 (For technical support please see http://www.ubuntu.com/support) 
[    16.104] Current version of pixman: 0.32.4
[    16.104]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    16.104] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.104] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  6 18:18:07 2015
[    16.105] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.106] (==) No Layout section.  Using the first Screen section.
[    16.106] (==) No screen section available. Using defaults.
[    16.106] (**) |-->Screen "Default Screen Section" (0)
[    16.106] (**) |   |-->Monitor "<default monitor>"
[    16.107] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    16.107] (==) Automatically adding devices
[    16.107] (==) Automatically enabling devices
[    16.107] (==) Automatically adding GPU devices
[    16.111] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.111]    Entry deleted from font path.
[    16.111] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.111]    Entry deleted from font path.
[    16.111] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.111]    Entry deleted from font path.
[    16.111] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.111]    Entry deleted from font path.
[    16.111] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.111]    Entry deleted from font path.
[    16.111] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    16.111] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.111] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.111] (II) Loader magic: 0x7fad34ce4d80
[    16.111] (II) Module ABI versions:
[    16.111]    X.Org ANSI C Emulation: 0.4
[    16.111]    X.Org Video Driver: 18.0
[    16.111]    X.Org XInput driver : 21.0
[    16.111]    X.Org Server Extension : 8.0
[    16.111] (II) xfree86: Adding drm device (/dev/dri/card0)
[    16.113] (--) PCI:*(0:0:2:0) 8086:0416:17aa:3978 rev 6, Mem @ 0xd1000000/4194304, 0xc0000000/268435456, I/O @ 0x00005000/64
[    16.113] (--) PCI: (0:1:0:0) 10de:1392:17aa:3978 rev 162, Mem @ 0xd0000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[    16.113] (II) LoadModule: "glx"
[    16.114] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    16.121] (II) Module glx: vendor="X.Org Foundation"
[    16.121]    compiled for 1.16.1.901, module version = 1.0.0
[    16.121]    ABI class: X.Org Server Extension, version 8.0
[    16.121] (==) AIGLX enabled
[    16.121] (==) Matched intel as autoconfigured driver 0
[    16.121] (==) Matched intel as autoconfigured driver 1
[    16.121] (==) Matched modesetting as autoconfigured driver 2
[    16.121] (==) Matched fbdev as autoconfigured driver 3
[    16.121] (==) Matched vesa as autoconfigured driver 4
[    16.121] (==) Assigned the driver to the xf86ConfigLayout
[    16.121] (II) LoadModule: "intel"
[    16.122] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    16.125] (II) Module intel: vendor="X.Org Foundation"
[    16.125]    compiled for 1.16.1.901, module version = 2.99.917
[    16.125]    Module class: X.Org Video Driver
[    16.125]    ABI class: X.Org Video Driver, version 18.0
[    16.125] (II) LoadModule: "modesetting"
[    16.126] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    16.126] (II) Module modesetting: vendor="X.Org Foundation"
[    16.126]    compiled for 1.16.0, module version = 0.9.0
[    16.126]    Module class: X.Org Video Driver
[    16.126]    ABI class: X.Org Video Driver, version 18.0
[    16.126] (II) LoadModule: "fbdev"
[    16.126] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.127] (II) Module fbdev: vendor="X.Org Foundation"
[    16.127]    compiled for 1.16.0, module version = 0.4.4
[    16.127]    Module class: X.Org Video Driver
[    16.127]    ABI class: X.Org Video Driver, version 18.0
[    16.127] (II) LoadModule: "vesa"
[    16.127] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.127] (II) Module vesa: vendor="X.Org Foundation"
[    16.127]    compiled for 1.16.0, module version = 2.3.3
[    16.127]    Module class: X.Org Video Driver
[    16.127]    ABI class: X.Org Video Driver, version 18.0
[    16.127] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    16.128] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    16.128] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    16.128] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    16.128] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    16.128] (II) FBDEV: driver for framebuffer: fbdev
[    16.128] (II) VESA: driver for VESA chipsets: vesa
[    16.128] (++) using VT number 7
[    16.129] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20140905
[    16.129] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150304.88e61542-0ubuntu0sarvatt~utopic (Robert Hooker <sarvatt@ubuntu.com>)
[    16.129] (II) intel(0): SNA compiled for use with valgrind
[    16.129] (WW) Falling back to old probe method for modesetting
[    16.130] (WW) Falling back to old probe method for fbdev
[    16.130] (II) Loading sub module "fbdevhw"
[    16.130] (II) LoadModule: "fbdevhw"
[    16.130] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.130] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.130]    compiled for 1.16.1.901, module version = 0.0.2
[    16.130]    ABI class: X.Org Video Driver, version 18.0
[    16.130] (WW) Falling back to old probe method for vesa
[    16.131] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    16.131] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[    16.131] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    16.131] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    16.131] (==) intel(0): RGB weight 888
[    16.131] (==) intel(0): Default visual is TrueColor
[    16.131] (II) intel(0): Output eDP1 has no monitor section
[    16.131] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[    16.131] (II) intel(0): Enabled output eDP1
[    16.131] (II) intel(0): Output VGA1 has no monitor section
[    16.131] (II) intel(0): Enabled output VGA1
[    16.131] (II) intel(0): Output HDMI1 has no monitor section
[    16.131] (II) intel(0): Enabled output HDMI1
[    16.131] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    16.131] (II) intel(0): Output VIRTUAL1 has no monitor section
[    16.131] (II) intel(0): Enabled output VIRTUAL1
[    16.131] (--) intel(0): Output eDP1 using initial mode 3840x2160 on pipe 0
[    16.131] (==) intel(0): TearFree disabled
[    16.131] (==) intel(0): DPI set to (96, 96)
[    16.131] (II) Loading sub module "dri2"
[    16.131] (II) LoadModule: "dri2"
[    16.131] (II) Module "dri2" already built-in
[    16.131] (II) Loading sub module "present"
[    16.131] (II) LoadModule: "present"
[    16.131] (II) Module "present" already built-in
[    16.132] (II) UnloadModule: "modesetting"
[    16.132] (II) Unloading modesetting
[    16.132] (II) UnloadModule: "fbdev"
[    16.132] (II) Unloading fbdev
[    16.132] (II) UnloadSubModule: "fbdevhw"
[    16.132] (II) Unloading fbdevhw
[    16.132] (II) UnloadModule: "vesa"
[    16.132] (II) Unloading vesa
[    16.132] (==) Depth 24 pixmap format is 32 bpp
[    16.135] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    16.135] (==) intel(0): Backing store enabled
[    16.135] (==) intel(0): Silken mouse enabled
[    16.135] (II) intel(0): HW Cursor enabled
[    16.135] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    16.136] (==) intel(0): DPMS enabled
[    16.136] (==) intel(0): Display hotplug detection enabled
[    16.136] (II) intel(0): [DRI2] Setup complete
[    16.136] (II) intel(0): [DRI2]   DRI driver: i965
[    16.136] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    16.136] (II) intel(0): direct rendering: DRI2 enabled
[    16.136] (II) intel(0): hardware support for Present enabled
[    16.136] (--) RandR disabled
[    16.141] (II) SELinux: Disabled on system
[    16.172] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    16.172] (II) AIGLX: enabled GLX_ARB_create_context
[    16.172] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    16.172] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    16.172] (II) AIGLX: enabled GLX_INTEL_swap_event
[    16.172] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    16.172] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    16.172] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    16.172] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    16.172] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    16.172] (II) AIGLX: Loaded and initialized i965
[    16.172] (II) GLX: Initialized DRI2 GL provider for screen 0
[    16.180] (II) intel(0): switch to mode 3840x2160@48.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    16.180] (II) intel(0): Setting screen physical size to 1016 x 571
[    16.190] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    16.192] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    16.192] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.192] (II) LoadModule: "evdev"
[    16.193] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.194] (II) Module evdev: vendor="X.Org Foundation"
[    16.194]    compiled for 1.16.0, module version = 2.9.0
[    16.194]    Module class: X.Org XInput Driver
[    16.194]    ABI class: X.Org XInput driver, version 21.0
[    16.194] (II) Using input driver 'evdev' for 'Power Button'
[    16.194] (**) Power Button: always reports core events
[    16.195] (**) evdev: Power Button: Device: "/dev/input/event3"
[    16.195] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.195] (--) evdev: Power Button: Found keys
[    16.195] (II) evdev: Power Button: Configuring as keyboard
[    16.195] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    16.195] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    16.195] (**) Option "xkb_rules" "evdev"
[    16.195] (**) Option "xkb_model" "pc105"
[    16.195] (**) Option "xkb_layout" "us"
[    16.195] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    16.195] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.195] (II) Using input driver 'evdev' for 'Video Bus'
[    16.195] (**) Video Bus: always reports core events
[    16.195] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    16.195] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    16.195] (--) evdev: Video Bus: Found keys
[    16.195] (II) evdev: Video Bus: Configuring as keyboard
[    16.195] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8/event6"
[    16.195] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    16.195] (**) Option "xkb_rules" "evdev"
[    16.195] (**) Option "xkb_model" "pc105"
[    16.195] (**) Option "xkb_layout" "us"
[    16.196] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.196] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.196] (II) Using input driver 'evdev' for 'Power Button'
[    16.196] (**) Power Button: always reports core events
[    16.196] (**) evdev: Power Button: Device: "/dev/input/event0"
[    16.196] (--) evdev: Power Button: Vendor 0 Product 0x1
[    16.196] (--) evdev: Power Button: Found keys
[    16.196] (II) evdev: Power Button: Configuring as keyboard
[    16.196] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    16.196] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    16.196] (**) Option "xkb_rules" "evdev"
[    16.196] (**) Option "xkb_model" "pc105"
[    16.196] (**) Option "xkb_layout" "us"
[    16.196] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    16.196] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    16.196] (II) Using input driver 'evdev' for 'Sleep Button'
[    16.196] (**) Sleep Button: always reports core events
[    16.196] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    16.196] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    16.196] (--) evdev: Sleep Button: Found keys
[    16.196] (II) evdev: Sleep Button: Configuring as keyboard
[    16.196] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input1/event1"
[    16.196] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    16.196] (**) Option "xkb_rules" "evdev"
[    16.196] (**) Option "xkb_model" "pc105"
[    16.196] (**) Option "xkb_layout" "us"
[    16.196] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    16.196] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    16.196] (II) Using input driver 'evdev' for 'Video Bus'
[    16.196] (**) Video Bus: always reports core events
[    16.196] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    16.196] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    16.196] (--) evdev: Video Bus: Found keys
[    16.196] (II) evdev: Video Bus: Configuring as keyboard
[    16.196] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:43/LNXVIDEO:00/input/input7/event5"
[    16.196] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 10)
[    16.196] (**) Option "xkb_rules" "evdev"
[    16.196] (**) Option "xkb_model" "pc105"
[    16.197] (**) Option "xkb_layout" "us"
[    16.197] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    16.197] (II) No input driver specified, ignoring this device.
[    16.197] (II) This device may have been added with another device file.
[    16.197] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event10)
[    16.197] (II) No input driver specified, ignoring this device.
[    16.197] (II) This device may have been added with another device file.
[    16.197] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event11)
[    16.197] (II) No input driver specified, ignoring this device.
[    16.197] (II) This device may have been added with another device file.
[    16.197] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event12)
[    16.197] (II) No input driver specified, ignoring this device.
[    16.197] (II) This device may have been added with another device file.
[    16.197] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event9)
[    16.197] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[    16.197] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[    16.197] (**) Lenovo EasyCamera: always reports core events
[    16.197] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event9"
[    16.197] (--) evdev: Lenovo EasyCamera: Vendor 0x5986 Product 0x55e
[    16.197] (--) evdev: Lenovo EasyCamera: Found keys
[    16.197] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[    16.197] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/input/input10/event9"
[    16.197] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 11)
[    16.197] (**) Option "xkb_rules" "evdev"
[    16.197] (**) Option "xkb_model" "pc105"
[    16.198] (**) Option "xkb_layout" "us"
[    16.198] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event13)
[    16.198] (II) No input driver specified, ignoring this device.
[    16.198] (II) This device may have been added with another device file.
[    16.198] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event14)
[    16.198] (II) No input driver specified, ignoring this device.
[    16.198] (II) This device may have been added with another device file.
[    16.198] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event8)
[    16.198] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[    16.198] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[    16.198] (**) Ideapad extra buttons: always reports core events
[    16.198] (**) evdev: Ideapad extra buttons: Device: "/dev/input/event8"
[    16.198] (--) evdev: Ideapad extra buttons: Vendor 0 Product 0
[    16.198] (--) evdev: Ideapad extra buttons: Found keys
[    16.198] (II) evdev: Ideapad extra buttons: Configuring as keyboard
[    16.198] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input9/event8"
[    16.198] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 12)
[    16.198] (**) Option "xkb_rules" "evdev"
[    16.198] (**) Option "xkb_model" "pc105"
[    16.198] (**) Option "xkb_layout" "us"
[    16.198] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    16.199] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    16.199] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    16.199] (**) AT Translated Set 2 keyboard: always reports core events
[    16.199] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    16.199] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    16.199] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    16.199] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    16.199] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    16.199] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    16.199] (**) Option "xkb_rules" "evdev"
[    16.199] (**) Option "xkb_model" "pc105"
[    16.199] (**) Option "xkb_layout" "us"
[    16.199] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    16.199] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    16.199] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    16.199] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    16.199] (II) LoadModule: "synaptics"
[    16.199] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    16.200] (II) Module synaptics: vendor="X.Org Foundation"
[    16.200]    compiled for 1.16.0, module version = 1.8.99
[    16.200]    Module class: X.Org XInput Driver
[    16.200]    ABI class: X.Org XInput driver, version 21.0
[    16.200] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    16.200] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.200] (**) Option "Device" "/dev/input/event7"
[    16.264] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    16.264] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5664 (res 42)
[    16.264] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4678 (res 51)
[    16.264] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    16.264] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    16.264] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    16.264] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    16.264] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    16.264] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    16.264] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    16.292] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event7"
[    16.292] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[    16.292] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    16.292] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    16.292] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[    16.292] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    16.292] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    16.292] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    16.292] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    16.292] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    16.292] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    16.292] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    16.913] (II) intel(0): EDID vendor "SDC", prod id 18514
[    16.914] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    16.914] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    16.914] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    16.914] (II) intel(0): Printing DDC gathered Modelines:
[    16.914] (II) intel(0): Modeline "3840x2160"x0.0  421.55  3840 3888 3920 3956  2160 2162 2167 2220 -hsync -vsync (106.6 kHz eP)
[    17.711] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    18.751] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    25.442] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.064] (II) intel(0): resizing framebuffer to 1920x1080
[    26.066] (II) intel(0): switch to mode 1920x1080@59.9 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    27.346] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    28.015] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm



```

xorg after installing nvidia-346 and after reboot:
```
[    12.202] X.Org X Server 1.16.1.901 (1.16.2 RC 1)
Release Date: 2014-11-02
[    12.202] X Protocol Version 11, Revision 0
[    12.202] Build Operating System: Linux 3.13.0-39-generic x86_64 Ubuntu
[    12.202] Current Operating System: Linux jd-laptop 3.18.3-031803-generic #201501161810 SMP Fri Jan 16 18:12:22 UTC 2015 x86_64
[    12.202] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.18.3-031803-generic root=UUID=9ba789c0-7d71-4b8e-b093-51d9db78b777 ro quiet splash
[    12.202] Build Date: 20 November 2014  09:55:19PM
[    12.202] xorg-server 2:1.16.1.901-1ubuntu1~utopic1 (For technical support please see http://www.ubuntu.com/support) 
[    12.202] Current version of pixman: 0.32.4
[    12.202] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    12.202] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.202] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  6 18:25:32 2015
[    12.203] (==) Using config file: "/etc/X11/xorg.conf"
[    12.203] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.204] (==) ServerLayout "layout"
[    12.204] (**) |-->Screen "nvidia" (0)
[    12.204] (**) |   |-->Monitor "<default monitor>"
[    12.205] (**) |   |-->Device "nvidia"
[    12.205] (==) No monitor specified for screen "nvidia".
	Using a default monitor configuration.
[    12.205] (**) |-->Inactive Device "intel"
[    12.205] (==) Automatically adding devices
[    12.205] (==) Automatically enabling devices
[    12.205] (==) Automatically adding GPU devices
[    12.207] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.207] 	Entry deleted from font path.
[    12.207] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.207] 	Entry deleted from font path.
[    12.207] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.207] 	Entry deleted from font path.
[    12.207] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.207] 	Entry deleted from font path.
[    12.207] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.207] 	Entry deleted from font path.
[    12.207] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    12.207] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.207] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.207] (II) Loader magic: 0x7fc5c0ac2d80
[    12.207] (II) Module ABI versions:
[    12.207] 	X.Org ANSI C Emulation: 0.4
[    12.207] 	X.Org Video Driver: 18.0
[    12.207] 	X.Org XInput driver : 21.0
[    12.207] 	X.Org Server Extension : 8.0
[    12.207] (II) xfree86: Adding drm device (/dev/dri/card1)
[    12.207] (II) xfree86: Adding drm device (/dev/dri/card0)
[    12.208] (--) PCI:*(0:0:2:0) 8086:0416:17aa:3978 rev 6, Mem @ 0xd1000000/4194304, 0xc0000000/268435456, I/O @ 0x00005000/64
[    12.208] (--) PCI: (0:1:0:0) 10de:1392:17aa:3978 rev 162, Mem @ 0xd0000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[    12.208] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    12.208] (II) "glx" will be loaded by default.
[    12.208] (WW) "xmir" is not to be loaded by default. Skipping.
[    12.208] (II) LoadModule: "glx"
[    12.209] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    12.302] (II) Module glx: vendor="NVIDIA Corporation"
[    12.303] 	compiled for 4.0.2, module version = 1.0.0
[    12.303] 	Module class: X.Org Server Extension
[    12.303] (II) NVIDIA GLX Module  346.47  Thu Feb 19 18:09:07 PST 2015
[    12.304] (II) LoadModule: "nvidia"
[    12.304] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    12.316] (II) Module nvidia: vendor="NVIDIA Corporation"
[    12.316] 	compiled for 4.0.2, module version = 1.0.0
[    12.316] 	Module class: X.Org Video Driver
[    12.317] (II) LoadModule: "intel"
[    12.319] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.324] (II) Module intel: vendor="X.Org Foundation"
[    12.324] 	compiled for 1.16.1.901, module version = 2.99.917
[    12.324] 	Module class: X.Org Video Driver
[    12.324] 	ABI class: X.Org Video Driver, version 18.0
[    12.324] (II) NVIDIA dlloader X Driver  346.47  Thu Feb 19 17:47:18 PST 2015
[    12.324] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    12.325] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    12.325] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    12.325] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    12.325] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    12.325] (++) using VT number 7


[    12.327] (II) Loading sub module "fb"
[    12.327] (II) LoadModule: "fb"
[    12.327] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.329] (II) Module fb: vendor="X.Org Foundation"
[    12.329] 	compiled for 1.16.1.901, module version = 1.0.0
[    12.329] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.329] (II) Loading sub module "wfb"
[    12.329] (II) LoadModule: "wfb"
[    12.329] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    12.331] (II) Module wfb: vendor="X.Org Foundation"
[    12.331] 	compiled for 1.16.1.901, module version = 1.0.0
[    12.331] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.331] (II) Loading sub module "ramdac"
[    12.331] (II) LoadModule: "ramdac"
[    12.331] (II) Module "ramdac" already built-in
[    12.334] (II) intel(G0): Using Kernel Mode Setting driver: i915, version 1.6.0 20140905
[    12.334] (II) intel(G0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150304.88e61542-0ubuntu0sarvatt~utopic (Robert Hooker <sarvatt@ubuntu.com>)
[    12.334] (II) intel(G0): SNA compiled for use with valgrind
[    12.335] (II) intel(G1): Using Kernel Mode Setting driver: i915, version 1.6.0 20140905
[    12.335] (II) intel(G1): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150304.88e61542-0ubuntu0sarvatt~utopic (Robert Hooker <sarvatt@ubuntu.com>)
[    12.335] (II) intel(G1): SNA compiled for use with valgrind
[    12.335] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"nvidia" for depth/fbbpp 24/32
[    12.335] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    12.335] (==) NVIDIA(0): RGB weight 888
[    12.335] (==) NVIDIA(0): Default visual is TrueColor
[    12.335] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    12.336] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    12.336] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    12.336] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    12.337] (**) NVIDIA(0): Enabling 2D acceleration
[    17.042] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[    17.043] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 860M (GM107-A) at PCI:1:0:0 (GPU-0)
[    17.043] (--) NVIDIA(0): Memory: 2097152 kBytes
[    17.043] (--) NVIDIA(0): VideoBIOS: 82.07.34.00.08
[    17.044] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    17.044] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 860M at PCI:1:0:0
[    17.044] (--) NVIDIA(0):     none
[    17.044] (II) NVIDIA(0): Validated MetaModes:
[    17.044] (II) NVIDIA(0):     "NULL"
[    17.044] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    17.044] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    17.044] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    17.044] (--) intel(G0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    17.044] (--) intel(G0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[    17.044] (==) intel(G0): Depth 24, (--) framebuffer bpp 32
[    17.044] (==) intel(G0): RGB weight 888
[    17.044] (==) intel(G0): Default visual is TrueColor
[    17.044] (**) intel(G0): Option "AccelMethod" "SNA"
[    17.045] (II) intel(G0): Output eDP1 has no monitor section
[    17.045] (--) intel(G0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[    17.045] (II) intel(G0): Enabled output eDP1
[    17.045] (II) intel(G0): Output VGA1 has no monitor section
[    17.045] (II) intel(G0): Enabled output VGA1
[    17.045] (II) intel(G0): Output HDMI1 has no monitor section
[    17.045] (II) intel(G0): Enabled output HDMI1
[    17.045] (--) intel(G0): Using a maximum size of 256x256 for hardware cursors
[    17.045] (II) intel(G0): Output VIRTUAL1 has no monitor section
[    17.045] (II) intel(G0): Enabled output VIRTUAL1
[    17.045] (==) intel(G0): TearFree disabled
[    17.045] (==) intel(G0): DPI set to (96, 96)
[    17.045] (II) Loading sub module "dri2"
[    17.045] (II) LoadModule: "dri2"
[    17.046] (II) Module "dri2" already built-in
[    17.046] (II) Loading sub module "present"
[    17.046] (II) LoadModule: "present"
[    17.046] (II) Module "present" already built-in
[    19.288] (EE) intel(G1): [drm] failed to set drm interface version: Permission denied [13].
[    19.288] (II) intel(G1): [drm] Contents of '/sys/kernel/debug/dri/0/clients':
[    19.288] (II) intel(G1): [drm]              command   pid dev master a   uid      magic
[    19.288] (II) intel(G1): [drm]            plymouthd   218   0   n    y     0          0
[    19.288] (II) intel(G1): [drm]                 Xorg  1849   0   y    y     0          0
[    19.288] (II) intel(G1): [drm]                 Xorg  1849   0   n    y     0          0
[    19.288] (EE) intel(G1): Failed to claim DRM device.
[    19.288] (II) UnloadModule: "intel"
[    19.288] (--) Depth 24 pixmap format is 32 bpp
[    19.291] (II) intel(G0): SNA initialized with Haswell (gen7.5, gt2) backend
[    19.291] (==) intel(G0): Backing store enabled
[    19.291] (==) intel(G0): Silken mouse enabled
[    19.291] (II) intel(G0): HW Cursor enabled
[    19.291] (II) intel(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    19.292] (==) intel(G0): DPMS enabled
[    19.292] (==) intel(G0): Display hotplug detection enabled
[    19.292] (II) intel(G0): [DRI2] Setup complete
[    19.292] (II) intel(G0): [DRI2]   DRI driver: i965
[    19.292] (II) intel(G0): [DRI2]   VDPAU driver: va_gl
[    19.292] (II) intel(G0): direct rendering: DRI2 enabled
[    19.292] (II) intel(G0): hardware support for Present enabled
[    19.292] (WW) intel(G0): Option "AllowEmptyInitialConfiguration" is not used
[    19.292] (WW) intel(G0): Option "IgnoreDisplayDevices" is not used
[    19.292] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    19.292] (II) NVIDIA:     access.
[    19.295] (II) NVIDIA(0): Setting mode "NULL"
[    19.309] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[    19.314] (==) NVIDIA(0): Disabling shared memory pixmaps
[    19.314] (==) NVIDIA(0): Backing store enabled
[    19.314] (==) NVIDIA(0): Silken mouse enabled
[    19.314] (==) NVIDIA(0): DPMS enabled
[    19.314] (II) Loading sub module "dri2"
[    19.314] (II) LoadModule: "dri2"
[    19.314] (II) Module "dri2" already built-in
[    19.314] (II) NVIDIA(0): [DRI2] Setup complete
[    19.314] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    19.314] (--) RandR disabled
[    19.318] (II) SELinux: Disabled on system
[    19.319] (II) Initializing extension GLX
[    19.319] (II) Indirect GLX disabled.(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.552] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    19.552] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.552] (II) LoadModule: "evdev"
[    19.552] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.554] (II) Module evdev: vendor="X.Org Foundation"
[    19.554] 	compiled for 1.16.0, module version = 2.9.0
[    19.554] 	Module class: X.Org XInput Driver
[    19.554] 	ABI class: X.Org XInput driver, version 21.0
[    19.554] (II) Using input driver 'evdev' for 'Power Button'
[    19.554] (**) Power Button: always reports core events
[    19.554] (**) evdev: Power Button: Device: "/dev/input/event3"
[    19.554] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.554] (--) evdev: Power Button: Found keys
[    19.554] (II) evdev: Power Button: Configuring as keyboard
[    19.554] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    19.554] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    19.554] (**) Option "xkb_rules" "evdev"
[    19.554] (**) Option "xkb_model" "pc105"
[    19.554] (**) Option "xkb_layout" "us"
[    19.555] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    19.555] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.555] (II) Using input driver 'evdev' for 'Video Bus'
[    19.555] (**) Video Bus: always reports core events
[    19.555] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    19.555] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    19.555] (--) evdev: Video Bus: Found keys
[    19.555] (II) evdev: Video Bus: Configuring as keyboard
[    19.555] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8/event6"
[    19.555] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    19.555] (**) Option "xkb_rules" "evdev"
[    19.555] (**) Option "xkb_model" "pc105"
[    19.555] (**) Option "xkb_layout" "us"
[    19.555] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.555] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.555] (II) Using input driver 'evdev' for 'Power Button'
[    19.555] (**) Power Button: always reports core events
[    19.555] (**) evdev: Power Button: Device: "/dev/input/event0"
[    19.555] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.555] (--) evdev: Power Button: Found keys
[    19.555] (II) evdev: Power Button: Configuring as keyboard
[    19.555] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    19.555] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    19.555] (**) Option "xkb_rules" "evdev"
[    19.555] (**) Option "xkb_model" "pc105"
[    19.555] (**) Option "xkb_layout" "us"
[    19.555] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    19.555] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    19.555] (II) Using input driver 'evdev' for 'Sleep Button'
[    19.555] (**) Sleep Button: always reports core events
[    19.555] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    19.556] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    19.556] (--) evdev: Sleep Button: Found keys
[    19.556] (II) evdev: Sleep Button: Configuring as keyboard
[    19.556] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input1/event1"
[    19.556] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    19.556] (**) Option "xkb_rules" "evdev"
[    19.556] (**) Option "xkb_model" "pc105"
[    19.556] (**) Option "xkb_layout" "us"
[    19.556] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    19.556] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.556] (II) Using input driver 'evdev' for 'Video Bus'
[    19.556] (**) Video Bus: always reports core events
[    19.556] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    19.556] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    19.556] (--) evdev: Video Bus: Found keys
[    19.556] (II) evdev: Video Bus: Configuring as keyboard
[    19.556] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:43/LNXVIDEO:00/input/input7/event5"
[    19.556] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 10)
[    19.556] (**) Option "xkb_rules" "evdev"
[    19.556] (**) Option "xkb_model" "pc105"
[    19.556] (**) Option "xkb_layout" "us"
[    19.556] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    19.556] (II) No input driver specified, ignoring this device.
[    19.556] (II) This device may have been added with another device file.
[    19.556] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event12)
[    19.556] (II) No input driver specified, ignoring this device.
[    19.556] (II) This device may have been added with another device file.
[    19.556] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event13)
[    19.556] (II) No input driver specified, ignoring this device.
[    19.556] (II) This device may have been added with another device file.
[    19.557] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event14)
[    19.557] (II) No input driver specified, ignoring this device.
[    19.557] (II) This device may have been added with another device file.
[    19.557] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event9)
[    19.557] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[    19.557] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[    19.557] (**) Lenovo EasyCamera: always reports core events
[    19.557] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event9"
[    19.557] (--) evdev: Lenovo EasyCamera: Vendor 0x5986 Product 0x55e
[    19.557] (--) evdev: Lenovo EasyCamera: Found keys
[    19.557] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[    19.557] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/input/input10/event9"
[    19.557] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 11)
[    19.557] (**) Option "xkb_rules" "evdev"
[    19.557] (**) Option "xkb_model" "pc105"
[    19.557] (**) Option "xkb_layout" "us"
[    19.557] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    19.557] (II) No input driver specified, ignoring this device.
[    19.557] (II) This device may have been added with another device file.
[    19.557] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    19.557] (II) No input driver specified, ignoring this device.
[    19.557] (II) This device may have been added with another device file.
[    19.557] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event8)
[    19.557] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[    19.557] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[    19.557] (**) Ideapad extra buttons: always reports core events
[    19.557] (**) evdev: Ideapad extra buttons: Device: "/dev/input/event8"
[    19.557] (--) evdev: Ideapad extra buttons: Vendor 0 Product 0
[    19.557] (--) evdev: Ideapad extra buttons: Found keys
[    19.557] (II) evdev: Ideapad extra buttons: Configuring as keyboard
[    19.557] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input9/event8"
[    19.557] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 12)
[    19.557] (**) Option "xkb_rules" "evdev"
[    19.557] (**) Option "xkb_model" "pc105"
[    19.557] (**) Option "xkb_layout" "us"
[    19.558] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    19.558] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.558] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    19.558] (**) AT Translated Set 2 keyboard: always reports core events
[    19.558] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    19.558] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    19.558] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    19.558] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    19.558] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    19.558] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    19.558] (**) Option "xkb_rules" "evdev"
[    19.558] (**) Option "xkb_model" "pc105"
[    19.558] (**) Option "xkb_layout" "us"
[    19.558] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    19.558] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    19.558] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    19.558] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    19.558] (II) LoadModule: "synaptics"
[    19.558] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    19.559] (II) Module synaptics: vendor="X.Org Foundation"
[    19.559] 	compiled for 1.16.0, module version = 1.8.99
[    19.559] 	Module class: X.Org XInput Driver
[    19.559] 	ABI class: X.Org XInput driver, version 21.0
[    19.559] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    19.559] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    19.559] (**) Option "Device" "/dev/input/event7"
[    19.568] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    19.568] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5664 (res 42)
[    19.568] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4678 (res 51)
[    19.568] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    19.568] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    19.568] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    19.568] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    19.568] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    19.568] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    19.568] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    19.580] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event7"
[    19.580] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[    19.580] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    19.580] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    19.580] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[    19.580] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    19.580] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    19.580] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    19.580] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    19.580] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    19.580] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    19.580] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    19.604] (II) intel(G0): EDID vendor "SDC", prod id 18514
[    19.604] (II) intel(G0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    19.604] (II) intel(G0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    19.604] (II) intel(G0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    19.604] (II) intel(G0): Printing DDC gathered Modelines:
[    19.604] (II) intel(G0): Modeline "3840x2160"x0.0  421.55  3840 3888 3920 3956  2160 2162 2167 2220 -hsync -vsync (106.6 kHz eP)
[    19.620] reporting 4 4 22 186
[    19.645] (II) intel(G0): switch to mode 3840x2160@48.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    19.646] reporting 4 4 22 186
[    19.648] reporting 4 4 22 186
[    19.668] reporting 4 4 22 186
[    19.692] (II) intel(G0): switch to mode 3840x2160@48.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    19.696] reporting 4 4 22 186
[    19.937] reporting 4 4 22 186
[    20.036] reporting 4 4 22 186
[    20.251] reporting 4 4 22 186
[    20.293] reporting 4 4 22 186
[    20.445] reporting 4 4 22 186

```

Then I tried installing nvidia-340 after uninstalling nvidia-346:
```

[    12.202] 
X.Org X Server 1.16.1.901 (1.16.2 RC 1)
Release Date: 2014-11-02
[    12.202] X Protocol Version 11, Revision 0
[    12.202] Build Operating System: Linux 3.13.0-39-generic x86_64 Ubuntu
[    12.202] Current Operating System: Linux jd-laptop 3.18.3-031803-generic #201501161810 SMP Fri Jan 16 18:12:22 UTC 2015 x86_64
[    12.202] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.18.3-031803-generic root=UUID=9ba789c0-7d71-4b8e-b093-51d9db78b777 ro quiet splash
[    12.202] Build Date: 20 November 2014  09:55:19PM
[    12.202] xorg-server 2:1.16.1.901-1ubuntu1~utopic1 (For technical support please see http://www.ubuntu.com/support) 
[    12.202] Current version of pixman: 0.32.4
[    12.202] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    12.202] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.202] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  6 18:25:32 2015
[    12.203] (==) Using config file: "/etc/X11/xorg.conf"
[    12.203] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.204] (==) ServerLayout "layout"
[    12.204] (**) |-->Screen "nvidia" (0)
[    12.204] (**) |   |-->Monitor "<default monitor>"
[    12.205] (**) |   |-->Device "nvidia"
[    12.205] (==) No monitor specified for screen "nvidia".
	Using a default monitor configuration.
[    12.205] (**) |-->Inactive Device "intel"
[    12.205] (==) Automatically adding devices
[    12.205] (==) Automatically enabling devices
[    12.205] (==) Automatically adding GPU devices
[    12.207] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.207] 	Entry deleted from font path.
[    12.207] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.207] 	Entry deleted from font path.
[    12.207] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.207] 	Entry deleted from font path.
[    12.207] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.207] 	Entry deleted from font path.
[    12.207] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.207] 	Entry deleted from font path.
[    12.207] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    12.207] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.207] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.207] (II) Loader magic: 0x7fc5c0ac2d80
[    12.207] (II) Module ABI versions:
[    12.207] 	X.Org ANSI C Emulation: 0.4
[    12.207] 	X.Org Video Driver: 18.0
[    12.207] 	X.Org XInput driver : 21.0
[    12.207] 	X.Org Server Extension : 8.0
[    12.207] (II) xfree86: Adding drm device (/dev/dri/card1)
[    12.207] (II) xfree86: Adding drm device (/dev/dri/card0)
[    12.208] (--) PCI:*(0:0:2:0) 8086:0416:17aa:3978 rev 6, Mem @ 0xd1000000/4194304, 0xc0000000/268435456, I/O @ 0x00005000/64
[    12.208] (--) PCI: (0:1:0:0) 10de:1392:17aa:3978 rev 162, Mem @ 0xd0000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[    12.208] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    12.208] (II) "glx" will be loaded by default.
[    12.208] (WW) "xmir" is not to be loaded by default. Skipping.
[    12.208] (II) LoadModule: "glx"
[    12.209] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    12.302] (II) Module glx: vendor="NVIDIA Corporation"
[    12.303] 	compiled for 4.0.2, module version = 1.0.0
[    12.303] 	Module class: X.Org Server Extension
[    12.303] (II) NVIDIA GLX Module  346.47  Thu Feb 19 18:09:07 PST 2015
[    12.304] (II) LoadModule: "nvidia"
[    12.304] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    12.316] (II) Module nvidia: vendor="NVIDIA Corporation"
[    12.316] 	compiled for 4.0.2, module version = 1.0.0
[    12.316] 	Module class: X.Org Video Driver
[    12.317] (II) LoadModule: "intel"
[    12.319] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    12.324] (II) Module intel: vendor="X.Org Foundation"
[    12.324] 	compiled for 1.16.1.901, module version = 2.99.917
[    12.324] 	Module class: X.Org Video Driver
[    12.324] 	ABI class: X.Org Video Driver, version 18.0
[    12.324] (II) NVIDIA dlloader X Driver  346.47  Thu Feb 19 17:47:18 PST 2015
[    12.324] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    12.325] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    12.325] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    12.325] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    12.325] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    12.325] (++) using VT number 7


[    12.327] (II) Loading sub module "fb"
[    12.327] (II) LoadModule: "fb"
[    12.327] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.329] (II) Module fb: vendor="X.Org Foundation"
[    12.329] 	compiled for 1.16.1.901, module version = 1.0.0
[    12.329] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.329] (II) Loading sub module "wfb"
[    12.329] (II) LoadModule: "wfb"
[    12.329] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    12.331] (II) Module wfb: vendor="X.Org Foundation"
[    12.331] 	compiled for 1.16.1.901, module version = 1.0.0
[    12.331] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    12.331] (II) Loading sub module "ramdac"
[    12.331] (II) LoadModule: "ramdac"
[    12.331] (II) Module "ramdac" already built-in
[    12.334] (II) intel(G0): Using Kernel Mode Setting driver: i915, version 1.6.0 20140905
[    12.334] (II) intel(G0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150304.88e61542-0ubuntu0sarvatt~utopic (Robert Hooker <sarvatt@ubuntu.com>)
[    12.334] (II) intel(G0): SNA compiled for use with valgrind
[    12.335] (II) intel(G1): Using Kernel Mode Setting driver: i915, version 1.6.0 20140905
[    12.335] (II) intel(G1): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150304.88e61542-0ubuntu0sarvatt~utopic (Robert Hooker <sarvatt@ubuntu.com>)
[    12.335] (II) intel(G1): SNA compiled for use with valgrind
[    12.335] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"nvidia" for depth/fbbpp 24/32
[    12.335] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    12.335] (==) NVIDIA(0): RGB weight 888
[    12.335] (==) NVIDIA(0): Default visual is TrueColor
[    12.335] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    12.336] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    12.336] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    12.336] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    12.337] (**) NVIDIA(0): Enabling 2D acceleration
[    17.042] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[    17.043] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 860M (GM107-A) at PCI:1:0:0 (GPU-0)
[    17.043] (--) NVIDIA(0): Memory: 2097152 kBytes
[    17.043] (--) NVIDIA(0): VideoBIOS: 82.07.34.00.08
[    17.044] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    17.044] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 860M at PCI:1:0:0
[    17.044] (--) NVIDIA(0):     none
[    17.044] (II) NVIDIA(0): Validated MetaModes:
[    17.044] (II) NVIDIA(0):     "NULL"
[    17.044] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    17.044] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    17.044] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    17.044] (--) intel(G0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    17.044] (--) intel(G0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[    17.044] (==) intel(G0): Depth 24, (--) framebuffer bpp 32
[    17.044] (==) intel(G0): RGB weight 888
[    17.044] (==) intel(G0): Default visual is TrueColor
[    17.044] (**) intel(G0): Option "AccelMethod" "SNA"
[    17.045] (II) intel(G0): Output eDP1 has no monitor section
[    17.045] (--) intel(G0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[    17.045] (II) intel(G0): Enabled output eDP1
[    17.045] (II) intel(G0): Output VGA1 has no monitor section
[    17.045] (II) intel(G0): Enabled output VGA1
[    17.045] (II) intel(G0): Output HDMI1 has no monitor section
[    17.045] (II) intel(G0): Enabled output HDMI1
[    17.045] (--) intel(G0): Using a maximum size of 256x256 for hardware cursors
[    17.045] (II) intel(G0): Output VIRTUAL1 has no monitor section
[    17.045] (II) intel(G0): Enabled output VIRTUAL1
[    17.045] (==) intel(G0): TearFree disabled
[    17.045] (==) intel(G0): DPI set to (96, 96)
[    17.045] (II) Loading sub module "dri2"
[    17.045] (II) LoadModule: "dri2"
[    17.046] (II) Module "dri2" already built-in
[    17.046] (II) Loading sub module "present"
[    17.046] (II) LoadModule: "present"
[    17.046] (II) Module "present" already built-in
[    19.288] (EE) intel(G1): [drm] failed to set drm interface version: Permission denied [13].
[    19.288] (II) intel(G1): [drm] Contents of '/sys/kernel/debug/dri/0/clients':
[    19.288] (II) intel(G1): [drm]              command   pid dev master a   uid      magic
[    19.288] (II) intel(G1): [drm]            plymouthd   218   0   n    y     0          0
[    19.288] (II) intel(G1): [drm]                 Xorg  1849   0   y    y     0          0
[    19.288] (II) intel(G1): [drm]                 Xorg  1849   0   n    y     0          0
[    19.288] (EE) intel(G1): Failed to claim DRM device.
[    19.288] (II) UnloadModule: "intel"
[    19.288] (--) Depth 24 pixmap format is 32 bpp
[    19.291] (II) intel(G0): SNA initialized with Haswell (gen7.5, gt2) backend
[    19.291] (==) intel(G0): Backing store enabled
[    19.291] (==) intel(G0): Silken mouse enabled
[    19.291] (II) intel(G0): HW Cursor enabled
[    19.291] (II) intel(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    19.292] (==) intel(G0): DPMS enabled
[    19.292] (==) intel(G0): Display hotplug detection enabled
[    19.292] (II) intel(G0): [DRI2] Setup complete
[    19.292] (II) intel(G0): [DRI2]   DRI driver: i965
[    19.292] (II) intel(G0): [DRI2]   VDPAU driver: va_gl
[    19.292] (II) intel(G0): direct rendering: DRI2 enabled
[    19.292] (II) intel(G0): hardware support for Present enabled
[    19.292] (WW) intel(G0): Option "AllowEmptyInitialConfiguration" is not used
[    19.292] (WW) intel(G0): Option "IgnoreDisplayDevices" is not used
[    19.292] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    19.292] (II) NVIDIA:     access.
[    19.295] (II) NVIDIA(0): Setting mode "NULL"
[    19.309] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[    19.314] (==) NVIDIA(0): Disabling shared memory pixmaps
[    19.314] (==) NVIDIA(0): Backing store enabled
[    19.314] (==) NVIDIA(0): Silken mouse enabled
[    19.314] (==) NVIDIA(0): DPMS enabled
[    19.314] (II) Loading sub module "dri2"
[    19.314] (II) LoadModule: "dri2"
[    19.314] (II) Module "dri2" already built-in
[    19.314] (II) NVIDIA(0): [DRI2] Setup complete
[    19.314] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    19.314] (--) RandR disabled
[    19.318] (II) SELinux: Disabled on system
[    19.319] (II) Initializing extension GLX
[    19.319] (II) Indirect GLX disabled.(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.552] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    19.552] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.552] (II) LoadModule: "evdev"
[    19.552] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.554] (II) Module evdev: vendor="X.Org Foundation"
[    19.554] 	compiled for 1.16.0, module version = 2.9.0
[    19.554] 	Module class: X.Org XInput Driver
[    19.554] 	ABI class: X.Org XInput driver, version 21.0
[    19.554] (II) Using input driver 'evdev' for 'Power Button'
[    19.554] (**) Power Button: always reports core events
[    19.554] (**) evdev: Power Button: Device: "/dev/input/event3"
[    19.554] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.554] (--) evdev: Power Button: Found keys
[    19.554] (II) evdev: Power Button: Configuring as keyboard
[    19.554] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    19.554] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    19.554] (**) Option "xkb_rules" "evdev"
[    19.554] (**) Option "xkb_model" "pc105"
[    19.554] (**) Option "xkb_layout" "us"
[    19.555] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    19.555] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.555] (II) Using input driver 'evdev' for 'Video Bus'
[    19.555] (**) Video Bus: always reports core events
[    19.555] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    19.555] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    19.555] (--) evdev: Video Bus: Found keys
[    19.555] (II) evdev: Video Bus: Configuring as keyboard
[    19.555] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8/event6"
[    19.555] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    19.555] (**) Option "xkb_rules" "evdev"
[    19.555] (**) Option "xkb_model" "pc105"
[    19.555] (**) Option "xkb_layout" "us"
[    19.555] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    19.555] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    19.555] (II) Using input driver 'evdev' for 'Power Button'
[    19.555] (**) Power Button: always reports core events
[    19.555] (**) evdev: Power Button: Device: "/dev/input/event0"
[    19.555] (--) evdev: Power Button: Vendor 0 Product 0x1
[    19.555] (--) evdev: Power Button: Found keys
[    19.555] (II) evdev: Power Button: Configuring as keyboard
[    19.555] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    19.555] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    19.555] (**) Option "xkb_rules" "evdev"
[    19.555] (**) Option "xkb_model" "pc105"
[    19.555] (**) Option "xkb_layout" "us"
[    19.555] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    19.555] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    19.555] (II) Using input driver 'evdev' for 'Sleep Button'
[    19.555] (**) Sleep Button: always reports core events
[    19.555] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    19.556] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    19.556] (--) evdev: Sleep Button: Found keys
[    19.556] (II) evdev: Sleep Button: Configuring as keyboard
[    19.556] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input1/event1"
[    19.556] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    19.556] (**) Option "xkb_rules" "evdev"
[    19.556] (**) Option "xkb_model" "pc105"
[    19.556] (**) Option "xkb_layout" "us"
[    19.556] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    19.556] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    19.556] (II) Using input driver 'evdev' for 'Video Bus'
[    19.556] (**) Video Bus: always reports core events
[    19.556] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    19.556] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    19.556] (--) evdev: Video Bus: Found keys
[    19.556] (II) evdev: Video Bus: Configuring as keyboard
[    19.556] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:43/LNXVIDEO:00/input/input7/event5"
[    19.556] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 10)
[    19.556] (**) Option "xkb_rules" "evdev"
[    19.556] (**) Option "xkb_model" "pc105"
[    19.556] (**) Option "xkb_layout" "us"
[    19.556] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    19.556] (II) No input driver specified, ignoring this device.
[    19.556] (II) This device may have been added with another device file.
[    19.556] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event12)
[    19.556] (II) No input driver specified, ignoring this device.
[    19.556] (II) This device may have been added with another device file.
[    19.556] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event13)
[    19.556] (II) No input driver specified, ignoring this device.
[    19.556] (II) This device may have been added with another device file.
[    19.557] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event14)
[    19.557] (II) No input driver specified, ignoring this device.
[    19.557] (II) This device may have been added with another device file.
[    19.557] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event9)
[    19.557] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[    19.557] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[    19.557] (**) Lenovo EasyCamera: always reports core events
[    19.557] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event9"
[    19.557] (--) evdev: Lenovo EasyCamera: Vendor 0x5986 Product 0x55e
[    19.557] (--) evdev: Lenovo EasyCamera: Found keys
[    19.557] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[    19.557] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/input/input10/event9"
[    19.557] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 11)
[    19.557] (**) Option "xkb_rules" "evdev"
[    19.557] (**) Option "xkb_model" "pc105"
[    19.557] (**) Option "xkb_layout" "us"
[    19.557] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    19.557] (II) No input driver specified, ignoring this device.
[    19.557] (II) This device may have been added with another device file.
[    19.557] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    19.557] (II) No input driver specified, ignoring this device.
[    19.557] (II) This device may have been added with another device file.
[    19.557] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event8)
[    19.557] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[    19.557] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[    19.557] (**) Ideapad extra buttons: always reports core events
[    19.557] (**) evdev: Ideapad extra buttons: Device: "/dev/input/event8"
[    19.557] (--) evdev: Ideapad extra buttons: Vendor 0 Product 0
[    19.557] (--) evdev: Ideapad extra buttons: Found keys
[    19.557] (II) evdev: Ideapad extra buttons: Configuring as keyboard
[    19.557] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input9/event8"
[    19.557] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 12)
[    19.557] (**) Option "xkb_rules" "evdev"
[    19.557] (**) Option "xkb_model" "pc105"
[    19.557] (**) Option "xkb_layout" "us"
[    19.558] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    19.558] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.558] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    19.558] (**) AT Translated Set 2 keyboard: always reports core events
[    19.558] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    19.558] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    19.558] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    19.558] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    19.558] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    19.558] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    19.558] (**) Option "xkb_rules" "evdev"
[    19.558] (**) Option "xkb_model" "pc105"
[    19.558] (**) Option "xkb_layout" "us"
[    19.558] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    19.558] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    19.558] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    19.558] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    19.558] (II) LoadModule: "synaptics"
[    19.558] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    19.559] (II) Module synaptics: vendor="X.Org Foundation"
[    19.559] 	compiled for 1.16.0, module version = 1.8.99
[    19.559] 	Module class: X.Org XInput Driver
[    19.559] 	ABI class: X.Org XInput driver, version 21.0
[    19.559] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    19.559] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    19.559] (**) Option "Device" "/dev/input/event7"
[    19.568] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    19.568] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5664 (res 42)
[    19.568] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4678 (res 51)
[    19.568] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    19.568] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    19.568] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    19.568] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    19.568] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    19.568] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    19.568] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    19.580] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event7"
[    19.580] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[    19.580] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    19.580] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    19.580] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[    19.580] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    19.580] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    19.580] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    19.580] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    19.580] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    19.580] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    19.580] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    19.604] (II) intel(G0): EDID vendor "SDC", prod id 18514
[    19.604] (II) intel(G0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    19.604] (II) intel(G0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    19.604] (II) intel(G0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    19.604] (II) intel(G0): Printing DDC gathered Modelines:
[    19.604] (II) intel(G0): Modeline "3840x2160"x0.0  421.55  3840 3888 3920 3956  2160 2162 2167 2220 -hsync -vsync (106.6 kHz eP)
[    19.620] reporting 4 4 22 186
[    19.645] (II) intel(G0): switch to mode 3840x2160@48.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    19.646] reporting 4 4 22 186
[    19.648] reporting 4 4 22 186
[    19.668] reporting 4 4 22 186
[    19.692] (II) intel(G0): switch to mode 3840x2160@48.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    19.696] reporting 4 4 22 186
[    19.937] reporting 4 4 22 186
[    20.036] reporting 4 4 22 186
[    20.251] reporting 4 4 22 186
[    20.293] reporting 4 4 22 186
[    20.445] reporting 4 4 22 186

```

And then after I installed nvidia-340 and after I rebooted:
```

[    18.384] 
X.Org X Server 1.16.1.901 (1.16.2 RC 1)
Release Date: 2014-11-02
[    18.384] X Protocol Version 11, Revision 0
[    18.384] Build Operating System: Linux 3.13.0-39-generic x86_64 Ubuntu
[    18.384] Current Operating System: Linux jd-laptop 3.18.3-031803-generic #201501161810 SMP Fri Jan 16 18:12:22 UTC 2015 x86_64
[    18.384] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.18.3-031803-generic root=UUID=9ba789c0-7d71-4b8e-b093-51d9db78b777 ro quiet splash
[    18.384] Build Date: 20 November 2014  09:55:19PM
[    18.384] xorg-server 2:1.16.1.901-1ubuntu1~utopic1 (For technical support please see http://www.ubuntu.com/support) 
[    18.384] Current version of pixman: 0.32.4
[    18.384] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.384] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.384] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  6 18:37:18 2015
[    18.385] (==) Using config file: "/etc/X11/xorg.conf"
[    18.385] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.387] (==) ServerLayout "layout"
[    18.387] (**) |-->Screen "nvidia" (0)
[    18.387] (**) |   |-->Monitor "<default monitor>"
[    18.387] (**) |   |-->Device "nvidia"
[    18.387] (==) No monitor specified for screen "nvidia".
	Using a default monitor configuration.
[    18.387] (**) |-->Inactive Device "intel"
[    18.387] (==) Automatically adding devices
[    18.387] (==) Automatically enabling devices
[    18.387] (==) Automatically adding GPU devices
[    18.389] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.389] 	Entry deleted from font path.
[    18.389] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.389] 	Entry deleted from font path.
[    18.389] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.389] 	Entry deleted from font path.
[    18.389] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.389] 	Entry deleted from font path.
[    18.389] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.389] 	Entry deleted from font path.
[    18.389] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    18.389] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.389] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.389] (II) Loader magic: 0x7fc316ec1d80
[    18.389] (II) Module ABI versions:
[    18.389] 	X.Org ANSI C Emulation: 0.4
[    18.389] 	X.Org Video Driver: 18.0
[    18.389] 	X.Org XInput driver : 21.0
[    18.389] 	X.Org Server Extension : 8.0
[    18.390] (II) xfree86: Adding drm device (/dev/dri/card1)
[    18.390] (II) xfree86: Adding drm device (/dev/dri/card0)
[    18.391] (--) PCI:*(0:0:2:0) 8086:0416:17aa:3978 rev 6, Mem @ 0xd1000000/4194304, 0xc0000000/268435456, I/O @ 0x00005000/64
[    18.391] (--) PCI: (0:1:0:0) 10de:1392:17aa:3978 rev 162, Mem @ 0xd0000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/524288
[    18.392] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    18.393] (II) "glx" will be loaded by default.
[    18.393] (WW) "xmir" is not to be loaded by default. Skipping.
[    18.393] (II) LoadModule: "glx"
[    18.393] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    18.486] (II) Module glx: vendor="NVIDIA Corporation"
[    18.486] 	compiled for 4.0.2, module version = 1.0.0
[    18.486] 	Module class: X.Org Server Extension
[    18.486] (II) NVIDIA GLX Module  340.76  Thu Jan 22 11:24:42 PST 2015
[    18.487] (II) LoadModule: "nvidia"
[    18.487] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    18.495] (II) Module nvidia: vendor="NVIDIA Corporation"
[    18.495] 	compiled for 4.0.2, module version = 1.0.0
[    18.495] 	Module class: X.Org Video Driver
[    18.496] (II) LoadModule: "intel"
[    18.497] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.500] (II) Module intel: vendor="X.Org Foundation"
[    18.500] 	compiled for 1.16.1.901, module version = 2.99.917
[    18.500] 	Module class: X.Org Video Driver
[    18.500] 	ABI class: X.Org Video Driver, version 18.0
[    18.500] (II) NVIDIA dlloader X Driver  340.76  Thu Jan 22 11:03:05 PST 2015
[    18.500] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    18.500] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    18.500] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    18.500] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    18.500] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    18.500] (++) using VT number 7


[    18.502] (II) Loading sub module "fb"
[    18.502] (II) LoadModule: "fb"
[    18.502] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.503] (II) Module fb: vendor="X.Org Foundation"
[    18.503] 	compiled for 1.16.1.901, module version = 1.0.0
[    18.503] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.503] (WW) Unresolved symbol: fbGetGCPrivateKey
[    18.503] (II) Loading sub module "wfb"
[    18.503] (II) LoadModule: "wfb"
[    18.503] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    18.505] (II) Module wfb: vendor="X.Org Foundation"
[    18.505] 	compiled for 1.16.1.901, module version = 1.0.0
[    18.505] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.505] (II) Loading sub module "ramdac"
[    18.505] (II) LoadModule: "ramdac"
[    18.505] (II) Module "ramdac" already built-in
[    18.508] (II) intel(G0): Using Kernel Mode Setting driver: i915, version 1.6.0 20140905
[    18.508] (II) intel(G0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150304.88e61542-0ubuntu0sarvatt~utopic (Robert Hooker <sarvatt@ubuntu.com>)
[    18.508] (II) intel(G0): SNA compiled for use with valgrind
[    18.509] (II) intel(G1): Using Kernel Mode Setting driver: i915, version 1.6.0 20140905
[    18.509] (II) intel(G1): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150304.88e61542-0ubuntu0sarvatt~utopic (Robert Hooker <sarvatt@ubuntu.com>)
[    18.509] (II) intel(G1): SNA compiled for use with valgrind
[    18.509] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"nvidia" for depth/fbbpp 24/32
[    18.509] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    18.509] (==) NVIDIA(0): RGB weight 888
[    18.509] (==) NVIDIA(0): Default visual is TrueColor
[    18.509] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    18.509] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    18.509] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    18.509] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    18.510] (**) NVIDIA(0): Enabling 2D acceleration
[    23.182] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[    23.183] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 860M (GM107-A) at PCI:1:0:0 (GPU-0)
[    23.183] (--) NVIDIA(0): Memory: 2097152 kBytes
[    23.183] (--) NVIDIA(0): VideoBIOS: 82.07.34.00.08
[    23.183] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    23.183] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 860M at PCI:1:0:0
[    23.183] (--) NVIDIA(0):     none
[    23.183] (II) NVIDIA(0): Validated MetaModes:
[    23.183] (II) NVIDIA(0):     "NULL"
[    23.183] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    23.183] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    23.183] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    23.184] (--) intel(G0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    23.184] (--) intel(G0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[    23.184] (==) intel(G0): Depth 24, (--) framebuffer bpp 32
[    23.184] (==) intel(G0): RGB weight 888
[    23.184] (==) intel(G0): Default visual is TrueColor
[    23.184] (**) intel(G0): Option "AccelMethod" "SNA"
[    23.184] (II) intel(G0): Output eDP1 has no monitor section
[    23.184] (--) intel(G0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[    23.184] (II) intel(G0): Enabled output eDP1
[    23.184] (II) intel(G0): Output VGA1 has no monitor section
[    23.184] (II) intel(G0): Enabled output VGA1
[    23.184] (II) intel(G0): Output HDMI1 has no monitor section
[    23.184] (II) intel(G0): Enabled output HDMI1
[    23.184] (--) intel(G0): Using a maximum size of 256x256 for hardware cursors
[    23.184] (II) intel(G0): Output VIRTUAL1 has no monitor section
[    23.184] (II) intel(G0): Enabled output VIRTUAL1
[    23.185] (==) intel(G0): TearFree disabled
[    23.185] (==) intel(G0): DPI set to (96, 96)
[    23.185] (II) Loading sub module "dri2"
[    23.185] (II) LoadModule: "dri2"
[    23.185] (II) Module "dri2" already built-in
[    23.185] (II) Loading sub module "present"
[    23.185] (II) LoadModule: "present"
[    23.185] (II) Module "present" already built-in
[    25.423] (EE) intel(G1): [drm] failed to set drm interface version: Permission denied [13].
[    25.423] (II) intel(G1): [drm] Contents of '/sys/kernel/debug/dri/0/clients':
[    25.423] (II) intel(G1): [drm]              command   pid dev master a   uid      magic
[    25.423] (II) intel(G1): [drm]            plymouthd   219   0   n    y     0          0
[    25.423] (II) intel(G1): [drm]                 Xorg  1694   0   y    y     0          0
[    25.423] (II) intel(G1): [drm]                 Xorg  1694   0   n    y     0          0
[    25.423] (EE) intel(G1): Failed to claim DRM device.
[    25.423] (II) UnloadModule: "intel"
[    25.423] (--) Depth 24 pixmap format is 32 bpp
[    25.426] (II) intel(G0): SNA initialized with Haswell (gen7.5, gt2) backend
[    25.426] (==) intel(G0): Backing store enabled
[    25.426] (==) intel(G0): Silken mouse enabled
[    25.427] (II) intel(G0): HW Cursor enabled
[    25.427] (II) intel(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    25.427] (==) intel(G0): DPMS enabled
[    25.427] (==) intel(G0): Display hotplug detection enabled
[    25.427] (II) intel(G0): [DRI2] Setup complete
[    25.427] (II) intel(G0): [DRI2]   DRI driver: i965
[    25.427] (II) intel(G0): [DRI2]   VDPAU driver: va_gl
[    25.427] (II) intel(G0): direct rendering: DRI2 enabled
[    25.427] (II) intel(G0): hardware support for Present enabled
[    25.427] (WW) intel(G0): Option "AllowEmptyInitialConfiguration" is not used
[    25.427] (WW) intel(G0): Option "IgnoreDisplayDevices" is not used
[    25.427] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    25.427] (II) NVIDIA:     access.
[    25.431] (II) NVIDIA(0): Setting mode "NULL"
[    25.431] (EE) NVIDIA(0): Failed to initiate mode change.
[    25.431] (EE) NVIDIA(0): Failed to complete mode change
[    25.440] (II) NVIDIA(0): Built-in logo is bigger than the screen.
[    25.445] (==) NVIDIA(0): Disabling shared memory pixmaps
[    25.445] (==) NVIDIA(0): Backing store enabled
[    25.445] (==) NVIDIA(0): Silken mouse enabled
[    25.445] (==) NVIDIA(0): DPMS enabled
[    25.446] (II) Loading sub module "dri2"
[    25.446] (II) LoadModule: "dri2"
[    25.446] (II) Module "dri2" already built-in
[    25.446] (II) NVIDIA(0): [DRI2] Setup complete
[    25.446] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    25.446] (--) RandR disabled
[    25.450] (II) SELinux: Disabled on system
[    25.450] (II) Initializing extension GLX
[    25.450] (II) Indirect GLX disabled.(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    25.684] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    25.684] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.684] (II) LoadModule: "evdev"
[    25.684] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    25.685] (II) Module evdev: vendor="X.Org Foundation"
[    25.686] 	compiled for 1.16.0, module version = 2.9.0
[    25.686] 	Module class: X.Org XInput Driver
[    25.686] 	ABI class: X.Org XInput driver, version 21.0
[    25.686] (II) Using input driver 'evdev' for 'Power Button'
[    25.686] (**) Power Button: always reports core events
[    25.686] (**) evdev: Power Button: Device: "/dev/input/event3"
[    25.686] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.686] (--) evdev: Power Button: Found keys
[    25.686] (II) evdev: Power Button: Configuring as keyboard
[    25.686] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    25.686] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    25.686] (**) Option "xkb_rules" "evdev"
[    25.686] (**) Option "xkb_model" "pc105"
[    25.686] (**) Option "xkb_layout" "us"
[    25.686] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    25.686] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.686] (II) Using input driver 'evdev' for 'Video Bus'
[    25.686] (**) Video Bus: always reports core events
[    25.686] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    25.686] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    25.686] (--) evdev: Video Bus: Found keys
[    25.686] (II) evdev: Video Bus: Configuring as keyboard
[    25.686] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8/event6"
[    25.686] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    25.686] (**) Option "xkb_rules" "evdev"
[    25.686] (**) Option "xkb_model" "pc105"
[    25.686] (**) Option "xkb_layout" "us"
[    25.686] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    25.686] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    25.686] (II) Using input driver 'evdev' for 'Power Button'
[    25.686] (**) Power Button: always reports core events
[    25.686] (**) evdev: Power Button: Device: "/dev/input/event0"
[    25.686] (--) evdev: Power Button: Vendor 0 Product 0x1
[    25.687] (--) evdev: Power Button: Found keys
[    25.687] (II) evdev: Power Button: Configuring as keyboard
[    25.687] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    25.687] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    25.687] (**) Option "xkb_rules" "evdev"
[    25.687] (**) Option "xkb_model" "pc105"
[    25.687] (**) Option "xkb_layout" "us"
[    25.687] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    25.687] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    25.687] (II) Using input driver 'evdev' for 'Sleep Button'
[    25.687] (**) Sleep Button: always reports core events
[    25.687] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    25.687] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    25.687] (--) evdev: Sleep Button: Found keys
[    25.687] (II) evdev: Sleep Button: Configuring as keyboard
[    25.687] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input1/event1"
[    25.687] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    25.687] (**) Option "xkb_rules" "evdev"
[    25.687] (**) Option "xkb_model" "pc105"
[    25.687] (**) Option "xkb_layout" "us"
[    25.687] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    25.687] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    25.687] (II) Using input driver 'evdev' for 'Video Bus'
[    25.687] (**) Video Bus: always reports core events
[    25.687] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    25.687] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    25.687] (--) evdev: Video Bus: Found keys
[    25.687] (II) evdev: Video Bus: Configuring as keyboard
[    25.687] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:43/LNXVIDEO:00/input/input7/event5"
[    25.687] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 10)
[    25.687] (**) Option "xkb_rules" "evdev"
[    25.687] (**) Option "xkb_model" "pc105"
[    25.687] (**) Option "xkb_layout" "us"
[    25.687] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    25.687] (II) No input driver specified, ignoring this device.
[    25.687] (II) This device may have been added with another device file.
[    25.688] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event9)
[    25.688] (II) No input driver specified, ignoring this device.
[    25.688] (II) This device may have been added with another device file.
[    25.688] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event10)
[    25.688] (II) No input driver specified, ignoring this device.
[    25.688] (II) This device may have been added with another device file.
[    25.688] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event11)
[    25.688] (II) No input driver specified, ignoring this device.
[    25.688] (II) This device may have been added with another device file.
[    25.688] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event14)
[    25.688] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[    25.688] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[    25.688] (**) Lenovo EasyCamera: always reports core events
[    25.688] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event14"
[    25.688] (--) evdev: Lenovo EasyCamera: Vendor 0x5986 Product 0x55e
[    25.688] (--) evdev: Lenovo EasyCamera: Found keys
[    25.688] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[    25.688] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/input/input15/event14"
[    25.688] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 11)
[    25.688] (**) Option "xkb_rules" "evdev"
[    25.688] (**) Option "xkb_model" "pc105"
[    25.688] (**) Option "xkb_layout" "us"
[    25.688] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event12)
[    25.688] (II) No input driver specified, ignoring this device.
[    25.688] (II) This device may have been added with another device file.
[    25.688] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event13)
[    25.688] (II) No input driver specified, ignoring this device.
[    25.688] (II) This device may have been added with another device file.
[    25.689] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event8)
[    25.689] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[    25.689] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[    25.689] (**) Ideapad extra buttons: always reports core events
[    25.689] (**) evdev: Ideapad extra buttons: Device: "/dev/input/event8"
[    25.689] (--) evdev: Ideapad extra buttons: Vendor 0 Product 0
[    25.689] (--) evdev: Ideapad extra buttons: Found keys
[    25.689] (II) evdev: Ideapad extra buttons: Configuring as keyboard
[    25.689] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input9/event8"
[    25.689] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 12)
[    25.689] (**) Option "xkb_rules" "evdev"
[    25.689] (**) Option "xkb_model" "pc105"
[    25.689] (**) Option "xkb_layout" "us"
[    25.689] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    25.689] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    25.689] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    25.689] (**) AT Translated Set 2 keyboard: always reports core events
[    25.689] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    25.689] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    25.689] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    25.689] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    25.689] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    25.689] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    25.689] (**) Option "xkb_rules" "evdev"
[    25.689] (**) Option "xkb_model" "pc105"
[    25.689] (**) Option "xkb_layout" "us"
[    25.689] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    25.689] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    25.689] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    25.689] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    25.689] (II) LoadModule: "synaptics"
[    25.689] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    25.690] (II) Module synaptics: vendor="X.Org Foundation"
[    25.690] 	compiled for 1.16.0, module version = 1.8.99
[    25.690] 	Module class: X.Org XInput Driver
[    25.690] 	ABI class: X.Org XInput driver, version 21.0
[    25.690] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    25.690] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.690] (**) Option "Device" "/dev/input/event7"
[    25.712] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    25.712] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5664 (res 42)
[    25.712] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4678 (res 51)
[    25.712] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    25.712] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    25.712] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    25.712] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    25.712] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    25.712] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    25.712] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    25.728] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event7"
[    25.728] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[    25.728] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    25.728] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    25.728] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[    25.728] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    25.728] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    25.728] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    25.728] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    25.728] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    25.728] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    25.728] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    25.754] (II) intel(G0): EDID vendor "SDC", prod id 18514
[    25.754] (II) intel(G0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    25.754] (II) intel(G0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    25.754] (II) intel(G0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    25.754] (II) intel(G0): Printing DDC gathered Modelines:
[    25.754] (II) intel(G0): Modeline "3840x2160"x0.0  421.55  3840 3888 3920 3956  2160 2162 2167 2220 -hsync -vsync (106.6 kHz eP)
[    25.768] reporting 4 4 22 186
[    25.787] (II) intel(G0): switch to mode 3840x2160@48.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    25.789] reporting 4 4 22 186
[    25.790] reporting 4 4 22 186
[    25.807] reporting 4 4 22 186
[    25.826] (II) intel(G0): switch to mode 3840x2160@48.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    25.830] reporting 4 4 22 186
[    26.068] reporting 4 4 22 186
[    26.196] reporting 4 4 22 186
[    26.409] reporting 4 4 22 186
[    26.452] reporting 4 4 22 186
[    26.593] reporting 4 4 22 186

```

So that happened. Good times.

---

### Post by Bashing-om on 2015-03-06
JDAIII ; Yeah !

Looks to me like the driver module did build on both that last 346 attempt and as well it built with the 340. Looks good !
What results when you start 'nvidia-setings' ? can you switch graphics sets ?
```

sudo lshw -C display

```


[INDENT][INDENT]maybe YES
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-03-06
JDAIII ; Hey;

My eyes are crossing, and my mind is blurring out ! Calling it a night for this session .
Will pick this back up in my AM and see what the progress/prognosis is .

[INDENT][INDENT]so far so good
[/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-06
Thanks for the help. Honestly I'm a couple glasses deep with a Drouthy Neebor. 

So I went ahead and installed nvidia-346 and before I rebooted, I opened nvidia-settings and set it to intel and rebooted. It worked. I can now reboot with drivers installed. The machine is still using the intel drivers, but this is interesting. I'm including a few things to this email so let me know what you think.

```

 &#10140; cat /var/log/Xorg.0.log                                                   ~ 
[    21.383] 
X.Org X Server 1.16.1.901 (1.16.2 RC 1)
Release Date: 2014-11-02
[    21.384] X Protocol Version 11, Revision 0
[    21.384] Build Operating System: Linux 3.13.0-39-generic x86_64 Ubuntu
[    21.384] Current Operating System: Linux jd-laptop 3.18.3-031803-generic #201501161810 SMP Fri Jan 16 18:12:22 UTC 2015 x86_64
[    21.384] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.18.3-031803-generic root=UUID=9ba789c0-7d71-4b8e-b093-51d9db78b777 ro quiet splash
[    21.384] Build Date: 20 November 2014  09:55:19PM
[    21.384] xorg-server 2:1.16.1.901-1ubuntu1~utopic1 (For technical support please see http://www.ubuntu.com/support) 
[    21.384] Current version of pixman: 0.32.4
[    21.384]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[    21.384] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.384] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  6 19:57:11 2015
[    21.385] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.386] (==) No Layout section.  Using the first Screen section.
[    21.386] (==) No screen section available. Using defaults.
[    21.386] (**) |-->Screen "Default Screen Section" (0)
[    21.386] (**) |   |-->Monitor "<default monitor>"
[    21.386] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    21.386] (==) Automatically adding devices
[    21.387] (==) Automatically enabling devices
[    21.387] (==) Automatically adding GPU devices
[    21.388] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.388]    Entry deleted from font path.
[    21.388] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.388]    Entry deleted from font path.
[    21.388] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.388]    Entry deleted from font path.
[    21.388] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.388]    Entry deleted from font path.
[    21.388] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.388]    Entry deleted from font path.
[    21.388] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[    21.388] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.388] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.389] (II) Loader magic: 0x7f7d14e25d80
[    21.389] (II) Module ABI versions:
[    21.389]    X.Org ANSI C Emulation: 0.4
[    21.389]    X.Org Video Driver: 18.0
[    21.389]    X.Org XInput driver : 21.0
[    21.389]    X.Org Server Extension : 8.0
[    21.389] (II) xfree86: Adding drm device (/dev/dri/card0)
[    21.390] (--) PCI:*(0:0:2:0) 8086:0416:17aa:3978 rev 6, Mem @ 0xd1000000/4194304, 0xc0000000/268435456, I/O @ 0x00005000/64
[    21.390] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    21.390] (II) "glx" will be loaded by default.
[    21.390] (WW) "xmir" is not to be loaded by default. Skipping.
[    21.390] (II) LoadModule: "glx"
[    21.390] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    21.397] (II) Module glx: vendor="X.Org Foundation"
[    21.397]    compiled for 1.16.1.901, module version = 1.0.0
[    21.397]    ABI class: X.Org Server Extension, version 8.0
[    21.397] (==) AIGLX enabled
[    21.397] (==) Matched intel as autoconfigured driver 0
[    21.397] (==) Matched intel as autoconfigured driver 1
[    21.397] (==) Matched modesetting as autoconfigured driver 2
[    21.397] (==) Matched fbdev as autoconfigured driver 3
[    21.397] (==) Matched vesa as autoconfigured driver 4
[    21.397] (==) Assigned the driver to the xf86ConfigLayout
[    21.397] (II) LoadModule: "intel"
[    21.398] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    21.401] (II) Module intel: vendor="X.Org Foundation"
[    21.401]    compiled for 1.16.1.901, module version = 2.99.917
[    21.401]    Module class: X.Org Video Driver
[    21.401]    ABI class: X.Org Video Driver, version 18.0
[    21.401] (II) LoadModule: "modesetting"
[    21.401] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    21.401] (II) Module modesetting: vendor="X.Org Foundation"
[    21.401]    compiled for 1.16.0, module version = 0.9.0
[    21.401]    Module class: X.Org Video Driver
[    21.401]    ABI class: X.Org Video Driver, version 18.0
[    21.401] (II) LoadModule: "fbdev"
[    21.401] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    21.402] (II) Module fbdev: vendor="X.Org Foundation"
[    21.402]    compiled for 1.16.0, module version = 0.4.4
[    21.402]    Module class: X.Org Video Driver
[    21.402]    ABI class: X.Org Video Driver, version 18.0
[    21.402] (II) LoadModule: "vesa"
[    21.402] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    21.402] (II) Module vesa: vendor="X.Org Foundation"
[    21.402]    compiled for 1.16.0, module version = 2.3.3
[    21.402]    Module class: X.Org Video Driver
[    21.402]    ABI class: X.Org Video Driver, version 18.0
[    21.402] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    21.403] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    21.403] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    21.403] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    21.403] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    21.403] (II) FBDEV: driver for framebuffer: fbdev
[    21.403] (II) VESA: driver for VESA chipsets: vesa
[    21.403] (++) using VT number 7
[    21.404] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20140905
[    21.404] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20150304.88e61542-0ubuntu0sarvatt~utopic (Robert Hooker <sarvatt@ubuntu.com>)
[    21.404] (II) intel(0): SNA compiled for use with valgrind
[    21.405] (WW) Falling back to old probe method for modesetting
[    21.405] (WW) Falling back to old probe method for fbdev
[    21.405] (II) Loading sub module "fbdevhw"
[    21.405] (II) LoadModule: "fbdevhw"
[    21.405] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    21.405] (II) Module fbdevhw: vendor="X.Org Foundation"
[    21.405]    compiled for 1.16.1.901, module version = 0.0.2
[    21.405]    ABI class: X.Org Video Driver, version 18.0
[    21.405] (WW) Falling back to old probe method for vesa
[    21.406] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    21.406] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2; using a maximum of 4 threads
[    21.406] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    21.406] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    21.406] (==) intel(0): RGB weight 888
[    21.406] (==) intel(0): Default visual is TrueColor
[    21.406] (II) intel(0): Output eDP1 has no monitor section
[    21.406] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1
[    21.406] (II) intel(0): Enabled output eDP1
[    21.406] (II) intel(0): Output VGA1 has no monitor section
[    21.406] (II) intel(0): Enabled output VGA1
[    21.406] (II) intel(0): Output HDMI1 has no monitor section
[    21.406] (II) intel(0): Enabled output HDMI1
[    21.406] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[    21.406] (II) intel(0): Output VIRTUAL1 has no monitor section
[    21.406] (II) intel(0): Enabled output VIRTUAL1
[    21.406] (--) intel(0): Output eDP1 using initial mode 3840x2160 on pipe 0
[    21.407] (==) intel(0): TearFree disabled
[    21.407] (==) intel(0): DPI set to (96, 96)
[    21.407] (II) Loading sub module "dri2"
[    21.407] (II) LoadModule: "dri2"
[    21.407] (II) Module "dri2" already built-in
[    21.407] (II) Loading sub module "present"
[    21.407] (II) LoadModule: "present"
[    21.407] (II) Module "present" already built-in
[    21.407] (II) UnloadModule: "modesetting"
[    21.407] (II) Unloading modesetting
[    21.407] (II) UnloadModule: "fbdev"
[    21.407] (II) Unloading fbdev
[    21.407] (II) UnloadSubModule: "fbdevhw"
[    21.407] (II) Unloading fbdevhw
[    21.407] (II) UnloadModule: "vesa"
[    21.407] (II) Unloading vesa
[    21.407] (==) Depth 24 pixmap format is 32 bpp
[    21.410] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[    21.410] (==) intel(0): Backing store enabled
[    21.410] (==) intel(0): Silken mouse enabled
[    21.410] (II) intel(0): HW Cursor enabled
[    21.410] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    21.411] (==) intel(0): DPMS enabled
[    21.411] (==) intel(0): Display hotplug detection enabled
[    21.411] (II) intel(0): [DRI2] Setup complete
[    21.411] (II) intel(0): [DRI2]   DRI driver: i965
[    21.411] (II) intel(0): [DRI2]   VDPAU driver: va_gl
[    21.411] (II) intel(0): direct rendering: DRI2 enabled
[    21.411] (II) intel(0): hardware support for Present enabled
[    21.411] (--) RandR disabled
[    21.417] (II) SELinux: Disabled on system
[    21.456] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    21.456] (II) AIGLX: enabled GLX_ARB_create_context
[    21.456] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    21.456] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    21.456] (II) AIGLX: enabled GLX_INTEL_swap_event
[    21.456] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    21.456] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    21.456] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    21.456] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    21.457] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[    21.457] (II) AIGLX: Loaded and initialized i965
[    21.457] (II) GLX: Initialized DRI2 GL provider for screen 0
[    21.467] (II) intel(0): switch to mode 3840x2160@48.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    21.467] (II) intel(0): Setting screen physical size to 1016 x 571
[    21.479] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    21.482] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    21.482] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.482] (II) LoadModule: "evdev"
[    21.482] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    21.484] (II) Module evdev: vendor="X.Org Foundation"
[    21.484]    compiled for 1.16.0, module version = 2.9.0
[    21.484]    Module class: X.Org XInput Driver
[    21.484]    ABI class: X.Org XInput driver, version 21.0
[    21.484] (II) Using input driver 'evdev' for 'Power Button'
[    21.484] (**) Power Button: always reports core events
[    21.484] (**) evdev: Power Button: Device: "/dev/input/event3"
[    21.485] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.485] (--) evdev: Power Button: Found keys
[    21.485] (II) evdev: Power Button: Configuring as keyboard
[    21.485] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    21.485] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    21.485] (**) Option "xkb_rules" "evdev"
[    21.485] (**) Option "xkb_model" "pc105"
[    21.485] (**) Option "xkb_layout" "us"
[    21.485] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    21.485] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    21.485] (II) Using input driver 'evdev' for 'Video Bus'
[    21.485] (**) Video Bus: always reports core events
[    21.485] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    21.485] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    21.485] (--) evdev: Video Bus: Found keys
[    21.485] (II) evdev: Video Bus: Configuring as keyboard
[    21.485] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input8/event6"
[    21.485] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    21.485] (**) Option "xkb_rules" "evdev"
[    21.485] (**) Option "xkb_model" "pc105"
[    21.485] (**) Option "xkb_layout" "us"
[    21.486] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    21.486] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    21.486] (II) Using input driver 'evdev' for 'Power Button'
[    21.486] (**) Power Button: always reports core events
[    21.486] (**) evdev: Power Button: Device: "/dev/input/event0"
[    21.486] (--) evdev: Power Button: Vendor 0 Product 0x1
[    21.486] (--) evdev: Power Button: Found keys
[    21.486] (II) evdev: Power Button: Configuring as keyboard
[    21.486] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    21.486] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    21.486] (**) Option "xkb_rules" "evdev"
[    21.486] (**) Option "xkb_model" "pc105"
[    21.486] (**) Option "xkb_layout" "us"
[    21.486] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    21.486] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    21.486] (II) Using input driver 'evdev' for 'Sleep Button'
[    21.486] (**) Sleep Button: always reports core events
[    21.486] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    21.486] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    21.486] (--) evdev: Sleep Button: Found keys
[    21.486] (II) evdev: Sleep Button: Configuring as keyboard
[    21.486] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input1/event1"
[    21.486] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    21.486] (**) Option "xkb_rules" "evdev"
[    21.486] (**) Option "xkb_model" "pc105"
[    21.486] (**) Option "xkb_layout" "us"
[    21.487] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    21.487] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    21.487] (II) Using input driver 'evdev' for 'Video Bus'
[    21.487] (**) Video Bus: always reports core events
[    21.487] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    21.487] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    21.487] (--) evdev: Video Bus: Found keys
[    21.487] (II) evdev: Video Bus: Configuring as keyboard
[    21.487] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:43/LNXVIDEO:00/input/input7/event5"
[    21.487] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 10)
[    21.487] (**) Option "xkb_rules" "evdev"
[    21.487] (**) Option "xkb_model" "pc105"
[    21.487] (**) Option "xkb_layout" "us"
[    21.487] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    21.487] (II) No input driver specified, ignoring this device.
[    21.487] (II) This device may have been added with another device file.
[    21.487] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event9)
[    21.487] (II) No input driver specified, ignoring this device.
[    21.487] (II) This device may have been added with another device file.
[    21.487] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event10)
[    21.488] (II) No input driver specified, ignoring this device.
[    21.488] (II) This device may have been added with another device file.
[    21.488] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event11)
[    21.488] (II) No input driver specified, ignoring this device.
[    21.488] (II) This device may have been added with another device file.
[    21.488] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event14)
[    21.488] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[    21.488] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[    21.488] (**) Lenovo EasyCamera: always reports core events
[    21.488] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event14"
[    21.488] (--) evdev: Lenovo EasyCamera: Vendor 0x5986 Product 0x55e
[    21.488] (--) evdev: Lenovo EasyCamera: Found keys
[    21.488] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[    21.488] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/input/input15/event14"
[    21.488] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 11)
[    21.488] (**) Option "xkb_rules" "evdev"
[    21.488] (**) Option "xkb_model" "pc105"
[    21.488] (**) Option "xkb_layout" "us"
[    21.488] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event12)
[    21.488] (II) No input driver specified, ignoring this device.
[    21.488] (II) This device may have been added with another device file.
[    21.489] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event13)
[    21.489] (II) No input driver specified, ignoring this device.
[    21.489] (II) This device may have been added with another device file.
[    21.489] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event8)
[    21.489] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[    21.489] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[    21.489] (**) Ideapad extra buttons: always reports core events
[    21.489] (**) evdev: Ideapad extra buttons: Device: "/dev/input/event8"
[    21.489] (--) evdev: Ideapad extra buttons: Vendor 0 Product 0
[    21.489] (--) evdev: Ideapad extra buttons: Found keys
[    21.489] (II) evdev: Ideapad extra buttons: Configuring as keyboard
[    21.489] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1f.0/PNP0C09:00/VPC2004:00/input/input9/event8"
[    21.489] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 12)
[    21.489] (**) Option "xkb_rules" "evdev"
[    21.489] (**) Option "xkb_model" "pc105"
[    21.489] (**) Option "xkb_layout" "us"
[    21.489] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    21.489] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    21.489] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    21.489] (**) AT Translated Set 2 keyboard: always reports core events
[    21.489] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    21.489] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    21.489] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    21.489] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    21.489] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    21.489] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[    21.490] (**) Option "xkb_rules" "evdev"
[    21.490] (**) Option "xkb_model" "pc105"
[    21.490] (**) Option "xkb_layout" "us"
[    21.490] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    21.490] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    21.490] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    21.490] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    21.490] (II) LoadModule: "synaptics"
[    21.490] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    21.491] (II) Module synaptics: vendor="X.Org Foundation"
[    21.491]    compiled for 1.16.0, module version = 1.8.99
[    21.491]    Module class: X.Org XInput Driver
[    21.491]    ABI class: X.Org XInput driver, version 21.0
[    21.491] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    21.491] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    21.491] (**) Option "Device" "/dev/input/event7"
[    21.504] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    21.504] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5664 (res 42)
[    21.504] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4678 (res 51)
[    21.504] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    21.504] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    21.504] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    21.504] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    21.504] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    21.504] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    21.504] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    21.524] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event7"
[    21.524] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[    21.524] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    21.524] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    21.524] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.038
[    21.524] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    21.524] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    21.524] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    21.524] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    21.524] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    21.524] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    21.524] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    22.130] (II) intel(0): EDID vendor "SDC", prod id 18514
[    22.130] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x0 mode
[    22.130] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1107 mode
[    22.130] (II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 0x1100 mode
[    22.130] (II) intel(0): Printing DDC gathered Modelines:
[    22.130] (II) intel(0): Modeline "3840x2160"x0.0  421.55  3840 3888 3920 3956  2160 2162 2167 2220 -hsync -vsync (106.6 kHz eP)
[    22.986] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    24.052] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    75.445] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    76.076] (II) intel(0): resizing framebuffer to 1920x1080
[    76.078] (II) intel(0): switch to mode 1920x1080@59.9 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    77.326] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[    77.994] (II) XKB: reuse xkmfile /var/lib/xkb/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm



```


With the intel drivers enabled.
```

 &#10140; sudo lshw -C display                                                      ~ 
  *-display               
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:31 memory:d1000000-d13fffff memory:c0000000-cfffffff ioport:5000(size=64)

```


I switched it to nvidia, logged out and back in. black screen. In the morning, I will do as I did before but actually remember to lshw this time. I blame the drouthy neebor for making me forget to do that.

---

### Post by Bashing-om on 2015-03-07
JDAIII; Welp;

A night's sleep, and I still can not fathom what is taking place.
From that last Xorg file, one can readily see that the Nvidia chip set is not seen by the system ( bios does not pass that info on ) when only Intel is enabled.

So we still have :
> 
I switched it to nvidia, logged out and back in. black screen.

However, all looks good to me, booting the 3.18 kernel with utopic's xorg-server:
> 
21.384] xorg-server 2:1.16.1.901-1ubuntu1~utopic1

I have to wonder if that is a problem in that vivid's xorg-server should be used here ?? I just do not know (yet) .
What do we have to point us in the right direction to 'see' what is going on ?
Do we have:
```

ls -al ~/.nvidia-settings-rc
ls -al /var/lib/dkms/nvidia/
ls -al / /etc/X11/Xorg.conf
ls -al  /lib/modules/`uname -r`/kernel/drivers/video/nvidia.ko##note those are "`" backticks##

```
think maybe this ( nvidia.ko) is the crux of the matter.
> 
A kernel module (/lib/modules/`uname -r`/kernel/drivers/video/nvidia.ko); this kernel module provides low-level access to your NVIDIA hardware for all of the above components. It is generally loaded into the kernel when the X server is started, and is used by the X driver and OpenGL. nvidia.ko consists of two pieces: the binary-only core, and a kernel interface that must be compiled specifically for your kernel version. Note that the Linux kernel does not have a consistent binary interface like the X server, so it is important that this kernel interface be matched with the version of the kernel that you are using. This can either be accomplished by compiling yourself, or using precompiled binaries provided for the kernels shipped with some of the more common Linux distributions.

--------------------------------
Again, I have to wonder what happens when booting the 3.16 (utopic) kernel with both chip sets enabled . As I have never worked with an out-of-release kernel before, I do not know what to expect.

Looking to find where in the process the failure occurs ->
[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-09
Hello There,

Sorry for the lack of reply over the weekend. I left power adapter and my door code wasn't working this weekend so no power for my laptop. 

Anyway, I installed nvidia-346 and ran a few tests for your previous request. I see that the file you mentioned for the kernel does not exist. See last bit of code. I'm going to install nvidia-346 as needed for testing, but I'll need to uninstall it as I need to restart my machine throughout the day.

```
 &#10140; cat ~/.nvidia-settings-rc                                                 ~ #
# /home/jd/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Fri Mar  6 20:06:30 2015
#


# ConfigProperties:


RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
UpdateRulesOnProfileNameChange = Yes


# Attributes:
```


```
&#10140; ls -al /var/lib/dkms/nvidia/                                              ~ 
ls: cannot access /var/lib/dkms/nvidia/: No such file or directory

 &#10140; ls -al /var/lib/dkms/nvidia-346                                           ~ 
total 12
drwxr-xr-x 3 root root 4096 Mar  9 08:18 .
drwxr-xr-x 5 root root 4096 Mar  9 08:18 ..
drwxr-xr-x 4 root root 4096 Mar  9 08:18 346.47
lrwxrwxrwx 1 root root   35 Mar  9 08:18 kernel-3.18.3-031803-generic-x86_64 -> 346.47/3.18.3-031803-generic/x86_64



```

```
&#10140; ls -al / /etc/X11/Xorg.conf                                               ~ ls: cannot access /etc/X11/Xorg.conf: No such file or directory
/:
total 108
drwxr-xr-x  24 root root  4096 Mar  9 08:18 .
drwxr-xr-x  24 root root  4096 Mar  9 08:18 ..
drwxr-xr-x   2 root root  4096 Feb 27 11:21 bin
drwxr-xr-x   3 root root  4096 Mar  9 08:18 boot
drwxrwxr-x   2 root root  4096 Jan  6 19:46 cdrom
drwxr-xr-x  18 root root  4300 Mar  9 08:04 dev
drwxr-xr-x 157 root root 12288 Mar  9 08:18 etc
drwxr-xr-x   4 root root  4096 Jan  6 19:48 home
lrwxrwxrwx   1 root root    37 Mar  6 14:51 initrd.img -> boot/initrd.img-3.18.3-031803-generic
lrwxrwxrwx   1 root root    33 Mar  2 08:18 initrd.img.old -> boot/initrd.img-3.16.0-31-generic
drwxr-xr-x  29 root root  4096 Mar  9 08:18 lib
drwxr-xr-x   2 root root  4096 Mar  9 08:18 lib32
drwxr-xr-x   2 root root  4096 Mar  2 08:18 lib64
drwx------   2 root root 16384 Jan  6 19:42 lost+found
drwxr-xr-x  10 root root  4096 Jan 16 14:12 media
drwxr-xr-x   2 root root  4096 Apr 10  2014 mnt
drwxr-xr-x  10 root root  4096 Mar  7 08:04 opt
dr-xr-xr-x 285 root root     0 Mar  9 08:04 proc
drwx------  12 root root  4096 Mar  4 14:52 root
drwxr-xr-x  28 root root   920 Mar  9 08:09 run
drwxr-xr-x   2 root root 12288 Mar  9 08:18 sbin
drwxr-xr-x   2 root root  4096 Jul 22  2014 srv
dr-xr-xr-x  13 root root     0 Mar  9 08:16 sys
drwxrwxrwt  10 root root  4096 Mar  9 08:19 tmp
drwxr-xr-x  11 root root  4096 Mar  9 08:18 usr
drwxr-xr-x  13 root root  4096 Jul 22  2014 var
lrwxrwxrwx   1 root root    34 Mar  6 14:51 vmlinuz -> boot/vmlinuz-3.18.3-031803-generic
lrwxrwxrwx   1 root root    30 Mar  2 08:18 vmlinuz.old -> boot/vmlinuz-3.16.0-31-generic



```

```
 &#10140; ls -al  /lib/modules/`uname -r`/kernel/drivers/video/nvidia.ko            ~ 
ls: cannot access /lib/modules/3.18.3-031803-generic/kernel/drivers/video/nvidia.ko: No such file or directory


 &#10140; ls -al  /lib/modules/`uname -r`/kernel/drivers/video/                ~ 
total 36
drwxr-xr-x  4 root root  4096 Mar  6 14:51 .
drwxr-xr-x 81 root root  4096 Mar  6 14:51 ..
drwxr-xr-x  2 root root  4096 Mar  6 14:51 backlight
drwxr-xr-x 14 root root  4096 Mar  6 14:51 fbdev
-rw-r--r--  1 root root 16652 Jan 16 10:23 vgastate.ko

```

---

### Post by Bashing-om on 2015-03-09
JDAIII; Well !

Disconcerting to say the least that files I consider crucial do not exist .
Further:
my output on a minimal system ->
```

sysop@1404mini:~$ ls -al  /lib/modules/`uname -r`/kernel/drivers/video/
total 1132
drwxr-xr-x 14 root root  4096 Mar  3 10:12 .
drwxr-xr-x 77 root root  4096 Feb 25 11:13 ..
-rw-r--r--  1 root root 20788 Mar  2 13:18 arcfb.ko
-rw-r--r--  1 root root 41156 Mar  2 13:18 arkfb.ko
drwxr-xr-x  2 root root  4096 Mar  3 10:12 aty
-rw-r--r--  1 root root  9324 Mar  2 13:18 auo_k1900fb.ko
-rw-r--r--  1 root root  9572 Mar  2 13:18 auo_k1901fb.ko
-rw-r--r--  1 root root 35244 Mar  2 13:18 auo_k190x.ko
drwxr-xr-x  2 root root  4096 Mar  3 10:12 backlight
-rw-r--r--  1 root root 21732 Mar  2 13:18 broadsheetfb.ko
-rw-r--r--  1 root root 18020 Mar  2 13:18 carminefb.ko
-rw-r--r--  1 root root 55436 Mar  2 13:25 cirrusfb.ko
-rw-r--r--  1 root root 26196 Mar  2 13:18 cyber2000fb.ko
-rw-r--r--  1 root root  6292 Mar  2 13:18 fb_ddc.ko
-rw-r--r--  1 root root  5692 Mar  2 13:25 fb_sys_fops.ko
-rw-r--r--  1 root root 13068 Mar  2 13:18 goldfishfb.ko
-rw-r--r--  1 root root 11388 Mar  2 13:18 hecubafb.ko
-rw-r--r--  1 root root 18788 Mar  2 13:18 hgafb.ko
-rw-r--r--  1 root root 23132 Mar  2 13:18 hyperv_fb.ko
-rw-r--r--  1 root root 31788 Mar  2 13:18 i740fb.ko
drwxr-xr-x  2 root root  4096 Mar  3 10:12 intelfb
drwxr-xr-x  2 root root  4096 Mar  3 10:12 kyro
-rw-r--r--  1 root root  9492 Mar  2 13:18 macmodes.ko
drwxr-xr-x  2 root root  4096 Mar  3 10:12 matrox
drwxr-xr-x  2 root root  4096 Mar  3 10:12 mb862xx
-rw-r--r--  1 root root 14884 Mar  2 13:18 metronomefb.ko
-rw-r--r--  1 root root 10092 Mar  2 13:18 n411.ko
-rw-r--r--  1 root root 33428 Mar  2 13:18 neofb.ko
drwxr-xr-x  2 root root  4096 Mar  3 10:12 nvidia
-rw-r--r--  1 root root  9252 Mar  2 13:25 output.ko
-rw-r--r--  1 root root 28060 Mar  2 13:18 pm2fb.ko
-rw-r--r--  1 root root 25684 Mar  2 13:18 pm3fb.ko
drwxr-xr-x  2 root root  4096 Mar  3 10:12 riva
-rw-r--r--  1 root root 18148 Mar  2 13:18 s1d13xxxfb.ko
-rw-r--r--  1 root root 56340 Mar  2 13:18 s3fb.ko
drwxr-xr-x  2 root root  4096 Mar  3 10:12 savage
drwxr-xr-x  2 root root  4096 Mar  3 10:12 sis
-rw-r--r--  1 root root 41556 Mar  2 13:18 sm501fb.ko
-rw-r--r--  1 root root 56580 Mar  2 13:18 smscufx.ko
-rw-r--r--  1 root root 30412 Mar  2 13:18 sstfb.ko
-rw-r--r--  1 root root 26812 Mar  2 13:18 svgalib.ko
-rw-r--r--  1 root root  7244 Mar  2 13:25 syscopyarea.ko
-rw-r--r--  1 root root  9452 Mar  2 13:25 sysfillrect.ko
-rw-r--r--  1 root root  6276 Mar  2 13:25 sysimgblt.ko
-rw-r--r--  1 root root 32956 Mar  2 13:18 tdfxfb.ko
-rw-r--r--  1 root root 17996 Mar  2 13:18 tmiofb.ko
-rw-r--r--  1 root root 32596 Mar  2 13:18 tridentfb.ko
-rw-r--r--  1 root root 41116 Mar  2 13:18 udlfb.ko
-rw-r--r--  1 root root 49708 Mar  2 13:18 uvesafb.ko
drwxr-xr-x  2 root root  4096 Mar  3 10:12 vermilion
-rw-r--r--  1 root root 28228 Mar  2 13:25 vga16fb.ko
-rw-r--r--  1 root root 15828 Mar  2 13:25 vgastate.ko
drwxr-xr-x  2 root root  4096 Mar  3 10:12 via
-rw-r--r--  1 root root 39316 Mar  2 13:18 vt8623fb.ko
-rw-r--r--  1 root root 21948 Mar  2 13:25 xen-fbfront.ko
sysop@1404mini:~$ 

```

What is going on that your system does not provide many of these XXX.ko files ; That your list is so so sparse ??

Let's see if the system holds any answers, do we have any logs we can consult ?:
```

ls -al /var/lib/dkms/

```
Maybe the build process is changed; do you have this file " nvidiafb.ko "?
```

 ls -al  /lib/modules/`uname -r`/kernel/drivers/video/nvidia/

``` 
in the meantime I do some home work and see if " /var/lib/dkms/nvidia/ " is no longer  applicable in a hybrid graphics situation.

Maybe time to open a thread with Nvida, and get some expert advise ?
Most interesting that the module build process is failing, the puzzle is to find out the why .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-09
I think that I am going to open a ticket with nvidia. We will see how their linux support rates.

```
 &#10140; ls -al /var/lib/dkms/                                                     ~ total 24
drwxr-xr-x  5 root root 4096 Mar  9 13:36 .
drwxr-xr-x 73 root root 4096 Mar  6 13:33 ..
drwxr-xr-x  3 root root 4096 Mar  9 08:18 bbswitch
-rw-r--r--  1 root root    6 Jul  8  2008 dkms_dbversion
drwxr-xr-x  3 root root 4096 Mar  9 13:36 nvidia-346
drwxr-xr-x  3 root root 4096 Mar  6 14:51 virtualbox
 &#10140; ls -al /var/lib/dkms/nvidia-346                                           ~ 
total 12
drwxr-xr-x 3 root root 4096 Mar  9 13:36 .
drwxr-xr-x 5 root root 4096 Mar  9 13:36 ..
drwxr-xr-x 4 root root 4096 Mar  9 13:36 346.47
lrwxrwxrwx 1 root root   35 Mar  9 13:36 kernel-3.18.3-031803-generic-x86_64 -> 346.47/3.18.3-031803-generic/x86_64






 &#10140;  ls -al  /lib/modules/`uname -r`/kernel/drivers/video/nvidia/             ~ 
ls: cannot access /lib/modules/3.18.3-031803-generic/kernel/drivers/video/nvidia/: No such file or directory
 &#10140;  ls -al  /lib/modules/`uname -r`/kernel/drivers/video/                    ~ 
total 36
drwxr-xr-x  4 root root  4096 Mar  6 14:51 .
drwxr-xr-x 81 root root  4096 Mar  6 14:51 ..
drwxr-xr-x  2 root root  4096 Mar  6 14:51 backlight
drwxr-xr-x 14 root root  4096 Mar  6 14:51 fbdev
-rw-r--r--  1 root root 16652 Jan 16 10:23 vgastate.ko



```

---

### Post by Bashing-om on 2015-03-09
JDAIII; OK;

Nvidia, from what I have seen, is very responsive and supportive of linux/ubuntu .
IF you do open a ticket with Nvidia, please so advise, I so want to be a part of this for my own stepping up on the learning curve.
In the meantime, I am still going to see what I can find out about why those files do not exist !


[INDENT][INDENT]in that process of learning
[/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-09
I posted my issue to nvidia support. Had limited space so I tried my best. I also noticed that the link I gave them to this thread didn't go through. I guess that they do not allow external links to be sent to their support:

```
[FONT=arial]I am trying to configure my lenovo y50 Laptop with 4K display running UbuntuGnome 14.10 to use the nvidia card in my laptop instead of the built in intel chip. I have installed the drivers multiple times using both nvidia-340 and nvidia-346. It appears to install correctly, but when I log off and back on, or I reboot, I get the black screen of death. I can see that I am missing the .ko files that would be in the kernel drivers folder. /lib/modules/`uname -r`/kernel/drivers/video/ has no nvidia related files, but I do see some in /var/lib/dkms/nvidia-346. I have working on this with some folks over at [link removed] but we have hit the end of our understanding of configuring nvidia drivers in UbuntuGnome using gdm. I am JDAIII on the forum and a link to the thread is here: [link removed][/FONT]
```

---

### Post by Bashing-om on 2015-03-09
JDAIII; Good:

You need to add the graphics chips set info ( Nvidia and Intel ) and as well post them the output of 
```

sudo lshw -C display

``` to prove the module does not build.

If you pass the link to us, I will subscribe to your Nvidia thread.

Meanwhile, still looking at that build process.

[INDENT][INDENT]all the help we can get
[/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-09
Thanks, I went ahead and added that. I have a feeling that if they get back, they will ask these again. But that is why I posted the submission on here. In case you had input which you did.

---

### Post by JDAIII on 2015-03-10
The first thing nvidia asked in their reply was if I could switch to windows and test the drivers. We will see where things go from here, but not encouraging.

---

### Post by Bashing-om on 2015-03-10
JDAIII; Well the good thing is ->

They do respond. That to me is a good way to make sure it is not a hardware failure to check that the card works in a different environment.

In my research I found this:
> 
On some notebooks with Optimus graphics, the NVIDIA driver may not be able to retrieve the Video BIOS due to interactions between the System BIOS and the Linux kernel's ACPI subsystem. On affected notebooks, applications that require the GPU will fail, and messages like the following may appear in the system log:

NVRM: failed to copy vbios to system memory.
NVRM: RmInitAdapter failed! (0x30:0xffffffff:858)
NVRM: rm_init_adapter(0) failed
Such problems are typically beyond the control of the NVIDIA driver, which relies on proper cooperation of ACPI and the System BIOS to retrieve important information about the GPU, including the Video BIOS.


Is something similar happening in your case ? I think it behooves us to look. 
If and when you have the Nvidia 346 driver installed ->
What is the return from terminal commands:
```

grep NVRM /var/log/syslog
grep NVRM /var/log/syslog.1
grep NVRM /var/log/dmesg

```
We isolate this and
[INDENT][INDENT]1 can help all
[/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-11
Here is the detail that you requested. Sorry for the delay.

No return for grep NVRM /var/log/syslog after installing the 346 drivers.
No return for grep NVRM /var/log/syslog.1 after installing the 346 drivers.
No return for grep NVRM /var/log/dmesg after installing the 346 drivers.

Nvidia is now saying that I have to talk to lenovo about my optimus graphics config in the bios even though my laptop is switchable graphics and not optimus. I'm starting to get frustrated. Looks like nvidia is doing everything they can to put this on lenovo and lenovo refuses to support linux on my machine and also refuses to support nvidia drivers. KMN.

---

### Post by Bashing-om on 2015-03-11
JDAIII; Sheesshhh ..

Good thing is that the problem is not related to (N)on (V)olatile (R)a(M).

I can understand your frustration, been fighting this for months, and the fight just gets stiffer.
As you can guess, this has progressed beyond my skill set, I am very dedicated to see what can be done, however when I do not know I do not know. I do want to work with you and learn the reason why.
There is a failure on the build process - somewhere. Proprietary driver and I can not say we will ever understand what is going on underneath in that build process.

Let me see if I can enlist the aid of one whose skills I have great respect for.
I see if he can offer some insight and guidance.

Before I enlist additional aid, have we tried to build the 346 driver booting the 3.16.0-31 kernel ?  Might be best at this point if we work with an in-release kernel and headers .
Edit: Are you using Nvidia's UNinstall option to purge the driver prior to trying to rebuild ?

[INDENT][INDENT]quitters never win, and Lord I try
[/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-11
I first tried this a dozen times with 340 and 346 from nvidia's website, xorgedgers, and mamarley before I tried this all. I installed kernel 3.18 after I started working with you when we first saw kernel issues.

I am not using nvidia's uninstall option, I am using ```
sudo apt-get remove --purge 'nvidia*'
``` If there is another way for me to do this, please let me know, but so far, this has done the job of clearing everything nvidia related.

---

### Post by Bashing-om on 2015-03-11
JDAIII; Welp'

There is an uninstall option in the Nvidia installer, though the 'purge' should work .

I have asked for aid.
We get a new perspective on this - so long as you are willing 
and continue the fight.

[INDENT][INDENT]ain't gonna let this whoop us
[/INDENT][/INDENT]

---

### Post by JDAIII on 2015-03-11
I am more than willing. Nvidia has passed the buck on to lenovo saying I need to change my bios to use the nvidia card where that is not an actual option and lenovo support is gone for the day. They are only open from 10AM-7PM IST. Gotta love outsourcing.

I would be happy to try anything to get this working.

---

### Post by Bashing-om on 2015-03-14
JDAIII; Update.

Nothing new to report to this time, just to assure you that you are not forgotten. The issue continues under consideration.

Meanwhile, As I am stuck
[INDENT][INDENT]I go ask for help
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-03-18
JDAIII;  A sad state of affairs.

I am getting nowhere with this. I fail to understand how to look to even find out why the driver does not install. None others offer an opinion.

Perhaps with this bump, will get the notice of others who can offer some advise.

[INDENT][INDENT]when I do not know, help
[/INDENT][/INDENT]

---

### Post by ak2766 on 2015-11-14
@Bashing-om:

Logged in just to say that I've never seen this level of support from anyone, anywhere, and with professional attitude through and through.

Damn, Canonical should be proud they have you helping people on this site.  Keep it up!

ak.

---

### Post by Bashing-om on 2015-11-14
@ ak2766;

Here I be, blushing .. 
I try hard as there is no better way to learn than to do .

And this is 'buntu
[INDENT][INDENT][INDENT]one for all and all for 1
[/INDENT][/INDENT][/INDENT]

---

### Post by i2000s2 on 2016-05-02
> **Bashing-om said:**
> @ ak2766;

Here I be, blushing .. 
I try hard as there is no better way to learn than to do .

And this is 'buntu[INDENT][INDENT][INDENT]one for all and all for 1
[/INDENT]
[/INDENT]
[/INDENT]


Bashing-om, you are the best! I have never seen anyone like you who can provide countless help to the community members! 

I have similar problem on a NVidia M1000M card with Ubuntu 16.04 (GNOME 3.20 installed). I will post it in a better place to see if anyone can help solve. Helpfully see you there :)

---

### Post by cariboo on 2016-05-03
Solved thread closed.

---

