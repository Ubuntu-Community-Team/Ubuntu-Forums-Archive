---
title: "Need Help Configuring Touchpad"
date: 2009-05-20
forum: Hardware
---

### Post by berlandb on 2009-05-20
Hi,

the default configuration of the touchpad in Jaunty (at least for my computer, an Apple Macbook Pro 4,1) is unacceptable.

There is a wiki page about customizing it, but it seems to be outdated since it breaks things. In another thread [1] somebody kindly posted a working configuration that I use now (see below).

My problem is that with the new configuration I cannot right click and drag (at the same time) anymore. Normal (left) click dragging works and so does two finger scrolling. I just can't move the mouse pointer while holding a right click.

However, the standard configuration did allow me to do so (although with 3 fingers), so it's technically possible. Unfortunately I can't compare with the default settings, because the provided .fdi file is basically empty.

Does somebody know what additional options or measures are needed or what might be wrong?

Thank you


PS: I started this new thread because I assume that this driver configuration isn't necessarily an Apple specific issue.


[1] [http://ubuntuforums.org/showpost.php?p=7178849&postcount=2](http://ubuntuforums.org/showpost.php?p=7178849&postcount=2)


For reference I'll attach the "empty" standard fdi file as well as the one that I have in use right now.

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        <merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->
    </match>
  </device>
</deviceinfo>

```

```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="bcm5974">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1100</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>

        <merge key="input.x11_options.FingerLow" type="string">15</merge>
        <merge key="input.x11_options.FingerHigh" type="string">25</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">2.5</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.15</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

---

