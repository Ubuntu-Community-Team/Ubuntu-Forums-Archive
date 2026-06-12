---
title: "No backlight control from gnome-power-manager --Sony laptop--"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by theverde on 2007-10-21
Hi to all! Well, after searching and reading a lot about this issue, im still not able to have the things working. I have a Sony Vaio PCG-Z1M laptop, running gutsy. I am able to change the brightness by pressing the Fn key in combination with f5 and f6, and also changing by hand the value in /sys/class/backlight/sony/brightness, but im not able to do this from the gnome-power-manager applet, not even from the gnome-brightness-applet. At first i used the fix described at [http://ubuntuforums.org/showthread.php?t=479034&highlight=sony+vaio]("http://ubuntuforums.org/showthread.php?t=479034&highlight=sony+vaio"), but without luck. After more investigating ive found out that the laptop_panel.num_levels value in the hal-device-manager is set on 134648572 (0x80692fc) . Similar bug reports are:

[https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/145611]("https://bugs.launchpad.net/ubuntu/+source/kde-guidance/+bug/145611")
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/139205]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/139205")
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/138956]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/138956")

Anyway, if i kill the gnome-power-manager and i start it again with "--no-daemon --verbose" option, i dont see any error or warning message, but, moving the slide of the brightness applet, the value changes between 7 and 134648572:

```
[gpm_backlight_brightness_evaluate_and_set] gpm-backlight.c:374 (01:03:41):      1. main brightness 0.000000
[gpm_backlight_brightness_evaluate_and_set] gpm-backlight.c:387 (01:03:41):      2. battery scale 1.000000, brightness 0.000000
[gpm_backlight_brightness_evaluate_and_set] gpm-backlight.c:402 (01:03:41):      3. idle scale 1.000000, brightness 0.000000
[gpm_backlight_brightness_evaluate_and_set] gpm-backlight.c:422 (01:03:41):      4. ambient scale 1.000000, brightness 0.000000
[gpm_backlight_brightness_evaluate_and_set] gpm-backlight.c:440 (01:03:41):      emitting brightness-changed : 0
[gpm_brightness_lcd_dim_hw] gpm-brightness-lcd.c:267 (01:03:41):         new_level_hw=0
[gpm_brightness_lcd_dim_hw_step] gpm-brightness-lcd.c:198 (01:03:41):    new_level_hw=0, last_set_hw=94253999
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 94253999 of 134648571
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 87521571 of 134648571
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 80789143 of 134648571
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 74056715 of 134648571
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 67324287 of 134648571
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 60591859 of 134648571
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 53859431 of 134648571
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 47127003 of 134648571
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 40394575 of 134648571
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 33662147 of 134648571
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 26929719 of 134648571
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 20197291 of 134648571
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 13464863 of 134648571
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 6732435 of 134648571
[gpm_brightness_lcd_set_hw] gpm-brightness-lcd.c:155 (01:03:41):         Setting 7 of 134648571

```

The only problem is that the backlight does not change :(

The very very strange thing, is that booting Gutsy in live session, all works perfectly :confused: , and the laptop_panel.num_levels is properly set to "8" . Of course, i can live without this, as long i can change the brightness aswell with Fn keys, but this thing makes me mad...why in live session is ok, and installed on the HD is messed up? what has changed? Sorry if it has been long, but i want to give all the informations that i have. Any hint is appreciated :)

---

### Post by theverde on 2007-10-22
I just got the things working, with the fix posted by jhkuo here:

[http://ubuntuforums.org/showthread.php?p=3599008#post3599008]("http://ubuntuforums.org/showthread.php?p=3599008#post3599008")

I simply added this line 

```
value="`expr $value / 19235509`"
```

in hal-system-lcd-set-brightness-linux, at the beginning of the script . Hope it helps!!!

---

