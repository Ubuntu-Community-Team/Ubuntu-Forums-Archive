---
title: "HP dv7-4285dx (dual graphic card) Intel / ATI HD6370"
date: 2011-05-07
forum: Hardware
---

### Post by geru59 on 2011-05-07
p { margin-bottom: 0.08in; }a:link {  }     	 	 	 	p { margin-bottom: 0.08in; }  Maker: HP
 Model: dv7-4285dx 



 
I tried to install the ATI driver  using the Ubuntu software (automate install) also manual install following the instructions from this link [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually) but the ATI driver installed on this laptop doesn't work. Here is X11 log file:
 

 X.Org X Server 1.7.6 
 Release Date: 2010-03-17 
 X Protocol Version 11, Revision 0 
 Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu 
 Current Operating System: Linux HP-Private 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011 x86_64 
 Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-31-generic root=UUID=9a50cbd0-8bbd-4269-9488-7ae0d8859810 ro  quiet splash 
 Build Date: 08 March 2011  08:22:34AM 
 xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))  
 Current version of pixman: 0.16.4 
 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) 
 	to make sure that you have the latest version. 
 Markers: (--) probed, (**) from config file, (==) default setting, 
 	(++) from command line, (!!) notice, (II) informational, 
 	(WW) warning, (EE) error, (NI) not implemented, (??) unknown. 
 (==) Log file: "/var/log/Xorg.4.log", Time: Sat May  7 10:43:29 2011 
 (==) Using config file: "/etc/X11/xorg.conf" 
 (==) Using config directory: "/usr/lib/X11/xorg.conf.d" 
 (==) No Layout section.  Using the first Screen section. 
 (**) |-->Screen "Default Screen" (0) 
 (**) |   |-->Monitor "<default monitor>" 
 (==) No device specified for screen "Default Screen". 
 	Using the first device section listed. 
 (**) |   |-->Device "Default Device" 
 (==) No monitor specified for screen "Default Screen". 
 	Using a default monitor configuration. 
 (==) Automatically adding devices 
 (==) Automatically enabling devices 
 (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist. 
 	Entry deleted from font path. 
 (==) FontPath set to: 
 	/usr/share/fonts/X11/misc, 
 	/usr/share/fonts/X11/100dpi/:unscaled, 
 	/usr/share/fonts/X11/75dpi/:unscaled, 
 	/usr/share/fonts/X11/Type1, 
 	/usr/share/fonts/X11/100dpi, 
 	/usr/share/fonts/X11/75dpi, 
 	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, 
 	built-ins 
 (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules" 
 (II) The server relies on udev to provide the list of input devices. 
 	If no devices become available, reconfigure udev or disable AutoAddDevices. 
 (II) Loader magic: 0x7cb840 
 (II) Module ABI versions: 
 	X.Org ANSI C Emulation: 0.4 
 	X.Org Video Driver: 6.0 
 	X.Org XInput driver : 7.0 
 	X.Org Server Extension : 2.0 
 (--) using VT number 8 
  
 (--) PCI:*(0:0:2:0) 8086:0046:103c:163d Intel Corporation Core Processor Integrated Graphics Controller rev 2, Mem @ 0xc0000000/4194304, 0xb0000000/268435456, I/O @ 0x00005050/8 
 (--) PCI: (0:1:0:0) 1002:68e4:103c:163d ATI Technologies Inc rev 0, Mem @ 0xa0000000/268435456, 0xc4400000/131072, I/O @ 0x00004000/256, BIOS @ 0x????????/131072 
 (II) Open ACPI successful (/var/run/acpid.socket) 
 (II) "extmod" will be loaded by default. 
 (II) "dbe" will be loaded by default. 
 (II) "glx" will be loaded. This was enabled by default and also specified in the config file. 
 (II) "record" will be loaded by default. 
 (II) "dri" will be loaded by default. 
 (II) "dri2" will be loaded by default. 
 (II) LoadModule: "glx" 
 (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so 
 (II) Module glx: vendor="FireGL - ATI Technologies Inc." 
 	compiled for 7.5.0, module version = 1.0.0 
 (II) Loading extension GLX 
 (II) LoadModule: "extmod" 
 (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so 
 (II) Module extmod: vendor="X.Org Foundation" 
 	compiled for 1.7.6, module version = 1.0.0 
 	Module class: X.Org Server Extension 
 	ABI class: X.Org Server Extension, version 2.0 
 (II) Loading extension MIT-SCREEN-SAVER 
 (II) Loading extension XFree86-VidModeExtension 
 (II) Loading extension XFree86-DGA 
 (II) Loading extension DPMS 
 (II) Loading extension XVideo 
 (II) Loading extension XVideo-MotionCompensation 
 (II) Loading extension X-Resource 
 (II) LoadModule: "dbe" 
 (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so 
 (II) Module dbe: vendor="X.Org Foundation" 
 	compiled for 1.7.6, module version = 1.0.0 
 	Module class: X.Org Server Extension 
 	ABI class: X.Org Server Extension, version 2.0 
 (II) Loading extension DOUBLE-BUFFER 
 (II) LoadModule: "record" 
 (II) Loading /usr/lib/xorg/modules/extensions/librecord.so 
 (II) Module record: vendor="X.Org Foundation" 
 	compiled for 1.7.6, module version = 1.13.0 
 	Module class: X.Org Server Extension 
 	ABI class: X.Org Server Extension, version 2.0 
 (II) Loading extension RECORD 
 (II) LoadModule: "dri" 
 (II) Loading /usr/lib/xorg/modules/extensions/libdri.so 
 (II) Module dri: vendor="X.Org Foundation" 
 	compiled for 1.7.6, module version = 1.0.0 
 	ABI class: X.Org Server Extension, version 2.0 
 (II) Loading extension XFree86-DRI 
 (II) LoadModule: "dri2" 
 (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so 
 (II) Module dri2: vendor="X.Org Foundation" 
 	compiled for 1.7.6, module version = 1.1.0 
 	ABI class: X.Org Server Extension, version 2.0 
 (II) Loading extension DRI2 
 (II) LoadModule: "fglrx" 
 (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so 
 (II) Module fglrx: vendor="FireGL - ATI Technologies Inc." 
 	compiled for 1.4.99.906, module version = 8.80.5 
 	Module class: X.Org Video Driver 
 (II) Loading sub module "fglrxdrm" 
 (II) LoadModule: "fglrxdrm" 
 (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so 
 (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc." 
 	compiled for 1.4.99.906, module version = 8.80.5 
 (II) ATI Proprietary Linux Driver Version Identifier:8.80.5 
 (II) ATI Proprietary Linux Driver Release Identifier: 8.801                                 
 (II) ATI Proprietary Linux Driver Build Date: Nov 25 2010 21:36:23 
 (II) Primary Device is: PCI 00@00:02:0 
 (WW) Falling back to old probe method for fglrx 
 (II) Loading PCS database from /etc/ati/amdpcsdb 
 (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:0) found 
 (EE) No devices detected. 
  
 Fatal server error: 
 no screens found 
  
 Please consult the The X.Org Foundation support  
 	 at [http://wiki.x.org](http://wiki.x.org) 
  for help.  
 Please also check the log file at "/var/log/Xorg.4.log" for additional information. 
  
  ddxSigGiveUp: Closing log

---

### Post by cruzsilvae on 2011-06-28
I have a similar one (dv7-4287nr) with the same ATI hybrid card.. I don't think the ATI catalyst driver provides support for these yet, you're better off with the open source drivers.  I tried using scripts to modify vga_switcheroo in order to switch graphics processors, but it didn't do it... so far I've been only able to use the Intel graphics.

---

