---
title: "Toshiba Satellite L40 - Brightness"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by _march_ on 2007-12-16
Hi :)
I've got a problem with my Toshiba Satellite L40. I can't control brightness with [Fn] + [F6] or [F7]. A box appears on the screen but nothing happens. I've searched the web but  I only found a workaround (in this forum) which allows me to control it manually:

```
cat /proc/acpi/video/VGA/LCDD/brightnesslevels:  100 90 30 40 50 60 70 80
current: 90
```

```
echo 30 | sudo dd of=/proc/acpi/video/VGA/LCD/brightness
```
```
echo 90 | sudo dd of=/proc/acpi/video/VGA/LCD/brightness
```

Is there a possibility to get it working again? It worked fine under Feisty - but isn't working under Gutsy. I'm running Xubuntu Gutsy Gibbon.

---

### Post by _march_ on 2007-12-17
I also created /etc/laptop-mode/batt-start::

```
#!/bin/sh
echo 10 > /proc/acpi/video/VGA/LCDD/brightness
```

and /etc/laptop-mode/batt-stop:
```
#!/bin/sh
echo 90 > /proc/acpi/video/VGA/LCDD/brightness
```
But this way is only rough solution...
Any ideas?

---

### Post by _march_ on 2007-12-20
Any solutions?

---

### Post by _march_ on 2007-12-22
I haven't found any solution on the web. May be I've chosen the wrong keywords... :(

---

### Post by _march_ on 2007-12-22
It's a bug. Hope it'll be fixed soon :)

---

### Post by pmenendez on 2007-12-29
I own a Toshiba Satellite L45 with ubuntu 7.10, and also had problems setting brightness with Fn keys. I found that the ACPI event was calling the script /etc/acpi/asus-brn-up.sh, instead of /etc/acpi/video_brightnessup.sh. I tried blacklisting module asus_acpi and after rebooting, Fn keys now can control brightness. Unfortunately, volume control using Fn keys stopped working. I think the problem is due to the fact that my notebook has both /sys/class/backlight/asus and /sys/class/backlight/acpi_video0, and HAL or ACPI are priorizing the asus key over the acpi_video0 one. With asus_acpi module unloaded, I have only the acpi_video0 key.

---

### Post by _march_ on 2007-12-31
Thanks for your reply  :)
It didn't work. Fn keys can't control brightness  unless volume control stopped working. ;)

---

### Post by pmenendez on 2008-01-15
Hi. I finally solved my issue with brightness, so in case this could help someone else, I'll describe what I did.

I noticed that my problem was just that hal daemon was triggering the wrong scripts. But I could change brightness echoing some value to the right device, in my case, echo 50 > /sys/class/backlight/acpi_video0/brightness. Hal was changing the value in /sys/class/backlight/asus/brightness. I found that unloading asus_acpi module solved the problem with brightness, but other Fn keys didn't work without this module. So I started looking for another way to disable the asus device. And I found that this could be done setting the device info.ignore key to true. This can be done creating a device information file in /etc/hal/fdi/preprobe with this content:

<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">

  <device>
    <!-- Para eliminar doble laptop_panel
        -->
    <match key="linux.sysfs_path" string="/sys/class/backlight/asus">
      <merge key="info.ignore" type="bool">true</merge>
    </match>
  </device>
</deviceinfo>

After rebooting, now I can control brightness with Fn keys. Please note that in my case, I wanted to disable /sys/class/backlight/asus. Maybe you will have to launch the device manager, and look for the correct key (you should have two Generic Backlight Devices)

Hope this helps somebody.

---

### Post by rosegarden78 on 2008-01-19
Try typing this command in a terminal
 
 xgamma -gamma 0.75
 
 I have posted my own solution here:
 
 [http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

---

