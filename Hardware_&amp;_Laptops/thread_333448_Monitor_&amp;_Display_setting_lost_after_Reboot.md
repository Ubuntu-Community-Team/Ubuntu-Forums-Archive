---
title: "Monitor &amp; Display setting lost after Reboot"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by elyse on 2007-01-07
I upgraded my LinuxCertified Laptop to 6.10 from 6.06 a couple of days ago, and I'm having a problem with the video settings that never occurred with Dapper. When I boot the laptop the display is just slightly wrong-- I see smeared artifacts in my wallpaper image.

If I open System Settings>Monitor & Display select Configure for Monitor #1, and change "Image format" to Widescreen, I am not offered the option of applying the change, but if I log out and back in the screen will be correct until the next boot.

The monitor type is shown as Plug'n'Play, and none of the selectable configurations matches my xorg.conf where the relevant sections are:

Section "Monitor"
  option "CalcAlgorithm" "CheckDesktopGeometry"
  option "DPMS"
  HorizSync 30-82
  Identifier "Monitor[0]"
  ModelName "1280X800@75HZ"
  VendorName "--> LCD"
  VertRefresh 58-75
  UseModes "Modes[0]"
EndSection

(This machine was delivered with SuSE 9.3 Linux installed, and I ported the xorg.conf when I moved to Kubuntu. Dapper didn't set things up properly, but the display worked reliably once xorg.conf was set to the current values.)

Is there a way to add my monitor type to the list recognized by Monitor & Display?

Alternatively, what config file needs to be updated to make the Widescreen Image format value stick?  

Where does System Settings store its values? I'd rather not have to reverse engineer this sucker...

---

### Post by teaker1s on 2007-01-07
recovery mode in grub
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR] 
this will reconfigure xserver
you can also search "modeline" in forums and you may need to manually edit your xorg file

---

### Post by elyse on 2007-01-07
As noted in my original message, the Ubuntu config tools get the configuration WRONG because they do not believe my combination of settings is possible. And I have already manually edited my xorg.conf. I need to know how to 

1. Add my monitor settings to the list of configurations that Ubuntu will accept as valid
or 
2. Set the Image format value in a config file somewhere so that it will stick.

---

### Post by elyse on 2007-01-07
I just tried the xserver-xorg upgrade. In advanced mode. At least it did not kill xorg.

Monitor & Display still does not hold its data across reboots. It came up the first time after the reconfigure showing a Custom Monitor type with Horizontal and Vertical sync numbers unrelated to what I typed in during the reconfig. I changed the format to Widescreen and re-logged in, and the display was OK (xorg.conf Monitor section values looked hosed, though). 

After a reboot the wallpaper was smeared again, but the monitor type was still Custom Widescreen.
After a second reboot the wallpaper was still smeared and the monitor type is plug'n'play widescreen, with bad values in the hsync and vsync fields.

I'm going back to my old xorg.conf, which at least contained accurate info about the screen.

Where does Monitor & Display store its data? Is there a way to figure out what keeps stepping on it? 
Could it be a problem with the ATI code?

---

