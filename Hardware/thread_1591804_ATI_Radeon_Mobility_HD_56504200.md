---
title: "ATI Radeon Mobility HD 5650/4200"
date: 2010-10-09
forum: Hardware
---

### Post by pab31966 on 2010-10-09
Hello everyone,

Please forgive me if this has been covered. I searched for a solution to this problem and came up with nothing.

I just got a Toshiba A665D-S6059 The specs [are here.]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2681438&rpn=PSAX3U&modelFilter=A665D-S6059&selCategory=2756709&selFamily=1073768663") 

I'm having the exact same problem as [this poor soul.]("http://ubuntuforums.org/showthread.php?t=1541621")  I looked through this members history and it appears as though they haven't solved the problem. 

My machine has the Radeon 5650, but the system is using the 4200 as the default. The ATI software provides no method for changing it to the 5650. I've un-installed the ATI driver numerous times, but have had no luck. I just did a complete OS re-install an hour ago hoping that I may have missed something the first time. I tried to install the 64-bit version, but all I got was a blank screen after the initial reboot, so I just went back to the 32. 

Here's my grep of lspci:

```
lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]

```

The 5650 is there, the system can see it, I just can't use it. Talk about frustrating. :confused:

I've yet to re-install the ATI driver after my recent OS re-install, in the hope that there's some sort of workaround for this. Honestly, I don't mind being stuck using the 4200 with 256Mb, it's just killing me to know that the 5650 is sitting there with a full Gig of ram and it's not being used!

Can anyone give me some advice? Is it even possible to use the 5650 at this time? Am I just wasting my time? :(

Thanks in advance for any help or guidance that any of you may be able to provide.

Edit:
Here's the relevant section from my lshw the 5650 is "unclaimed" (whatever that means.):
        ```
*-pci:0
             description: PCI bridge
             product: Toshiba America Info Systems
             vendor: Toshiba America Info Systems
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
             resources: ioport:e000(size=4096) memory:fe600000-fe7fffff ioport:b0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: M880G [Mobility Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:18 memory:b0000000-bfffffff(prefetchable) ioport:e000(size=256) memory:fe700000-fe70ffff memory:fe600000-fe6fffff
           *-multimedia
                description: Audio device
                product: RS880 Audio Device [Radeon HD 4200]
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0
                resources: irq:19 memory:fe710000-fe713fff
        *-pci:1
             description: PCI bridge
             product: RS780 PCI to PCI bridge (ext gfx port 1)
             vendor: Advanced Micro Devices [AMD]
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:d000(size=4096) memory:fea00000-feafffff ioport:90000000(size=268435456)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: Redwood [Radeon HD 5600 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi cap_list
                configuration: latency=0
                resources: memory:90000000-9fffffff(prefetchable) memory:fea20000-fea3ffff ioport:d000(size=256) memory:fea00000-fea1ffff(prefetchable)
```

---

### Post by di3gopa on 2010-10-10
Hello pab, i have the same  problem, with no Luck.

I have a HP dv6-3050us

my lspci | grep VGA:
```
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff)

```

What drivers are you using? Drivers from amd page or the drivers that ubuntu recommends? I don't see drivers for Ati Radeon Mobility Radeon HD 5650 on the amd site.


I saw a thread on linuxindore, a guy that is using the ati radeon mobility 4600 drivers for the 5650. 

[Here is the link]("http://linuxindore.com/desktop-fantasy/ati-mobility-radeon-hd-5650-driver"), if you try them let me know.

Thanks :).

---

### Post by pab31966 on 2010-10-11
> **di3gopa said:**
> What drivers are you using? Drivers from amd page or the drivers that ubuntu recommends? I don't see drivers for Ati Radeon Mobility Radeon HD 5650 on the amd site.


I saw a thread on linuxindore, a guy that is using the ati radeon mobility 4600 drivers for the 5650. 

[Here is the link]("http://linuxindore.com/desktop-fantasy/ati-mobility-radeon-hd-5650-driver"), if you try them let me know.

Thanks :).I'm using the latest driver from AMD found at:[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx")

