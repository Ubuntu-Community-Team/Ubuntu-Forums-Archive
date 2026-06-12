---
title: "Monitor cut off"
date: 2014-08-25
forum: Hardware
---

### Post by gery3 on 2014-08-25
I just changed the graphics card in my old PC from an ATi 1900XTX to an AMD HD4850, however now my screen is cut off on the left and right side. I use a DVI to HDMI cable (the monitor doesn't have DVI or Display Port). I know that it works with the HD4850 card and Windows. It is a LG Flatron L245WP-BN with a resolution of 1920x1200 pixels. I'm using the open source drivers, tried to upgrade them with the oibaf ppa which didn't help.
I have the same issue when connecting my laptop with a normal HDMI cable. The laptop uses Intel HD Graphics 4400 and a Nvidia 750m with bumblebee.

It may be that the newer open source drivers incorrectly detect the monitor as a TV because it is using HDMI. At least that's what happens on Windows with Nvidia drivers, unfortunately the howto I found is only for Windows: [http://www.voetsjoeba.com/misc/edid/](http://www.voetsjoeba.com/misc/edid/)

Does anyone know how to correct this on Linux?

xrandr output:
> Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 8192 x 8192
DVI-0 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 432mm x 324mm
   1920x1200      60.0*+
   1920x1080      60.0     50.0     50.0     59.9  
   1920x1080i     60.1     50.0     60.0  
   1600x1200      60.0  
   1680x1050      59.9  
   1280x1024      75.0     60.0  
   1280x960       75.0  
   1280x720       60.0     50.0     59.9  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   720x576        50.0  
   720x480        60.0     59.9     59.9  
   640x480        75.0     60.0     59.9  
   720x400        70.1  
DIN disconnected (normal left inverted right x axis y axis)
DVI-1 disconnected (normal left inverted right x axis y axis)


---

### Post by grahammechanical on 2014-08-25
Have you tried using the Displays utility to Detect Displays?

I recently started using a Sharp TV as a monitor. I only had a VGA cable available and I could not get the full range of resolutions. Then I brought  HDMI cable (TV did not have a DVI socket) and now I get the full resolution the instruction manual says the TV is capable of.

There might be settings in the TV menu that help. My Sharp TV has a setting called Autoposition (in PC mode) - Automatically optimises the display. Another setting, H position (in PC mode) - shifts the image horizontally to the right or left hand side of the screen. And a third, V position (In PC mode) - shifts the image vertically towards the top or bottom of the screen.

Regards.

---

### Post by Vladlenin5000 on 2014-08-26
Yes, it looks like the typical overscan issue. The correct setting depends on the monitor brand/model. In some it's just 'overscan off', in others as mentioned in the previous post it's 'PC Mode' (and variants) and in a few others it's 'Just Scan' (or similar).
Bottom line: Look for the correct setting in whichever TV's menu handles proportions (16:9 / 4:3 / etc.) and/or consult your user's manual.

---

### Post by gery3 on 2014-08-26
The only option the monitor has when connected to the HD4850 via HDMI is Auto and fullscreen (options like position are greyed out and only available when connected via VGA). Fullscreen just streches the the cutoff screen on one side which looks really bad. When I connect my X1900XTX which doesn't have this issue the only available option is 1:1.
There is also an option to switch between monitor and TV mode which doesn't change anything visible however.

I now connected via VGA which works. However I'd still like to use HDMI. The issue looks exactly like the one I linked to which doesn't seem to be a simple overscan issue to me unfortunately.

Edit: Forgot to mention that I'm using Kubuntu 14.04.
Edit 2: Seems that there is a way to fix it: [https://bugs.freedesktop.org/show_bug.cgi?id=33285](https://bugs.freedesktop.org/show_bug.cgi?id=33285)

Edit 3: Extracted the edid file from the X1900XTX and tried to apply it with 
echo edid >/sys/module/drm_kms_helper/parameters/edid_firmware
as stated in the bug description, however that didn't help. Will try again tomorrow. Anyone has experience with this?

---

