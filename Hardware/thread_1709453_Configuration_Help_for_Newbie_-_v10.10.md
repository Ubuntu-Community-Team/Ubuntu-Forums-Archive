---
title: "Configuration Help for Newbie - v10.10"
date: 2011-03-18
forum: Hardware
---

### Post by Cee# on 2011-03-18
I know nothing about Linux. I just installed it on my old laptop, a Toshiba with a 200m ATI graphics card. I managed to stumble around and figure out how to change to Safe Mode which works fine. I would like to make my configuration match Safe Mode.
 
I have reviewed many posts on the internet with about a zillion different opinions on configuring drivers for this card. Those that seemed to actually represent my problem were completed by a friend and didn't work. Logging in with the ability to make these changes is my first question... sudo what?
 
Then getting to the right configuration file is my second.
 
Then editing and saving changes is my third.
 
I need help with finding a document that actually describes how to do this stuff in simple detail would work fine, but I can't find that either.
 
Any instructions made for an idiot would be greatly appreciated.
 
TIA
 
C#

---

### Post by Bucky Ball on 2011-03-18
Welcome.

What Ubuntu release you are using (10.04 LTS, 10.10?)?

I take it you are online on this machine? Try System>Administration>Additional Drivers. Is there an ATI driver there disabled?

Also, System>Admin>Update Manager. Get all updates then try that again.

---

### Post by Cee# on 2011-03-18
OK. Let me say what I said again...
 
All of the updates and drivers have been installed and configured by a friend... he knows how to follow the multitude of various instructions on the internet about installing the third party source drivers since ATI doesn't support Linux.
 
As stated in the title of the message I am using v10.10.
 
I have no way of knowing what is enabled or disabled. The only thing I can do is boot in safe mode. Sooooooooooo..... I want the default boot to be the same as safe mode so that alterations I make to my configurations (wireless will be my next challenge) are saved in the >boot< configuration which is, I believe, all in /root. I need administrator rights to see /root and I think I remember that he did this by using sudo -i but I'm not sure. So what I'm hoping for is for someone to answer the questions that I asked in the original message.
 
Not to complain about your desire to help, but there are a multitude of wild goose chases on the internet about this very problem. I just want to move on.
 
C#

---

### Post by Cee# on 2011-04-11
OK. So Linux is a vast wasteland intended for geeks only?
 
I can't see how Linux will ever go anywhere is someone doesn't figure out how to get this beast under control and provide simple and meaninful information about using it.
 
But, I guess, it isn't intended "to go anywhere" is it?

---

### Post by Yellow Pasque on 2011-04-11
200m should work without any configuration. If it doesn't, (try to) start the GUI (log in) and post your /var/log/Xorg.0.log

---

### Post by Cee# on 2011-04-11
It isn't necessarily the graphics card... I managed to figure out how to use lshw to see what driver is loaded. Both the safe mode and the desktop mode are using the same driver (there may be different settings, however, but I don't know how to find this out).
 
I get the login dialog box when starting up in Desktop mode... and when I fill in the password, it doesn't load the GUI (whatever that is called).
 
I don't understand what you mean by try to start the GUI login... unless you mean that you want to see the log from 'trying to start' the GUI even thought it fails. To do that I suppose I would log in to the GUI and then use Alt-F2 to login again in the terminal window? And then I can somehow get a copy of the /var/log/Xorg.0.log file and post it? There are not any third party proprietry drivers loaded that I can tell. It is using the legacy ATI driver, which is working in Safe Mode. Let me repeat my question (a simple one, I believe) again...
 
HOW DO I MAKE MY LOGIN CONFIGURATION MATCH THE ONE THAT IS USED FOR SAFE MODE?
 
If I need to get geeky... then how do I look at what is loaded (hardware and drivers) for both Safe Mode and the Desktop Login configuration? How do I output the ENTIRE list and configuration at once? What format can I ouput it to? Can I make it a text file? Through this approach can I find the difference between the two? I do not use UNIX, btw.
 
