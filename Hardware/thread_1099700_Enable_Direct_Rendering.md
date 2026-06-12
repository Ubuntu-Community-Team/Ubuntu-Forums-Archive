---
title: "Enable Direct Rendering"
date: 2009-03-18
forum: Hardware
---

### Post by grapeape25 on 2009-03-18
I'm trying to enable Direct Rendering in Kubuntu, with a "Intel Graphics Media Accelerator 950".

Here are the relevant entries in my xorg.conf

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

### Post by grapeape25 on 2009-03-18
Also, I'm using Hardy Heron and I get no errors in the /var/log/Xorg.0.log, although it says this in it:

```
(II) intel(0): direct rendering: Enabled
```

---

