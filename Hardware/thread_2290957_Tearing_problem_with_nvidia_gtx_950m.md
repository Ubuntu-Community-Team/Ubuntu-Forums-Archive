---
title: "Tearing problem with nvidia gtx 950m"
date: 2015-08-16
forum: Hardware
---

### Post by aliuygurerol on 2015-08-16
Hi,

I've recently bought a Msi ge70 2qd. It's a hybrid machine with an intel and a nvidia (gtx 950m) graphic card. I tried using Bumblebee many times but it gives error while launching in optirun mode so I abandoned. Then, I installed the latest nvidia driver with prime. It looks like there is a general tearing problem that I can't manage to fix. I tried some of the recommendations on forums but it didn't work. Can you help me with that?

Thanks in advance,

---

### Post by astralnysledz on 2015-08-17
1. Specifically, which branch of the nvidia drivers are you using? The most recent nvidia-340-* or any of the earlier editions?
2. What is the error you get when using optirun? This can fail for various reasons, from permission for bumblebee to actual problems with the drivers.
3. Did you use optirun with nvidia or nouveau?
4. Can you describe the tearing in more details? The most common I saw related to nouveau and certain Nvidia cards and showed in the form of a black or colored screen with a row of purple dots in the upper section of the screen.

Finally, could you check for your card in dmesg and post the relevant output?

---

### Post by aliuygurerol on 2015-08-17
Hi astralnysledz,

Thanks for your reply.

1 I tried every driver that ubuntu recommends in additional drivers : 355.06, 346.87, 352.30 and the 346.82. I'm using currently the last one, it's the only "propriétaire" one (sorry my ubuntu is in french), with update.
2 The error that I get was about accessing the gpu.
3 I'm sorry, I don't know what is nouveau. But if this can help: I was using nvidia-current that came with Bumblebee and then tried to update it later (I did all the stuff about, changing the driver names in config etc.). Anyway, if possible for my configuration i'd like to continue using prime. Didn't like the idea of going command line each time you start a program. 
4 The screen tearing happens each time when I watch a video (yt, vlc). In movement, the picture gets fragmented. Weird thing is games dont seem to have the problem. But I have to switch windows to watch videos...

Sorry again, I'm a newbie. Hope this is the one :

[    3.206484] i915 0000:00:02.0: irq 48 for MSI/MSI-X
[    3.206498] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    3.206499] [drm] Driver supports precise vblank timestamp query.
[    3.206534] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.213311] nvidia: module license 'NVIDIA' taints kernel.
[    3.213314] Disabling lock debugging due to kernel taint
[    3.218947] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[    3.224126] nvidia 0000:01:00.0: enabling device (0006 -> 0007)

Also, lspci : 

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM86 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 3D controller: NVIDIA Corporation Device 139a (rev ff)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5249 (rev 01)
04:00.0 Ethernet controller: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller (rev 13)
05:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)

---

