---
title: "How can I override bad EDID with a xorg.conf?"
date: 2015-12-21
forum: Hardware
---

### Post by Xorcist on 2015-12-21
[COLOR=#222426][FONT=Helvetica Neue]So I am using the default opensource Radeon driver supplied with Ubuntu 14.04 LTS, and pretty much every desktop environment (unity, mate, xfce, etc.) is being supplied a bad EDID from my Samsung LN52B750 television.

Specifically the physical size is being returned as 7.2" (160x90mm), however it should be more like 39.8" (880x500mm), everything else seems to be in order though.
[/FONT][/COLOR]
[COLOR=#222426][FONT=Helvetica Neue]I used a Windows machine to dump and edit my EDID, added the updated file to my Ubunutu 14.04 LTS machine, generated an xorg.conf, and finally added a CustomEDID option in the device section specifying my EDID file as an override.

But upon reboot I see lines like this in my xorg.0.log:

"[COLOR=#747C87][FONT=Lato][ 6.022] (WW) RADEON(0): Option "CustomEDID" is not used[/FONT][/COLOR]"
[/FONT][/COLOR]
[COLOR=#222426][FONT=Helvetica Neue]Are there any xorg experts out there, that can help me out? Please note that this only happens when connected via HDMI, via VGA everything seems okay, however VGA is not an option for me, as I need the HDMI for audio too.
[/FONT][/COLOR]
[COLOR=#222426][FONT=Helvetica Neue]
[/FONT][/COLOR]

---

