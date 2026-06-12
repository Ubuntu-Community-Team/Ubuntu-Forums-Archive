---
title: "new ATi Driver 8.14.13"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by ferdy on 2005-06-09
[ATI](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

---

### Post by SWAT on 2005-06-09
EDIT:
The new ATI installer works fine (automatic mode) and you even get a nice ATI control config icon in gnome!
Now about performance, it slightly increased, and I mean really slightly. (before/after)
Glxgears: 3328/3341
World of warcraft (menu): 92/99
World of warcraft (Ironforge): 12/13
World of warcraft (Ironforge outside): 13/14

EDIT:
I'm running this driver for a day now, and I haven't noticed any problems. I also played World of warcraft without problems.

---

### Post by Chetic on 2005-06-09
I'm trying it right now, I'll tell you how (bad) it goes :razz:

---

### Post by Dracontopes on 2005-06-09
Whoop! 

I'm am going to try them right now.

Update: No problems encountered.
```
OpenGL version string: 1.3.5140 (X4.3.0-8.14.13)
``` 
glxgears ~ 4122.400 FPS (radeon 9700pro)

---

### Post by Abild on 2005-06-09
I was able to install the driver without any problems using the GUI installer, but i'm still only getting 450 fps the same framerate as i got with VESA drivers... My graphics card is an X800XL. Can anyone help me making my card perfom better?

---

### Post by Curlydave on 2005-06-09
How did you guys install it?

---

### Post by Chetic on 2005-06-09
I installed everything with the installer, pretty much went for most stuff default in fglrxconfig and restarted, but now I get this everytime I try to start a GL application:
> glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
I have an X800XL which is SUPPOSED to work with this release.
I'm using the 64-bit stuff all the way.

---

### Post by Curlydave on 2005-06-09
[QUOTE=Chetic]I installed everything with the installer, pretty much went for most stuff default in fglrxconfig and restarted, but now I get this everytime I try to start a GL application:

I have an X800XL which is SUPPOSED to work with this release.
I'm using the 64-bit stuff all the way.[/QUOTE]

I'm pretty sure I've had that one before, don't remember when. I think the problem is that you just ran the installer. It's NEVER that easy; you're kidding yourself if you think it is.  ;-)

---

### Post by Zingam on 2005-06-09
So, no success yet?


Why do I get this error:

[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
[fglrx:firegl_unlock] *ERROR* Process 7051 using kernel context 0
ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: disabled - APM is not SMP safe.
cs: IO port probe 0x0100-0x04ff: excluding 0x480-0x48f 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: excluding 0x818-0x877 0x880-0x887 0x898-0x89f
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
eth0: no IPv6 routers present
[fglrx] module unloaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
[fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
[fglrx] module unloaded - fglrx 8.8.25 [Jan 14 2005] on minor 0


It seems to load the old driver that is included in Ubuntu but I haven't installed it at all. According to the ATI Control Panel: I have Driver Version 8.14.13. Before running fglrxconfig this panel was empty.

lsmod does not show fglrx

---

### Post by ferdy on 2005-06-09
can you tell me, how do you install the driver?
i install linux-headers, build-essential and then i run the ati-installer, but i become an error message, can you help me?

[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-686/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Gehe in Verzeichnis »/usr/src/linux-headers-2.6.10-5-686«
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
In Datei, eingefügt von /lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:125:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:56:48: Warnung: Backslash und Newline durch Leerzeichen getrennt
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:57:6: Warnung: Backslash und Newline durch Leerzeichen getrennt
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:58:41: Warnung: Backslash und Newline durch Leerzeichen getrennt
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In Funktion »firegl_stub_putminor«:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:508: Warnung: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:510: Warnung: `inter_module_unregister' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In Funktion »firegl_stub_register«:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:530: Warnung: `inter_module_register' is deprecated (declared at include/linux/module.h:577)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:561: Warnung: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: Auf höchster Ebene:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2647: Warnung: Initialisierung von inkompatiblem Zeigertyp
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In Funktion »__ke_agp_uninit«:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3185: Warnung: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Verlasse Verzeichnis »/usr/src/linux-headers-2.6.10-5-686«
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
failed.
[Error] Kernel Module : Failed to install compiled kernel module - please consult readme.

---

### Post by Iuliux on 2005-06-09
what is ATI Driver Installer??

---

### Post by manatlan on 2005-06-09
[QUOTE=Iuliux]what is ATI Driver Installer??[/QUOTE]

it's a new graphical frontend to install the drivers
i've tried it, it works .... but have built my ko in a wrong folder ...
i moved it to the good place ... and it works well

my 9200 ati card,  fglrxinfo :
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 8500 Prototype DDR Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 1.3.1003 (X4.3.0-8.14.13)

QUESTIONS :
1) is it normal that it show "8500", when my card is a 9200 ?

2) it seems that DRI and COMPOSITE are not able to work together
is anybody has got the shadow around windows (composite/xcompmgr), with 3D accel enabled ??

---

### Post by Zingam on 2005-06-09
[QUOTE=manatlan]it's a new graphical frontend to install the drivers
i've tried it, it works .... but have built my ko in a wrong folder ...
i moved it to the good place ... and it works well

my 9200 ati card,  fglrxinfo :
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 8500 Prototype DDR Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 1.3.1003 (X4.3.0-8.14.13)

QUESTIONS :
1) is it normal that it show "8500", when my card is a 9200 ?

2) it seems that DRI and COMPOSITE are not able to work together
is anybody has got the shadow around windows (composite/xcompmgr), with 3D accel enabled ??[/QUOTE]
 It is not graphical it is text based! Really :) There are no shiny windows (as these from the screenshots) but an ugly text based interface.