Even though I've installed the latest driver, it still defaults to the 4200 with no way to change it. I don't see a solution to this problem in the near future, but there has to be a way to tell the OS that it needs to use the 5650 and not the 4200. As my lshw code shows, the 5650 is "unclaimed". There has to be some way to claim it and use it. I'll check out the link that you found, and continue my search. Thanks for posting it.

---

### Post by borolo on 2010-10-11
> **di3gopa said:**
> Hello pab, i have the same  problem, with no Luck.

I have a HP dv6-3050us

my lspci | grep VGA:
```
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff)

```What drivers are you using? Drivers from amd page or the drivers that ubuntu recommends? I don't see drivers for Ati Radeon Mobility Radeon HD 5650 on the amd site.


I saw a thread on linuxindore, a guy that is using the ati radeon mobility 4600 drivers for the 5650. 

[Here is the link]("http://linuxindore.com/desktop-fantasy/ati-mobility-radeon-hd-5650-driver"), if you try them let me know.

Thanks :).

Same here, I have the same laptop as you. I guess you can't use the HDMI output? cause it seems it is for the 5650 only.... don't know. vga outputs ok.

---

### Post by di3gopa on 2010-10-12
As you, i cannot use the HDMI output...

---

### Post by pab31966 on 2010-10-12
> **borolo said:**
> Same here, I have the same laptop as you. I guess you can't use the HDMI output? cause it seems it is for the 5650 only.... don't know. vga outputs ok.Yeah, same here - VGA output is  good to go, no HDMI output. I searched a little more and found this [http://ohioloco.ubuntuforums.org/showthread.php?t=1560955](http://ohioloco.ubuntuforums.org/showthread.php?t=1560955) It Looks as if we're stuck using the 4200 until ATI decides to fix it.  ](*,)

---

### Post by borolo on 2010-10-14
> **pab31966 said:**
> Yeah, same here - VGA output is  good to go, no HDMI output. I searched a little more and found this [http://ohioloco.ubuntuforums.org/showthread.php?t=1560955](http://ohioloco.ubuntuforums.org/showthread.php?t=1560955) It Looks as if we're stuck using the 4200 until ATI decides to fix it.  ](*,)


Yeah I was the last one to write in that thread. Too bad HP won't let us change the Bios settings for this. Gonna have to keep watching movies on my TV with W7, oh well.

Have any of you updated to 10.10? cause I saw somewhere that we need to wait for the catalyst driver 10.10 to come out due to lack of support of the new x.org 1.9

[http://www.phoronix.com/scan.php?page=news_item&px=ODY2OA](http://www.phoronix.com/scan.php?page=news_item&px=ODY2OA)

---

### Post by di3gopa on 2010-10-15
> **borolo said:**
> 
Have any of you updated to 10.10? cause I saw somewhere that we need to wait for the catalyst driver 10.10 to come out due to lack of support of the new x.org 1.9

[http://www.phoronix.com/scan.php?page=news_item&px=ODY2OA](http://www.phoronix.com/scan.php?page=news_item&px=ODY2OA)

I am using 10.10 with no problems at all (well, obviously with the 4200...).

I am using the ati proprietary drivers supplied by the distro.

---

### Post by pab31966 on 2010-10-15
> **borolo said:**
> Yeah I was the last one to write in that thread. Too bad HP won't let us change the Bios settings for this. Gonna have to keep watching movies on my TV with W7, oh well.

Have any of you updated to 10.10? cause I saw somewhere that we need to wait for the catalyst driver 10.10 to come out due to lack of support of the new x.org 1.9

[http://www.phoronix.com/scan.php?page=news_item&px=ODY2OA](http://www.phoronix.com/scan.php?page=news_item&px=ODY2OA)
I tried to go to 10.10 a couple of days ago, and all I got was a black screen. I didn't feel like messing with it, so I just abandoned that idea. I may try to install 64 sometime this weekend though.

---

### Post by ICANSEEYOU7687 on 2010-10-15
I was using the 4200 so not the same issue.
 
I do remember with the HDMI audio I had to open pulse audio and unmute the HDMI audio connection.
 
You can also try installing (if its not already) alsa.
 
and in the terminal type alsamixer
 
or alsamixer -c 1 and make sure the device is not muted

---

### Post by borolo on 2010-10-15
> **ICANSEEYOU7687 said:**
> I was using the 4200 so not the same issue.
 
I do remember with the HDMI audio I had to open pulse audio and unmute the HDMI audio connection.
 
You can also try installing (if its not already) alsa.
 
and in the terminal type alsamixer
 
or alsamixer -c 1 and make sure the device is not muted

Does this allow us to use the hdmi output for video? Will give it a try this weekend as I'm out of town.

---

### Post by di3gopa on 2010-10-16
> **pab31966 said:**
> I tried to go to 10.10 a couple of days ago, and all I got was a black screen. I didn't feel like messing with it, so I just abandoned that idea. I may try to install 64 sometime this weekend though.

With the 64-bit version works fine

---

### Post by pab31966 on 2010-10-19
> **di3gopa said:**
> With the 64-bit version works fineI tried the 32-bit & the 64-bit version. 32 loads from the CD straight to a black screen. 64 actually goes through the entire install process, and then upon reboot I get a black screen. I'll mess with it some other time. I've got too many other things going on right now.

---

### Post by TweFoju on 2010-12-22
Hello , im in the same boat with you all

i own HP Pavilion DV6Z with 5650

but yeah, same problem, i have the latest Catalyst installed, but still reads 4200

this is just frustrating

---

### Post by AncientMan on 2010-12-31
I have the same issue with a dv7-4045ea (ATI Mobility Radeon™ HD 5650 Graphics) running Ubuntu 10.10. If I start the laptop in recovery mode and run
```
aticonfig --lsa
```I get

```

* 0. 01:05.0 ATI Mobility Radeon HD 4200 Series
  1. 02:00.0 ATI Mobility Radeon HD 5000 Series 

* - Default adapter

```However, when I try to use the Radeon 5650 I get the following

```
[    22.848] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    22.848] X Protocol Version 11, Revision 0
[    22.848] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    22.848] Current Operating System: Linux merlin 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64
[    22.848] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-24-generic root=UUID=946aebfd-0491-473c-b2b1-21fcf013608d ro quiet splash
[    22.848] Build Date: 23 November 2010  11:54:56PM
[    22.848] xorg-server 2:1.9.0-0ubuntu7.1 (For technical support please see http://www.ubuntu.com/support) 
[    22.848] Current version of pixman: 0.18.4
[    22.848]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    22.848] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.848] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 31 22:20:50 2010
[    23.243] (==) Using config file: "/etc/X11/xorg.conf"
[    23.243] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    23.555] (==) ServerLayout "aticonfig Layout"
[    23.555] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    23.555] (**) |   |-->Monitor "<default monitor>"
[    23.555] (**) |   |-->Device "aticonfig-Device[0]-0"
[    23.555] (==) No monitor specified for screen "aticonfig-Screen[0]-0".
    Using a default monitor configuration.
[    23.555] (**) |-->Screen "amdcccle-Screen[1]-1" (1)
[    23.555] (**) |   |-->Monitor "<default monitor>"
[    23.555] (**) |   |-->Device "amdcccle-Device[1]-1"
[    23.555] (==) No monitor specified for screen "amdcccle-Screen[1]-1".
    Using a default monitor configuration.
[    23.555] (**) |-->Screen "amdcccle-Screen[2]-0" (2)
[    23.555] (**) |   |-->Monitor "<default monitor>"
[    23.556] (**) |   |-->Device "amdcccle-Device[2]-0"
[    23.556] (==) No monitor specified for screen "amdcccle-Screen[2]-0".
    Using a default monitor configuration.
[    23.556] (==) Automatically adding devices
[    23.556] (==) Automatically enabling devices
[    23.797] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    23.797]     Entry deleted from font path.
[    24.186] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    24.186] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.186] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.186] (II) Loader magic: 0x7d17a0
[    24.186] (II) Module ABI versions:
[    24.186]     X.Org ANSI C Emulation: 0.4
[    24.186]     X.Org Video Driver: 8.0
[    24.186]     X.Org XInput driver : 11.0
[    24.186]     X.Org Server Extension : 4.0
[    24.187] (--) PCI:*(0:1:5:0) 1002:9712:103c:147b rev 0, Mem @ 0xd0000000/268435456, 0xf0400000/65536, 0xf0300000/1048576, I/O @ 0x00004000/256
[    24.187] (--) PCI: (0:2:0:0) 1002:68c1:103c:147b rev 0, Mem @ 0xe0000000/268435456, 0xf0200000/131072, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    24.188] (II) Open ACPI successful (/var/run/acpid.socket)
[    24.188] (II) "extmod" will be loaded by default.
[    24.188] (II) "dbe" will be loaded by default.
[    24.188] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    24.188] (II) "record" will be loaded by default.
[    24.188] (II) "dri" will be loaded by default.
[    24.188] (II) "dri2" will be loaded by default.
[    24.188] (II) LoadModule: "glx"
[    24.399] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    24.575] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    25.184]     compiled for 7.6.0, module version = 1.0.0
[    25.185] (II) Loading extension GLX
[    25.185] (II) LoadModule: "extmod"
[    25.604] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    25.683] (II) Module extmod: vendor="X.Org Foundation"
[    25.833]     compiled for 1.9.0, module version = 1.0.0
[    25.833]     Module class: X.Org Server Extension
[    25.833]     ABI class: X.Org Server Extension, version 4.0
[    25.833] (II) Loading extension MIT-SCREEN-SAVER
[    25.834] (II) Loading extension XFree86-VidModeExtension
[    25.834] (II) Loading extension XFree86-DGA
[    25.834] (II) Loading extension DPMS
[    25.834] (II) Loading extension XVideo
[    25.834] (II) Loading extension XVideo-MotionCompensation
[    25.834] (II) Loading extension X-Resource
[    25.834] (II) LoadModule: "dbe"
[    25.834] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    26.157] (II) Module dbe: vendor="X.Org Foundation"
[    26.157]     compiled for 1.9.0, module version = 1.0.0
[    26.157]     Module class: X.Org Server Extension
[    26.157]     ABI class: X.Org Server Extension, version 4.0
[    26.157] (II) Loading extension DOUBLE-BUFFER
[    26.157] (II) LoadModule: "record"
[    26.158] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    26.512] (II) Module record: vendor="X.Org Foundation"
[    26.712]     compiled for 1.9.0, module version = 1.13.0
[    26.712]     Module class: X.Org Server Extension
[    26.712]     ABI class: X.Org Server Extension, version 4.0
[    26.712] (II) Loading extension RECORD
[    26.712] (II) LoadModule: "dri"
[    26.712] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    26.768] (II) Module dri: vendor="X.Org Foundation"
[    26.968]     compiled for 1.9.0, module version = 1.0.0
[    26.968]     ABI class: X.Org Server Extension, version 4.0
[    26.968] (II) Loading extension XFree86-DRI
[    26.968] (II) LoadModule: "dri2"
[    26.968] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    27.046] (II) Module dri2: vendor="X.Org Foundation"
[    27.100]     compiled for 1.9.0, module version = 1.2.0
[    27.100]     ABI class: X.Org Server Extension, version 4.0
[    27.100] (II) Loading extension DRI2
[    27.100] (II) LoadModule: "fglrx"
[    27.101] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    28.103] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    28.205]     compiled for 1.4.99.906, module version = 8.78.30
[    28.205]     Module class: X.Org Video Driver
[    28.287] (II) Loading sub module "fglrxdrm"
[    28.294] (II) LoadModule: "fglrxdrm"
[    28.294] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    28.332] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    28.332]     compiled for 1.8.99.905, module version = 8.78.30
[    28.332] (II) ATI Proprietary Linux Driver Version Identifier:8.78.30
[    28.333] (II) ATI Proprietary Linux Driver Release Identifier: 8.78.3                               
[    28.333] (II) ATI Proprietary Linux Driver Build Date: Sep 20 2010 21:31:08
[    28.333] (++) using VT number 7

[    28.333] (WW) Falling back to old probe method for fglrx
[    28.476] (II) Loading PCS database from /etc/ati/amdpcsdb
[    28.492] (--) Chipset Supported AMD Graphics Processor (0x9712) found
[    28.492] (--) Chipset Supported AMD Graphics Processor (0x68C1) found
[    28.492] (--) Chipset Supported AMD Graphics Processor (0x9712) found
[    28.518] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    28.518] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    28.518] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    28.518] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    28.518] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    28.518] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    28.518] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    28.518] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    28.518] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    28.518] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    28.518] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
[    28.518] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
[    28.518] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[    28.518] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    28.538] (II) AMD Video driver is signed
[    28.538] (II) fglrx(0): pEnt->device->identifier=0x13cbc10
[    28.538] (II) fglrx(1): pEnt->device->identifier=0x13cc310
[    28.538] (II) fglrx(2): pEnt->device->identifier=0x13cbc10
[    28.538] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[    28.540] (II) Loading sub module "vgahw"
[    28.540] (II) LoadModule: "vgahw"
[    28.544] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    28.550] (II) Module vgahw: vendor="X.Org Foundation"
[    28.550]     compiled for 1.9.0, module version = 0.1.0
[    28.550]     ABI class: X.Org Video Driver, version 8.0
[    28.550] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    28.550] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    28.550] (==) fglrx(0): Default visual is TrueColor
[    28.550] (==) fglrx(0): RGB weight 888
[    28.550] (II) fglrx(0): Using 8 bits per RGB 
[    28.550] (==) fglrx(0): Buffer Tiling is ON
[    28.551] (II) Loading sub module "fglrxdrm"
[    28.551] (II) LoadModule: "fglrxdrm"
[    28.551] (II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    28.554] ukiDynamicMajor: found major device number 250
[    28.554] ukiDynamicMajor: found major device number 250
[    28.554] ukiOpenByBusid: Searching for BusID PCI:1:5:0
[    28.554] ukiOpenDevice: node name is /dev/ati/card0
[    28.554] ukiOpenDevice: open result is 14, (OK)
[    28.554] ukiOpenByBusid: ukiOpenMinor returns 14
[    28.554] ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
[    28.554] (==) fglrx(0): NoAccel = NO
[    28.554] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    28.554] (--) fglrx(0): Chipset: "ATI Mobility Radeon HD 4200 Series" (Chipset = 0x9712)
[    28.554] (--) fglrx(0): (PciSubVendor = 0x103c, PciSubDevice = 0x147b)
[    28.554] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    28.554] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    28.554] (--) fglrx(0): MMIO registers at 0xf0400000
[    28.554] (--) fglrx(0): I/O port at 0x00004000
[    28.554] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    28.632] (II) fglrx(0): ATIF platform detected
[    28.657] (II) fglrx(0): AC Adapter is used
[    28.921] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    28.922] (II) fglrx(0): Detected: Switchable-graphics system with an AMD chipset
[    28.922] (II) fglrx(0): Using integrated graphics. Some display types may not be supported
[    28.922] (II) fglrx(0): Please use xrandr to check displays supported by the integrated controller
[    28.972] (II) Loading sub module "vbe"
[    28.972] (II) LoadModule: "vbe"
[    28.972] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    29.174] (II) Module vbe: vendor="X.Org Foundation"
[    29.174]     compiled for 1.9.0, module version = 1.1.0
[    29.174]     ABI class: X.Org Video Driver, version 8.0
[    29.174] (II) fglrx(0): VESA BIOS detected
[    29.174] (II) fglrx(0): VESA VBE Version 3.0
[    29.174] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    29.175] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    29.175] (II) fglrx(0): VESA VBE OEM Software Rev: 10.94
[    29.175] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    29.175] (II) fglrx(0): VESA VBE OEM Product: RS880M
[    29.175] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    29.186] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    29.186] (II) fglrx(0): UMA/SP interleave mode is enabled in the BIOS
[    29.186] (--) fglrx(0): Video RAM: 327680 kByte, Type: DDR3
[    29.186] (II) fglrx(0): PCIE card detected
[    29.186] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    29.186] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    29.218] (II) fglrx(0): Turned off the discrete card
[    29.222] (II) fglrx(0): Using adapter: 1:5.0.
[    29.231] (II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x14000000)
[    29.295] (II) fglrx(0): Interrupt handler installed at IRQ 18.
[    29.295] (II) fglrx(0): RandR 1.2 support is enabled!
[    29.295] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    29.296] (==) fglrx(0): Center Mode is disabled 
[    29.296] (II) Loading sub module "fb"
[    29.296] (II) LoadModule: "fb"
[    29.296] (II) Loading /usr/lib/xorg/modules/libfb.so
[    29.392] (II) Module fb: vendor="X.Org Foundation"
[    29.392]     compiled for 1.9.0, module version = 1.0.0
[    29.392]     ABI class: X.Org ANSI C Emulation, version 0.4
[    29.393] (==) fglrx(0): Active stereo disabled
[    29.393] (II) Loading sub module "ddc"
[    29.393] (II) LoadModule: "ddc"
[    29.393] (II) Module "ddc" already built-in
[    29.985] (II) fglrx(0): Finished Initialize PPLIB!
[    30.096] (II) fglrx(0): Output LVDS using monitor section 0-LVDS
[    30.096] (**) fglrx(0): Option "PreferredMode" "1600x900"
[    30.096] (**) fglrx(0): Option "Position" "0 0"
[    30.096] (**) fglrx(0): Option "Disable" "false"
[    30.096] (**) fglrx(0): Option "Rotate" "normal"
[    30.096] (**) fglrx(0): Option "TargetRefresh" "60"
[    30.096] (II) fglrx(0): Output CRT1 has no monitor section
[    30.104] (II) Loading sub module "ddc"
[    30.104] (II) LoadModule: "ddc"
[    30.104] (II) Module "ddc" already built-in
[    30.104] (II) fglrx(0): Connected Display0: LVDS
[    30.105] (II) fglrx(0): Display0 EDID data ---------------------------
[    30.105] (II) fglrx(0): Manufacturer: LGD  Model: 27a  Serial#: 0
[    30.105] (II) fglrx(0): Year: 2009  Week: 0
[    30.105] (II) fglrx(0): EDID Version: 1.3
[    30.105] (II) fglrx(0): Digital Display Input
[    30.105] (II) fglrx(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[    30.105] (II) fglrx(0): Gamma: 2.20
[    30.105] (II) fglrx(0): No DPMS capabilities specified
[    30.105] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    30.105] (II) fglrx(0): First detailed timing is preferred mode
[    30.105] (II) fglrx(0): redX: 0.615 redY: 0.346   greenX: 0.314 greenY: 0.602
[    30.105] (II) fglrx(0): blueX: 0.151 blueY: 0.109   whiteX: 0.312 whiteY: 0.328
[    30.105] (II) fglrx(0): Manufacturer's mask: 0
[    30.105] (II) fglrx(0): Supported detailed timing:
[    30.105] (II) fglrx(0): clock: 97.8 MHz   Image Size:  382 x 215 mm
[    30.105] (II) fglrx(0): h_active: 1600  h_sync: 1648  h_sync_end 1696 h_blank_end 1784 h_border: 0
[    30.105] (II) fglrx(0): v_active: 900  v_sync: 902  v_sync_end 905 v_blanking: 912 v_border: 0
[    30.105] (II) fglrx(0):  
[    30.105] (II) fglrx(0):  LP173WD1-TLC3
[    30.105] (II) fglrx(0): EDID (in hex):
[    30.105] (II) fglrx(0):     00ffffffffffff0030e47a0200000000
[    30.105] (II) fglrx(0):     00130103802615780aa8c09d58509a26
[    30.105] (II) fglrx(0):     1c505400000001010101010101010101
[    30.105] (II) fglrx(0):     0101010101012f2640b860840c303030
[    30.105] (II) fglrx(0):     23007ed7100000190000000000000000
[    30.105] (II) fglrx(0):     00000000000000000000000000fe0000
[    30.105] (II) fglrx(0):     00004c47446973706c61790a000000fe
[    30.105] (II) fglrx(0):     004c503137335744312d544c433300c2
[    30.105] (II) fglrx(0): End of Display0 EDID data --------------------
[    30.207] (II) fglrx(0): EDID vendor "LGD", prod id 634
[    30.207] (II) fglrx(0): Printing DDC gathered Modelines:
[    30.207] (II) fglrx(0): Modeline "1600x900"x0.0   97.75  1600 1648 1696 1784  900 902 905 912 -hsync -vsync (54.8 kHz)
[    30.207] (II) fglrx(0): Output LVDS connected
[    30.207] (II) fglrx(0): Output CRT1 disconnected
[    30.207] (II) fglrx(0): Using user preference for initial modes
[    30.207] (II) fglrx(0): Output LVDS using initial mode 1600x900
[    30.207] (II) fglrx(0): Display dimensions: (380, 210) mm
[    30.207] (II) fglrx(0): DPI set to (106, 108)
[    30.207] (II) fglrx(0): Adapter ATI Mobility Radeon HD 4200 Series has 2 configurable heads and 1 displays connected.
[    30.207] (==) fglrx(0):  PseudoColor visuals disabled
[    30.207] (II) Loading sub module "ramdac"
[    30.207] (II) LoadModule: "ramdac"
[    30.207] (II) Module "ramdac" already built-in
[    30.207] (==) fglrx(0): NoDRI = NO
[    30.207] (==) fglrx(0): Capabilities: 0x00000000
[    30.207] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    30.207] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    30.207] (==) fglrx(0): UseFastTLS=0
[    30.207] (==) fglrx(0): BlockSignalsOnLock=1
[    30.207] (II) fglrx(1): === [xdl_x760_atiddxPreInit] === begin
[    30.208] (WW) fglrx(1): Quitting screen 1 -- no monitor specified.
[    30.208] (II) fglrx(1): === [xdl_x760_atiddxPreInit] === end
[    30.208] (II) fglrx(2): === [xdl_x760_atiddxPreInit] === begin
[    30.208] (**) fglrx(2): Depth 24, (--) framebuffer bpp 32
[    30.208] (II) fglrx(2): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    30.208] (==) fglrx(2): Default visual is TrueColor
[    30.208] (**) fglrx(2): Option "Monitor-Default Monitor" "1-Default monitor"
[    30.208] (==) fglrx(2): RGB weight 888
[    30.208] (II) fglrx(2): Using 8 bits per RGB 
[    30.208] (==) fglrx(2): Buffer Tiling is ON
[    30.208] (II) Loading sub module "fglrxdrm"
[    30.208] (II) LoadModule: "fglrxdrm"
[    30.208] (II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    30.211] ukiDynamicMajor: found major device number 250
[    30.211] ukiDynamicMajor: found major device number 250
[    30.211] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    30.211] ukiOpenDevice: node name is /dev/ati/card0
[    30.211] ukiOpenDevice: open result is 19, (OK)
[    30.211] ukiOpenByBusid: ukiOpenMinor returns 19
[    30.211] ukiOpenByBusid: ukiGetBusid reports PCI:1:5:0
[    30.211] ukiOpenDevice: node name is /dev/ati/card1
[    30.211] ukiOpenDevice: open result is 19, (OK)
[    30.211] ukiOpenByBusid: ukiOpenMinor returns 19
[    30.211] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    30.212] (==) fglrx(2): NoAccel = NO
[    30.212] (==) fglrx(2): ATI 2D Acceleration Architecture enabled
[    30.212] (--) fglrx(2): Chipset: "ATI Mobility Radeon HD 5000 Series " (Chipset = 0x68c1)
[    30.212] (--) fglrx(2): (PciSubVendor = 0x103c, PciSubDevice = 0x147b)
[    30.212] (==) fglrx(2): board vendor info: third party graphics adapter - NOT original ATI
[    30.212] (--) fglrx(2): Linear framebuffer (phys) at 0xe0000000
[    30.212] (--) fglrx(2): MMIO registers at 0xf0200000
[    30.212] (--) fglrx(2): I/O port at 0x00003000
[    30.212] (==) fglrx(2): ROM-BIOS at 0x000c0000
[    30.214] (II) fglrx(0): ATIF platform detected
[    30.215] (II) fglrx(0): AC Adapter is used

```

As you can see it doesn't think the 5650 is an original ATI card, what can we do to get this fixed, is it an ATI problem or an HP thing?

---

### Post by Yellow Pasque on 2010-12-31
Switchable graphics just aren't supported well on Linux right now. There's not much you can do about it if you can't disable the integrated video in BIOS (and IIRC someone got a reply from HP that they have no plans to support that).

---

### Post by ljack8 on 2011-01-02
Hi,

I was able to successfully install ubuntu 10.10 AMD64. I have a Toshiba Satellite A665D-S6051 with ATI Radeon 4250 (Detailed specs: [http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_A665D-S6051.pdf](http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_A665D-S6051.pdf)).

I was also getting blank screen after booting from CD. I installed as dual boot with windows vista but it also hanged.

Here's what I did:

1) Restore your BIOS to factory defaults (so we are sure we are starting from scratch - you can try skipping this step);

2) Disable "USB Legacy Emulation" (don't ask me why but this was the only way to boot from CD without a blank screen - SERIOUSLY! - Can someone tell me why?);

3) When CD starts booting press any key to go to the language menu. Press F6 and select nodmraid and nomodeset. Now press ESC and choose "Try Ubuntu without installing" from the main menu;

4) Install ubuntu;

5) When your system boots for the first time you must change /etc/default/grub configuration with this:

```
GRUB_CMDLINE_LINUX="nomodeset nodmraid"
```

save the file and then run:

```
sudo update-grub
```

6) Now you're able to restart your system and I hope it works!