The installation is the one that was automatic from the ISO CD and no changes were made but updates were run... it was made to a blank drive and there is not a dual boot configuation between linux and windows, for example.
 
C#

---

### Post by Yellow Pasque on 2011-04-11
> I don't understand what you mean by try to start the GUI login... unless you mean that you want to see the log from 'trying to start' the GUI even thought it fails. To do that I suppose I would log in to the GUI and then use Alt-F2 to login again in the terminal window? And then I can somehow get a copy of the /var/log/Xorg.0.log file and post it? 
Yeah, that's what I had in mind. (Ctrl+Alt+F1 , not Alt+F2). IIRC, you can also just restart in safe mode, and then the log from the previous attempt will be called Xorg.1.log

> HOW DO I MAKE MY LOGIN CONFIGURATION MATCH THE ONE THAT IS USED FOR SAFE MODE?
What configuration? The programs you start? The video configuration? You'll have to be more specific. It really sounds like a GPU or general system problem to me if gdm can't start. If you were having issues after log in, then it might have something to do with user settings.

---

### Post by Cee# on 2011-04-11
> **Temüjin said:**
> Yeah, that's what I had in mind. (Ctrl+Alt+F1 , not Alt+F2). IIRC, you can also just restart in safe mode, and then the log from the previous attempt will be called Xorg.1.log
 
 
What configuration? The programs you start? The video configuration? You'll have to be more specific. It really sounds like a GPU or general system problem to me if gdm can't start. If you were having issues after log in, then it might have something to do with user settings.
 
To get the same hardware and drivers are loaded in the default configuration as in the safe mode. The SYSTEM configuration, I suppose, would be an accurate description. The only thing that I am doing without in Safe Mode so far is the wireless networking, which, as I understand it, is also a nightmare. And before you ask, yes, I do have a hardwired internet connection. This is not on me... it is a bug or incompatability with my old Toshiba laptop which ran Win XP Pro just fine... slow, but fine.
 
Unless a different video mode is being set with the GPU when not in Safe Mode, I don't understand why it would be the GPU. It is the same graphics card driver in both instances.
 
Let me say again... I am just trying to start the plain vanilla installation of Ubuntu 10.10 from the Desktop version, not the safe mode, and it has never, ever, gone past the login where displaying the GUI should be showing up. The Ubuntu operating system, as is created as a default from the ISO CD, is doing something different for the desktop configuration that it isn't doing in the desktop configuration. How difficult an explanation does this have to be? Is the GUI a different program in normal mode than it is is safe mode? I don't think it is, but what do I know?

---

### Post by Yellow Pasque on 2011-04-11
> Unless a different video mode is being set with the GPU when not in Safe Mode

Safe mode uses a generic, unaccelerated video driver (vesa).

> How difficult an explanation does this have to be?
I'm wondering the same thing (I still don't see an Xorg log ;) )

> The Ubuntu operating system, as is created as a default from the ISO CD, is doing something different for the desktop configuration that it isn't doing in the desktop configuration.
I understand, and that's why I'm asking for Xorg log so we can fix the problem and hopefully put it back the way it should be. Either that, or you can reinstall...

---

### Post by Cee# on 2011-04-12
I think at the beginning I said "I know nothing about Linux".
 
I was trying to do this without learning Unix at the command prompt. I don't even know how to change directories at the command prompt. I'm not particularly interested in learning how to do so, either. However, it looks like I can't escape doing so.
 
I haven't had to use DOS for 10 years... and I'm not interested in >going back< to that, either. In my opinion unless you are a systems engineer, there should be no reason to conduct business at the command prompt in a modern day OS.
 
I will try to figure out how to find the file you are looking for and how to paste it into the email program that comes with Ubuntu and then how to post it. I'm doing all of this 'communicating' from my desktop in Win7. 
 
I appreciate that you are doing this 'for fun' and thanks for the help. Nonetheless, it shouldn't be necessary if someone is trying to develop a succesful product, free or otherwise.
 
