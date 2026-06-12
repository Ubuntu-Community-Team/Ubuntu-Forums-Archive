---
title: "how to change from integrated graphics to discrete"
date: 2010-08-25
forum: Hardware
---

### Post by sxmaxchine on 2010-08-25
I have looked for an answer to this question however the only answer i find says i need to change the settings in my bios. However when i looked in my bios there are no options for my graphics at all. 

I have a hp dv6 notebook.

---

### Post by endotherm on 2010-08-25
those instructions are only really for desktop pcs. I've never seen a laptop with more than one vidcard/gpu except mabey some alienware sli rig. in that case though, both gpus would be discrete.

---

### Post by Zimmer on 2010-08-25
As Endotherm says, likely you will have ONE Graphics option only on your laptop, but which one?

Do you know what Graphics you have on your DV6  (mine is an NVIDIA card, but the DV6 comes in many flavours).
Take a look at your Xorg.log (Administration>Logfile Viewer)

find an Entry that relates to your card eg (Mine looks like this)

(--) PCI:*(0:1:0:0) 10de:0427:103c:30cc nVidia Corporation G86 [GeForce 8400M GS]

let us know what you find..

---

### Post by sxmaxchine on 2010-08-25
if i did it correctly i got this:

(--) PCI:*(0:1:5:0) 1002:9712:103c:1440 ATI Technologies Inc M880G [Mobility Radeon HD 4200] rev 0, Mem @ 0xd0000000/268435456, 0xf0400000/65536, 0xf0300000/1048576, I/O @ 0x00004000/256
(--) PCI: (0:2:0:0) 1002:68c1:103c:1440 ATI Technologies Inc Redwood [Radeon HD 5600 Series] rev 0, Mem @ 0xe0000000/268435456, 0xf0200000/131072, I/O @ 0x00003000/256, BIOS @ 0x????????/131072

---

### Post by mexicanseaf00d on 2010-08-25
Oh lord, please let there be some config where we can tell the drivers to use the discrete card! I just came on the forum and wanted to post exact same problem! :D

I have also a HP, DV7 notebook with no BIOS setting for switching from Intel to the ATI card...

Thanks for bringing this topic up, sxmaxchine!

---

### Post by Fafler on 2010-08-25
There has been some threads about Nvidia cards with the same issue. Maybe searching for those could provide some info.

---

### Post by sxmaxchine on 2010-08-25
> **mexicanseaf00d said:**
> Oh lord, please let there be some config where we can tell the drivers to use the discrete card! I just came on the forum and wanted to post exact same problem! :D

I have also a HP, DV7 notebook with no BIOS setting for switching from Intel to the ATI card...

Thanks for bringing this topic up, sxmaxchine!

no problem

---

### Post by sxmaxchine on 2010-08-25
> **Fafler said:**
> There has been some threads about Nvidia cards with the same issue. Maybe searching for those could provide some info.

il have a look into it thanks for the advice

---

### Post by endotherm on 2010-08-25
you can manually configure your xorg to use teh differant busID and driver, so hopefully you will be fine without a bios hack, but you may want to contact HP (they have a nice "chat with a technician" service). sometimes they have flashes that open up additional bios options.

---

### Post by Zimmer on 2010-08-26
What does entering

lspci -nn | grep VGA

in a Terminal return as your Graphics card ?

---

### Post by ramnathsagar on 2010-08-26
Is nt there an option in your BIOS to change from integrated to discrete?

---

### Post by endotherm on 2010-08-26
> **ramnathsagar said:**
> Is nt there an option in your BIOS to change from integrated to discrete?
per the ops first post, no. 
HP really locks down their bios.

---

### Post by ramnathsagar on 2010-08-26
Oops. My bad,I guess I didnt read the 1st post properly.
Do you have Radeon card? I think I had the same issue a year ago, and later I realized that I didnt install the proprietary driver and amd catalyst center.

---

### Post by sxmaxchine on 2010-08-26
> **Zimmer said:**
> What does entering

lspci -nn | grep VGA

in a Terminal return as your Graphics card ?

when u use that command i get the result:

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1] (rev ff)

---

### Post by sxmaxchine on 2010-08-26
> **endotherm said:**
> you can manually configure your xorg to use teh differant busID and driver, so hopefully you will be fine without a bios hack, but you may want to contact HP (they have a nice "chat with a technician" service). sometimes they have flashes that open up additional bios options.

how can i edit my xorg, when i type:

Xorg -configure

i get this result:

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log

---

### Post by endotherm on 2010-08-26
> **sxmaxchine said:**
> how can i edit my xorg, when i type:

Xorg -configure

i get this result:

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log

well there are a couple issues. the first is that you need to not have X running in order to reconfigure. second it is recomended to use 'dpkg --reconfigure -P high xserver.xorg' instead of xorg -configure, **but only on pre-Intrepid versions of ubuntu**. the newer versions do not react to this command, so all you are doing is blanking out the existing file. 

you will have to type it by hand i'm afraid. it's not that hard, for a single head display. one device section, one monitor section, and one screen section. voila.

