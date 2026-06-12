---
title: "dual head nvidia + kvm"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by chicos on 2006-11-04
All,

i've been having a small problem recently with nvidia card. it's nothing that annoys me, but it is a little awkward and I'd like to get rid of the issue / make it work (if possible, that is ;)).

I'm using three machines in total here (pegasos, a1 and pc) that are connected thru kvm switch. the card on my pc has two dvi outputs, so the display is connected via dvi-vga connector. second output is connected directly to my display's dvi in (dell 2005fpw), so i can enjoy hi-quality picture and - if i need - switch between machines quickly.

that is my wishful thinking. 

the problem is, kvm does not pass edid information back to card. i have been trying a dozen different settings to make the second display (pseudo-crt) working, but without luck (i can eventually make it go up in 640x480@60, with random luck). there is nothing wrong in my logs (i guess), except the warning that nv driver was unable to obtain crt's edid, and later compute dpi:

```

(**) NVIDIA(0): Option "ConnectedMonitor" "DFP-0, CRT-1"
(**) NVIDIA(0): Option "TwinView" "true"
(**) NVIDIA(0): Option "TwinViewOrientation" "Clone"
(**) NVIDIA(0): Option "MetaModes" "DFP-0:1680x1050, CRT-1:1680x1050i;"
(**) NVIDIA(0): Option "Coolbits" "1"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP-0, CRT-1"
(**) NVIDIA(0): OpenGL flipping disabled
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "DFP-0, CRT-1"
(WW) NVIDIA(0): Unable to read EDID for display device CRT-1
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.39.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0):     Dell 2005FPW (DFP-0)
(--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): Dell 2005FPW (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Dell 2005FPW (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Devices: CRT-1, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP-0:1680x1050,CRT-1:1680x1050i"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
(WW) NVIDIA(0):     from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in defaul

```

but it goes ahead correctly. the mode "1680x1050i" is the modeline i added for vga input, but that does not change anything.

settings for my card:

```

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option         "ConnectedMonitor" "DFP-0, CRT-1"
    Option         "TwinView" "true"
    Option         "UseDisplayDevice" "DFP-0, CRT-1"
    Option         "NoFlip" "true"
    Option         "TwinViewOrientation" "Clone"
    Option         "CoolBits" "1"
    Option         "TrippleBuffer" "true"
#    Option         "SecondMonitorHorizSync" "30-83"
#    Option         "SecondMonitorVertRefresh" "56-75"
    Option         "MetaModes" "DFP-0:1680x1050, CRT-1:1680x1050i;"
#    Option         "UseEDID" "false"
#    Option         "AllowGLXWithComposite" "true"
EndSection

```

i have tried uncommenting the secondmonitor* and useedid. if i get the useedid line uncommented (to disable edid) the display goes up, but only at 640x480 (and same thing happens with DFP - no more 1680x1050).

has anyone ever fought similar issues? is there anything i could do to make the "crt" line up & running at 1680x1050?

many thanks for your help people,
tom.

---

