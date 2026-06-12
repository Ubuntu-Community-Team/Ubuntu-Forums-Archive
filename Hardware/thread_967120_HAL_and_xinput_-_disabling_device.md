---
title: "HAL and xinput - disabling device"
date: 2008-11-01
forum: Hardware
---

### Post by kyozo on 2008-11-01
Hi, I just upgraded to Ubuntu Intrepid Ibex and sadly found that my IBM USB Keyboard with Ultranav wasn't working properly anymore. 

I have previously had problems with using scrolling and with disabling the touchpad, but got that solved using xorg.conf.

Apparantly xorg.conf isn't used to configure input devices anymore, so I searched around a bit, and found out, that I needed to configure HAL to enable my scrolling. I got that to work by creating a .fdi file and using x11 configuration options in that one.

Now I need to disable my Touchpad - I can do that runtime using the command 
```
xinput set-int-prop 4 "Device Enabled" 32 0
```
I use the device id 4 in the command (i found that using xinput list) since I have 2 entries named "Synaptics Inc. Composite Touchpad / Trackpoint".

But I want to do that automatically everytime my system boots. I could probably run a script at startup that executes the above command, but there must be a better way. Can I somehow disable the touchpad, I feel that there must be a way to set this permanently.

Thanks for your help.

/Kyozo

---

### Post by kyozo on 2008-11-11
Bump - come on, there must be somebody that knows this :)

/Kyozo

---

### Post by ninukab on 2008-11-12
for me it works in /etc/gdm/PostLogin/Default

---

### Post by t3hmikez0r on 2009-01-04
Kyozo,

I got it working with mostly your earlier setup, plus one additional section in my xorg.conf:

Section "ServerFlags"
        Option "AutoAddDevices" "False"
EndSection 

I did not do anything with HAL.  Scrolling and all that work just fine.  If you need to see my xorg.conf, let me know.

---

### Post by t3hmikez0r on 2009-01-04
May or may not be related:

After making that change in my xorg.conf file, the mouse would randomly cut out.  It looked like it was being-recreated very rapidly (input device numbers quickly approaching 100).

I removed that xorg.conf entry that I added, and haven't seen problems so far...

Probably have to give it a go with HAL.

---

