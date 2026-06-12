---
title: "eee PC 1015PE - eth0 disappears when Fn keys fix enabled"
date: 2010-07-25
forum: Hardware
---

### Post by verminform on 2010-07-25
Ok, strange problem after using the fix for function keys here

[Link]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1466802&highlight=eeepc+function+keys")

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  acpi_osi=Linux"
```

But, my eth0 totally disappeared (as in, not listed for lspci). 

So, was recommended to change the value to:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash  acpi_osi='!Windows 2009'"
```

eth0 came back, but function keys turned off again. 

Now, when you use acpi_osi=Linux it will set the wlan off within the BIOS, but it still works within lucid.

The only thing I really care about is having the switch to toggle the FRIGGEN touch pad on/off.

Any help would be appreciated; I can hardly type with this thing enabled.

Thank you.

---

### Post by verminform on 2010-07-25
A bit more info.

Right now I have acpi_osi=Linux enabled.  The eth0 doesn't register within lspci, but all of the Fn keys respond properly; WLAN was disabled within BIOS, but it works without hitting the hotkeys.  

Now the only strange thing is when I hit fn+f3 (to disable touchpad) it produces this error:

"Unable to enable touchpad; ensure xorg.conf is properly configured."

But, the touchpad still works....

Restarted, and switch wlan back on within bios; eth0 came back, but wlan gets disabled again after every reboot.

** I apologize for any typing errors as I am simply trying to get the touchpad to toggle on/off.

---

