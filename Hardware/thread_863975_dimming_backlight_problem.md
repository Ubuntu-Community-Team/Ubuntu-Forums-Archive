---
title: "dimming backlight problem"
date: 2008-07-19
forum: Hardware
---

### Post by oguzy on 2008-07-19
I am trying to decrease the backlight. I am using Nvidia Geforce 5600 series video card with the latest 173 version Nvidia driver. I am able to change the brightness with the nvidia-setting. But what i want is to dim the backlight. 

I am not sure whether my backlight is able to be dimmed by gpm so here is some logs that may help. 

gnome-power-bugreport.sh > gpm.log  [http://pastebin.com/f6c86023a](http://pastebin.com/f6c86023a)
t
lshal > lshal.txt [http://pastebin.com/f3987c387](http://pastebin.com/f3987c387)

I tried to send dbus signals but they didn't work.

$ dbus-send --type=method_call --print-reply --dest=org.freedesktop.PowerManagement --session /org/freedesktop/PowerManagement/Backlight org.freedesktop.PowerManagement.Backlight.GetBrightness
method return sender=:1.11 -> dest=:1.80 reply_serial=2
   uint32 0

$ dbus-send --type=method_call --print-reply --dest=org.freedesktop.PowerManagement --session /org/freedesktop/PowerManagement/Backlight org.freedesktop.PowerManagement.Backlight.SetBrightness uint32:0
method return sender=:1.11 -> dest=:1.83 reply_serial=2

I had also trid to change the values unde /proc/acpi/video/*/brightness but this didnt't help either. Power Manager Brightness Applet is not adjusting the brightness level, too. 

Also:
$ xbacklight -get
No outputs have backlight property

and tried  smartdimmer, i installed it from its source and eveytime i set the levet it always shows the level 0. 

So i dont't know what to do now.

My system is a fresh installed Hardy with the latest upgrades done.

---

