---
title: "Compiz not Running when Xrandr enabled"
date: 2008-09-23
forum: General Help
---

### Post by croghar on 2008-09-23
Hi everyone,

the compiz tools are not running when I extend my monitor using xrandr.

Here is the ouptut of the compiz-check script:
```

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


```

Maybe a hint what goes wrong. To enable the dual monitor view I had to update my xorg.conf Screen section with the following lines:
```

        SubSection "Display"
                   Virtual 2560         1024
        EndSubSection

```

Without the subsection compiz works fine when restarting the Xserver.

Any suggestions what to do?

---

