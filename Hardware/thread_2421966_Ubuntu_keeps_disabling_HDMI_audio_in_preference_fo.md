---
title: "Ubuntu keeps disabling HDMI audio in preference for analog, stating HDMI unplugged"
date: 2019-06-30
forum: Hardware
---

### Post by adfh on 2019-06-30
I have a media server connected to my lounge TV. By default, it's configured to automatically log into media user profile, and launch Kodi.. but I can also interrupt the auto-login timer and log in with normal desktop environment.

```

# lsb_release -a
...
Distributor ID:    Ubuntu
Description:    Ubuntu 19.04
Release:    19.04
Codename:    disco

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

#lspci -v
...
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4250] (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd RS880 [Radeon HD 4250]
    Flags: bus master, fast devsel, latency 0, IRQ 18, NUMA node 0
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at ee00 [size=256]
    Memory at fdfe0000 (32-bit, non-prefetchable) [size=64K]
    Memory at fde00000 (32-bit, non-prefetchable) [size=1M]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: radeon
    Kernel modules: radeon


01:05.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series]
    Subsystem: Gigabyte Technology Co., Ltd RS880 HDMI Audio [Radeon HD 4200 Series]
    Flags: bus master, fast devsel, latency 0, IRQ 19, NUMA node 0
    Memory at fdffc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 3
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
...

# dmidecode
...
Base Board Information
        Manufacturer: Gigabyte Technology Co., Ltd.
        Product Name: GA-880GM-UD2H
...

# get-edid | edid-decode 
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
1 potential busses found: 1
256-byte EDID successfully retrieved from i2c bus 1
Looks like i2c was successful. Have a good day.
EDID version: 1.3
Manufacturer: SNY Model 8204 Serial Number xxxxxxxx
Made in week 1 of 2018
Digital display
Maximum image size: 122 cm x 68 cm
Gamma: 2.20
RGB color display
First detailed timing is preferred timing
Display x,y Chromaticity:
  Red:   0.6250, 0.3398
  Green: 0.2802, 0.5947
  Blue:  0.1552, 0.0703
  White: 0.2832, 0.2978
Established timings supported:
  640x480@60Hz 4:3 HorFreq: 31469 Hz Clock: 25.175 MHz
  800x600@60Hz 4:3 HorFreq: 37900 Hz Clock: 40.000 MHz
  1024x768@60Hz 4:3 HorFreq: 48400 Hz Clock: 65.000 MHz
Standard timings supported:
  1280x1024@60Hz 5:4 HorFreq: 64000 Hz Clock: 108.000 MHz
  1600x900@60Hz 16:9
  1152x864@75Hz 4:3 HorFreq: 67500 Hz Clock: 108.000 MHz
  1680x1050@60Hz 16:10 HorFreq: 64700 Hz Clock: 119.000 MHz
Detailed mode: Clock 594.000 MHz, 1218 mm x 685 mm
               3840 4016 4104 4400 hborder 0
               2160 2168 2178 2250 vborder 0
               +hsync +vsync 
               VertFreq: 60 Hz, HorFreq: 135000 Hz
Detailed mode: Clock 148.500 MHz, 1218 mm x 685 mm
               1920 2008 2052 2200 hborder 0
               1080 1084 1089 1125 vborder 0
               +hsync +vsync 
               VertFreq: 60 Hz, HorFreq: 67500 Hz
Monitor name: SONY TV  *00
Monitor ranges (GTF): 23-62Hz V, 14-136kHz H, max dotclock 600MHz
Has 1 extension blocks
Checksum: 0xdd (valid)


CTA extension block
Extension version: 3
97 bytes of CTA data
  Video data block
    VIC  97 3840x2160@60Hz 16:9  HorFreq: 135000 Hz Clock: 594.000 MHz
    VIC  96 3840x2160@50Hz 16:9  HorFreq: 112500 Hz Clock: 594.000 MHz
    VIC  93 3840x2160@24Hz 16:9  HorFreq: 54000 Hz Clock: 297.000 MHz
    VIC  94 3840x2160@25Hz 16:9  HorFreq: 56250 Hz Clock: 297.000 MHz
    VIC  95 3840x2160@30Hz 16:9  HorFreq: 67500 Hz Clock: 297.000 MHz
    VIC  98 4096x2160@24Hz 256:135  HorFreq: 54000 Hz Clock: 297.000 MHz
    VIC  31 1920x1080@50Hz 16:9  HorFreq: 56250 Hz Clock: 148.500 MHz
    VIC  16 1920x1080@60Hz 16:9  HorFreq: 67500 Hz Clock: 148.500 MHz
    VIC  20 1920x1080i@50Hz 16:9  HorFreq: 28125 Hz Clock: 74.250 MHz
    VIC   5 1920x1080i@60Hz 16:9  HorFreq: 33750 Hz Clock: 74.250 MHz
    VIC  19 1280x720@50Hz 16:9  HorFreq: 37500 Hz Clock: 74.250 MHz
    VIC   4 1280x720@60Hz 16:9  HorFreq: 45000 Hz Clock: 74.250 MHz
    VIC  32 1920x1080@24Hz 16:9  HorFreq: 27000 Hz Clock: 74.250 MHz
    VIC  34 1920x1080@30Hz 16:9  HorFreq: 33750 Hz Clock: 74.250 MHz
    VIC  60 1280x720@24Hz 16:9  HorFreq: 18000 Hz Clock: 59.400 MHz
    VIC  62 1280x720@30Hz 16:9  HorFreq: 22500 Hz Clock: 74.250 MHz
    VIC  18 720x576@50Hz 16:9  HorFreq: 31250 Hz Clock: 27.000 MHz
    VIC  22 1440x576i@50Hz 16:9  HorFreq: 15625 Hz Clock: 27.000 MHz
    VIC   3 720x480@60Hz 16:9  HorFreq: 31469 Hz Clock: 27.000 MHz
    VIC   7 1440x480i@60Hz 16:9  HorFreq: 15734 Hz Clock: 27.000 MHz
    VIC  17 720x576@50Hz 4:3  HorFreq: 31250 Hz Clock: 27.000 MHz
    VIC  21 1440x576i@50Hz 4:3  HorFreq: 15625 Hz Clock: 27.000 MHz
    VIC   2 720x480@60Hz 4:3  HorFreq: 31469 Hz Clock: 27.000 MHz
    VIC   6 1440x480i@60Hz 4:3  HorFreq: 15734 Hz Clock: 27.000 MHz
    VIC   1 640x480@60Hz 4:3  HorFreq: 31469 Hz Clock: 25.175 MHz
    VIC 101 4096x2160@50Hz 256:135  HorFreq: 112500 Hz Clock: 594.000 MHz
    VIC 102 4096x2160@60Hz 256:135  HorFreq: 135000 Hz Clock: 594.000 MHz
  Audio data block
    Linear PCM, max channels 6
      Supported sample rates (kHz): 192 176.4 96 88.2 48 44.1 32
      Supported sample sizes (bits): 24 20 16
    AC-3, max channels 6
      Supported sample rates (kHz): 48 44.1 32
      Maximum bit rate: 640 kb/s
    DTS, max channels 6
      Supported sample rates (kHz): 48 44.1 32
      Maximum bit rate: 1504 kb/s
    Dolby Digital+, max channels 8
      Supported sample rates (kHz): 48 44.1
  Speaker allocation data block
    Speaker map:
      FL/FR - Front Left/Right
      LFE - Low Frequency Effects
      FC - Front Center
      BL/BR - Back Left/Right
  Vendor-specific data block, OUI 000c03 (HDMI)
    Source physical address 3.0.0.0
    Supports_AI
    DC_36bit
    DC_30bit
    DC_Y444
    Maximum TMDS clock: 300MHz
    Supported Content Types:
      Graphics
      Photo
      Cinema
      Game
    Extended HDMI video details:
      HDMI VIC 1 3840x2160@30Hz 16:9 HorFreq: 67500 Hz Clock: 297.000 MHz
      HDMI VIC 2 3840x2160@25Hz 16:9 HorFreq: 56250 Hz Clock: 297.000 MHz
      HDMI VIC 3 3840x2160@24Hz 16:9 HorFreq: 54000 Hz Clock: 297.000 MHz
      HDMI VIC 4 4096x2160@24Hz 256:135 HorFreq: 54000 Hz Clock: 297.000 MHz
  Vendor-specific data block, OUI c45dd8 (HDMI Forum)
    Version: 1
    Maximum TMDS Character Rate: 600MHz
    SCDC Present
    Supports 10-bits/component Deep Color 4:2:0 Pixel Encoding
  Extended tag: Vendor-specific video data block
  Extended tag: Video capability data block
    YCbCr quantization: Selectable (via AVI YQ) (1)
    RGB quantization: Selectable (via AVI Q) (1)
    PT scan behaviour: No Data (0)
    IT scan behaviour: Always Underscanned (2)
    CE scan behaviour: Support both over- and underscan (3)
  Extended tag: Colorimetry data block
    xvYCC601
    xvYCC709
    sYCC601
    AdobeYCC601
    AdobeRGB
    BT2020cYCC
    BT2020YCC
    BT2020RGB
  Extended tag: YCbCr 4:2:0 capability map data block
    VSD Index 0
    VSD Index 1
    VSD Index 25
    VSD Index 26
  Extended tag: HDR static metadata data block
    Electro optical transfer functions:
      Traditional gamma - SDR luminance range
      SMPTE ST2084
      Hybrid Log-Gamma
    Supported static metadata descriptors:
      Static metadata type 1
Underscans PC formats by default
Basic audio support
Supports YCbCr 4:4:4
Supports YCbCr 4:2:2
0 native detailed modes
Detailed mode: Clock 74.250 MHz, 1218 mm x 685 mm
               1280 1390 1430 1650 hborder 0
                720  725  730  750 vborder 0
               +hsync +vsync 
               VertFreq: 60 Hz, HorFreq: 45000 Hz
Checksum: 0x2 (valid)

```

