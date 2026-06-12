---
title: "Nvidia Twinview resolution 5120x1600 Problem."
date: 2009-07-30
forum: Hardware
---

### Post by semy on 2009-07-30
Hi,

I have a major issue with my resolution setup using Nvidia-settings.

The hardware-setup is:
01:00.0 VGA compatible controller: nVidia Corporation G71GL [Quadro FX 3500] (rev a1)
With dual DELL3007WFPHC

This gives a 5120x1600 resolution. Which is not supported apperantly? This wasn't a problem before when using 8.04 of Ubuntu.

When reinstalling my Ubuntu workstation, I now get this in Xorg.log:
(--) NVIDIA(0): Connected display device(s) on Quadro FX 3500 at PCI:1:0:0:
(--) NVIDIA(0):     DELL3007WFPHC (DFP-0)
(--) NVIDIA(0):     DELL3007WFPHC (DFP-1)
(--) NVIDIA(0): DELL3007WFPHC (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL3007WFPHC (DFP-0): Internal Dual Link TMDS
(--) NVIDIA(0): DELL3007WFPHC (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL3007WFPHC (DFP-1): Internal Dual Link TMDS
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select,nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 5120 x 1600
(WW) NVIDIA(0): Virtual screen width of 5120 pixels is too large; clamping to
(WW) NVIDIA(0):     4096
(WW) NVIDIA(0): Mode "nvidia-auto-select,nvidia-auto-select" is larger than
(WW) NVIDIA(0):     virtual size 4096 x 1600; discarding mode
(EE) NVIDIA(0): Failure to construct a valid mode list: no modes remaining.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"

Been trying to run Xinerama instead of Twinview but can't get it running properly.

Trying to find someone who got this running on jaunty that has posted how to sort it out has failed. Nothing of my tricks will fix this for me.

Anyone got some advice towards a solution? Google points out that more people have this problem but I can't find any solutions.

Thanks in advance.

---

### Post by jaygo on 2010-08-17
I'm not sure how it was working with 8.04 because nvidia says it's a hardware limitation on older cards (using chips prior to G80) when using TwinView: [http://www.nvnews.net/vbulletin/showthread.php?t=57619]("http://www.nvnews.net/vbulletin/showthread.php?t=57619")

---

