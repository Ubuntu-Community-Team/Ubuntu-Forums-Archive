---
title: "When HDMI output in use, display freezes for 100ms every 700ms on nvidia-390"
date: 2018-11-25
forum: Hardware
---

### Post by semw2 on 2018-11-25
When an HDMI output is connected, the display output freezes/stutters for 100ms every 700ms, on both displays (normal monitor and the HDMI output).

When HDMI is connected, Xorg.0.log is full of a continuous flow of:
```

[   811.155] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): connected
[   811.155] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): Internal TMDS
[   811.155] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): 225.0 MHz maximum pixel clock
[   811.155] (--) NVIDIA(GPU-0): 
[   811.252] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): connected
[   811.252] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): Internal TMDS
[   811.252] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): 225.0 MHz maximum pixel clock
[   811.252] (--) NVIDIA(GPU-0): 
[   811.820] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): connected
[   811.821] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): Internal TMDS
[   811.821] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): 225.0 MHz maximum pixel clock
[   811.821] (--) NVIDIA(GPU-0): 
[   811.885] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): connected
[   811.885] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): Internal TMDS
[   811.885] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): 225.0 MHz maximum pixel clock
[   811.885] (--) NVIDIA(GPU-0): 
[   812.453] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): connected
[   812.454] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): Internal TMDS
[   812.454] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): 225.0 MHz maximum pixel clock
[   812.454] (--) NVIDIA(GPU-0): 
[   812.518] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): connected
[   812.518] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): Internal TMDS
[   812.518] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): 225.0 MHz maximum pixel clock
[   812.518] (--) NVIDIA(GPU-0): 
[   813.119] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): connected
[   813.119] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): Internal TMDS
[   813.119] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): 225.0 MHz maximum pixel clock
[   813.119] (--) NVIDIA(GPU-0): 
[   813.216] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): connected
[   813.216] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): Internal TMDS
[   813.216] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): 225.0 MHz maximum pixel clock
[   813.216] (--) NVIDIA(GPU-0): 
[   813.784] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): connected
[   813.784] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): Internal TMDS
[   813.784] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): 225.0 MHz maximum pixel clock
[   813.784] (--) NVIDIA(GPU-0): 
[   813.881] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): connected
[   813.881] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): Internal TMDS
[   813.881] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): 225.0 MHz maximum pixel clock
[   813.881] (--) NVIDIA(GPU-0): 
[   814.482] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): connected
[   814.482] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): Internal TMDS
[   814.482] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): 225.0 MHz maximum pixel clock
[   814.482] (--) NVIDIA(GPU-0): 
[   814.578] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): connected
[   814.578] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): Internal TMDS
[   814.578] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): 225.0 MHz maximum pixel clock
[   814.578] (--) NVIDIA(GPU-0): 
[   815.179] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): connected
[   815.179] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): Internal TMDS
[   815.179] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): 225.0 MHz maximum pixel clock
[   815.179] (--) NVIDIA(GPU-0): 
[   815.276] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): connected
[   815.276] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): Internal TMDS
[   815.276] (--) NVIDIA(GPU-0): XXX AAA (DFP-1): 225.0 MHz maximum pixel clock
[   815.276] (--) NVIDIA(GPU-0): 

```

Note the timestamps -- the pause between successive message trios alternates between ~100ms and ~600ms.

During the freeze, CPU usage by xorg very briefly spikes to 100%.

At the suggestion of [http://forums.debian.net/viewtopic.php?f=6&t=129776](http://forums.debian.net/viewtopic.php?f=6&t=129776) (someone with similar log issue, though no comment about stuttering), I tried downgrading my nvidia driver version to 340. This did indeed fix the problem. But also caused other problems which have been fixed in newer drivers, so I'd rather not downgrade if at all possible. (Newer 410 versions of the nvidia driver drop support for my (Fermi) graphics card, so upgrading isn't an option).

Have tried `xset -dpms`; it doesn't fix it. Also tried `drm_kms_helper.poll=0` in the grub cmdline; no difference. Also tried various different modes (resolutions, refresh rates) for the hdmi output with xrandr, and every configurable option in nvidia-settings; none make any difference.

Any suggestions?

---

### Post by Autodave on 2018-11-26
Can you give us some specs on your machine? Especially what Nvidia card?  Where did you get the driver from?

---

### Post by semw2 on 2018-11-27
> Can you give us some specs on your machine? Especially what Nvidia card?

Nvidia card is a GTX 460. ie fermi arch.

Complete output of lshw in case anything else is relevant: [https://pastebin.com/raw/aT74uFZ1](https://pastebin.com/raw/aT74uFZ1)

> Where did you get the driver from?

The  default repositories. Ubuntu 18.04, both 390 and 340 drivers are   included: [https://packages.ubuntu.com/bionic/nvidia-driver-390](https://packages.ubuntu.com/bionic/nvidia-driver-390) ;   [https://packages.ubuntu.com/bionic/nvidia-340](https://packages.ubuntu.com/bionic/nvidia-340) .

---

### Post by semw2 on 2018-11-28
Update: it was a dodgy HDMI cable.

---