### Post by astralnysledz on 2015-08-17
Dear [**[COLOR=#000000]aliuygurerol[/COLOR]**]("http://ubuntuforums.org/member.php?u=1996575"),

1. I usually try to stay clear of the Additional Drivers app, since I had major problems with it in Lubuntu 12.04 and 14.04. If something goes wrong with the installation, no error message is printed and more often than not the driver ends up in a half-installed state. I personally recommend using the Synaptic Package Manager for nvidia driver installs.

2. The error you mentioned may relate to privileges for Bumblebee or wrong directory path. Since Ubuntu offers prime we might not need Bumblebee at all.

3. Nouveau is the open-source Nvidia driver implementation. It doesn't offer as much performance as the proprietary driver, but is well integrated with the linux kernel and works for most Nvidia cards alike. 

4. If games don't have the problem, but videos do, this might relate to vdpau from the nvidia-vdpau (or similarly named) package. I randomly found this thread mentioning something similar: [http://ubuntuforums.org/showthread.php?t=1683875](http://ubuntuforums.org/showthread.php?t=1683875). VDPAU allows the Nvidia card to handle video rendering better. Check if you have it enabled. Normally VDPAU is not necessary.

dmesg output looks clean, except for the warnings concerning the nvidia kernel module. This is normal however, since the module came from a third-party source (Nvidia itself), rather than being part of the kernel proper.

lspci only shows me a list of PCI devices. lspci -k would show the kernel modules loaded for each PCI device and lspci -v their capabilities (specs).

Hope any of my advice helps :).

---

### Post by aliuygurerol on 2015-08-18
Thx for the detailed reply man. I really apreciate it but the problem still persists...

I reinstalled the drivers as u recommended. Then, as I tried many times installing Bumblebee before and didnt succed, I formated the drive and reinstalled ubuntu 14.04.3 hoping that maybe new kernel will help too...

Funny thing about nouveau : as my computer is in french I thought the line where it's written "nouveau driver" means "the new driver" :) The nouveau driver doesn't work with hybrid sistems I guess cause after installing it, Intel card became the default one. Or maybe I am wrong how does it work on a hybrid system do you have an idea?

I checked the link and VDPAU was installed but I installed another VDPAU hoping it may help : it's called "VDPAU driver with OpenGL/VAAPI backend", libvdpau-va-gl1. Also, the vdpau info gives me that : 

display: :0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  346.82  Wed Jun 17 10:02:13 PDT 2015


Video surface:


name   width height types
-------------------------------------------
420     4096  4096  NV12 YV12 
422     4096  4096  UYVY YUYV 


Decoder capabilities:


name               level macbs width height
-------------------------------------------
MPEG1                 0 65536  4080  4080
MPEG2_SIMPLE          3 65536  4080  4080
MPEG2_MAIN            3 65536  4080  4080
H264_MAIN            41 65536  4096  4096
H264_HIGH            41 65536  4096  4096
VC1_SIMPLE            1  8190  2048  2048
VC1_MAIN              2  8190  2048  2048
VC1_ADVANCED          4  8190  2048  2048
MPEG4_PART2_SP        3  8192  2048  2048
MPEG4_PART2_ASP       5  8192  2048  2048
DIVX4_QMOBILE         0  8192  2048  2048
DIVX4_MOBILE          0  8192  2048  2048
DIVX4_HOME_THEATER    0  8192  2048  2048
DIVX4_HD_1080P        0  8192  2048  2048
DIVX5_QMOBILE         0  8192  2048  2048
DIVX5_MOBILE          0  8192  2048  2048
DIVX5_HOME_THEATER    0  8192  2048  2048
DIVX5_HD_1080P        0  8192  2048  2048


Output surface:


name              width height nat types
----------------------------------------------------
B8G8R8A8         16384 16384    y  Y8U8V8A8 V8U8Y8A8 
R10G10B10A2      16384 16384    y  Y8U8V8A8 V8U8Y8A8 


Bitmap surface:


name              width height
------------------------------
B8G8R8A8         16384 16384
R8G8B8A8         16384 16384
R10G10B10A2      16384 16384
B10G10R10A2      16384 16384
A8               16384 16384


Video mixer:


feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        y
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -


parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y         1     4096
VIDEO_SURFACE_HEIGHT             y         1     4096
CHROMA_TYPE                      y  
LAYERS                           y         0        4


attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y  


Thx in advance,

---

### Post by aliuygurerol on 2015-08-18
I've just discovered that I also have the same problem in games. I installed xonotic to test and it's playable in ultra but with tearing. sorry i didnt see that before.

---

### Post by astralnysledz on 2015-08-19
The nouveau driver works with Bumblebee, but not with the nvidia-prime package, because the latter belongs to the proprietary Nvidia driver setup.

I feel you're trying to accomplish too many things at the same time. If that is not a problem, try to re-install the system again (cleanly) and test your videos before even installing Bumblebee or Nvidia drivers. By default you should have the nouveau kernel module loaded, but the card itself not accessible, because the display is connected to the integrated Intel iGPU, not to the dedicated Nvidia GPU.

Next, if there is no tearing, install the most recent nvidia drivers (nvidia-346 package, I believe), enable the card in the PRIME panel and test once more.

If you see tearing before any of the Nvidia drivers was installed, there is nothing we can do. If only after installing them, you can try to setup Bumblebee with nouveau or proprietary Nvidia drivers and somehow live with tear-free videos (run without Bumblebee's optirun) and tear-full games (run with Bumblebee's optirun, if 3D acceleration is favorable).

Last but not least, you could try Arch Linux with Bumblebee + Nvidia drivers. Arch tends to have more recent packages, excellent documentation on Bumblebee and the repos contain an additional branch of Nvidia drivers for new graphics cards (not only the 304 and 340 branches available to other distributions).

---