here is some info:
[http://www.freebsd.org/doc/handbook/x-config.html](http://www.freebsd.org/doc/handbook/x-config.html)

here are the core bits (don;'t actually use these, they won;t work for your hardware):
```

Section "Device"
    Identifier "*card0*"
    Driver     "*driver*"
    BusID      "01:05.0"
EndSection:
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        HorizSync    30-107
        VertRefresh  48-120
EndSection
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 24
        SubSection "Display"
                Viewport  0 0
                Depth     24
                Modes     "1024x768"
        EndSubSection
EndSection


```

on the device, the important values are the driver, and the busid *(busid is the leading set of numbers for your device as shown by 'lspci'). the screen binds the device and the monitor together to generate the X geometry.

---

### Post by sxmaxchine on 2010-08-26
thanks for the help

---

### Post by sxmaxchine on 2010-08-26
also is it possible to view my current configuration file that i need to re write

---

### Post by Zimmer on 2010-08-26
> **sxmaxchine said:**
> when u use that command i get the result:

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1] (rev ff)

Anyone else find it strange that this reports two different graphics adapters on 2 PCI slots on the same laptop?

What does Windows report as your Video card(s) ??

If one is 'onboard' VGA then there should be an option in the BIOS (Onboard peripherals) to Disable it. 

I am curious.....

---

### Post by Zimmer on 2010-08-26
> **sxmaxchine said:**
> also is it possible to view my current configuration file that i need to re write

The xorg.conf file is located at /etc/X11

You can view it, but it is owned by root ..

As an aside, as I have no current experience with ATI cards I am not the best person to guide you here. I suggest, though , that you find and read the official and community documentation on the installation of drivers for ATI cards that will give you 3D capabilities.Also, see if you can find an up-to-date HOWTO for them.

Good Luck
Zimmer

---

### Post by sxmaxchine on 2010-08-26
ok il have a look thanks

---

### Post by mexicanseaf00d on 2010-08-27
> **Zimmer said:**
> Anyone else find it strange that this reports two different graphics adapters on 2 PCI slots on the same laptop?

What does Windows report as your Video card(s) ??

If one is 'onboard' VGA then there should be an option in the BIOS (Onboard peripherals) to Disable it. 

I am curious.....


You're able to switch to the integrated one when on battery power, saves a lot of energy. HP forgot to program the BIOS to turn off one or the other GFXcard....:o

---

### Post by jingcha007 on 2010-08-27
You will have to download the catalyst from this link,
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
and then u can change to the graphics card from onboard.

---

### Post by sxmaxchine on 2010-08-29
catalyst 10.8 doesnt support my card, and when i tried it my x configuration got messed up so i had to go back to the one i got from software center.

---

### Post by borolo on 2010-09-11
I have a HP DV6 with amd 930 quad and the same ati card:

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1] (rev ff)


this is what shows with fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200
OpenGL version string: 3.3.10151 Compatibility Profile Context

installed the last catalyst and worked better than the one from the distro. Is your laptop getting hot? with the previous catalyst it was like an oven and now its perfect.

can't activate the discrete card though.

---

### Post by borolo on 2010-09-11
Downloaded catalyst from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)

and it states that the radeon mobility 5x series is supported, so i don't know why it doesn't give us a chance to change it.

---

### Post by borolo on 2010-09-11
data from lspi -v

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
    Subsystem: Hewlett-Packard Company Device 1440
    Flags: bus master, 66MHz, medium devsel, latency 0
    Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f0300000-f04fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel modules: shpchp

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f0200000-f02fffff
    Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f0100000-f01fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0600000-f09fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f00fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 1440
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    I/O ports at 5038 [size=8]
    I/O ports at 504c [size=4]
    I/O ports at 5030 [size=8]
    I/O ports at 5048 [size=4]
    I/O ports at 5010 [size=16]
    Memory at f0508000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 1440
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0507000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 1440
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0508600 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 1440
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0506000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 1440
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0508500 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
    Subsystem: Hewlett-Packard Company Device 1440
    Flags: 66MHz, medium devsel
    Kernel modules: i2c-piix4

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: Hewlett-Packard Company Device 1440
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f0500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
    Subsystem: Hewlett-Packard Company Device 1440
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40) (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=64

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 1440
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0505000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 1440
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at f0504000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 1440
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at f0508400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
    Flags: fast devsel
    Kernel modules: amd64_edac_mod

00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
    Flags: fast devsel
    Capabilities: <access denied>
    Kernel driver in use: k10temp
    Kernel modules: k10temp

00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
    Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
    Subsystem: Hewlett-Packard Company Device 1440
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=256]
    Memory at f0400000 (32-bit, non-prefetchable) [size=64K]
    Memory at f0300000 (32-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

02:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx

02:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: HDA Intel

03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
    Subsystem: Hewlett-Packard Company Device 1483
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 1440
    Flags: bus master, fast devsel, latency 0, IRQ 27
    I/O ports at 2000 [size=256]
    Memory at f0004000 (64-bit, prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at f0010000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

uname -a
Linux cuky-laptop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux


any ideas?

---

