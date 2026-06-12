---
title: "Xorg + RCA L32WD22 LCD TV"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by immerohnegott on 2007-12-27
Howdy...just recieved the aforementioned set for christmas and am having some trouble getting linux to play nice with it. I'm running an Nvidia 7950 GT w/ nvidia-glx-new from synaptic (too lazy to install direct from nvidia). Output is through a DVI to HDMI conversion cable.

The issue I'm getting is that, regardless of resolution, the edges of the screen run off the panel and are therefore invisible. According to the manual, the TV has a max res of 1360 X 768  (which ironically doesn't work in windows either...at all. setting that res garbles the display something fierce). The only way i managed to get this thing viewable was wrangling windows/nvidia control panel to allow me to set the res to 1200 x 684 @ 60 hz. I copied xorg.conf to a backup file and attempted to add this resolution to the xorg.conf file under the monitor section. Attempt one failed and the option didn't appear in the "Change screen resolution" dialog box. Attempt two went further and totally bombed my xorg. Replaced xorg.conf with the copy and am back at square one. Any help would be greatly appreciated.

<edit>
broke down and bought a VGA cable at radio shack (this set has a VGA input as well as HDMI). Works like a charm. No stretching...nothin. 

Sys: Pentium D presler 3.0 ghz (clocked to 3.6); 2 x 1024 + 2 x 512 Corsair XMS2 DDR2 800 CL5; Aforementioned GeForce 7950 GT; ASUS P5B motherboard (intel P965 Express + ICH8 chipsets); running ubuntu 7.10 64-bit.

---