I've installed the driver with the installer and it works. I had to manually delete all the fglrx.ko files because the system was loading the older module found in Ubuntu.

And although that it works, when I press ctrl+alt+Fx (anything from F1 to F6) and then I try to switch to the graphic interface the computer crashes... like all previous ATI drivers. Anyone having the same problem?

BTW: don't forget to rung fglrxconfig. If you have a problem with xkb then edit xorg.conf and replace xfree86 with xorg.

For those who don't have the development packages... install GCC (full), build-essentials, etc.

Note: :) Linux is still a system for Hackers & Programmers, not Users and I guess it will always be that way. Linux <> Desktop system.

---

### Post by Zingam on 2005-06-09
> QUESTIONS :
1) is it normal that it show "8500", when my card is a 9200 ?

I don't think so. 8500 is quite different from 9200 or maybe not? Hmm... I don't know.

I have M11 but ATIs drivers always report it as M10. There is probably no difference between M11 and M10 but the higher clock speeds.

---

### Post by mendicant on 2005-06-09
I think the graphical installer refers to the ATI Driver Installer:
ATI Driver Installer
	Download
	35.1 	06/09/05 	Version: 8.14.1

[http://www2.ati.com/drivers/linux/ati-driver-installer-8.14.13.run](http://www2.ati.com/drivers/linux/ati-driver-installer-8.14.13.run)

---

### Post by manatlan on 2005-06-09
[QUOTE=Zingam]And although that it works, when I press ctrl+alt+Fx (anything from F1 to F6) and then I try to switch to the graphic interface the computer crashes... like all previous ATI drivers. Anyone having the same problem?[/QUOTE]

i'd got the same problem and i'd replaced

Option "UseInternalAGPGART" "yes"

by

Option "UseInternalAGPGART" "no"

and it works great .... hope it helps

note : there are windows in gtk1.x in the new installer ! sure ...

---

### Post by Cynon on 2005-06-09
Na

---

### Post by GazaM on 2005-06-09
Ok, I am really happy with ATI now for finally bringing a graphical installer to make my life easier. I installed the drivers without a hitch, and for the first time ever didn't get a black screen! Bad news is that I forgot to remove restricted-modules before install and I got the driver version does *NOT* match module etc. error. So I uninstalled the restricted-modules and I now get this error in the log:

> [drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

So I basically have no module. Could someone please tell me how to fix this? I have never gotten 3d accel working with my X700Pro before and I feel that this may be it if I could get the module. Any help is GREATLY appreciated. Thanks.

---

### Post by barnone on 2005-06-09
[QUOTE=manatlan]i'd got the same problem and i'd replaced

Option "UseInternalAGPGART" "yes"

by

Option "UseInternalAGPGART" "no"

and it works great .... hope it helps

note : there are windows in gtk1.x in the new installer ! sure ...[/QUOTE]

I tried this and still have the same problem.  Radeon 9800 Pro 128MB here.

-barnone

---

### Post by manatlan on 2005-06-10
[QUOTE=GazaM]Ok, I am really happy with ATI now for finally bringing a graphical installer to make my life easier. I installed the drivers without a hitch, and for the first time ever didn't get a black screen! Bad news is that I forgot to remove restricted-modules before install and I got the driver version does *NOT* match module etc. error. So I uninstalled the restricted-modules and I now get this error in the log [...]
[...]So I basically have no module. Could someone please tell me how to fix this? I have never gotten 3d accel working with my X700Pro before and I feel that this may be it if I could get the module. Any help is GREATLY appreciated. Thanks.[/QUOTE]

if it's like me ...
the **new intaller of ati** had build my kernel module (.ko) in :
/lib/modules/fglrx/fglrx.2.6.10-5-686.ko (and a symbolic link in the same place ?!)
i'd juste have to move it to :
/lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx.ko
and xorg was able to boot correctly, with the DRI (3D acceleration)

hope it help

---

### Post by Zingam on 2005-06-10
[QUOTE=manatlan]if it's like me ...
the **new intaller of ati** had build my kernel module (.ko) in :
/lib/modules/fglrx/fglrx.2.6.10-5-686.ko (and a symbolic link in the same place ?!)
i'd juste have to move it to :
/lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx.ko
and xorg was able to boot correctly, with the DRI (3D acceleration)

hope it help[/QUOTE]
 or delete all fglrx.ko-s before installing the drivers!

---

### Post by Curlydave on 2005-06-10
Two questions.

1: Should you just install them, or build a debian specific package?

2: How do you install the xorg version? The site says that the installer has both, but I can only get it to install hte xfree version; the tutorial shows you a "customize" option that lets you pick, but in the actual installer is MIA. (much like the pretty gui shots they also show on the site.) I think this is why it's giving me that DRI error and really low fps with glxgears, and not letting me run fgl_glxgears. If I do that apt-xorg fix thing  it works, but according to the ATI control panel, it is then using the older drivers, as it tells you the driver version.

---

### Post by Abild on 2005-06-10
I've just got the driver working now :D

The only ting i had to do was to remove the fglrx driver included in the kernel from this location: /lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx.ko

Then the driver installed without problems. I'm getting about 8000 fps in glxgears with my X800XL.

fglrxinfo output:
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XL Generic
OpenGL version string: 1.3.5140 (X4.3.0-8.14.13)

---

### Post by somez on 2005-06-10
[QUOTE=Abild]I've just got the driver working now :D

The only ting i had to do was to remove the fglrx driver included in the kernel from this location: /lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx.ko

Then the driver installed without problems. I'm getting about 8000 fps in glxgears with my X800XL.

fglrxinfo output:[/QUOTE]

My only use Mesa3D and I don't know why :-((
I have a Radeon 9550. Which option should I check to work? Maybe I should set agpgart=y?

---

### Post by brj on 2005-06-10
hi,

the same question as always ;)

does the driver work with a tft connected on the dvi output ?

jakob

---

### Post by GazaM on 2005-06-10
OK, I got the module installed, and now I'm back to getting a black screen ](*,) ! I have had a look at the log and it's stopping at the exact same spot as in the last drivers, here:

> ...
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) fglrx(0): I2C bus "DDC" initialized.
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) fglrx(0): Connector Layout from BIOS -------- 
(II) fglrx(0): Connector0: DDCType-1, DACType-0, TMDSType--1, ConnectorType-2
(II) fglrx(0): Connector1: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(**) fglrx(0): MonitorLayout Option: 
	Monitor1--Type AUTO, Monitor2--Type AUTO

