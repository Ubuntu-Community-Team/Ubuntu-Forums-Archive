---
title: "[SOLVED] Graphics driver SiS 630"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by samden on 2008-12-05
I am attempting to boot Xubuntu 8.04 from the live cd on an old desktop machine (it has a Windows ME sticker on the side to give you an idea of the age). It hangs when it has to select the graphics driver, and says it cannot configure this correctly. I have gone through the manual configuration dialogue and tried every single driver available, with no luck - whenever I click the "test" button I get the message "Configuration test failed".

lspci -v
```
VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI AGP VGA Display Adapter (rev 21) (prog-if 00 [VGA controller])
     Subsystem: ASUSTek Computer Inc. Unknown device 80e1
     Flags: 66MHz, medium devsel, IRQ 11
     BIST result: 00
     Memory at f0000000 (32-bit, prefetchable) [size=128M]
     Memory at e9800000 (32-bit, non-prefetchable) [size=128K]
     I/O ports at a800 [size=128]
     Capabilities: <access denied> 
```

I see from the forums that SiS cards aren't very well supported, but most people just seem to have issues getting them to run at the correct resolution. My computer doesn't seem to recognise the card at all.

What might I do to work around this and get Xubuntu installed on this computer?

---

### Post by littlebat on 2008-12-05
Try vesa driver.

Try Xubuntu 8.04 alternative CD , because I know alternative CD is better than others on an old machine.

