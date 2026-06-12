---
title: "Second monitor blank after screen saver when using KVM switch"
date: 2014-07-12
forum: Hardware
---

### Post by JonoBNZ on 2014-07-12
Hi everyone,

I've got a bit of a weird problem that I haven't been able to find any help for.  I'm not even sure where to look because I've never had to debug any video issues in linux before.

Basically it goes like this:

I have Ubuntu 12.04 installed (running Mate as a desktop environment, though) with dual monitors through an nvidia graphics card.  I'm using the nvidia binary blob drivers.

The primary monitor has all the menus etc. on with the 2nd monitor as just extra workspace.  The 2nd monitor is connected through a KVM switch that I use with other PCs as well.

The issue is that when I have the KVM switch set to use the other PC and my Ubuntu PC goes into screensaver mode, instead of going black straight away as it's set to, it seems to reconfigure the monitors so that the 2nd monitor no longer works (no signal, just goes to sleep if I set the KVM switch back to my Ubuntu PC) and the 1st monitor keeps the same programs open on it etc. but no longer has the taskbar or menu bar on it.  There appears to be an invisible workspace to the right now which I assume has the menu bars on.  Additionally, if the PC is left like this and goes to screensaver (just powers off the monitors and locks the PC) then sometimes the login screen appears on the invisible workspace as well, so I have to type in the password blind.

I can get the monitors back to normal by loading nvidia-settings and clicking detect displays.  This brings it all back to how it should be.

This doesn't happen if the KVM switch is set to the Ubuntu PC and the screensaver kicks in.  Additionally, I've been running this setup for a couple of years now and this has only started happening in the past ~6 months.

I've checked in dmesg and anything in /var/log that looks likely but haven't come across any messages that seem to relate.  Anyone have any idea where I should be looking for this?

Given that the nvidia-settings detect displays brings it back, I'm assuming this is probably an issue with the display driver itself, not with Mate.  If it's likely to be an issue with Mate, is there anyone else here using it or should I be looking elsewhere for help?

Sorry for the lack of concrete information here.  I'm hoping someone can point me to a few steps to retrieve whatever info is useful.

Edit:  Wow, made this account in 2007 and have never posted... Didn't realise how long I'd been lurking here!

---

### Post by JonoBNZ on 2014-07-12
I've pulled this out of /var/log/Xorg.0.log when it does it.

The first section (837572-837573) is when the screensaver tries to come on and the screens reshuffle themselves and then the rest is when I loaded nvidia-settings and clicked detect displays to bring it back to normal.

Sorry for the large timestamp numbers, I tend to leave this PC on until it needs an update restart.

[837572.658] (II) NVIDIA(GPU-0): Display (DELL U2412M (CRT-1)) does not support NVIDIA 3D
[837572.658] (II) NVIDIA(GPU-0):     Vision stereo.
[837572.658] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[837572.658] (**) NVIDIA(0):     device DELL U2412M (CRT-1) (Using EDID frequencies has
[837572.658] (**) NVIDIA(0):     been enabled on all display devices.)
[837572.727] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[837572.727] (II) NVIDIA(GPU-0):     Vision stereo.
[837572.727] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[837572.727] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[837572.727] (**) NVIDIA(0):     been enabled on all display devices.)
[837572.883] (II) NVIDIA(GPU-0): Display (DELL U2412M (CRT-1)) does not support NVIDIA 3D
[837572.883] (II) NVIDIA(GPU-0):     Vision stereo.
[837572.883] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[837572.883] (**) NVIDIA(0):     device DELL U2412M (CRT-1) (Using EDID frequencies has
[837572.883] (**) NVIDIA(0):     been enabled on all display devices.)
[837572.952] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[837572.952] (II) NVIDIA(GPU-0):     Vision stereo.
[837572.952] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[837572.952] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[837572.952] (**) NVIDIA(0):     been enabled on all display devices.)
[837573.098] (II) NVIDIA(0): Setting mode "DVI-I-2: nvidia-auto-select @1920x1200 +0+0, DVI-I-1: nvidia-auto-select @1920x1200 +1920+0"
[837637.929] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[837637.929] (II) NVIDIA(GPU-0):     Vision stereo.
[837637.929] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[837637.929] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[837637.929] (**) NVIDIA(0):     been enabled on all display devices.)
[837637.998] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-1)) does not support NVIDIA 3D
[837637.998] (II) NVIDIA(GPU-0):     Vision stereo.
[837637.998] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[837637.998] (**) NVIDIA(0):     device DELL U2412M (DFP-1) (Using EDID frequencies has
[837637.998] (**) NVIDIA(0):     been enabled on all display devices.)
[837638.174] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[837638.174] (II) NVIDIA(GPU-0):     Vision stereo.
[837638.174] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[837638.174] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[837638.174] (**) NVIDIA(0):     been enabled on all display devices.)
[837638.243] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-1)) does not support NVIDIA 3D
[837638.243] (II) NVIDIA(GPU-0):     Vision stereo.
[837638.243] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[837638.243] (**) NVIDIA(0):     device DELL U2412M (DFP-1) (Using EDID frequencies has
[837638.243] (**) NVIDIA(0):     been enabled on all display devices.)
[837638.363] (II) NVIDIA(0): Setting mode "DVI-I-2: nvidia-auto-select @1920x1200 +0+0, DVI-I-3: nvidia-auto-select @1920x1200 +1920+0"

---

### Post by JonoBNZ on 2014-07-14
No ideas from anyone?  Is it because I'm using Mate, an old version of Ubuntu, posted in the wrong place, etc.?  I'd love to know!

---