(II) fglrx(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) fglrx(0): I2C device "DDC:ddc2" removed.
(II) fglrx(0): DDC detected on DDCType 2 with Monitor Type 3

that's it, nothing after that?! So now I'm back with vesa :? If anybody can help I'd appreciate it greatly. When the module was missing the everything went fine (except 3d accel obviously) so why is it that when the fglrx driver is actually there the driver crashes!!??

---

### Post by Curlydave on 2005-06-10
[QUOTE=brj]hi,

the same question as always ;)

does the driver work with a tft connected on the dvi output ?

jakob[/QUOTE]

I'm having issues with it, but I strongly doubt that the DVI connection has anything to do with it.

---

### Post by noerej on 2005-06-10
Well, for the first time since I've been using Linux, the drivers installed without a hitch, and fglrxconfig did'nt mess up my xorg.conf as well!
In comparison to the last drivers, my glxgears scores went up from 3300 something to 4500 something!! I think it might be related to the agpart stuff, I don't know if it was enabled or not, but now it's not. 
Great job ATI!

---

### Post by daveisadork on 2005-06-10
Does Xinerama work in this one? I wish I could use the ATI drivers but their "big desktop" setting is a joke. Do they have it where it behaves like a proper dual monitor setup yet?

---

### Post by brj on 2005-06-10
[QUOTE=Curlydave]I'm having issues with it, but I strongly doubt that the DVI connection has anything to do with it.[/QUOTE]

