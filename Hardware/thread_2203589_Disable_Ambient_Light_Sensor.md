---
title: "Disable Ambient Light Sensor"
date: 2014-02-04
forum: Hardware
---

### Post by Binary-Synapse on 2014-02-04
Hello.

I have an Intel Classmate laptop with Ubuntu 12.04LTS installed.
The computer has an ALS (Ambient Light Sensor) that I would like to disable by software means.

Already tried Google  - found some HP and Asus instructions that didn't work.

Also...
Gnome Control Center + Monitors = doesn't have any brightness settings
Gnome Control Center + Power = doesn't have any brightness settings
Gnome Control Center + Brightness and Lock = only shows settings which apply during locking/unlocking user session

I am positive that the ALS is being controlled by the kernel, because when using older kernels (<3.2.x) the ALS doesn't work.

So... Is there some way to disable ALS (maybe by disabling it's embedded kernel module or something)?
Please view the attached lsmod.

Thank you

---

### Post by Kirboosy on 2014-02-04
I can't seem to find anything on how to do it from Ubuntu. Some people are reporting success by booting up into Windows and using utilities included on the laptop to disable the sensor. I'm not sure if the Classmate has similar software on it from the factory.

I also saw a guide for enabling it on a HP. The guide shows this as one of the steps
```
cat /sys/devices/platform/hp-wmi/als
```

Now, if you did ```
find |grep als
```

Does it return anything under a related directory ? (My laptops don't have ALS so I can't find any directories or files that match but yours might have something similar.)

Hope that helps!
~Caboose

---

### Post by Binary-Synapse on 2014-02-06
Hello Caboose.

I tried to find some folder with relevant information about ALS.
Unfortunately I found too much files and I don't know exactly which ones are relevant.

For example here is what gets listed under [COLOR=#0000cd]/sys/devices/platform/[/COLOR]
```
drwxr-xr-x 13 root root    0 feb  6 10:04 ./
drwxr-xr-x 17 root root    0 feb  6 10:04 ../
drwxr-xr-x  3 root root    0 feb  6 10:04 alarmtimer/
drwxr-xr-x  4 root root    0 feb  6 10:05 coretemp.0/
drwxr-xr-x  3 root root    0 feb  6 10:04 eisa.0/
drwxr-xr-x  4 root root    0 feb  6 10:04 Fixed MDIO bus.0/
drwxr-xr-x  8 root root    0 feb  6 10:04 i8042/
drwxr-xr-x  3 root root    0 feb  6 10:05 microcode/
drwxr-xr-x  3 root root    0 feb  6 10:04 pcspkr/
drwxr-xr-x  2 root root    0 feb  6 13:30 power/
drwxr-xr-x  4 root root    0 feb  6 10:04 reg-dummy/
drwxr-xr-x  3 root root    0 feb  6 10:05 regulatory.0/
drwxr-xr-x  4 root root    0 feb  6 10:04 serial8250/
-rw-r--r--  1 root root 4096 feb  6 10:05 uevent
```

Next I tried some recursive searches with the strings "[COLOR=#0000cd]als[/COLOR]" and "[COLOR=#0000cd]light[/COLOR]".

Here is the result of [COLOR=#0000cd]sudo find / -type d -iname als[/COLOR]
This command only returns directories:
```
/var/lib/alsa
/usr/src/linux-headers-3.8.0-32-generic/include/config/thinkpad/acpi/alsa
/usr/lib/i386-linux-gnu/alsa-lib
/usr/share/doc/alsa-base
/usr/share/doc/alsa-utils
/usr/share/alsa-base
/usr/share/bug/alsa-base
/usr/share/sounds/alsa
/usr/share/alsa
/usr/share/alsa/alsa.conf.d
/usr/share/pulseaudio/alsa-mixer
```

I also ran command [COLOR=#0000cd]sudo find / grep -i als
[/COLOR]Unfortunately the command returned >2200 results (which included files and directories).
But I was able to narrow the results down to these 5 hits:
```

/lib/modules/3.8.0-32-generic/kernel/drivers/iio/light/hid-sensor-als.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/iio/light/lm3533-als.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/misc/apds9802als.ko
/usr/src/linux-headers-3.8.0-32-generic/include/config/apds9802als.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/hid/sensor/als.h

```


Command [COLOR=#0000cd]sudo find / grep -i light[/COLOR] returns the following (I filtered out the irrelevant results):
```
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/type
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/brightness
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/power
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/power/control
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/power/runtime_active_time
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/power/autosuspend_delay_ms
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/power/runtime_status
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/power/runtime_suspended_time
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/bl_power
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/max_brightness
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/device
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/subsystem
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/uevent
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/actual_brightness
/sys/devices/pci0000:00/0000:00:02.0/backlight
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/type
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/control
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/runtime_active_time
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/autosuspend_delay_ms
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/runtime_status
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/runtime_suspended_time
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/bl_power
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/max_brightness
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/device
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/subsystem
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/uevent
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/actual_brightness

/lib/modules/3.8.0-32-generic/kernel/drivers/iio/light
/lib/modules/3.8.0-32-generic/kernel/drivers/iio/light/hid-sensor-als.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/iio/light/vcnl4000.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/iio/light/lm3533-als.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/iio/light/adjd_s311.ko

/lib/modules/3.8.0-32-generic/kernel/drivers/staging/iio/light
/lib/modules/3.8.0-32-generic/kernel/drivers/staging/iio/light/tsl2x7x_core.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/staging/iio/light/isl29028.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/staging/iio/light/tsl2563.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/staging/iio/light/isl29018.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/staging/iio/light/tsl2583.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/leds/ledtrig-backlight.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/ams369fg06.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/pandora_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/da903x_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/ltv350qv.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/tps65217_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/ili9320.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/generic_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/tdo24m.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/lms283gf05.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/lm3630_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/pwm_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/da9052_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/88pm860x_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/ld9040.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/max8925_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/platform_lcd.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/wm831x_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/apple_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/kb3886_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/pcf50633-backlight.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/lm3533_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/adp8870_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/cr_bllcd.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/s6e63m0.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/lp855x_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/vgg2432a4.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/adp8860_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/adp5520_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/aat2870_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/lm3639_bl.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/lcd.ko
/lib/modules/3.8.0-32-generic/kernel/drivers/video/backlight/l4f00242t03.ko

/usr/src/linux-headers-3.8.0-32-generic/include/config/fb/nvidia/backlight.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/fb/aty128/backlight.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/fb/radeon/backlight.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/fb/backlight.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/fb/aty/backlight.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/fb/riva/backlight.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/leds/trigger/backlight.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/drm/nouveau/backlight.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/hid/picolcd/backlight.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/apple.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/sahara.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/adp8870.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/max8925.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/aat2870.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/lp855x.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/da9052.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/pwm.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/tps65217.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/88pm860x.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/da903x.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/lm3533.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/pcf50633.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/generic.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/adp5520.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/lm3630.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/adp8860.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/wm831x.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/pandora.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/carillo
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/carillo/ranch.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/lm3639.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/lcd
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/lcd/support.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/class
/usr/src/linux-headers-3.8.0-32-generic/include/config/backlight/class/device.h
/usr/src/linux-headers-3.8.0-32-generic/include/config/i2c/parport/light.h
/usr/src/linux-headers-3.8.0-32-generic/include/linux/backlight.h
/usr/src/linux-headers-3.8.0-32-generic/include/linux/pwm_backlight.h
/usr/src/linux-headers-3.8.0-32/include/linux/backlight.h
/usr/src/linux-headers-3.8.0-32/include/linux/mfd/pcf50633/backlight.h
/usr/src/linux-headers-3.8.0-32/include/linux/pwm_backlight.h
/usr/src/linux-headers-3.8.0-32/drivers/iio/light
/usr/src/linux-headers-3.8.0-32/drivers/iio/light/Makefile
/usr/src/linux-headers-3.8.0-32/drivers/iio/light/Kconfig
/usr/src/linux-headers-3.8.0-32/drivers/staging/iio/light
/usr/src/linux-headers-3.8.0-32/drivers/staging/iio/light/Makefile
/usr/src/linux-headers-3.8.0-32/drivers/staging/iio/light/Kconfig
/usr/src/linux-headers-3.8.0-32/drivers/video/backlight
/usr/src/linux-headers-3.8.0-32/drivers/video/backlight/Makefile
/usr/src/linux-headers-3.8.0-32/drivers/video/backlight/Kconfig
/usr/src/linux-headers-3.8.0-32/arch/powerpc/include/asm/backlight.h
/usr/src/linux-headers-3.8.0-32/arch/arm/plat-samsung/include/plat/backlight.h

```

Do you think this information helps?

Thank you Caboose

---

### Post by Kirboosy on 2014-02-06
Hmmmm, I think that these files would be the ones of interest to us. The .ko ,h and o files aren't meant to be human readable.

```

/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/type
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/brightness
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/power
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/power/control
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/power/runtime_active_time
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/power/autosuspend_delay_ms
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/power/runtime_status
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/power/runtime_suspended_time
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/bl_power
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/max_brightness
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/device
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/subsystem
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/uevent
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/intel_backlight/actual_brightness
/sys/devices/pci0000:00/0000:00:02.0/backlight
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/type
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/control
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/runtime_active_time
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/autosuspend_delay_ms
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/runtime_status
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/runtime_suspended_time
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/bl_power
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/max_brightness
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/device
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/subsystem
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/uevent
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/actual_brightness
```

If you open up the following file is it human readable? 

```
sudo nano /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/control
```

I'm stabbing in the dark so hopefully this isn't a giant rabbit hole.

~Caboose

---

### Post by Binary-Synapse on 2014-02-12
Hello Caboose,

[COLOR=#696969]*I'm stabbing in the dark so hopefully this isn't a giant rabbit hole.*[/COLOR]
Yes I know, but that's OK.
Unfortunately there isn't too much documentation about ALS and Linux, so I am also trying everything.

Now, regarding your questions...

```
sudo nano /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/control
```
Returns:
```
auto
```
So it is human readable (and not some compiled binary file).
I tried changing this file's value by issuing command:
sudo echo 0 > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/control
sudo echo "off" > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/control
sudo echo "disabled" > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/control
None of the commands worked, and they all return the same error:
```
bash: echo: write error: Invalid argument
```
I guess that I am trying to write invalid strings into the file, because if type in the following:
```
sudo echo "auto" > /sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/power/control

```...the system doesn't return any errors. So it does accept "auto".
**Do you know if there is a way to determine what are the possible string values?**


[B] Manual Brightness Levels Check:
[/B]Another thing I noticed is that whenever I manually change the brightness levels (by pressing Fn keys) the file
/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/actual_brightness
changes it's content.
Possible values are:
0 (minimum brightness level)
2
4
6
8
10 (maximum brightness level)


[B]Manual Brightness Level Modification:
[/B]To manually change the brightness, you just have to modify the integer present in  "/sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness"
to any of the levels listed above.
You can also do the same by using file "/sys/class/backlight/acpi_video0/brightness".


So... now I know how and where I can view/control the manual brightness levels, but still not the ALS.

If you have any ideas, please share.

---

### Post by Kirboosy on 2014-02-14
I'm not sure what value should go there. I was hoping they would have some notes in the file of possible values.

I've been researching and I found a package called "[xbacklight]("http://linux.die.net/man/1/xbacklight")" Its simply just a command line utility to change the backlight brightness. 

Other than that I haven't really found much information. I found a wiki page on Ubuntu dedicated to backlight [troubleshooting]("https://wiki.ubuntu.com/Kernel/Debugging/Backlight")

~Caboose

---

### Post by Binary-Synapse on 2014-02-19
Hi Caboose

I will try your links and report back.

Thank you for your help.

---

