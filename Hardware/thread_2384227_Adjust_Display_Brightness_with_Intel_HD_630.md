---
title: "Adjust Display Brightness with Intel HD 630?"
date: 2018-02-04
forum: Hardware
---

### Post by roots on 2018-02-04
Hi all,

I'm running Ubuntu 16.04 on an Intel 7700k based Desktop PC with a 26" LG Flatron display connected via DVI. The display is roughly 10 years old and gives me a nasty loud hum when set at brightness levels lower than 100% - which in turn will require cat 4 sunglasses to work with. Therefore, I've been trying to adjust display brightness using Ubuntu Brightness/Lock, but changing the slider has no effect. 

```

$ ls /sys/class/backlight/
$ acpi_video0

```

Indicates intel_backlight is not recognised as expected. I've added 

```
acpi_osi=Linux acpi_backlight=vendor
```

to the kernel boot options, but that resulted in the brightness slider disappearing completely and ls /sys/class/backlight/ returning NULL.

Creating a /usr/share/X11/xorg.conf.d/20-intel.conf with 

```

Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "acpi_video0"
        BusID       "PCI:0:2:0"
EndSection
```

did not solve the issue either.


Any suggestions?


Cheers,
roots

---

### Post by minhkstn on 2018-02-04
I got the same problem. My laptop is HP Probook 450 G4 using Intel HD 620. And even when I check 
$ ls /sys/class/backlight/
It returns nothing which means that there's nothing in this folder.

I tried all above suggestions but nothing worked.

Can any one help me?

---

### Post by wildmanne39 on 2018-02-04
Hi minhkstn, please start your own thread and do not hijack someone else's, you both will get better help in separate threads.

Thanks

---

