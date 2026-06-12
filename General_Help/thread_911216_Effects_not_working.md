---
title: "Effects not working"
date: 2008-09-05
forum: General Help
---

### Post by JakeG1 on 2008-09-05
I installed Ubuntu yesterday on a spare laptop and everything was working great so I shut it down for the night. Today however, when I started it up my desktop effects weren't working. No Desktop cube, no Cairo Dock, no compiz. After reading through the forums and nothing working, hopefully someone will be able to help. Thanks

When I enter Compiz in the terminal:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

_Edit: Here is my lspci_:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566MC Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
03:09.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller


```

---

### Post by overdrank on 2008-09-05
Hi and what catches my eye is ```
No manageable screens found on display :0.0
``` you may try and change the resolution as this worked for me on a laptop.

---

### Post by JakeG1 on 2008-09-05
> **overdrank said:**
> Hi and what catches my eye is ```
No manageable screens found on display :0.0
``` you may try and change the resolution as this worked for me on a laptop.

Thanks, I tried changing my screen resolution, but it did nothing. I'm not sure if this matters, but I hooked up my monitor to my laptop, so I'm not using the actual laptop screen.

---

### Post by JakeG1 on 2008-09-05
*Bump* Still trying to figure this out.

---

### Post by overdrank on 2008-09-06
> **JakeG1 said:**
> Thanks, I tried changing my screen resolution, but it did nothing. I'm not sure if this matters, but I hooked up my monitor to my laptop, so I'm not using the actual laptop screen.

Hi and yes this may cause issues with a external monitor. You may try and use the xfix option when booting into recovery mode. Also you may try the command ```
gksu displayconfig-gtk
``` and set the driver and screen there.

---

### Post by JakeG1 on 2008-09-06
> **overdrank said:**
> Hi and yes this may cause issues with a external monitor. You may try and use the xfix option when booting into recovery mode. Also you may try the command ```
gksu displayconfig-gtk
``` and set the driver and screen there.

Hey, thanks for the reply. I tried the Xfix and nothing happened so I went on to use that code. These are the windows that popped up:

[IMG]http://i97.photobucket.com/albums/l231/JakeG1991/Screen1.jpg[/IMG]
[IMG]http://i97.photobucket.com/albums/l231/JakeG1991/screen2.jpg[/IMG]

I think it might have something to do with the Graphics Card drivers. I have no idea though :P.

Edit: Here are the manufacture specs for the notebook: [http://support.gateway.com/s/Mobile/2007/ViperSR/2905955R/2905955Rsp2.shtml](http://support.gateway.com/s/Mobile/2007/ViperSR/2905955R/2905955Rsp2.shtml)

---

### Post by JakeG1 on 2008-09-07
Okay, reinstalled Ubuntu and everything works again. Hopefully nothing will happen again X_X. I guess this can be labeled [solved (half-assed)].

---