you got me wrong. 
usually i have no problem with the ati driver when using the analog output, but as soon as i want to use the dvi the screen gets black.

---

### Post by Iuliux on 2005-06-10
I've got also a big problem...i've installed the driver but it works only on the default kernel...I woul like it to run on my 2.6.11.1-k7 kernel... what do i have to do?

---

### Post by Curlydave on 2005-06-10
[QUOTE=Iuliux]I've got also a big problem...i've installed the driver but it works only on the default kernel...I woul like it to run on my 2.6.11.1-k7 kernel... what do i have to do?[/QUOTE]

Uninstall the other kernal. (386 I'm guessing.) If you're using an AMD, no reason to keep the intel kernel, as the K7/K8 ones have some amd-specific optimizations.

---

### Post by Curlydave on 2005-06-10
[QUOTE=Curlydave]Two questions.

1: Should you just install them, or build a debian specific package?

2: How do you install the xorg version? The site says that the installer has both, but I can only get it to install hte xfree version; the tutorial shows you a "customize" option that lets you pick, but in the actual installer is MIA. (much like the pretty gui shots they also show on the site.) I think this is why it's giving me that DRI error and really low fps with glxgears, and not letting me run fgl_glxgears. If I do that apt-xorg fix thing  it works, but according to the ATI control panel, it is then using the older drivers, as it tells you the driver version.[/QUOTE]


anyone?

---

### Post by Iuliux on 2005-06-10
1)sudo apt-get install xorg-driver-fglrx
2)fglrxconfig
3)echo fglrx | sudo tee -a /etc/modules
4)sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

---

### Post by songochain on 2005-06-10
Well guys, anyone can run ati control panel? If i try do it i get this error:
```
fireglcontrolpanel: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```
Thanks

---

### Post by Iuliux on 2005-06-10
[QUOTE=songochain]Well guys, anyone can run ati control panel?[/QUOTE]
what's the command for that?

---

