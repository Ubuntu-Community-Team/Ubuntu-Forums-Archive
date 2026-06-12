---
title: "Disable SHMConfig in Karmic"
date: 2009-11-10
forum: Hardware
---

### Post by FokkerCharlie on 2009-11-10
Hello!

I, along with a few others on these forums, have an Acer 5920 laptop, which is equipped with both a Synaptics Touchpad, and a set of touch-sensitive media keys, which are, in fact, a second synaptics touchpad.

Previously, we had been able to use gsynaptics to configure the touchpad behaviour by this:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">

  <device>
    <match key="input.originating_device" string="/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port">
        <merge key="input.x11_options.SHMConfig" type="string">True</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">2</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">3</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">4</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">5</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">2</merge>
        <merge key="input.x11_options.TapButton3" type="string">3</merge>
        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">0</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">0</merge>
    </match>
  </device>
</deviceinfo>
```

in the file /etc/hal.fdi.policy/touchpad.fdi.  That worked fine, because up until Jaunty, SHMConfig was 'off' by default.  Now, I need to specify that I don't want SHMConfig for the Media Keys touchpad, and I've attempted this in another fdi file:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">

  <device>
    <match key="input.originating_device" string="/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX2_port">
        <merge key="input.x11_options.SHMConfig" type="string">False</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">0</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">0</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">0</merge>
        <merge key="input.x11_options.TapButton3" type="string">0</merge>
        <merge key="input.x11_options.PalmDetect" type="string">0</merge>
        <merge key="input.x11_options.PalmMinWidth" type="string">10</merge>
        <merge key="input.x11_options.PalmMinZ" type="string">200</merge>
    </match>
  </device>

</deviceinfo>
```

Unfortunately, this isn't working.  Is it possible to turn off SHMConfig for a touchpad like this?  Or some other way?  It effects not only the configuring of the main touchpad, but also syndaemon, which is a pretty necessary utility.

All advice appreciated!

Charlie

---

### Post by SXW on 2010-04-15
Check out what worked for me here:

[http://ubuntuforums.org/showpost.php?p=9115579&postcount=28](http://ubuntuforums.org/showpost.php?p=9115579&postcount=28)
[]("http://ubuntuforums.org/showthread.php?t=1313893&page=3")

---