Yeah, it's a 4K TV, and an old PC only putting out 1080 :) .. but hey, it's a bits-box PC and not a fresh buy.. and 1080 looks fine.

If I log in fresh (either to the Kodi-only profile, or the "Ubuntu" Gnome profile), then I get no audio. When I go into the Ubuntu profile, I'm told that either a Dummy device is connected, or the analog output is connected... and the standard sound control panel will NOT show the HDMI output.

If I go into pavucontrol, and then Configuration, it will advise me that the HDMI device (onboard ATI/AMD HDMI) is in the "unplugged" state and has no profile selected.
I can then override the profile and select "Output: HDMI Stereo" (or similarly worded) and then everything's fine... until I log out.
... then everything's back to normal.

_**How can I instruct Ubuntu to ignore that it thinks HDMI audio is "unplugged", and tell it to always use the HDMI audio out?**_

I did search before posting, and...
[LIST]
[*]I've seen some documentation that talks about editing /etc/pulse/default.pa - so far, I've only managed to completely hide my HDMI audio when I do that.
[*]I've seen some other documentation that talks about editing ~/.asoundrc to similar negative effect (though my understanding is that's tweaking ALSA which sits beneath Pulseaudio right?)
[/LIST]
... it's likely that these would be near the solution, but I've not yet figured out the magic combination. Is there some systemd autodetect magic going on that I need to defeat or is this all Pulseaudio?

Worst comes to worst, I figure there's a pacmd or similar command I can stick in the session init scripts? Where is "unplugged" state determined?

---