### Post by Curlydave on 2005-06-10
Got it working! It was either the restricted modules or the fglrx.ko files that were messing me up, as I deleted both as indicated in this thread. (Duh you need to uninstall the old fglrx driver.) I then ran the script, changed "ati" to "fglrx" in xorg, and boom, 1900 more fps in glxgears! (~5100 to ~7000) My fgl_glxgears score is now ~1250.

ATI control panel should be installed in the gnome menu. It's useless though, and doens't include even the most basic 3D settings. I'll ask this for the millionth time: How do you turn on 3d settings such as AA, AF, vsync, Triple buffering etc?

---

### Post by Zeroedout on 2005-06-11
if you generate your xorg.conf with fglrxconfig, you will have a section with this :
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"

My guess would be if you change the first option to yes and the second to .......... you've got it.

---

### Post by hellraiser_rob on 2005-06-11
[QUOTE=Curlydave]Got it working! It was either the restricted modules or the fglrx.ko files that were messing me up, as I deleted both as indicated in this thread. (Duh you need to uninstall the old fglrx driver.) I then ran the script, changed "ati" to "fglrx" in xorg, and boom, 1900 more fps in glxgears! (~5100 to ~7000) My fgl_glxgears score is now ~1250.

ATI control panel should be installed in the gnome menu. It's useless though, and doens't include even the most basic 3D settings. I'll ask this for the millionth time: How do you turn on 3d settings such as AA, AF, vsync, Triple buffering etc?[/QUOTE]

aren't these directX features?

---

### Post by Curlydave on 2005-06-11
[QUOTE=hellraiser_rob]aren't these directX features?[/QUOTE]

Not at all. These are fundamental 3D settings that are extremely important, and are in OpenGL/D3D.

---

### Post by Caboto on 2005-06-11
[QUOTE=Zingam][...]
BTW: don't forget to rung fglrxconfig. If you have a problem with xkb then edit xorg.conf and replace xfree86 with xorg.
[...][/QUOTE]
After downloading kernel headers (which took me about 60mins to find out, that they're missing, because the installer doesn't print out an error message (only to the log, of course) :roll: ), moving the fglrx.ko to the right directory and replacing xfree86 with xorg in my xorg.conf at the XKB section, the driver is now running.
Thanks for the help guys! :)

---

### Post by songochain on 2005-06-11
[QUOTE=Iuliux]what's the command for that?[/QUOTE]
fireglcontrolpanel
Still i cant run it

---

### Post by esh on 2005-06-12
[QUOTE=Abild]I've just got the driver working now :D

The only ting i had to do was to remove the fglrx driver included in the kernel from this location: /lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx.ko

Then the driver installed without problems. I'm getting about 8000 fps in glxgears with my X800XL.

fglrxinfo output:[/QUOTE]
THANK YOU!!!!!!! :D :D :D

I've used so f**king much time to get this to work...and now its just working...thank you very much :)

(Men nu er du jo også dansker...vi er jo generelt klogere end andre;-))

---

### Post by rugmonster on 2005-06-12
Has anyone figured out how to get the module to load when receiving this error?

FATAL: Error inserting fglrx (/lib/modules/2.6.11-1-amd64-k8/kernel/drivers/char/drm/fglrx.ko): No such device

I tried last night and again this morning. I see that the module is installed there, I have build-essentials and the kernel headers installed. It appears to build fine (with the exception of the following:

Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3

Otherwise, I've tried copying the module file to the alternate locations, run depmod -a and still get the "No such device" error. I've got a Sapphire 9800XT. Here is the output from lspci.

0000:01:00.1 Display controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT] (Secondary)

---

### Post by daveman on 2005-06-15
[QUOTE=ferdy]can you tell me, how do you install the driver?
==============================
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
failed.
[Error] Kernel Module : Failed to install compiled kernel module - please consult readme.[/QUOTE]
I have this same problem, have you found a fix?

---

### Post by ferdy on 2005-06-16
yes i have a result.