My questions are: what exactly am I loosing by adding nomodeset? I guess nothing. I am sure RAID is useless for me at my notebook.

And by the way, if you want the backlit keyboard led on just add acpi=off as a parameter in step 5.

Best regards!

---

### Post by Splat_NJ on 2011-01-02
I have a different card, Radeon HD 4650, but had the same no-video problem after a fresh Ubuntu install. What you need to do is press <shift> key while bootup,  getting you to the boot options screen. Press <e> key to edit the first entry, then  append "text" at the end of the line that ends with "quiet splash" in the Grub.cfg file.  This will let you boot to the shell where you can install the graphics driver. For more info see [here]("http://ubuntuforums.org/showpost.php?p=10306271&postcount=15").

---

### Post by pab31966 on 2011-01-12
> **ljack8 said:**
> Hi,

I was able to successfully install ubuntu 10.10 AMD64. I have a Toshiba Satellite A665D-S6051 with ATI Radeon 4250 (Detailed specs: [http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_A665D-S6051.pdf](http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_A665D-S6051.pdf)).


Thank you. I was finally able to get 10.10 64 installed. Here's what I did:

At first I just disabled USB Legacy Emulation and nothing happened. It still booted from the cd to a black screen. 

I left Legacy Emulation off and changed the SATA mode from "AHCI" to "Compatibilty". Bingo! I was able to get the OS installed and functioning. At this point I really don't care about the why, I'm just happy to have 64 installed and running! Again, thanks for pointing me in the right direction. :D

