---
title: "Hybrid Graphics 12.04 almost working"
date: 2012-03-21
forum: Hardware
---

### Post by delsus on 2012-03-21
Edit: Hit the wrong prefix this is an Ubuntu problem, and I cant find where to change it.

After failing to get my discreet GPU working in ubuntu 11.10 I decided to install 12.04 to see if it was working and I believe I am getting somewhere with it.

I installed the fglrx drivers through jockey and ran ```
aticonfig --initial -f
```However it came up with this powerXpress error:

```
PowerXpress error: Cannot stat '/usr/lib64/fglrx': No such file or directory
Failed to initialize libglx for discrete GPU
```I however ignored this and rebooted, and rather than completely failing to boot it boots to low graphics mode (which is progress) but I cannot configure my graphics adapter and screen,

Here are my xorg.conf and my xorg.0.log files:

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

``````
[    15.420] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    15.420] X Protocol Version 11, Revision 0
[    15.420] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    15.420] Current Operating System: Linux mike-ubuntu 3.2.0-17-generic #27-Ubuntu SMP Fri Feb 24 15:37:36 UTC 2012 x86_64
[    15.420] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-17-generic root=UUID=ff081b73-4bb3-4c52-8153-e789022d6a06 ro quiet splash vt.handoff=7
[    15.420] Build Date: 22 February 2012  03:16:54AM
[    15.420] xorg-server 2:1.11.4-0ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[    15.420] Current version of pixman: 0.24.4
[    15.420]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    15.420] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.420] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 21 20:44:20 2012
[    15.420] (==) Using config file: "/etc/X11/xorg.conf"
[    15.420] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.421] (==) ServerLayout "aticonfig Layout"
[    15.421] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    15.421] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    15.421] (**) |   |-->Device "aticonfig-Device[0]-0"
[    15.421] (==) Automatically adding devices
[    15.421] (==) Automatically enabling devices
[    15.421] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.421]     Entry deleted from font path.
[    15.421] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    15.421]     Entry deleted from font path.
[    15.421] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    15.421]     Entry deleted from font path.
[    15.421] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    15.421]     Entry deleted from font path.
[    15.421] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    15.421]     Entry deleted from font path.
[    15.429] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[    15.429]     Entry deleted from font path.
[    15.429]     (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[    15.429] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    15.429] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.429] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.429] (II) Loader magic: 0x7f40d6b22b00
[    15.429] (II) Module ABI versions:
[    15.429]     X.Org ANSI C Emulation: 0.4
[    15.429]     X.Org Video Driver: 11.0
[    15.429]     X.Org XInput driver : 16.0
[    15.429]     X.Org Server Extension : 6.0
[    15.431] (--) PCI:*(0:0:2:0) 8086:0046:103c:144a rev 2, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00005050/8
[    15.431] (--) PCI: (0:1:0:0) 1002:68e0:103c:144a rev 0, Mem @ 0xa0000000/268435456, 0xc4400000/131072, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
[    15.431] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.431] (II) "extmod" will be loaded by default.
[    15.431] (II) "dbe" will be loaded by default.
[    15.431] (II) "glx" will be loaded by default.
[    15.431] (II) "record" will be loaded by default.
[    15.431] (II) "dri" will be loaded by default.
[    15.431] (II) "dri2" will be loaded by default.
[    15.431] (II) LoadModule: "extmod"
[    15.448] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.448] (II) Module extmod: vendor="X.Org Foundation"
[    15.448]     compiled for 1.11.3, module version = 1.0.0
[    15.448]     Module class: X.Org Server Extension
[    15.448]     ABI class: X.Org Server Extension, version 6.0
[    15.448] (II) Loading extension MIT-SCREEN-SAVER
[    15.448] (II) Loading extension XFree86-VidModeExtension
[    15.448] (II) Loading extension XFree86-DGA
[    15.448] (II) Loading extension DPMS
[    15.448] (II) Loading extension XVideo
[    15.448] (II) Loading extension XVideo-MotionCompensation
[    15.448] (II) Loading extension X-Resource
[    15.448] (II) LoadModule: "dbe"
[    15.448] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.448] (II) Module dbe: vendor="X.Org Foundation"
[    15.449]     compiled for 1.11.3, module version = 1.0.0
[    15.449]     Module class: X.Org Server Extension
[    15.449]     ABI class: X.Org Server Extension, version 6.0
[    15.449] (II) Loading extension DOUBLE-BUFFER
[    15.449] (II) LoadModule: "glx"
[    15.449] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/extensions/libglx.so
[    15.449] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    15.449]     compiled for 6.9.0, module version = 1.0.0
[    15.449] (II) Loading extension GLX
[    15.449] (II) LoadModule: "record"
[    15.449] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.449] (II) Module record: vendor="X.Org Foundation"
[    15.449]     compiled for 1.11.3, module version = 1.13.0
[    15.449]     Module class: X.Org Server Extension
[    15.449]     ABI class: X.Org Server Extension, version 6.0
[    15.449] (II) Loading extension RECORD
[    15.449] (II) LoadModule: "dri"
[    15.449] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.449] (II) Module dri: vendor="X.Org Foundation"
[    15.449]     compiled for 1.11.3, module version = 1.0.0
[    15.449]     ABI class: X.Org Server Extension, version 6.0
[    15.449] (II) Loading extension XFree86-DRI
[    15.449] (II) LoadModule: "dri2"
[    15.450] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.450] (II) Module dri2: vendor="X.Org Foundation"
[    15.450]     compiled for 1.11.3, module version = 1.2.0
[    15.450]     ABI class: X.Org Server Extension, version 6.0
[    15.450] (II) Loading extension DRI2
[    15.450] (II) LoadModule: "fglrx"
[    15.450] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so
[    15.728] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    15.740]     compiled for 1.4.99.906, module version = 8.91.4
[    15.740]     Module class: X.Org Video Driver
[    15.826] (II) Loading sub module "fglrxdrm"
[    15.826] (II) LoadModule: "fglrxdrm"
[    15.826] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/linux/libfglrxdrm.so
[    15.850] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    15.850]     compiled for 1.4.99.906, module version = 8.91.4
[    15.850] (II) ATI Proprietary Linux Driver Version Identifier:8.91.4
[    15.850] (II) ATI Proprietary Linux Driver Release Identifier: 8.911                                
[    15.850] (II) ATI Proprietary Linux Driver Build Date: Oct 25 2011 21:24:13
[    15.850] (++) using VT number 7