- install build-essential and the  linux-headers
- xorg.conf change ati to fglrx and insert Option "UseInternalAGPGART" "no"

- than run the install, ignore the Error
- ATI build the kernel module (.ko) in : /lib/modules/fglrx/fglrx.2.6.10-5-686.ko
- move it to : /lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx.ko
- that is it

I hope i could help you.

---

### Post by daveman on 2005-06-16
Thanks, but running into this when I X starts.

> 
(EE) No devices detected.

Fatal server error:
no screens found


I have
> 
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 (M7 LW)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseInternalAGPGART"	"no"
EndSection


My screen definition hasn't changed at all from before when it was working with the ati driver.

---

### Post by ackattack on 2005-06-18
OK, this is probably something obvious... but I've got the new ati drivers loading by following all the above (AMD64 system), no longer getting any errors in my /var/log/Xorg.0.log, but ATI control panel will not run and most disturbingly OpenGL seems broken... 

attempting to run glxgears results in

> glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

the libGL.so.1 symlink seems fine, not broken, and points to 

> libGL.so.1 -> /usr/X11R6/lib/libGL.so.1.2

what am I missing?

---

### Post by ackattack on 2005-06-18
disregard...   I was able to get it to work by using the .rpm package with alien (and killing X prior to the install).

Now everything's working fine including TV out.  

What I did was uninstall the xorg-driver-fglrx using the package manager.
Install linux-kernel-headers
install linux-restricted-modules

quit X using ctrl-alt-F1   sudo /etc/init.d/gdm stop
sudo alien fglrx*.rpm
sudo dpkg --force-overwrite -i fglrx*.deb
cd /lib/modules/fglrx/build_mod
sudo sh make.sh
cd ..
sudo sh make_install.sh
sudo modprobe fglrx
sudo fglrxconfig
startx

everything now works great.  glxgears gives 2700 with my radeon 9600 pro.

---