---

### Post by tormod on 2011-06-15
Just found this (and this thread) on google, maybe it can help:
[http://www.aimxhaisse.com/laptop-heat-hybrid.html](http://www.aimxhaisse.com/laptop-heat-hybrid.html)

---

### Post by masterbrumm on 2011-08-25
I have the same issue with HDMI output on my ati hd5650 an gets reconiced as ati hd4200. I have tried 10.04, 10.10 and even the 11.10 beta same problem . Have anyone had any luck fixing this?

---

### Post by ziocane1 on 2011-08-25
Me too! 
Acer aspire 5553g, lucid 32 bit, kernel pae 2.6.32-34 and 2.6.39 (non-pae).
How can I solve it?

---

### Post by Splat_NJ on 2011-08-25
You can boot either from the Live cd or off a hd install but you need to go to the command line, not the GUI, and install the driver(s) from there. See my previous posts. This worked for me and now a few friends of mine who have since switched to Ubuntu that I helped. Good luck.

---

### Post by ziocane1 on 2011-08-28
Finally I solved:

1- disabled the 4200 card in the bios
2- forced the reinstallation of the catalyst 11.8
3- completely removed that driver by this how-to:

- Problem: Need to fully remove -fglrx and reinstall -ati from scratch
[https://wiki.ubuntu.com/X/Troublesho...thRadeonDriver]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver")

4- removed the kernel 2.6.39 and  2.6.33 pae
5- installed the 2.6.32 pae kernel
6- installed the propretary driver by jockey

Tnx for the help

---