I will see if I can do this without taking a Unix tutorial and if I can't it will be a while before I post the log. I hope you will keep your eye out for when I finally do.
 
Thanks again.
 
C#

---

### Post by Cee# on 2011-04-12
Well, not from my email, obviously... I need more coffee...

[    22.990] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    22.990] X Protocol Version 11, Revision 0
[    22.990] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    22.990] Current Operating System: Linux craig-Satellite-L25 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686
[    22.990] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=486a9c66-a1dc-4e8d-8d41-8ff4b86ee081 ro quiet splash
[    22.990] Build Date: 09 January 2011  12:14:58PM
[    22.990] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    22.990] Current version of pixman: 0.18.4
[    22.990] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    22.990] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.990] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 12 09:58:45 2011
[    23.047] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.048] (==) No Layout section.  Using the first Screen section.
[    23.048] (==) No screen section available. Using defaults.
[    23.048] (**) |-->Screen "Default Screen Section" (0)
[    23.048] (**) |   |-->Monitor "<default monitor>"
[    23.048] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    23.048] (==) Automatically adding devices
[    23.048] (==) Automatically enabling devices
[    23.048] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.048] 	Entry deleted from font path.
[    23.048] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    23.048] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    23.048] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    23.049] (II) Loader magic: 0x81f9b00
[    23.049] (II) Module ABI versions:
[    23.049] 	X.Org ANSI C Emulation: 0.4
[    23.049] 	X.Org Video Driver: 8.0
[    23.049] 	X.Org XInput driver : 11.0
[    23.049] 	X.Org Server Extension : 4.0
[    23.050] (--) PCI:*(0:1:5:0) 1002:5a62:1179:ff31 rev 0, Mem @ 0xd0000000/268435456, 0xc0100000/65536, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
[    23.051] (II) Open ACPI successful (/var/run/acpid.socket)
[    23.051] (II) LoadModule: "extmod"
[    23.062] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    23.062] (II) Module extmod: vendor="X.Org Foundation"
[    23.062] 	compiled for 1.9.0, module version = 1.0.0
[    23.062] 	Module class: X.Org Server Extension
[    23.063] 	ABI class: X.Org Server Extension, version 4.0
[    23.063] (II) Loading extension MIT-SCREEN-SAVER
[    23.063] (II) Loading extension XFree86-VidModeExtension
[    23.063] (II) Loading extension XFree86-DGA
[    23.063] (II) Loading extension DPMS
[    23.063] (II) Loading extension XVideo
[    23.063] (II) Loading extension XVideo-MotionCompensation
[    23.063] (II) Loading extension X-Resource
[    23.063] (II) LoadModule: "dbe"
[    23.063] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    23.063] (II) Module dbe: vendor="X.Org Foundation"
[    23.063] 	compiled for 1.9.0, module version = 1.0.0
[    23.063] 	Module class: X.Org Server Extension
[    23.063] 	ABI class: X.Org Server Extension, version 4.0
[    23.063] (II) Loading extension DOUBLE-BUFFER
[    23.063] (II) LoadModule: "glx"
[    23.063] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    23.064] (II) Module glx: vendor="X.Org Foundation"
[    23.064] 	compiled for 1.9.0, module version = 1.0.0
[    23.064] 	ABI class: X.Org Server Extension, version 4.0
[    23.064] (==) AIGLX enabled
[    23.064] (II) Loading extension GLX
[    23.064] (II) LoadModule: "record"
[    23.064] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    23.064] (II) Module record: vendor="X.Org Foundation"
[    23.064] 	compiled for 1.9.0, module version = 1.13.0
[    23.064] 	Module class: X.Org Server Extension
[    23.064] 	ABI class: X.Org Server Extension, version 4.0
[    23.064] (II) Loading extension RECORD
[    23.064] (II) LoadModule: "dri"
[    23.065] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    23.065] (II) Module dri: vendor="X.Org Foundation"
[    23.065] 	compiled for 1.9.0, module version = 1.0.0
[    23.065] 	ABI class: X.Org Server Extension, version 4.0
[    23.065] (II) Loading extension XFree86-DRI
[    23.065] (II) LoadModule: "dri2"
[    23.065] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    23.065] (II) Module dri2: vendor="X.Org Foundation"
[    23.066] 	compiled for 1.9.0, module version = 1.2.0
[    23.066] 	ABI class: X.Org Server Extension, version 4.0
[    23.066] (II) Loading extension DRI2
[    23.066] (==) Matched ati as autoconfigured driver 0
[    23.066] (==) Matched vesa as autoconfigured driver 1
[    23.066] (==) Matched fbdev as autoconfigured driver 2
[    23.066] (==) Assigned the driver to the xf86ConfigLayout
[    23.066] (II) LoadModule: "ati"
[    23.066] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    23.066] (II) Module ati: vendor="X.Org Foundation"
[    23.066] 	compiled for 1.9.0, module version = 6.13.1
[    23.066] 	Module class: X.Org Video Driver
[    23.066] 	ABI class: X.Org Video Driver, version 8.0
[    23.066] (II) LoadModule: "radeon"
[    23.067] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    23.067] (II) Module radeon: vendor="X.Org Foundation"
[    23.067] 	compiled for 1.9.0, module version = 6.13.1
[    23.067] 	Module class: X.Org Video Driver
[    23.067] 	ABI class: X.Org Video Driver, version 8.0
[    23.067] (II) LoadModule: "vesa"
[    23.069] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.069] (II) Module vesa: vendor="X.Org Foundation"
[    23.069] 	compiled for 1.8.99.905, module version = 2.3.0
[    23.069] 	Module class: X.Org Video Driver
[    23.069] 	ABI class: X.Org Video Driver, version 8.0
[    23.069] (II) LoadModule: "fbdev"
[    23.070] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.070] (II) Module fbdev: vendor="X.Org Foundation"
[    23.070] 	compiled for 1.8.99.905, module version = 0.4.2
[    23.070] 	ABI class: X.Org Video Driver, version 8.0
[    23.070] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
	CEDAR