Here are some useful links you can read:
Ubuntu System Requirements - Community Ubuntu Documentation
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Install Ubuntu on Old Computer(You can install ubuntu with iso image puted in the hard disk without burning a CD.)
[http://www.learndiary.com/en/2008/11/install-ubuntu-on-old-computer.htm](http://www.learndiary.com/en/2008/11/install-ubuntu-on-old-computer.htm)

---

### Post by samden on 2008-12-05
I have tried vesa, no luck. I have been unable to boot the alternative cd yet as I only have a usb keyboard, and this isn't recognised until Linux boots. The live cd automatically loads but the alternative cd won't without some keyboard input. I will borrow a PS/2 keyboard later today if possible to try the alternative cd.

Is there another driver that may work but not be installed on the cd by default, that I could download?

---

### Post by abn91c on 2008-12-05
the pc im on right now has that card and ubuntu 8.10, select start ubuntu in low graphics mode option and you may be able to get to the desktop.for you keyboard issue check your BIOS for an USB DOS support setting, mine is 10 yrs old and it has that. i ws able to install ubuntu 8.10, it runs at 1024 x 768 with low graphics, you cant tell the difference much. No compix or 3D effects, everything else is normal considering its a generic 400mhz celeron with 40 gig IDE HDD and 448Mb ram and SIS chipset pC100 motherboard.
If you get one of those initrams> prompt at reboot  wait a few seconds at the prompt then type exit then hit enter. thats what mine does, sometime i have to type kinit at the prompt then the exit hit enter combination once or twice to get going normally, a minor inconvinience for me but i get full use of Ubuntu 8.10

---

### Post by tazza on 2008-12-05
I think that I have a similar problem. I'm trying to install Ubuntu 7.04 (Feisty Fawn) on a new Toshiba Sattelite laptop and get these errors in the log file:

```

(EE) VESA(0): No matching modes
(II) UnloadModule: "vesa"
(II) UnloadModule: "ddc"
 ~other stuff~
(EE) Screen(s) found, but none have a useable configuration.
Fatal server error:
no screens found

```

before starting the $ prompt.

lspci shows the following:
```

00:02.0 VGA compatible controller: Intel Corporation Unknown device 2a42 (rev 07) (prog-if 00 [VGA])
      Subsystem: Toshiba America Info Systems Unknown device ff67
      Flags: bus master, fast devsel, latency 0, IRQ 11
      Memory at 50000000 (64-bit, non-prefetchable) [size=4M]
      Memory at 40000000 (64-bit, prefetchable) [size=256M]
      I/O ports at 5140 [size=8]
      Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Unknown device 2a43 (rev 07)
      Subsystem: Toshiba America Info Systems Unknown device ff67
      Flags: bus master, fast devsel, latency 0
      Memory at 53500000 (64-bit, non-prefetchable) [size=1M]
      Capabilities: <access denied>

```
among other things. Does this mean that the computer isn't recognising the graphics card?
I tried using BIOs to no avail, so I'm guessing that this is a configuration problem.

---

### Post by littlebat on 2008-12-05
> I'm trying to install Ubuntu 7.04 (Feisty Fawn) on a new Toshiba Sattelite laptop

Maybe you need install restricted modules drivers for your video card, is it a ATI Radeon card? If it is, see: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by samden on 2008-12-06
I obtained a PS/2 keyboard and managed to install from the alternate cd. However I am stuck with 800 x 600 resolution, which is frustrating. It is great to have the computer running, but this does limit what I can do with it.

How might I get the resolution higher? There is no option for a higher resolution in the screen resolution control panel (it only offers 800x600 and 640x480). I note that abn91c has 1024x768 with the same hardware, how did you achieve that?

---

### Post by littlebat on 2008-12-07
See the Driver parameter in Section "Device" in file "/etc/X11/xorg.conf" if it is "sis". If it is "sis", make sure your hardware (include monitor and video card) support 1024x768x16, then try edit file "/etc/X11/xorg.conf" manually.
Add "1024x768" into the Modes line like below:
> 
    Subsection "Display"
        Depth       16
        Modes       "1024x768" "800x600" "640x480"
    EndSubsection

If it can't work, try change Depth from "16" to "8".

---

### Post by samden on 2008-12-07
Thanks heaps, that worked perfectly. I now have it running at 1024x768. I can't seem to get it to go any higher than that so it is probably the limit of the card, the monitor can go higher. Excellent, now I have a usable computer!

By the way, I've put Fluxbox on it now, very practical, I'd recommend it for anyone else with a low spec computer like this one. Xfce idle uses 125Mb of RAM, half what I have, while Fluxbox only uses 47Mb - massive saving.

---

### Post by samden on 2008-12-10
I celebrated too soon, it's gone back to 800x600 again for no apparant reason and whatever I do to xorg.conf (sis or vesa, whatever resolutions I type in) it is determined not to go above that. Not enough time to try and fix it today, but it is extremely frustrating. I have no idea why one day it would work perfectly and the next day it would stop.

---

### Post by abn91c on 2008-12-10
> **samden said:**
> I obtained a PS/2 keyboard and managed to install from the alternate cd. However I am stuck with 800 x 600 resolution, which is frustrating. It is great to have the computer running, but this does limit what I can do with it.

How might I get the resolution higher? There is no option for a higher resolution in the screen resolution control panel (it only offers 800x600 and 640x480). I note that abn91c has 1024x768 with the same hardware, how did you achieve that?

 not sure if it matters but I have a $10.00 emachines 17" monitor from goodwill, when the startup ask's me to "run ubuntu in low graphics mode, i do that, my monitor supports a higher resolution plus 1024 x768 at 0mhz. It works well, colors are fine. Also its a pc100 motherboard

---

### Post by littlebat on 2008-12-10
> **samden said:**
> I celebrated too soon, it's gone back to 800x600 again for no apparant reason and whatever I do to xorg.conf (sis or vesa, whatever resolutions I type in) it is determined not to go above that. Not enough time to try and fix it today, but it is extremely frustrating. I have no idea why one day it would work perfectly and the next day it would stop.
Have you changed anything for your system from the last time it can work at 1024x768?
Keep your Driver parameter in "/etc/X11/xorg.conf" to "sis", and try delete "800x600" and "640x480" entries in Modes parameter. Change "Depth" parameter to "8" and use this Depth as your default Depth.
If this can't work, post your "/etc/X11/xorg.conf" here.

---

### Post by samden on 2008-12-10
I can't think of anything I would have changed that would have affected the display. Current xorg.conf is:```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"sis" #vesa
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
        DefaultDepth    16
	SubSection "Display"
		Modes   "1024x768" 
	EndSubSection
EndSection
``` I have tried using the vesa driver. I have tried with a depth of 8 - and I get nasty old colours (256 colours brings back memories!) but still an 800x600 resolution.

---

### Post by littlebat on 2008-12-11
Try change
> 
	SubSection "Display"
		Modes   "1024x768" 
	EndSubSection

into
> 
	SubSection "Display"
                Depth 16	
		Modes   "1024x768" 
	EndSubSection


---

### Post by samden on 2008-12-11
No luck unfortunately, still 800x600.

---

### Post by littlebat on 2008-12-11
If you haven't changed anything related to displaying, no idea for why this happen and how to resolve this broblem.

At last,
1, Try edit Section "Monitor" to limit its fresh rate
> 
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync    30 - 50
        VertRefresh  50 - 75
EndSection


2, If it can't work, revert /etc/X11/xorg.conf to the initial status when the system installed initially;

Good luck!

---

### Post by littlebat on 2008-12-11
Have you tried to use Xfce4 again and select screen resolution in the "Display setting" menu? Are there "1024x768" entry in the options? Keep your "/etc/X11/xorg.conf" as the status it can work at "1024x768". And, use Xfce4 again, if Xfce4 still can't work at "1024x768", try to rename your Xfce4 display setting config file "~/.config/xfce4/mcs_settings/display.xml" and restart Xfce4, it will use default display setting.

If you have any new discovery, please share with us.

---

### Post by samden on 2008-12-14
Littlebat, thanks heaps for all your help, it is working now! The refresh rate must have fixed it.

My working xorg.conf now contains:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        HorizSync       30 - 50
        VertRefresh     50 - 75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes   "1024x768"
	EndSubSection
EndSection
``` For some reason it keeps choking on the sis driver, so I've had to stick with vesa. Hopefully it doesn't die again, but I've got this backed up just in case it does.

---

### Post by samden on 2009-12-31
I have upgraded this same machine to Karmic (fresh install), and am having the same problem configuring the screen again. Unfortunately nothing I do to the xorg.conf file appears to make any difference to the Display preferences. I have copied the exact xord.conf code posted here that worked last time, with no luck, and have tried various variations on this with both the vesa and sis drivers with no apparant result - I'm still sitting on 800x600 resolution, with 640x480 my only other option.

Has anything changed between 8.04 and 9.10 that would require me to modify this code?

---

