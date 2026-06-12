---
title: "Asus Laptop Button problems"
date: 2006-07-01
forum: Hardware &amp; Laptops
---

### Post by razahel on 2006-07-01
When I try to disable my touchpad nothing happens so I looked at /etc/acpi/events  and they use synclient -l if i try to read that out manualy i get following answer:
Can't access shared memory area. SHMConfig disabled?


Does anybody now know what to do?


regards razahel

---

### Post by Eversmann on 2006-07-01
Don't know. I used to disable it, or just disable the tapping.

On /etc/X11/xorg.conf you'll see this section:

```
Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection
```

You can set Option "SendCoreEvents" from "true" to "false" and at the next reboot (or rebooting gdm), you'll have it disabled.

If you want to disable the tapping, add this line:

Option      "MaxTapTime" "0"

Hope it helps.

---

### Post by razahel on 2006-07-02
Sorry but this does not help,

because disableing that way I know but this is not acceptable for "short" disableing.

---

### Post by XioNoX on 2006-07-02
in your synaptics "InputDevice" section, add :
Option	"ShmConfig"	"true"
and reboot xorg.
Now the disable touchpad button should work

---