[    23.085] (II) VESA: driver for VESA chipsets: vesa
[    23.085] (II) FBDEV: driver for framebuffer: fbdev
[    23.085] (++) using VT number 7

[    23.086] (II) [KMS] Kernel modesetting enabled.
[    23.086] (WW) Falling back to old probe method for vesa
[    23.086] (WW) Falling back to old probe method for fbdev
[    23.086] (II) Loading sub module "fbdevhw"
[    23.086] (II) LoadModule: "fbdevhw"
[    23.086] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.087] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.087] 	compiled for 1.9.0, module version = 0.0.2
[    23.087] 	ABI class: X.Org Video Driver, version 8.0
[    23.087] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    23.087] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    23.087] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    23.087] (==) RADEON(0): Default visual is TrueColor
[    23.087] (==) RADEON(0): RGB weight 888
[    23.087] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    23.087] (--) RADEON(0): Chipset: "ATI Radeon XPRESS 200M 5A62 (PCIE)" (ChipID = 0x5a62)
[    23.087] (II) RADEON(0): PCI card detected
[    23.087] (II) RADEON(0): KMS Color Tiling: enabled
[    23.087] drmOpenDevice: node name is /dev/dri/card0
[    23.087] drmOpenDevice: open result is 9, (OK)
[    23.087] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    23.087] drmOpenDevice: node name is /dev/dri/card0
[    23.087] drmOpenDevice: open result is 9, (OK)
[    23.087] drmOpenByBusid: drmOpenMinor returns 9
[    23.087] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    23.145] (II) RADEON(0): Output VGA-0 has no monitor section
[    23.146] (II) RADEON(0): Output LVDS has no monitor section
[    23.146] (II) RADEON(0): Output S-video has no monitor section
[    23.219] (II) RADEON(0): EDID for output VGA-0
[    23.219] (II) RADEON(0): EDID for output LVDS
[    23.219] (II) RADEON(0): Manufacturer: SHP  Model: 13b7  Serial#: 0
[    23.219] (II) RADEON(0): Year: 1990  Week: 0
[    23.220] (II) RADEON(0): EDID Version: 1.3
[    23.220] (II) RADEON(0): Digital Display Input
[    23.220] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 23
[    23.220] (II) RADEON(0): Gamma: 2.20
[    23.220] (II) RADEON(0): DPMS capabilities: StandBy Suspend
[    23.220] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    23.220] (II) RADEON(0): First detailed timing is preferred mode
[    23.220] (II) RADEON(0): redX: 0.000 redY: 0.000   greenX: 0.000 greenY: 0.000
[    23.220] (II) RADEON(0): blueX: 0.000 blueY: 0.000   whiteX: 0.000 whiteY: 0.000
[    23.220] (II) RADEON(0): Supported established timings:
[    23.220] (II) RADEON(0): 1024x768@60Hz
[    23.220] (II) RADEON(0): Manufacturer's mask: 0
[    23.220] (II) RADEON(0): Supported standard timings:
[    23.220] (II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    23.220] (II) RADEON(0): Supported detailed timing:
[    23.220] (II) RADEON(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
[    23.220] (II) RADEON(0): h_active: 1024  h_sync: 1036  h_sync_end 1172 h_blank_end 1344 h_border: 0
[    23.220] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[    23.220] (II) RADEON(0): EDID (in hex):
[    23.220] (II) RADEON(0): 	00ffffffffffff004d10b71300000000
[    23.220] (II) RADEON(0): 	00000103801e1778ca00000000000000
[    23.220] (II) RADEON(0): 	00000000080061400101010101010101
[    23.220] (II) RADEON(0): 	01010101010164190040410026300c88
[    23.220] (II) RADEON(0): 	360030e4100000180000001000000000
[    23.220] (II) RADEON(0): 	00000000000000000a20000000100000
[    23.220] (II) RADEON(0): 	000000000000000000000a2000000010
[    23.220] (II) RADEON(0): 	004c5131353058314c425332200a0056
[    23.220] (II) RADEON(0): Printing probed modes for output LVDS
[    23.220] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1036 1172 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.220] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.220] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    23.220] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    23.220] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    23.220] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    23.220] (II) RADEON(0): EDID for output S-video
[    23.221] (II) RADEON(0): Output VGA-0 disconnected
[    23.221] (II) RADEON(0): Output LVDS connected
[    23.221] (II) RADEON(0): Output S-video disconnected
[    23.221] (II) RADEON(0): Using exact sizes for initial modes
[    23.221] (II) RADEON(0): Output LVDS using initial mode 1024x768
[    23.221] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    23.221] (II) RADEON(0): mem size init: gart size :1dff000 vram size: s:8000000 visible:7cc0000
[    23.221] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    23.221] (==) RADEON(0): DPI set to (96, 96)
[    23.221] (II) Loading sub module "fb"
[    23.221] (II) LoadModule: "fb"
[    23.221] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.221] (II) Module fb: vendor="X.Org Foundation"
[    23.221] 	compiled for 1.9.0, module version = 1.0.0
[    23.221] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.221] (II) Loading sub module "ramdac"
[    23.221] (II) LoadModule: "ramdac"
[    23.222] (II) Module "ramdac" already built-in
[    23.222] (II) Loading sub module "exa"
[    23.222] (II) LoadModule: "exa"
[    23.222] (II) Loading /usr/lib/xorg/modules/libexa.so
[    23.222] (II) Module exa: vendor="X.Org Foundation"
[    23.222] 	compiled for 1.9.0, module version = 2.5.0
[    23.222] 	ABI class: X.Org Video Driver, version 8.0
[    23.222] (II) UnloadModule: "vesa"
[    23.222] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.222] (II) UnloadModule: "fbdev"
[    23.222] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.222] (II) UnloadModule: "fbdevhw"
[    23.222] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    23.222] (--) Depth 24 pixmap format is 32 bpp
[    23.223] (II) RADEON(0): [DRI2] Setup complete
[    23.223] (II) RADEON(0): [DRI2]   DRI driver: r300
[    23.223] (II) RADEON(0): Front buffer size: 3072K
[    23.223] (II) RADEON(0): VRAM usage limit set to 112204K
[    23.223] (==) RADEON(0): Backing store disabled
[    23.223] (II) RADEON(0): Direct rendering enabled
[    23.223] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    23.223] (II) RADEON(0): Setting EXA maxPitchBytes
[    23.223] (II) EXA(0): Driver allocated offscreen pixmaps
[    23.223] (II) EXA(0): Driver registered support for the following operations:
[    23.223] (II)         Solid
[    23.223] (II)         Copy
[    23.223] (II)         Composite (RENDER acceleration)
[    23.223] (II)         UploadToScreen
[    23.223] (II)         DownloadFromScreen
[    23.223] (II) RADEON(0): Acceleration enabled
[    23.223] (==) RADEON(0): DPMS enabled
[    23.223] (==) RADEON(0): Silken mouse enabled
[    23.223] (II) RADEON(0): Set up textured video
[    23.223] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    23.233] (--) RandR disabled
[    23.233] (II) Initializing built-in extension Generic Event Extension
[    23.233] (II) Initializing built-in extension SHAPE
[    23.233] (II) Initializing built-in extension MIT-SHM
[    23.233] (II) Initializing built-in extension XInputExtension
[    23.233] (II) Initializing built-in extension XTEST
[    23.233] (II) Initializing built-in extension BIG-REQUESTS
[    23.233] (II) Initializing built-in extension SYNC
[    23.233] (II) Initializing built-in extension XKEYBOARD
[    23.233] (II) Initializing built-in extension XC-MISC
[    23.233] (II) Initializing built-in extension SECURITY
[    23.233] (II) Initializing built-in extension XINERAMA
[    23.233] (II) Initializing built-in extension XFIXES
[    23.233] (II) Initializing built-in extension RENDER
[    23.233] (II) Initializing built-in extension RANDR
[    23.233] (II) Initializing built-in extension COMPOSITE
[    23.233] (II) Initializing built-in extension DAMAGE
[    23.233] (II) Initializing built-in extension GESTURE
[    23.271] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    23.271] (II) AIGLX: enabled GLX_INTEL_swap_event
[    23.271] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    23.271] (II) AIGLX: enabled GLX_SGI_make_current_read
[    23.271] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    23.272] (II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
[    23.272] (II) GLX: Initialized DRI2 GL provider for screen 0
[    23.273] (II) RADEON(0): Setting screen physical size to 270 x 203
[    23.307] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.320] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    23.320] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.320] (II) LoadModule: "evdev"
[    23.320] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.321] (II) Module evdev: vendor="X.Org Foundation"
[    23.321] 	compiled for 1.9.0, module version = 2.3.2
[    23.321] 	Module class: X.Org XInput Driver
[    23.321] 	ABI class: X.Org XInput driver, version 11.0
[    23.321] (**) Power Button: always reports core events
[    23.321] (**) Power Button: Device: "/dev/input/event2"
[    23.321] (II) Power Button: Found keys
[    23.321] (II) Power Button: Configuring as keyboard
[    23.321] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.321] (**) Option "xkb_rules" "evdev"
[    23.321] (**) Option "xkb_model" "pc105"
[    23.321] (**) Option "xkb_layout" "us"
[    23.324] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.324] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.324] (**) Power Button: always reports core events
[    23.324] (**) Power Button: Device: "/dev/input/event1"
[    23.324] (II) Power Button: Found keys
[    23.324] (II) Power Button: Configuring as keyboard
[    23.324] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.324] (**) Option "xkb_rules" "evdev"
[    23.324] (**) Option "xkb_model" "pc105"
[    23.324] (**) Option "xkb_layout" "us"
[    23.325] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    23.325] (II) No input driver/identifier specified (ignoring)
[    23.326] (II) config/udev: Adding input device Microsoft Microsoft Optical Mouse with Tilt Wheel (/dev/input/event4)
[    23.326] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: Applying InputClass "evdev pointer catchall"
[    23.326] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: always reports core events
[    23.326] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: Device: "/dev/input/event4"
[    23.326] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found 9 mouse buttons
[    23.326] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found scroll wheel(s)
[    23.326] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found relative axes
[    23.327] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Found x and y relative axes
[    23.327] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: Configuring as mouse
[    23.327] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: YAxisMapping: buttons 4 and 5
[    23.327] (**) Microsoft Microsoft Optical Mouse with Tilt Wheel: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.327] (II) XINPUT: Adding extended input device "Microsoft Microsoft Optical Mouse with Tilt Wheel" (type: MOUSE)
[    23.327] (II) Microsoft Microsoft Optical Mouse with Tilt Wheel: initialized for relative axes.
[    23.327] (II) config/udev: Adding input device Microsoft Microsoft Optical Mouse with Tilt Wheel (/dev/input/mouse0)
[    23.327] (II) No input driver/identifier specified (ignoring)
[    23.331] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    23.331] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.331] (**) AT Translated Set 2 keyboard: always reports core events
[    23.331] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    23.331] (II) AT Translated Set 2 keyboard: Found keys
[    23.331] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    23.331] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    23.331] (**) Option "xkb_rules" "evdev"
[    23.331] (**) Option "xkb_model" "pc105"
[    23.331] (**) Option "xkb_layout" "us"
[    23.332] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    23.332] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    23.332] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    23.332] (II) LoadModule: "synaptics"
[    23.332] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    23.333] (II) Module synaptics: vendor="X.Org Foundation"
[    23.333] 	compiled for 1.9.0, module version = 1.2.2
[    23.333] 	Module class: X.Org XInput Driver
[    23.333] 	ABI class: X.Org XInput driver, version 11.0
[    23.333] (II) Synaptics touchpad driver version 1.2.2
[    23.333] (**) Option "Device" "/dev/input/event5"
[    23.333] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    23.333] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    23.333] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    23.333] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    23.333] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    23.333] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    23.333] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    23.333] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    23.333] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    23.333] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    23.333] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    23.333] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    23.334] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    23.334] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    23.334] (II) No input driver/identifier specified (ignoring)
[    24.461] (II) RADEON(0): EDID vendor "SHP", prod id 5047
[    24.461] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.461] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1036 1172 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.462] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.500] (II) RADEON(0): EDID vendor "SHP", prod id 5047
[    24.500] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.500] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1036 1172 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.500] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.550] (II) RADEON(0): EDID vendor "SHP", prod id 5047
[    24.551] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.551] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1036 1172 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.551] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.576] (II) RADEON(0): EDID vendor "SHP", prod id 5047
[    24.576] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.576] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1036 1172 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.577] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    45.295] (II) RADEON(0): EDID vendor "SHP", prod id 5047
[    45.295] (II) RADEON(0): Printing DDC gathered Modelines:
[    45.295] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1036 1172 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    45.295] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    45.321] (II) RADEON(0): EDID vendor "SHP", prod id 5047
[    45.321] (II) RADEON(0): Printing DDC gathered Modelines:
[    45.321] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1036 1172 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    45.321] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    45.347] (II) RADEON(0): EDID vendor "SHP", prod id 5047
[    45.347] (II) RADEON(0): Printing DDC gathered Modelines:
[    45.347] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1036 1172 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    45.347] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)

---

### Post by Cee# on 2011-04-12
Three warnings... that's all I saw. To me it 'looks like' the driver is trying to load a vesa mode... which would be fine for this machine.

---

