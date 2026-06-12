---
title: "Intel video card,HDMI video output not recognized"
date: 2013-03-19
forum: Hardware
---

### Post by giuliocoluccia on 2013-03-19
[COLOR=#101010][FONT=Ubuntu]Hei everybody,[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]I have a Dell Optiplex 3010 desktop and a Dell P2012H monitor. Ubuntu 12.10 64bit. The VGA-VGA link works fine. The HDMI-DVI link (cable HDMI (pc) DVI (monitor)) doesn't. Here what happens:[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]- if I boot my PC with the digital link, only, I can see the bootstrap and Ubuntu boot until a second before the login screen. Then, the monitor freezes, becomes black and gives me a "no signal".  If ithen I pulg the VGS cable, I can see that the system booted in  Low Graphics Mode, but none of the proposed options seems to be working. Even going in a terminal and launching lightdm by hand does not wake up the DVI input.[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]- if I boot the PC with both VGA and digital cables plugged, VGA input only works.[/FONT][/COLOR]
[COLOR=#101010][FONT=Ubuntu]- if I boot the PC in dual monitor mode using a second display, on the HDMI-DVI connected monitor I can see the bootstrap only, as in the first case.[/FONT][/COLOR]

[COLOR=#101010][FONT=Ubuntu]It looks like Ubuntu does not detect the HDMI output. Indeed, the output of ```
[/FONT][/COLOR][COLOR=#555555][FONT=Monaco]xrandr[/FONT][/COLOR][COLOR=#101010][FONT=Ubuntu]
``` is
```
[/FONT][/COLOR]Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192VGA1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 443mm x 249mm
   1600x900       60.0*+
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0  
   1280x800       74.9     59.8  
   1152x864       75.0  
   1280x768       74.9     59.9  
   1024x768       75.1     70.1     60.0  
   1024x576       60.0  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
[COLOR=#101010][FONT=Ubuntu]
```[/FONT][/COLOR] 
with no reference to HDMI (even in the audio section there seems to be no choice to HDMI audio).

The output of ```
[COLOR=#555555][FONT=Monaco]lspci | grep VGA[/FONT][/COLOR]
``` is
```
[COLOR=#555555][FONT=Monaco]00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)[/FONT][/COLOR]
```

I installed latest Intel drivers using a specific application, but nothing changed. Any idea?

---

### Post by giuliocoluccia on 2013-03-25
Anybody with the same issue or with a solution? :)

---

### Post by foresthill on 2013-03-25
Have you tested the HDMI to DVI cable in Windows or in another computer, so you can rule that out? Have you tried using a different monitor to connect to so you can rule that out?

---

### Post by giuliocoluccia on 2013-03-25
> **foresthill said:**
> Have you tested the HDMI to DVI cable in Windows or in another computer, so you can rule that out? Have you tried using a different monitor to connect to so you can rule that out?
Hi foresthill,
the cable is definitely working (tested with same monitor but different pc running win 7). Moreover, in my setup it works during the bootstrap (I can go into the "bios" and so on), it "loses" the signal right before the login. Moreover, I tested it with my PC but different monitor, and it shows exactly the same symptoms.

---