[    15.851] (WW) Falling back to old probe method for fglrx
[    15.931] (II) Loading PCS database from /etc/ati/amdpcsdb
[    15.952] (--) Chipset Supported AMD Graphics Processor (0x68E0) found
[    15.958] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    15.958] (II) fglrx: intel VGA device detected, load intel driver.
[    15.958] (II) LoadModule: "intel"
[    15.958] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.958] (II) Module intel: vendor="X.Org Foundation"
[    15.958]     compiled for 1.11.3, module version = 2.17.0
[    15.958]     Module class: X.Org Video Driver
[    15.958]     ABI class: X.Org Video Driver, version 11.0
[    15.960] ukiDynamicMajor: found major device number 249
[    15.960] ukiDynamicMajor: found major device number 249
[    15.960] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.960] ukiOpenDevice: node name is /dev/ati/card0
[    15.960] ukiOpenDevice: open result is 11, (OK)
[    15.960] ukiOpenByBusid: ukiOpenMinor returns 11
[    15.960] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.971] (WW) PowerXpress feature is not supported on A+I Mux platform. Please uninstall fglrx driver.
[    15.971] (EE) No devices detected.
[    15.971] (==) Matched intel as autoconfigured driver 0
[    15.971] (==) Matched vesa as autoconfigured driver 1
[    15.971] (==) Matched fbdev as autoconfigured driver 2
[    15.971] (==) Assigned the driver to the xf86ConfigLayout
[    15.971] (II) LoadModule: "intel"
[    15.971] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    15.971] (II) Module intel: vendor="X.Org Foundation"
[    15.971]     compiled for 1.11.3, module version = 2.17.0
[    15.971]     Module class: X.Org Video Driver
[    15.971]     ABI class: X.Org Video Driver, version 11.0
[    15.971] (II) UnloadModule: "intel"
[    15.971] (II) Unloading intel
[    15.971] (II) Failed to load module "intel" (already loaded, 32576)
[    15.971] (II) LoadModule: "vesa"
[    15.971] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.972] (II) Module vesa: vendor="X.Org Foundation"
[    15.972]     compiled for 1.11.3, module version = 2.3.0
[    15.972]     Module class: X.Org Video Driver
[    15.972]     ABI class: X.Org Video Driver, version 11.0
[    15.972] (II) LoadModule: "fbdev"
[    15.972] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.972] (II) Module fbdev: vendor="X.Org Foundation"
[    15.972]     compiled for 1.11.3, module version = 0.4.2
[    15.972]     ABI class: X.Org Video Driver, version 11.0
[    15.972] (II) ATI Proprietary Linux Driver Version Identifier:8.91.4
[    15.972] (II) ATI Proprietary Linux Driver Release Identifier: 8.911                                
[    15.972] (II) ATI Proprietary Linux Driver Build Date: Oct 25 2011 21:24:13
[    15.972] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    15.972] (II) VESA: driver for VESA chipsets: vesa
[    15.972] (II) FBDEV: driver for framebuffer: fbdev
[    15.972] (++) using VT number 7