### Post by ferdy on 2005-06-18
@ daveman
sorry, I don`t have an answer.

---

### Post by Philodox on 2005-06-19
I've got a similar problem as somebody before, the installation completes until it gets to the postprocessing phase, then I get this error message: "[Error] Kernel Module : Failed to install compiled kernel module - please consult readme."

The complete error log is pasted below.  When I try doing "sudo modprobe fglrx" I get the error message "FATAL: Error inserting fglrx (/lib/modules/2.6.10-5-686/kernel/drivers/char/drm/fglrx.ko): Operation not permitted"

> [Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-686/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-686'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/nvidia-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agpgart_be.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/i7505-agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
In file included from /lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:125:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:56:48: warning: backslash and newline separated by space
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:57:6: warning: backslash and newline separated by space
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.h:58:41: warning: backslash and newline separated by space
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_putminor':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:508: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:510: warning: `inter_module_unregister' is deprecated (declared at include/linux/module.h:578)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `firegl_stub_register':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:530: warning: `inter_module_register' is deprecated (declared at include/linux/module.h:577)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:561: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: At top level:
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:2647: warning: initialization from incompatible pointer type
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c: In function `__ke_agp_uninit':
/lib/modules/fglrx/build_mod/2.6.x/firegl_public.c:3185: warning: `inter_module_put' is deprecated (declared at include/linux/module.h:582)
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
failed.
[Error] Kernel Module : Failed to install compiled kernel module - please consult readme.

---

### Post by Chetic on 2005-06-19
[QUOTE=Chetic]I installed everything with the installer, pretty much went for most stuff default in fglrxconfig and restarted, but now I get this everytime I try to start a GL application:
> glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

I have an X800XL which is SUPPOSED to work with this release.
I'm using the 64-bit stuff all the way.[/QUOTE]

I'm STILL having this problem! I can't even start mplayer, so I tend to stay away from GNU/Linux now... which is horrible.
PLEASE somebody PLEASE help me with this.

---

### Post by GreatSunJester on 2005-06-19
O....K....

I have followed every suggestion from the various posts about the ATI drivers to no effect.  Before I get to the newbie request, I wonder:  When I run the ATI installer, I never get the GUI installer -- only a text based one.  Yes, this is the 8.14.13 downloaded from ATI.

System is P4 2.4, 1gig ram, 160 and 80 gig HDs (ubuntu on part of the 80), onboard sound and NIC, ATI 9800pro 128 meg

Now the newbie request,  Assume my Ubuntu install is fresh (it is, I installed it as a dual boot on this computer yesterday), what steps should I do BEFORE I try to install the ATI drivers?   Simply put, can someone give me the hoops I must jump through to prepare my system to actually install the ATI drivers the first time I try?

---

### Post by Fuzzlet on 2005-06-23
[QUOTE=ackattack]disregard...   I was able to get it to work by using the .rpm package with alien (and killing X prior to the install).

Now everything's working fine including TV out.  

What I did was uninstall the xorg-driver-fglrx using the package manager.
Install linux-kernel-headers
install linux-restricted-modules

quit X using ctrl-alt-F1   sudo /etc/init.d/gdm stop
sudo alien fglrx*.rpm
sudo dpkg --force-overwrite -i fglrx*.deb
cd /lib/modules/fglrx/build_mod
sudo sh make.sh
cd ..
sudo sh make_install.sh
sudo modprobe fglrx
sudo fglrxconfig
startx

everything now works great.  glxgears gives 2700 with my radeon 9600 pro.[/QUOTE]

I just want to give you a **BIG BIG** THANK YOU!!!!

I've been trying for days to get this driver installed, and your way finally worked. THANKS AGAIN!!!

---

### Post by phantom on 2005-06-23
I'm stuck with the installation, I have always been able to install ATI drivers but now  ](*,) 

I installed using the new ATI Gfx installer, all went well, module compiled, I ran fglrxconfig, that went ok also, X starts, but I'm still on MESA GLX.

```
manu@tuxtop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
``` 

When I check if the module is loaded, and/or I try to load it with a modprobe fglrx, I get this:

```
manu@tuxtop:~$ lsmod | grep fglrx
fglrx                 237088  0
``` 

That looks like the module is loaded but when I check with Dmesg:

```
[fglrx] module unloaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
[fglrx] Maximum main memory to use for locked dma buffers: 680 MBytes.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
[fglrx] module unloaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
[fglrx] Maximum main memory to use for locked dma buffers: 680 MBytes.
ACPI: PCI interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[fglrx] module loaded - fglrx 8.8.25 [Jan 14 2005] on minor 0
[fglrx:firegl_unlock] *ERROR* Process 8796 using kernel context 0
``` 

That doesn't look good, and don't have a clue what it's all about.

I did install this time using the i686 kernel because I had some trouble getting ndiswrapper to work with my wifi card and the i386 kernel.

All my kernel patches, sources and headers are there.

Card: Ati Mobility 9700 Pro 128mb
CPU: Amd64 Mobile 2800+
OS: Kubuntu, fully upgraded to KDE 3.4.1.

Oh, I've seen somewhere gcc-4.0-base being installed, could that cause any trouble ?

---

### Post by StacyWebb on 2005-06-23
run 
sudo fglrxinfo

and tell us what your results are, 

I have noticed that the new ati drivers give 3d to root but not to the local user. This may be your issue.

---

### Post by phantom on 2005-06-23
Thanks, but I just found the problem.

There was another fglrx.ko files, but this one was included in the kernel source, that was causing trouble.

This has resolved the problem:

 ```

sudo rm /lib/modules/2.6.10-5-686/kernel/drivers/video/fglrx.ko
sudo rm /lib/modules/2.6.10-5-686/kernel/drivers/char/drm/fglrx.ko              

``` 

Reinstalled the driver, rebooted, and all ok now  :grin: 

The same kind of problem happened while installin ndiswrapper, they should include a routine in their installation scripts that checks for these things.

---

