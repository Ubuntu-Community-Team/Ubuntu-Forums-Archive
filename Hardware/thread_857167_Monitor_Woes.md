---
title: "Monitor Woes"
date: 2008-07-12
forum: Hardware
---

### Post by EmyrB on 2008-07-12
Hi All

Just installed a new system and I am having a really hard time getting Ubuntu Hardy Heron 8.04.1 to detect my monitor. The Monitor is a Hanns.G HN198D but my xorg.conf lists nothing except "Compatibility Monitor".

When I booted from the LiveCD, I had a resolution of 1280 x 768, which wasn't right, but it was better than nothing. The install went okay, and I rebooted into my shiny new 64bit Ubuntu with a resolution of 1280 x 768. It detected my nVidia 8400GS and downloaded the restricted driver. After I rebooted, I was left with a screen resolution of 640 x 480 and I have tried in vain all morning to get a higher resolution but to no avail.

HELP!

---

### Post by Zimmer on 2008-07-12
Have a look at post #3  here to try for correct Monitor settings..
[http://ubuntuforums.org/showthread.php?t=276650](http://ubuntuforums.org/showthread.php?t=276650)

Regards

---

### Post by EmyrB on 2008-07-13
Hi Zimmer,

I did what you said in your link and this is what was in /var/log/xorg.0.log: -

(WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-1's EDID.

Crivens!! :(

---

### Post by Zimmer on 2008-07-13
errr.. right...
So I tried looking at my last log...
(II) fglrx(0): Connected Display1: CRT on primary DAC
(II) fglrx(0):  Display1: No EDID information from DDC.
(WW) fglrx(0): Specified desktop setup not supported: 8
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000004
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 324/189MHz @ 50Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 12 modes found for primary display.
(--) fglrx(0): Virtual size is 1024x768 (pitch 1024)
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 772 817 interlace
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
..... etc.

So, since I last did that, something has changed either in X or the fglrx drivers or H/W detection . No info for my monitor either, and it is the same AL1511 ...
However, The modelines following this info could be derived from info from the monitor. A guess, but they do not come from my xorg.conf, 'cos there's only one there and it does not match (comes close) any either.
It may be that you need to select a modeline from the list and put it in your xorg.conf.. I say MAY, I will need to go away and see if I can find out.  
Regards
Zimmer

EDIT#1
[http://www.x.org/wiki/FAQVideoModes](http://www.x.org/wiki/FAQVideoModes)
This confirms what I wrote originally, so I must go and see if my monitor is connected ok.(I put an extension vga cable on it some months back!!)
Ok. Removed extension cable and my EID info is now recorded in log.
So, check your cable, perhaps.
EDIT#2 found hsync and vsync for your monitor
                     
Input           H-Frequency 31KHz – 80KHz
                V-Frequency 55 – 75Hz
Display Colors              16.2M Colors
Dot Clock                   135MHz
Max. Resolution             1280 x 1024 @75Hz

                            HORIZONTAL       VERTICAL
  VIDEO MODE   RESOLUTION
                          FREQUENCY (kHz) FREQUENCY (Hz)
              640 × 480      31.469           59.94
         VGA  640 × 480      37.500           75.00
              640 × 480      37.861           72.81
              800 × 600      35.156           56.25
              800 × 600      37.879           60.32
         SVGA
              800 × 600      48.077           72.19
VESA
              800 × 600      46.875           75.00
              1024 × 768     48.363           60.00
         XGA  1024 × 768     56.476           70.07
              1024 × 768     60.023           75.03
              1280 × 1024    63.981           60.02
         SXGA
              1280 × 1024    79.976           75.03
              640 × 350      31.469           70.09
IBM      DOS  640 × 400      31.469           70.09
              720 × 400      31.469           70.09
              640 × 480      35.000           66.67
MAC           832 × 624      49.725           74.55
              1152 × 870     68.681           75.06
may help constructing a valid modeline statement.

---

### Post by EmyrB on 2008-07-14
Ah Zimmer you are a god send. I cannot thank you enough. I shall construct my xorg.conf tonight with the data you have supplied and if all works, I shall make a copy of the xorg.conf so that in future as long as my GFX hardware doesn't change I shall be sorted.

Cheers

---

### Post by EmyrB on 2008-07-17
I have managed to construct a new xorg.conf file with the information and links Zimmer supplied, but now I have an issue with gdm. It appears to me as if 1280 x 1024 login screen is been displayed on a 640 x 480 resolution. If I change the Virtual Mode in my xorg.conf, I end up changing the resolution for the desktop.

Is there anyway to alter the resolution that gdm uses without affecting the resolution of the desktop?

Cheers

EmyrB

---

### Post by cocopuffz on 2008-07-17
try this gksudo displayconfig-gtk

I was told this was a gui for the xorg file. Just select auto detect monitor or try the plug and play monitor with your desired resolution from the list. 

Good luck.

---

### Post by Zimmer on 2008-07-17
> **EmyrB said:**
> I have managed to construct a new xorg.conf file with the information and links Zimmer supplied, but now I have an issue with gdm. It appears to me as if 1280 x 1024 login screen is been displayed on a 640 x 480 resolution. If I change the Virtual Mode in my xorg.conf, I end up changing the resolution for the desktop.

Is there anyway to alter the resolution that gdm uses without affecting the resolution of the desktop?

Cheers

EmyrB

Have you been to  System>Preferences>Screen resolution and played with the settings? That may sort the gdm....
http://ubuntuforums.org/showthread.php?t=797264

---

### Post by EmyrB on 2008-07-18
Thanks guys. Zimmer I will give that a shot. Cocopuffz thanks for that, but unfortunately I do not want to reconfigure my xorg.conf file as I now have that setup correctly, but then again...

Cheers

EmyrB

---

