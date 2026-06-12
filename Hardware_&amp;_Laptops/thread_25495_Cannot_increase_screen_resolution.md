---
title: "Cannot increase screen resolution?"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by spirilis on 2005-04-10
I have an ATI Radeon 9800Pro 256MB video card in my machine.  I just installed Ubuntu 5.04 an hour ago and am fiddling with the X settings.

The monitor is a Dell 2005FPW 20" Widescreen LCD monitor, maximum resolution 1680x1050.
Ubuntu has locked me into 1280x1024, which looks rather unsightly after previously using 1680x1050 in SuSE.  I cannot increase the resolution for some reason.  I have tried adding "1680x1050" to the Modes in /etc/X11/xorg.conf but Xorg seems to be ignoring them.

The /var/log/Xorg.0.log file indicates the following regarding modes:
(II) RADEON(0): DDC Type: 3, Detected Type: 0
(II) RADEON(0): EDID data from the display on port 1 ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: e009  Serial#: 875968332
(II) RADEON(0): Year: 2005  Week: 6
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 43  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.637 redY: 0.340   greenX: 0.297 greenY: 0.610
(II) RADEON(0): blueX: 0.146 blueY: 0.071   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 119.0 MHz   Image Size:  434 x 270 mm
(II) RADEON(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) RADEON(0): Serial No: T6130529467L
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 83 kHz, PixClock max 140 MHz
(II) RADEON(0): Monitor name: DELL 2005FPW
(II) RADEON(0):
(II) RADEON(0): Primary:
 Monitor   -- TMDS
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=29000
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): DFP table revision: 4
(II) RADEON(0): Panel infos found from DDC detailed: 1680x1050
(II) RADEON(0): Valid Mode from Detailed timing table: 1680x1050
(II) RADEON(0): Valid Mode from standard timing table: 1280x1024
(II) RADEON(0): Valid Mode from standard timing table: 1152x864
(II) RADEON(0): Valid Mode from established timing table: 1280x1024
(II) RADEON(0): Valid Mode from established timing table: 1024x768
(II) RADEON(0): Valid Mode from established timing table: 1024x768
(II) RADEON(0): Valid Mode from established timing table: 800x600
(II) RADEON(0): Valid Mode from established timing table: 800x600
(II) RADEON(0): Valid Mode from established timing table: 640x480
(II) RADEON(0): Valid Mode from established timing table: 640x480
(II) RADEON(0): Total of 10 mode(s) found.
(II) RADEON(0): Total number of valid DDC mode(s) found: 10
(--) RADEON(0): Virtual size is 1280x1024 (pitch 1280)
(**) RADEON(0): *Default mode "1280x1024": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1280x1024"  119.00  1280 1728 1760 1840  1024 1053 1059 1080 +hsync +vsync
(**) RADEON(0): *Default mode "1152x864": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1152x864"  119.00  1152 1728 1760 1840  864 1053 1059 1080 +hsync +vsync
(**) RADEON(0): *Default mode "1024x768": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1024x768"  119.00  1024 1728 1760 1840  768 1053 1059 1080 +hsync +vsync
(**) RADEON(0): *Default mode "800x600": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "800x600"  119.00  800 1728 1760 1840  600 1053 1059 1080 +hsync +vsync
(**) RADEON(0): *Default mode "640x480": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "640x480"  119.00  640 1728 1760 1840  480 1053 1059 1080 -hsync -vsync
(**) RADEON(0):  Default mode "1280x1024": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1280x1024"  119.00  1280 1728 1760 1840  1024 1053 1059 1080 +hsync +vsync
(**) RADEON(0):  Default mode "1024x768": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "1024x768"  119.00  1024 1728 1760 1840  768 1053 1059 1080 -hsync -vsync
(**) RADEON(0):  Default mode "800x600": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "800x600"  119.00  800 1728 1760 1840  600 1053 1059 1080 +hsync +vsync
(**) RADEON(0):  Default mode "640x480": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
(II) RADEON(0): Modeline "640x480"  119.00  640 1728 1760 1840  480 1053 1059 1080 -hsync -vsync
(--) RADEON(0): Display dimensions: (430, 270) mm
(--) RADEON(0): DPI set to (75, 96)


