---
title: "Default Monitor"
date: 2009-11-12
forum: Hardware
---

### Post by Shamess707 on 2009-11-12
I have ubuntu 9.10 and running dual monitor display, a 22 inch wide screen as my main and a 19 inch as my peripheral monitor. The Widescreen monitor is off the DVI output of my video card and the 19 is the VGA. As of right now Ubuntu is defaulting to the 19 inch, but I want the 22 inch to be default. Any help?

my xorg.conf file says

```

Section "Screen"
        Identifier      "Configured Screen Device"
        Device  "Configured Video Device"
        SubSection "Display"
                Virtual 2960 1450
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

```

---

### Post by Shamess707 on 2009-11-12
bump

---

### Post by Shamess707 on 2009-11-13
bump

---

### Post by Shamess707 on 2009-11-15
bump

---

### Post by Shamess707 on 2009-11-16
...Sigh

---

