---
title: "how to add a quirk option to pm-suspend?"
date: 2010-01-03
forum: Hardware
---

### Post by perilandmishap on 2010-01-03
I've discovered that ```
sudo pm-suspend --quirk-save-pci
``` fixes the issues I've been having resuming from suspend (namely that the video display never came back on).

So awesome, except I can't figure out how to get ubuntu 9.10 to use this option.  ```
sudo pm-suspend --quirk-save-pci--store-quirks-as-fdi
``` looks really promising, but it causes my display to show graphic gibberish and the laptop doesn't go into suspend at all.

I've got a Toshiba Satellite M110, so I took a peak at
/usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-toshiba.fdi
None of the system.hardware.product seem to match my system... and I don't really know where to go from there.

Just for kicks I also tried commenting out all of sleep.sh except ```
pm-suspend --quirk-save-pci
```, but that didn't alter suspend behavior.

So, how do I get ubuntu to use a specific quirk option when going into suspend?

---

### Post by perilandmishap on 2010-01-05
So, I got this working by modifying /usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-toshiba.fdi to look like so:

```
<?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
  <device>
    <match key="system.hardware.vendor" string="TOSHIBA">
      <!-- Satellite Laptops -->
      <match key="system.hardware.product" prefix="Satellite">
        <!-- added by me, for my M110 -->
        <match key="system.hardware.product" string="Satellite M110">
          <merge key="power_management.quirk.save_pci" type="bool">true</merge>
          <merge key="power_management.quirk.vbe_post" type="bool">false</merge>
          <merge key="power_management.quirk.dpms_on" type="bool">false</merge>
          <merge key="power_management.quirk.vbestate_restore" type="bool">false</merge>
          <merge key="power_management.quirk.vbemode_restore" type="bool">false</merge>
          <merge key="power_management.quirk.dpms_suspend" type="bool">false</merge>
          <merge key="power_management.quirk.vga_mode_3" type="bool">false</merge>
        </match>
        <!-- end addition by me -->
....

```

All the false values were required because while the suspend worked with just the --save-pci option it did not work with that and all the default options 99-video-quirk-default.fdi was adding.  Specifying these parameters as false prevented 99-video-quirk-default.fdi from adding them.

If you are doing this for something other than a M110 you can find system.hardware.product with the following
```
lshal | grep system.hardware.product
```

If you want to see for sure what quirks are getting passed to pm-suspend you can find them in /var/log/pm-suspend.log.

---

