---
title: "HAL not reading touchpad's configurations at startup"
date: 2009-12-15
forum: Hardware
---

### Post by henriquemaia on 2009-12-15
I'm trying to get HAL to load my touchpad's preferences at startup, but for some unknown reason to me, it isn't. 

I've got a an Eee PC 1000 HE with an Elantech Touchpad.
I've followed an Howto on how to create a fdi file on /etc/hal/fdi/policy/ . The file is there with the same permissions as the other ones, the configurations work when invoked directly through synclient, but HAL fails to load them. What am I doing wrong?

My fdi file:

> <?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="SynPS/2 Synaptics TouchPad">
      <append key="info.capabilities" type="strlist">input.touchpad</append>
    </match>
      <match key="info.capabilities" contains="input.touchpad">
      <merge key="input.x11_driver" type="string">synaptics</merge>
      <merge key="input.x11_options.LeftEdge" type="string">53</merge>
      <merge key="input.x11_options.RightEdge" type="string">1099</merge>
      <merge key="input.x11_options.TopEdge" type="string">48</merge>
      <merge key="input.x11_options.BottomEdge" type="string">720</merge>
      <merge key="input.x11_options.FingerLow" type="string">70</merge>
      <merge key="input.x11_options.FingerHigh" type="string">100</merge>
      <merge key="input.x11_options.FastTaps" type="string">1</merge>
      <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">100</merge>
      <merge key="input.x11_options.VertScrollDelta" type="string">75</merge>
      <merge key="input.x11_options.HorizScrollDelta" type="string">75</merge>
      <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
      <merge key="input.x11_options.MinSpeed" type="string">0.3</merge>
      <merge key="input.x11_options.MaxSpeed" type="string">0.8</merge>
      <merge key="input.x11_options.RTCornerButton" type="string">2</merge>
      <merge key="input.x11_options.RBCornerButton" type="string">3</merge>
      <merge key="input.x11_options.TapButton2" type="string">2</merge>
      <merge key="input.x11_options.TapButton3" type="string">3</merge>
      <maerge key="input.x11_options.ClickFinger2" type="string">2</merge>
      <maerge key="input.x11_options.ClickFinger3" type="string">3</merge>
    </match>
  </device>
</deviceinfo>

---

### Post by henriquemaia on 2009-12-15
I haven't solved this, but I'm using a workaround that works (so far).

I've created a bash script with the command line invoking synclient and its options. I've saved it and made it executable. I've added it to the startup apps and the options are loaded as expected. I would rather prefer the "proper way" of doing things, but this one gets it done nonetheless.

---

