---
title: "Graphics tablet + Dual Monitor Problems"
date: 2010-04-17
forum: Hardware
---

### Post by -nat- on 2010-04-17
(Ubuntu 8.10) I've managed to get my graphics tablet (Aiptek 600U) working fine on a single monitor, but am having problems when I plug in my second screen. My screens are arranged one on top of the other, the top one has a res of 1280x960 and the bottom one has a res 1280x800.

Before doing any fiddling with HAL settings, the tablet just stretched across both monitors (so the top of the tablet = the top of the top monitor, the bottom of the tablet = the bottom of the bottom monitor) which made circles become very stretched ovals.
I then tried added various lines to the config file in */usr/share/hal/fdi/policy*, but the best thing I could get was the tablet mapped to just the top 85% of the top monitor, while optimally I would want to have it mapped to all of the bottom monitor (and none of the top one).

Here are the contents of the config file I'm using: (/usr/share/hal/fdi/policy/10-linuxaiptek.fdi)
```
<?xml version="1.0" encoding="UTF-8"?> 
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="WALTOP">
      <merge key="input.x11_driver" type="string">stylus</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true</merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
      <merge key="input.x11_options.zMin" type="string">0</merge>
<merge key="input.x11_options.KeepShape" type="string">off</merge>
    <merge key="input.x11_options.Twinview" type="string">vertical</merge>
<merge key="input.x11_options.zMax" type="string">1023</merge>
    </match>
  </device>
</deviceinfo>

```If anyone could help me out in getting the tablet mapped to only the bottom monitor, that would be great!

[EDIT] I've managed to get it working by adding 'TopX', 'BottomX', 'TopY' and 'BottomY' values.

---

