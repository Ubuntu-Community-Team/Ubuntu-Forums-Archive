---
title: "Lenovo Z370 - Hotkeys not working anymore after update to 13.10"
date: 2013-10-21
forum: Hardware
---

### Post by Chip88 on 2013-10-21
Hi there!

After updating to 13.10 my multimedia keys for volume up / down and mute unfortunately do not work anymore.

Before, I could fix this issue by adding ```
ENV{DMI_VENDOR}=="LENOVO", ATTR{[dmi/id]product_name}=="IdeaPad Z370", RUN+="keyboard-force-release.sh $devpath common-volume-keys"
``` to ```
/lib/udev/rules.d/95-keyboard-force-release.rules
```.

But now, there is no *95-keyboard-force-release.rules *anymore.

I'd be happy if someone could help me getting back my multimedia keys to work.

Thanks in advance!

Regards,
Chipy

---

### Post by stefanlobas on 2013-10-26
I think I solved the issue. I added the necessary lines to /lib/udev/hwdb.d/60-keyboard.hwdb by executing ```
gksu gedit /lib/udev/hwdb.d/60-keyboard.hwdb
```
Scroll down to the Lenovo section and add the following lines:
```

# IdeaPad Z370
keyboard:dmi:bvn*:bvr*:svnLENOVO*:pn*IdeaPad*Z370*:pvr*
 KEYBOARD_KEY_a0=!mute
 KEYBOARD_KEY_ae=!volumedown
 KEYBOARD_KEY_b0=!volumeup

```
After saving update the udev hwdb by executing
```
gksu udevadm hwdb --update
```
After a reboot the volume keys worked again as supposed ;-)

Stefan

---

### Post by Chip88 on 2013-10-27
Hi stefanlobas!

You're a genious...

Your solution worked also fine for me!!!

Thank you very much!!!

Regards from Germany,
Mark

**EDIT:**
I posted the instruction with a reference to here in the German Ubuntu - Forum.
It can be find here: [http://forum.ubuntuusers.de/topic/lenovo-ideapad-z370-multimedia-keys-funktionie/#post-6063777](http://forum.ubuntuusers.de/topic/lenovo-ideapad-z370-multimedia-keys-funktionie/#post-6063777) .

---

