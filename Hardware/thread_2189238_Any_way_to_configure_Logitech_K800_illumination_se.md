---
title: "Any way to configure Logitech K800 illumination settings?"
date: 2013-11-21
forum: Hardware
---

### Post by donotspamme532 on 2013-11-21
Hi everyone,

I have a Logitech K800 keyboard.  The keyboard works fine out of the box for all basic functions.  However, in Windows I would set illumination settings in SetPoint to make it so that the illumination activates when I type (instead of using proximity detection), and remains illuminated for 10 minutes after I stop typing (currently have to use old version of SetPoint for that to work right).  While this does drain the batteries more quickly, I prefer this setup to the proximity detection system that is the keyboard's default.

I want to be able to adjust those settings in Ubuntu/Kubuntu if possible.  I'm currently running Ubuntu 12.04 LTS with the kubuntu-desktop meta installed.

Hope you can help :)

Thanks,
Drake

---

### Post by donotspamme532 on 2013-11-22
Nothing?  Not even a "there is no way to do this at this time"?  I would appreciate some input.

Thanks,
Drake

---

### Post by donotspamme532 on 2013-11-22
OK, I figured out how to get it working.  I did some more searching and found a tool for the Logitech Unifying Receiver.  The tool is call [Solaar]("https://github.com/pwr/Solaar") and is basically a graphical interface for working with LUR devices.  As a part of that, it allows configuration of some settings on the hardware itself (not a lot of settings, but some), and one of the settings it allows on the K800 keyboard is to turn off the proximity detection system.  Setting this "Hand Detection" setting to "off" in Solaar makes the keyboard stop using proximity detection and instead uses illumination on keypress and remains illuminated for a duration.  It does not allow me to change the duration of the delay before illumination turns off again when the keyboard is idle, but right now for my system it is using a 10-minute delay.  This may mean that it defaults to 10 minutes, or it may mean that it uses whatever settings have already been established by SetPoint in windows (since I have a 10 minute delay set up in Windows through SetPoint).

In any case, thanks to Solaar I have my keyboard illumination working the way I want.


CORRECTION:  After a logout and then log back in the illumination delay was reset to 1 minute, which I believe is the keyboard default as that is what SetPoint defaults to.  I don't know if there is a way to set up Solaar configuration files to change this, I haven't looked yet.  Still, it works closer to the way I want it.  Now if I can just get repeat keys to work properly (but that's another matter).

---

