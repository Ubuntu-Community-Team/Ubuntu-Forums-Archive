---
title: "Intel 855GM does not load i915 on Ubuntu 14.04"
date: 2014-07-22
forum: Hardware
---

### Post by Martin_Gergov on 2014-07-22
Hello all,

I have a 32 bit Ubuntu 14.04 LTS installed on a machine with Intel 855GM[8086:3582] graphics card.
When I do:
```
**sudo modprobe i915**
```

It fails with: 
```
modprobe: ERROR: could not insert 'i915': No such device
```

Here is more info:

```
**lsb_release -a**
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

```


```

**uname -a**
Linux immmon 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 i686 i686 i686 GNU/Linux

```

```
**dmesg | grep "agp"**
[    1.951486] Linux agpgart interface v0.103
[    1.952046] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[    1.952220] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
[    1.952943] agpgart-intel 0000:00:00.0: detected 32768K stolen memory
[    1.953771] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xd8000000

```

```
**lspci -k | grep -C 3 "VGA"**
    Subsystem: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
    Subsystem: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
    Subsystem: Intel Corporation 82852/855GM Integrated Graphics Device
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
    Subsystem: Intel Corporation 82852/855GM Integrated Graphics Device

```

```

**lsmod | grep "i"**
Module                  Size  Used by
snd_intel8x0           33110  0 
gpio_ich               13229  0 
snd_ac97_codec        105709  1 snd_intel8x0
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
mac_hid                13037  0 
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60871  8 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
serio_raw              13230  0 
i2c_algo_bit           13197  0 
lpc_ich                16864  0 
hid_generic            12492  0 
usbhid                 46997  0 
hid                    87604  2 hid_generic,usbhid
mii                    13654  2 8139cp,8139too

```

```
**dpkg -s xserver-xorg-video-intel**
Package: xserver-xorg-video-intel
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 2814
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 2:2.99.910-0ubuntu1
Provides: xorg-driver-video
Depends: libc6 (>= 2.17), libdrm-intel1 (>= 2.4.38), libdrm2 (>= 2.4.30), libpciaccess0 (>= 0.8.0+git20071002), libpixman-1-0 (>= 0.30.0), libudev1 (>= 183), libx11-6, libx11-xcb1, libxcb-dri2-0, libxcb-util0 (>= 0.3.8), libxcb1, libxv1, libxvmc1, xorg-video-abi-15, xserver-xorg-core (>= 2:1.14.99.902)
Description: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides the driver for the Intel i8xx and i9xx family
 of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945
 and i965 series chips.
 .
 This package also provides XvMC (XVideo Motion Compensation) drivers
 for i810/i815 and i9xx and newer chipsets.
 .
 This package is built from the X.org xf86-video-intel driver module.
Homepage: http://www.x.org/
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>

```
[B]

UPDATE[/B]

Turns out ACPI was disabled in BIOS. The driver loads, but now the screen is heavily distorted and flickers.

Here are the more interesting parts of **dmesg**:

```

[   30.554483] ACPI Warning: 0x000040b0-0x000040bf SystemIO conflicts with Region \GPO2 1 (20131115/utaddress-251)
[   30.554507] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   30.554513] ACPI Warning: 0x00004080-0x000040af SystemIO conflicts with Region \GPO_ 1 (20131115/utaddress-251)
[   30.554522] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   30.554526] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   30.614445] [drm] Initialized drm 1.1.0 20060810
...
[   32.948961] [drm] Memory usable by graphics device = 128M
[   32.948981] checking generic (d8000000 500000) vs hw (d8000000 8000000)
[   32.948987] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   32.949221] Console: switching to colour dummy device 80x25
[   33.088318] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   33.088335] [drm] Driver supports precise vblank timestamp query.
[   33.089001] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   33.297744] [drm] GMBUS [i915 gmbus panel] timed out, falling back to bit banging on pin 3
[   33.387154] [drm] initialized overlay support
[   34.066083] fbcon: inteldrmfb (fb0) is primary device
[   34.393293] Console: switching to colour frame buffer device 100x37
[   34.398746] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   34.398753] i915 0000:00:02.0: registered panic notifier
[   34.432472] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   37.796805] init: Failed to obtain startpar-bridge instance: Unknown parameter: INSTANCE
[   38.786523] init: failsafe main process (547) killed by TERM signal
[   38.872108] intel8x0_measure_ac97_clock: measured 52149 usecs (2513 samples)
[   38.872121] intel8x0: clocking to 48000
[   40.051543] init: udev-fallback-graphics main process (667) terminated with status 1

```

---

### Post by Axxon95 on 2014-07-30
That IGP probably isn't good enough to run Unity3D(and Unity2D was removed in 12.10).
Just helped someone yesterday trying to use a Radeon 9000 Mobility(which IS supported with OpenGL 1.3) that Ubuntu wouldn't utilize(kept going to software raster) because of hardware limitations and Ubuntu probing for Unity3D support on startup.
I have an older 845G chipset box here than I run Lubuntu on and it has some minor graphical errors even on a lightweight environment, but it does get hardware OpenGL support, 1.3 if I recall correctly.
Best bet, try X/Lubuntu and report back with your findings.
Unity is a killer on older chips.

---

### Post by Martin_Gergov on 2014-07-31
Thank you for the reply.
I didn't have the intention of running Unity at all, however, this will be an X+awesome wm+midori(fullscreen) machine so it doesn't even need a full desktop enviroment.

By the way I forgot to mention that the flickers and distortion begin on the tty stage even before I login.

---

### Post by mörgæs on 2014-07-31
I agree that Lubuntu 14.04.1 is a better choice. It might get even better if you add an xorg.conf as described in the link in my signature.

---