^^ It would seem that it recognizes 1680x1050, but it's locking the "Virtual" size into 1280x1024.  I do not see *anything* in /etc/X11/xorg.conf which is setting a Virtual size at all.

Can someone please advise?

Thanks!

---

### Post by soul_rebel on 2005-04-10
did you added the resolution you want as the FIRST mode?

---

### Post by spirilis on 2005-04-10
Yes:
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 9800 (R350 NI)"
        Monitor         "DELL 2005FPW"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

(it's not doing 1400x1050 either, even though the mode is there)

---

### Post by soul_rebel on 2005-04-10
config file is ok. Does the log say anything about "not using resolution xxx*xxx (cause)" ? I have a lot of those lines

---

### Post by spirilis on 2005-04-10
[QUOTE=soul_rebel]config file is ok. Does the log say anything about "not using resolution xxx*xxx (cause)" ? I have a lot of those lines[/QUOTE]
 Nope.  It does say (you can see above) that 1680x1050 is a valid mode from "Detailed timing table"

The only clue I can see is that 1280x1024 is the highest Supported VESA Video Mode (also see above).  If I had an idea, I would assume that Xorg is somehow locking me into VESA video modes only, but I don't see any kind of configuration directive mandating that.

Is there a full list of device options for the "ati" driver anywhere?  Maybe I need an option somewhere to slap it into shape...

---

### Post by soul_rebel on 2005-04-10
are the ati driver working correclty? do you have 3d acceleration working?

---

### Post by spirilis on 2005-04-10
[QUOTE=soul_rebel]are the ati driver working correclty? do you have 3d acceleration working?[/QUOTE]
 I haven't touched 3D and don't intend to anytime soon.  I need this resolution problem fixed first, or else I'll have to search for another distro to install :)

---

### Post by soul_rebel on 2005-04-10
are you sure you are running the ATI proprietary driver? they require some packages (and some tweaking i think)

---

### Post by spirilis on 2005-04-10
I am not running the proprietary ATI driver... I am running what came out-of-the-box with Ubuntu.  It seems to be using an 'ati' driver of some sort that came with the distro.  Based on the detailed output of Xorg.0.log, I'd assume this driver should be capable of doing the job...
I suppose I *could* try the proprietary drivers if this doesn't work...

FYI, here's details on the driver from Xorg.0.log:
```
(II) LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 6.5.6
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.7
```

---

### Post by spirilis on 2005-04-10
[QUOTE=spirilis]I am not running the proprietary ATI driver... I am running what came out-of-the-box with Ubuntu.  It seems to be using an 'ati' driver of some sort that came with the distro.  Based on the detailed output of Xorg.0.log, I'd assume this driver should be capable of doing the job...
I suppose I *could* try the proprietary drivers if this doesn't work...

FYI, here's details on the driver from Xorg.0.log:
```
(II) LoadModule: "ati"
(II) Loading /usr/X11R6/lib/modules/drivers/ati_drv.o
(II) Module ati: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 6.5.6
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.7
```[/QUOTE]
 I'm going to attempt to install the proprietary ATI drivers now.  I'll see how this goes...

---

### Post by spirilis on 2005-04-10
[QUOTE=spirilis]I'm going to attempt to install the proprietary ATI drivers now.  I'll see how this goes...[/QUOTE]
 Ahhh, nevermind, I just realized I am being a complete idiot.

I was making changes to xorg.conf, then Logging Out and wondering why those changes were not taking effect.

I didn't realize that Log Out didn't actually kill the X server.
Now that I CTRL-ALT-BACKSPACE'd the sucker, I am up and running just fine with the new fglrx driver.  I will report once I get 3D working :D

*happily computing at 1680x1050*

---

### Post by spirilis on 2005-04-10
It appears DRI is working fine too.  I'll do a reboot and make sure things come up properly.

Thanks again everyone for hearing out my rant of noobism  \\:D/

---

