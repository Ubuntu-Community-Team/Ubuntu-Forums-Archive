---
title: "Latpop VGA Out + Dell 2007 WFP Odd Gamma Problem"
date: 2006-12-02
forum: Hardware &amp; Laptops
---

### Post by tehmatticus on 2006-12-02
Ive had my Dell 2006 WFP for about six months now.  Its been a beautiful experience, the big display compensating for the little 15" 1400x1050 panel I have in my Sager notebook.  However, my notebook only has a VGA out, which is fine but oddly it has a strange issue where with this monitor, the brightness/gamma is extremely high by default.  In windows, I'm able to correct this issue by using the driver control panel to tone down the contrast, gamma, and brightness a bit.  However, with the proprietary FGLRX driver in Dapper, i'm unable to do so.

So far, i've just been living with it, though the fact that my screen appears completely washed out has prevented me from really switching full time to linux as i'd like to.  

Interestingly enough, today as I was hunting through my Xorg logs, I noticed this.

```
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: DEL  Model: a018  Serial#: 843854156
(II) fglrx(0): Year: 2006  Week: 18
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 43  vert.: 27
(II) fglrx(0): **Gamma: 2.20**
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): Default color space is primary color space
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329

```

Is my monitor's EDID tags giving out an incorrect gamma?  I tested this monitor on another machine using DVI and VGA as well, and it appeared to have no issues.  It only seems that this laptop has problems with this monitor.  I thought it may have been the video card, but recently the video card died and I sent it back to sager for some out of warranty repairs, which included replacing the video card, and alas, no fix.  

Using xgamma or the fireglcontrol, i'm able to change the gamma, but this really does not help because the colors are still washed out completely.  I leave it up to you, oh mighty Ubuntuforums inhabitants, to help me fix my screen and let me make the full switch to linux!

Thanks,
Matt

---