[    15.972] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    15.972] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    15.972] (WW) Falling back to old probe method for fglrx
[    15.972] (II) Loading PCS database from /etc/ati/amdpcsdb
[    15.972] (WW) Falling back to old probe method for vesa
[    15.972] (WW) Falling back to old probe method for fbdev
[    15.972] (EE) No devices detected.
[    15.972] 
Fatal server error:
[    15.972] no screens found
[    15.972] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    15.972] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    15.972] 
```Also here is my lshw -C -video output

```
*-display               
       description: VGA compatible controller
       product: Manhattan [Mobility Radeon HD 5400 Series]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:4000(size=256) memory:c4440000-c445ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:5050(size=8)

```Any help to get this working will be appreciated.

---

### Post by sirblew on 2012-03-22
+1 to this problem!

I can't get the "radeon" driver to work either in 12.04.  vgaswitcheroo seems to have no effect.


blew@brendanpc:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series] (rev ff)
blew@brendanpc:~$ lsmod | grep radeon
radeon                804304  0 
ttm                    76949  1 radeon
drm_kms_helper         42489  2 radeon,i915
drm                   241873  5 radeon,i915,ttm,drm_kms_helper
i2c_algo_bit           13423  2 radeon,i915
blew@brendanpc:~$ glxinfo 
name of display: :0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

---

### Post by edup_pt on 2012-05-03
I have the same problem. I can't get fglrx working on 12.04. It worked fine in 11.10. Neither the community ubuntu drivers, neither the amd ati driver 12.4/12.3/12.1...


I have the same output for xorg log. "Fatal Error: no screens found" (info files in attach).


When i run aticonfig --initial -f i get several warnings but the file is created. When i reboot the ubuntu runs into failsafe (low graphic mode)

<code>
root@beatsaudio:/home/edup/Downloads/tmp# aticonfig --initial -f
Uninitialised file found, configuring.
PowerXpress info: Diagnostic output from /usr/lib/fglrx/switchlibglx:
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/i386-linux-gnu/xorg/extra-modules with a link.
</code>


It worked great on 11.10. Can someone help?

Thanks

---

### Post by jamesmuga on 2012-05-13
this help me with my hybrid graphics...

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)

---

