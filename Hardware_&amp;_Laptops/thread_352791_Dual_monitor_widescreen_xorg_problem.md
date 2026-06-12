---
title: "Dual monitor widescreen xorg problem"
date: 2007-02-03
forum: Hardware &amp; Laptops
---

### Post by krisnilsen on 2007-02-03
Hey everyone,

I have just got my self a new 22" acer widscreen monitor. 
I have it setup in twinview with a 17" LCD.
I am trying to get th 22" to work at its natural 1680x1050 res with my 17" running at 1280x1024.
For some reason the monitor turns off when i try this combo of res. I can get each monitor to work individually at these res.

Here is some of the xorg.conf
Option "TwinView"
Option "SecondMonitorHorizSync" "31.5 - 60.7"
Option "SecondMonitorVertRefresh" "60 - 75"
Option "TwinViewOrientation"    "RightOf" 
Option "MetaModes"     "1280x1024, 1680x1050"

I have had twinview with 2 17" LCD working fine in the past.
At he moment I have it running at "1280x1024,1024x768", it will let me do that.
PS (I got it to work in windows)
thanks

---

### Post by kerry_s on 2007-02-03
-> [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/README/index.html)

---

### Post by krisnilsen on 2007-02-05
I have already looked there and I cant find a solution.
I have done the twinview setup. The only thing i can think of is
it thinks my card it limited by the pixel clock, but it should not.

---

### Post by krisnilsen on 2007-02-05
I think i found the problem in the log though

did an nvidia-bug-report.log
found this
(II) NVIDIA(0): Validating Mode "1680x1050":
(II) NVIDIA(0): 1680 x 1050 @ 60 Hz
(II) NVIDIA(0): Mode Source: X Server
(II) NVIDIA(0): Pixel Clock : 147.14 MHz
(II) NVIDIA(0): HRes, HSyncStart : 1680, 1784
(II) NVIDIA(0): HSyncEnd, HTotal : 1968, 2256
(II) NVIDIA(0): VRes, VSyncStart : 1050, 1051
(II) NVIDIA(0): VSyncEnd, VTotal : 1054, 1087
(II) NVIDIA(0): H/V Polarity : +/+
(WW) NVIDIA(0): Mode is rejected: PixelClock (147.1 MHz) too high for EDID
(WW) NVIDIA(0): (EDID Max: 135.0 MHz).

THis is not right. The monitor can go to ~165 Mz
 I ran it again without
logverbose 6
and found another section
II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NvAGP" "1"
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "31.5 - 60.7"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "56 - 75"
(**) NVIDIA(0): Option "MetaModes" "1280x1024, 1680x1050"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0): enabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): Use of NVIDIA internal AGP requested
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5900XT at PCI:3:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.35.20.32.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5900XT at
(--) NVIDIA(0): PCI:3:0:0:
(--) NVIDIA(0): IQT Q17 Analog (CRT-0)
(--) NVIDIA(0): Acer AL2216W (DFP-0)
(--) NVIDIA(0): IQT Q17 Analog (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): Acer AL2216W (DFP-0): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): Acer AL2216W (DFP-0): External Single Link TMDS
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): "1280x1024,1680x1050"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC? No, I don't.


So it knows that it has a max of 165 MHz
I have tried adding in
Option "ModeValidation" "NoMaxPClkCheck"
to xorg.conf
and I tried manually setting the virtual screen size with no luck for either

---

### Post by krisnilsen on 2007-02-08
It is alright, I fixed it.
Turns out I had manually set my max HSync rate in the xorg.conf so it would not let me do that clock freq with that res.
Commented that line out and it worked no probs
Stupid me

---

### Post by Slim Odds on 2007-03-14
> **krisnilsen said:**
> It is alright, I fixed it.
Turns out I had manually set my max HSync rate in the xorg.conf so it would not let me do that clock freq with that res.
Commented that line out and it worked no probs
Stupid me

Can you please post your xorg.conf file so that we can refer to it?

Thanks

---

