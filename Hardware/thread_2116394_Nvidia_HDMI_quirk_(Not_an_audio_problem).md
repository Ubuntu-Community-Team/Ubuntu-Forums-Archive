---
title: "Nvidia HDMI quirk (Not an audio problem)"
date: 2013-02-15
forum: Hardware
---

### Post by Subv3rse on 2013-02-15
Hi All,

Wonder if someone can help me out here; I have an Nvidia GTX670 hooked up to a dell 23" via DVI and an LG 42" LW450U-ZB.  (Generically known as 42LW450U)

Sort of hard to explain this so I'll break it down into bullet points:

-If i'm on Unity desktop, everything is fine
-If i'm at the login window* everything is fine, minus the * point below.
-Xubuntu (previous installs) works fine
-Openbox / Kubuntu  / *Ubuntu top right corner restart box at login screen and various other configs / setups give me ENORMOUS fonts IF either the HDMI is set to the primary / mirrored output OR the only output (monitor disconnected)

The odd thing is that the windows / graphics rendering actually stay the correct size. As an indication (although I'm using Ubuntu / Unity again now, but in Kubuntu I had to drop font size down from 9pt to 4pt to be able to get a semi-usable desktop.

I'm not sure whether this is of note, but on installation of (any) Ubuntu (or derivative) it doesn't appear to be creating an /etc/X11/xorg.conf file; I have to manually create one using Nvidia's 310 drivers; at which point if I try making my HDMI/TV primary / mirrored then the font's bug out.

Nvidia settings recognise the TV as "LG Electronics LG TV" running at 1920x1080, no problem. Ubuntu's own "Displays" on the other hand appears to think it's a Goldstar Company Ltd 7" screen. A stab in the dark on my part would suggest that X is rendering the fonts thinking it's that, whereas Nvidia is handling the rest of it, and therefore getting a bit mixed up, but I don't know enough about linux to know what's going on or how to fix it.

To repeat, actual Ubuntu login screen is fine, except for the box to shutdown / restart in the top right.
Unity / XFCE don't display problems.
OpenBox / KDE (all of it) etc (and that login screen window) or anything that generates "that" type of window it seems tends to break.

Latest effort to fix it was to delete xorg.conf and either not use any other DE, or have the monitor on and connected with desktops in extended (rather than mirrored) modes for things to work properly.

Problem exhibits on 12.04.2 / 12.10,, x64 and all derivatives. Using Nvidia 310.14 prop.

Any ideas? 

-Subv3rse

---

### Post by eac537 on 2013-02-20
I have this exact graphics card and an LG 42LV5500, and almost this exact problem. See a representative snipped my Xorg.0.log below. (The same messages repeat many times.)

I installed via the normal Ubuntu 12.10, but then installed kde-full and use that now exclusively; I'm observing this symptom in the kdm login screen and in the actual kde desktop. 

```

[    22.994] (II) NVIDIA(GPU-0): Display (Apple LED Cinema (DFP-4)) does not support NVIDIA 3D
[    22.994] (II) NVIDIA(GPU-0):     Vision stereo.
[    22.994] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    22.994] (**) NVIDIA(0):     device Apple LED Cinema (DFP-4) (Using EDID frequencies
[    22.994] (**) NVIDIA(0):     has been enabled on all display devices.)
[    98.061] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    98.061] (**) NVIDIA(0):     device LG Electronics LG TV (DFP-3) (Using EDID
[    98.061] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    98.062] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-3) contradicts itself:
[    98.062] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    98.062] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (57.000-63.000 Hz) would
[    98.062] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (30.0 Hz); ignoring
[    98.062] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    98.062] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-3) contradicts itself:
[    98.062] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    98.062] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (31.000-82.000 kHz) would
[    98.062] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (27.0 kHz); ignoring
[    98.062] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1920x1080".
[    98.062] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-3) contradicts itself:
[    98.062] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    98.062] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (57.000-63.000 Hz) would
[    98.062] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (24.0 Hz); ignoring
[    98.062] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    98.083] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    98.083] (**) NVIDIA(0):     device LG Electronics LG TV (DFP-3) (Using EDID
[    98.083] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    98.083] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-3) contradicts itself:
[    98.083] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    98.083] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (57.000-63.000 Hz) would
[    98.083] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (30.0 Hz); ignoring
[    98.083] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[    98.083] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-3) contradicts itself:
[    98.083] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    98.083] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (31.000-82.000 kHz) would
[    98.083] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (27.0 kHz); ignoring
[    98.083] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1920x1080".
[    98.083] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-3) contradicts itself:
[    98.083] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[    98.083] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (57.000-63.000 Hz) would
[    98.083] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (24.0 Hz); ignoring
[    98.083] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[   102.777] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   102.777] (**) NVIDIA(0):     device LG Electronics LG TV (DFP-3) (Using EDID
[   102.777] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[   102.778] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-3) contradicts itself:
[   102.778] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[   102.778] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (57.000-63.000 Hz) would
[   102.778] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (30.0 Hz); ignoring
[   102.778] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
[   102.778] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-3) contradicts itself:
[   102.778] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[   102.778] (WW) NVIDIA(GPU-0):     EDID's valid HorizSync range (31.000-82.000 kHz) would
[   102.778] (WW) NVIDIA(GPU-0):     exclude this mode's HorizSync (27.0 kHz); ignoring
[   102.778] (WW) NVIDIA(GPU-0):     HorizSync check for mode "1920x1080".
[   102.778] (WW) NVIDIA(GPU-0): The EDID for LG Electronics LG TV (DFP-3) contradicts itself:
[   102.778] (WW) NVIDIA(GPU-0):     mode "1920x1080" is specified in the EDID; however, the
[   102.778] (WW) NVIDIA(GPU-0):     EDID's valid VertRefresh range (57.000-63.000 Hz) would
[   102.778] (WW) NVIDIA(GPU-0):     exclude this mode's VertRefresh (24.0 Hz); ignoring
[   102.778] (WW) NVIDIA(GPU-0):     VertRefresh check for mode "1920x1080".
```

---

