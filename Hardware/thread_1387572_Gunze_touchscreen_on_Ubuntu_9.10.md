---
title: "Gunze touchscreen on Ubuntu 9.10"
date: 2010-01-22
forum: Hardware
---

### Post by maddis on 2010-01-22
Hi,

I searched the forums and saw that there are threads about Gunze touchscreen earlier, but none of them helped now.

I had working system with Ubuntu 8.04, but reasons beyond me I had to upgrade to Ubuntu 9.10 and of course the touchscreen (among other things) is not working anymore.

Touchscreen hardware has serial port that I then converted to with inputattach in a format that I could use with Xorg. In Xorg I used driver found from [http://www.plop.at]("http://www.plop.at"). Evtouch didn't work correctly. I also had to use older inputattach since the latest didn't support Gunze anymore.

With the Ubuntu 9.10, when I installed the old inputattach, things seemed to work ok. lshal reported that there is Gunze Touchscreen found. Also evtouch and tslib reported in Xorg-log that they have found Gunze, but neither of them got it work. There was always some error after the detection. I compiled the Plop - driver to new xorg (it needed some work to get it compiled). I also added the needed part to /etc/X11/xorg.conf to take the driver in use.

If I added ServerLayout section that I had in older xorg.conf the xorg wouldn't get the system up and running correctly. Only InputDevice section worked, but I'm not sure if that's enough since no driver is being loaded now. I'm also not sure if it's because of HAL that the external driver isn't being used.

Of course the root cause can be that my modifications to the driver to get it compiled for new Xorg aren't correct, but does anyone has ideas what to do or has anyone used Gunze touchscreen with Ubuntu 9.10 with success?

---

### Post by maddis on 2010-01-26
I got the touchscreen working by adding the plpevtch driver configuration to new file in /usr/share/hal/fdi/policy/20thirdparty/40-x11-plpevtch.fdi.

Configuration is:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
<device>
<match key="info.capabilities" contains="input.touchpad">
<match key="info.product" contains="Gunze AHL-51S TouchScreen">
<merge key="input.x11_driver" type="string">plpevtch</merge>
<merge key="input.X11_options.Device" type="string">/dev/input/touch</merge>
<merge key="input.x11_options.Calibrate" type="string">False</merge>
<merge key="input.x11_options.MinX" type="string">9</merge>
<merge key="input.x11_options.MaxX" type="string">1010</merge>
<merge key="input.x11_options.MinY" type="string">5</merge>
<merge key="input.x11_options.MaxY" type="string">1010</merge>
<merge key="input.x11_options.InvX" type="string">1</merge>
<merge key="input.x11_options.InvY" type="string">1</merge>
<merge key="input.x11_options.RightClick" type="string">True</merge>
<merge key="input.x11_options.RightClickMS" type="string">3000</merge>
<merge key="input.x11_options.RightClickSquare" type="string">10</merge>
<merge key="input.x11_options.TouchFilter" type="string">True</merge>
<merge key="input.x11_options.TouchFilterMS" type="string">200</merge>
</match>
</match>
</device>
</deviceinfo>

```

After editing the file and rebooting the device, the touchscreen isn't working. When I reboot the device another time the touchscreen starts working, but at the same time mouse and keyboard stop working! If I edit the configuration and reboot the device the keyboard and mouse start working, but touchscreen not. And the second boot turns the things other way around. And the third boot won't make any difference anymore.

Any idea what might cause the problem? I'm using plpevtch version 0.4.0.

---

