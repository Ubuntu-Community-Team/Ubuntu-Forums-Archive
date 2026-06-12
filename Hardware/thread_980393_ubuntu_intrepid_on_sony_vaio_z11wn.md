---
title: "ubuntu intrepid on sony vaio z11wn"
date: 2008-11-12
forum: Hardware
---

### Post by thetom on 2008-11-12
hi everyone!!
i'm an italian ubuntu user, but I write here because anyone in italian forum can help me!I apologize for my english..
I'm to trying to get intrepid work on my new sony vaio vgn-z11wn.
here's a little hardware description:
- CPU intel p8400 @ 2,4 ghz
- Ram: 4GB ddr3
- Hard disk : 250GB (190GB Vista, 15GB UBUNTU,25GB empty fat32 )
- Screen 13" resolution 1600x900
- GPU1 nvidia geforce 9300M GS 256mb
- GPU2 Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller
(the 2 GPUs are selectable with a switch but can't be powered off from the bios)
- wireless: intel wireless wifi link 5100
- ethernet:Intel® 82567LM Gigabit Network Connection

I've installed ubuntu 8.10 correctly, but there are several problems:
1- nVidia drivers don't work, I tried both 173 and 177, and tried a couple of xorg.conf setting but nothing want to work. when ubuntu starts I have only the login textual mode.
2- The fun is always running the temperatures are hot.
3- when I plug some headphones they work correctly but both notebook speaker and headphone work toghether.
4- I have a integrated 3G module but I can't make it work
5- The battery doesn't last as much as with vista. In Vista using stamina mode i have about 5 hours of autonomy. with ubuntu at laest 2 hours.
6- I can't make the webcam(motion eye) work.

I can't correct these problems..so, please help me...
here's my lspci:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
06:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
0b:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
0b:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
0b:04.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
0b:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)

so, can someone please help me? thank u so much!!!

---

### Post by piernoli on 2008-11-19
Hi,
I have a sony vaio vgn-z21vn, which is very similar to yours and I am experiencing the same problems.
This is the output of  lspci:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
06:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
0b:04.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
0b:04.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
0b:04.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
0b:04.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)



