---
title: "radeonhd dvi gives mis-aligned colour on samsung Synmaster 225bw"
date: 2010-10-01
forum: Hardware
---

### Post by samjam on 2010-10-01
I have an HP laptop and docking station with DVI and VGA out.

I have 2 Samsung Syncmaster 225bw monitors connected. Often the DVI monitor has one or two colors misaligned by one pixel giving a horrid blurry effect.

I've tried swapping monitors, but the only the one in the DVI  has the problem. If I re-power the monitor the amount of blur may change, and sometimes goes away after being powered up for a long time - but may come back if I reboot the laptop (suggesting it is a graphics card problem).

lspci lists my graphics adaptor as being:

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]

My xorg.conf lists the DVI monitor as:
Section "Monitor"
        Identifier   "DVI-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1680x1050"
        Option      "TargetRefresh" "60"
        Option      "RightOf" "VGA-0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Anyone know what I might to to tweak the graphics card - I think I want to offset the sync by less than one pixel so that the monitor samples the VGA at a different point.

---