The greatest problem is the speed/stamina switch (and relative change in video cards): I think this switch is not working under intrepid.
The two status leds of the switch are both off in both modes and video cards are both presents in each position of the switch (no differences in lspci in the two configurations). 
This sounds very bad because other solutions to switch between the two modes under linux use the differences in lspci (see: [http://ariel.vardi.free.fr/ariel//vaiosz.html](http://ariel.vardi.free.fr/ariel//vaiosz.html)) 

I tried to install ubuntu nvidia dirvers and to use the script NVIDIA-Linux-x86-177.80-pkg1.run without success. I also modified the xorg.conf (generated by nvidia-xconfig) by putting Busid "PCI:1:0:0", but I got the following errors:

(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0.
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) Screen(s) found, but none have a usable configuration.


I am also very worried because the fan is always running...

My webcam is working, at least in skype, while I did not fint a way to have the internal microphone working (I didn't try an external one)


Of course hibernate/sleep don't work.


I also have problems with volume keys : mute works, but volup and voldwn only show the current volume level without modifying it


Any help is appreciated.

Thanks,
pier

---

### Post by acolebourne on 2008-11-19
This thread is discussing a similar topic [http://ubuntuforums.org/showthread.php?p=5933425](http://ubuntuforums.org/showthread.php?p=5933425)

Hope this helps. Hopefully we'll find a solution soon :)

---

### Post by piernoli on 2008-11-20
Many thanks acolebourne,
I'll keep an eye on that thread.

---

### Post by jollo on 2008-11-21
Ciao everyone (I'm an Italian user too ;) )

I have exactly the same problem with Intrepid on a Vaio Z21VN (very handsome machine, btw): *both* VGA adapters are always on, regardless of the switch position (which is clearly a "soft" switch)

```
brunello@brunello-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev 
```

This is already bad for battery life, but it's even worse because X seems to be confused by this configuration when autodetecting on startup and, with the nVidia driver (177) installed, strands me to the command line. 

So, a first minimal question could be: never mind the switch, never mind the power waste of having 2 adapters constantly on, but how can I manage to get Xorg to get straight to nVidia@1600*900 with the proprietary driver and just ignore Intel? Or, second-best option, use only the Intel adapter and ignore nVidia? 

A second step could be: how can we permanently disable one of the VGA adapters? By "permanent" I mean that the choice would be hard-coded in some configuration files and never mind switching on the fly between the two (no chip eradication, please :) ). This would of course solve automatically question 1, but I suspect it's harder to get to and would involve reverse-engineering feats.

A third and final step would be: how do I switch between the two adapters without rebooting, ideally using the physical switch intended for such use?

I sincerely hope someone can help us, because it is quite distressing to keep on saying to friends and co-workers "no, don't install Ubuntu on your new Vaio yet because you get stuck to command line"...

Thanks

---

### Post by jollo on 2008-11-21
A few more info:

the relevant lines of lspci are in the previous post, and show how 2 adapters are simultaneously active in the system. 

After installing nVidia driver 177.80-0ubuntu2 with EnnyNG and restarting, X fails to startup and I get the following Xorg.0.log (edited for relevance):

```
(!!) More than one possible primary device found
(--) PCI: (0@0:2:0) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xe8400000/0, 0xd0000000/0, I/O @ 0x00008130/0
(--) PCI: (0@1:0:0) nVidia Corporation GeForce 9300M GS rev 161, Mem @ 0xe4000000/0, 0xc0000000/0, 0xe2000000/0, I/O @ 0x00007000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  177.80  Wed Oct  1 15:06:06 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  177.80  Wed Oct  1 14:45:01 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: 
(EE) No devices detected.

Fatal server error:
no screens found
```

I then tried to "force" usage of the nVidia video device (in order to pursue the "minimal" solution described in the previous post) by editing my Xorg.conf file:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	BusID	"PCI:1:0:0"
EndSection

```

but the result is still not quite satisfying; this is the Xorg.0.log I get:

```
(!!) More than one possible primary device found
(--) PCI: (0@0:2:0) Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xe8400000/0, 0xd0000000/0, I/O @ 0x00008130/0
(--) PCI: (0@1:0:0) nVidia Corporation GeForce 9300M GS rev 161, Mem @ 0xe4000000/0, 0xc0000000/0, 0xe2000000/0, I/O @ 0x00007000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  177.80  Wed Oct  1 15:06:06 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  177.80  Wed Oct  1 14:45:01 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: 
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

So I seem to get a bit further along the road, but the nVidia graphic device still fails to initialize. Can anybody suggest how to troubleshoot this?

Thanks and cheers

---

### Post by thetom on 2008-11-22
I took a look around and i've understood something useful.
windows vista blocks the stamina/speed switch somehow and it can't be correctly seen and used under linux.
it's explayned in the site posted in the thread advised by acolebourne. here's the [ link ]("http://neotokyo.sytes.net/vgn-z11/Ubuntu8.10_vaio_vgn_z11.html") .
so,IMHO if you want to have the cards correctly working you have to install xp and delete vista.
has someone tried to ask something to the sony support center?
maybe they know something that we don't know...

---

### Post by jollo on 2008-11-23
> **thetom said:**
> ...
so,IMHO if you want to have the cards correctly working you have to install xp and delete vista.
has someone tried to ask something to the sony support center?
maybe they know something that we don't know...

I don't mean to sound disrespectful of the various efforts to get things going, but I think that booting Windoze (never mind if XP or Vista) just to select the video card prior to every Linux boot is pushing it a little too far even for a workaround.

I am confident that if we can get someone who knows a little his way around in Xorg innards, finding a way to ignore the Intel adapter and using only the nVidia card shouldn't be so hard (I imagine through a little xorg.config tweaking or a purposeful randr, though I personally have no clue... yet).

I'm noticing that this thread is just between us newbies: hey, dear Ubuntu-gurus, soul of this community: hear us *bump* this issue and, please, let us hear at least some clear-headed ideas.

Btw, there is another [thread]("http://ubuntuforums.org/showthread.php?t=939580") on this exact issue: perhaps merging the two would be useful to concentrate efforts.

Thanks!

---

### Post by thetom on 2008-11-23
you're right jollo, but it seems that no one want to listen us..
i've wrote some posts both in ubuntu english forum and in italian one, but I didn't recive any good news. 
I really hope that someone would listen us!

---

### Post by thetom on 2008-11-27
and what about the other problems like webcam or the 3g module or the audio??? has anyone found any issue to solve these problems??

---

### Post by robsearles on 2008-12-01
Hi TheTom

I too am trying to get Intrepid on my Vaio Z11WN and I've encountered similar problems to you.

I can't get nVidia working (as discussed above, currently dual booting with Vista and I have no intention of installing XP)

Not sure if you have managed to yet, but for benefit of Googlers out there I have managed to get the Intel graphics card working by adding the BusID to the Device section in xorg.conf
```

Section "Device"
        Identifier      "Configured Video Device"
        Busid   "PCI:0:2:0"
        Driver  "intel"
EndSection

```

I found the PCI value by running
```
lspci | grep -i "vga"
```
and it outputted
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)

```

The "00:02.0" above is translated to "PCI:0:2:0" in xorg.conf
(I tried using PCI:1:0:0 but doesn't work)

**Headphones**

Exactly the same was happening to me. I'm running Xubuntu and the volume control didn't help, but then I tried the Gnome Volume Control by running
```
gnome-volume-control
```
You'll see there is a "Front" switch, which when muted cut off the sound from the main speakers stop, but the headphones carry on working. No idea if a fluke for me, but is working and that's all that matters


**Webcam**

I have only tested it with Cheese
```
sudo apt-get install cheese
```
and appears to be working fine. But I haven't used anything else with it so it might just be a cheese thing

Hope this helps.

I still have loads to try and fix - reboot, hibernate, screen brightness, microphone etc etc etc! But if I make any progress I'll post it on the board.

One another note, going back to the nVidia thing, is anyone single booting Intrepid (no XP or Vista) and if so, does it work?

Have fun
Rob

---

### Post by lowtraxx on 2008-12-02
Hi,

there are more discussions going on concerning this issue. We should merge the info we gather somewhere, and look if we can go on from there together.

Threads with the same topic:
[http://www.nvnews.net/vbulletin/showthread.php?p=1861296#post1861296]("http://www.nvnews.net/vbulletin/showthread.php?p=1861296#post1861296")
[http://ubuntuforums.org/showthread.php?p=5933425]("http://ubuntuforums.org/showthread.php?p=5933425")

Any Suggestions (like a wiki or something)

Greetz

---

### Post by pandora26 on 2008-12-03
Hi guys,

Just bought a new vaio vgn z11mn and I'm experiencing the same problems as all of you. I followed the different threads without success. Did someone already figured out how to make work the stamina/speed switcher? Case not, has someone been able at least to make the nVidia card work?

Greets

Antonio

:(

---

### Post by robsearles on 2008-12-03
Hi lowtraxx, sounds like a good idea to me. I'm not massively up on the technical details of all this, just following stuff in the forums but I'll be glad to help out if I can. 

Antonio, from what I understand there currently isn't a fix to get the nVidia card working. The speed/stamina switch is apparently now a software switch, not hardware like it was on the old SZ* version, and as such work needs to be done on this - but it'll have to be someone much brighter than me :)

---

### Post by pandora26 on 2008-12-04
All this sounds awful. I hope someone finds a solution soon. In the meantime I'll work with the Intel built-in card but the pity is I cannot use the extra visual effects and, therefore, compiz manager! Does anyone knows if this card supports 3d effects with some specific driver?

---

### Post by robsearles on 2008-12-04
I managed to get some of the desktop effects working, after installing "Advance Desktop Effects Settings (ccsm)" and "Compiz Fusion Icon", but thinking about it no fancy 3D stuff. I don't really use all the advanced stuff anyway as I have a dual monitor setup and I found it slowed it down too much, so have now disabled compiz.

Hopefully we can persuade one of the big brained Ubuntu guys to tackle this problem! Till then we'll have to struggle on :)

---

### Post by pandora26 on 2008-12-04
Yes, I know, but I'm really touchy with these things!

By the way, I know is not the correct thread but since most of us have a z-series vaio perhaps someone encountered the same problem I did when rebooting. It never finishes the restart process and the last thing you can see, before manually assisting it, is a black screen and the green light of the power button. Any idea on how to fix this?

---

### Post by AlanR8 on 2008-12-04
I run a Vaio, but a VGN-FZ21S and had the same audio issue, plug headphones in and the speakers did not mute. I found the following fix n these forums, respect to the original author:

> Edit /etc/modprobe.d/alsa-base (sudo gedit /etc/modprobe.d/alsa-base) and add this in the bottom of it

options snd-hda-intel model=vaio

then do this:

sudo apt-get install linux-backports-modules-$(uname -r)


Worked for me

Still haven't found a fix for my web cam though

---

### Post by piernoli on 2008-12-08
> **thetom said:**
> and what about the other problems like webcam or the 3g module or the audio??? has anyone found any issue to solve these problems??
I have found another issue: my SD card and Memory Stick readers are not working!!!

---

### Post by hihihi on 2008-12-11
for those who happen to have a sony VAIO FZ or with an Nvidia-card in it, and not being able to control brightness of LCD, try this how to:

[http://ubuntuforums.org/showthread.php?p=6325299#post6325299](http://ubuntuforums.org/showthread.php?p=6325299#post6325299)

works very well on mine!



for those who have a sony with the STAMINA-switch try the following, if you know what u are doing, own risk:

we need a script for recognition of the video-card that is selected at boot-up: this script will automatically link to the right libs and will also link to right xorg.conf.
at the end it works like on windows: u switch u boot up and it is working.

1.)
create a working xorg.conf for your intel-card, name it 'xintel' and save it inside your home-dir ~/
or if you are currently on intel-card and your xorg.conf is working just copy that like this into your home-dir:

```
sudo cp /etc/X11/xorg.conf ~/xintel
```

2.)
create a working xorg.conf for your nvidia-card, name it 'xnvidia' and save it inside your home-dir ~/
or if you are currently on nvidia-card and your xorg.conf is working, just copy that like this into your home-dir:

```
sudo cp /etc/X11/xorg.conf ~/xnvidia
```


3.)
now we need to create a symlink in your home-dir that it will point to /etc/X11/xorg.conf like this:

```
ln -s /etc/X11/xorg.conf ~/x
```

4.) finally we need the recognition script which will do all the job at boot-up.
please note that the last 4digits here -> libglx.so.1.0.9639 <- have to be replace with your current nvidia-driver version, and of course check if the path is right and correct this if needed.

if you first installed with your ubuntu with nvidia enabled, you will need to get the GLX-libs for intel and put them in a folder.
back than i made a folder /usr/lib/xorg/modules/extensions/intel/ and saved the intel-glx-library like this: libglx.so.intel 
also here check if the path is right and correct this if needed.


create a file:

```
 sudo gedit /etc/init.d/vaio
```

paste this into it and save it:


```
#!/bin/bash

##switch between stamina and speed mode

VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then

cp -f ~/xnvidia ~/x

ln -sf /usr/lib/xorg/modules/libglx.so.1.0.9639 /usr/lib/xorg/modules/libglx.so

ln -sf /usr/lib/libGL.so.1.0.9639 /usr/lib/libGL.so.1

else

cp -f ~/xintel ~/x

ln -sf /usr/lib/xorg/modules/extensions/intel/libglx.so.intel /usr/lib/xorg/modules/libglx.so

ln -sf /usr/lib/xorg/modules/extensions/intel/libGL.so.1.2 /usr/lib/libGL.so.1

fi
```


2.
now make it executable:

	```
sudo chmod 755 /etc/init.d/vaio
```

3.
and finally simlink it:

	```
sudo ln -s /etc/inid.d/vaio /etc/rc2.d/S12vaio
```



this should do the trick....if u do everything right, you end up with hardware-acceleration on both chops... it worked with my old laptop.

byebye

---

### Post by pandora26 on 2008-12-12
Thanks a lot for your answer

There are few things to say concerning your answer:

1) The link to the howto doesn't work

2) Your explanation for the stamina/speed switch looks very similar to the standard one (explained in other posts) that didn't worked for most of us. Anyway I'll go through it, compare it with the former ones and see if it works.

My main problem is that I only have ubuntu in my laptop so I cannot follow the procedure of booting into windows to make it detect the card and then reboot to linux. My two lights are always off and I don't even know which card is using ubuntu. Knowing which one is under use would be a good starting point. Someone has an idea?

Greetz

---

### Post by hihihi on 2008-12-12
> **pandora26 said:**
> Thanks a lot for your answer

There are few things to say concerning your answer:

1) The link to the howto doesn't work

2) Your explanation for the stamina/speed switch looks very similar to the standard one (explained in other posts) that didn't worked for most of us. Anyway I'll go through it, compare it with the former ones and see if it works.

My main problem is that I only have ubuntu in my laptop so I cannot follow the procedure of booting into windows to make it detect the card and then reboot to linux. My two lights are always off and I don't even know which card is using ubuntu. Knowing which one is under use would be a good starting point. Someone has an idea?

Greetz



ok, i corrected the link, it should be ok now.

about the switch:
on my old laptop, i did install ubuntu with the switch on nvidia.
once i got nvidia-card fully working, i dived into the stamina-switch thing.
on that laptop things were like this:
shut-down, switch to intel, boot, and it is intel working. 
the first script i had found on the net regarding stamina was useful, but when i would switch to intel, the xserver would crash before login. so i would always have to go to ctrl+alt+f1 and cp the right xorg.conf and restart gdm. so later i added this to the script  and i had to do nothing.

i do not know why you have to go to windows to switch the card.
but i hope this little how-to gives you some more inspiration on the way...

good luck.:KS

---

### Post by pandora26 on 2009-01-03
I will take the opportunity to report herein some other problems I've encountered the last two weeks in my vaio vgn z11-mn with ubuntu intrepid.

* The internal microphone is not working. I get no errors when testing it and apparently everything works fine but I never get to hear what I've recorded.

* I cannot reboot. It gets freezed in the last stage of the process.

* Fn+FX keys don't work. Just F2,F3 and F4 (related with volume) do their work. I've tried the workaround related with brightness without success.

* The Pro Magic Gate slots for memory cards don't work neither.

Does anyone has a solution for any of this problems?

---

### Post by lowtraxx on 2009-01-12
> * I cannot reboot. It gets freezed in the last stage of the process.


In this case a BIOS Update helps.


> * The internal microphone is not working. I get no errors when testing it and apparently everything works fine but I never get to hear what I've recorded.


Microphone works fine here, maybe a BIOS/EFI issue to?


> * Fn+FX keys don't work. Just F2,F3 and F4 (related with volume) do their work. I've tried the workaround related with brightness without success.


Cannot help here, as for me neither of the Cards are working right.


> * The Pro Magic Gate slots for memory cards don't work neither.


Support for that should be in the new kernel.


HTH (If a little late :))

Oli

---

### Post by pandora26 on 2009-01-12
Ok, I'll try the BIOS update but first things first: ¿Does someone happen to know how to do an upgrade without a windows partition? In VAIO website you can find instructions and executables for Windows, not for Linux goners :(

---

### Post by lowtraxx on 2009-01-12
Hi,

I think BartPE with an integrated BIOS Updater would be the way to go. The catch is that you need another Computer running Windows to manufacture one. With this CD you could boot into Windows and then apply the BIOS-Update.

Greets

Oli

---

### Post by rfer on 2009-02-28
I just bought my Vaio Z today, looks great!

About both cards...What is the current state? I recon that it's not possible to make the switch, but are they working fine if we boot XP first? I mean, if I boot XP first in speed mode is the Geforce still working AND the intel turned off?

---

### Post by rfer on 2009-03-05
Just got BOTH GRAPHICS CARDS WORKING WITHOUT BOOTING XP first!

[http://blog.shiftreduce.org/?p=13](http://blog.shiftreduce.org/?p=13)

Any doubts just ask! ;)

---

### Post by alci on 2009-04-07
You might want to have a look at [http://www.basyskom.org/~eva/log_installation_vaio_z21vnx.html](http://www.basyskom.org/~eva/log_installation_vaio_z21vnx.html)

Interesting work going on...

---

### Post by craig100 on 2009-05-17
Would there be any possibility of someone taking that work and compiling a package for Ubuntu 9.04 that we Z11 users could install and get most of our issues working?  I'm a bit of a newbie so it's just a question to the masses, but with my fingers crossed:)  Probably a bit of a big ask!

---

