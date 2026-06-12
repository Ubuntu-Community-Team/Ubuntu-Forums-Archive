---
title: "force resolution to 1440x900"
date: 2007-05-15
forum: Hardware &amp; Laptops
---

### Post by mailbinoy on 2007-05-15
I am close to getting everything working as i need( 3 monitors 2 graphics cards  nvidia and ati) 
I cant get the resolution set to 1440x900. It is always out of the screen vertically by 30 - 40 pixels.
 
```
(II) NVIDIA(1): Assigned Display Device: CRT-1
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "1440x900"
(II) NVIDIA(1):     "1280x1024"
(II) NVIDIA(1):     "1024x768"
(II) NVIDIA(1):     "800x600"
(II) NVIDIA(1):     "640x480"
(II) NVIDIA(1): Virtual screen size determined to be 1440 x 1024
(--) NVIDIA(1): DPI set to (89, 87); computed from "UseEdidDpi" X config
(--) NVIDIA(1):     option
```

here's the xorg

```
Section "Screen"
    Identifier     "Screen0-0"
    Device         "Videocard0-0"
    Monitor        "Monitor0-0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection

EndSection
```

---

### Post by heimo on 2007-05-15
> **mailbinoy said:**
> 
I cant get the resolution set to 1440x900. It is always out of the screen vertically by 30 - 40 pixels.
 

Could you elaborate? Is it off by a fixed amount of pixels, or does it scroll with you mouse pointer? I'm asking because there's a way to setup virtual screen which is larger than resolution, and it would cause such behaviour, but from your explanation I'm not sure if this has anything to do with it.

---

### Post by mailbinoy on 2007-05-15
> **heimo said:**
> Could you elaborate? Is it off by a fixed amount of pixels, or does it scroll with you mouse pointer? I'm asking because there's a way to setup virtual screen which is larger than resolution, and it would cause such behaviour, but from your explanation I'm not sure if this has anything to do with it.

Yes the screen does scroll with the mouse pointer.

---

### Post by heimo on 2007-05-15
> **mailbinoy said:**
> Yes the screen does scroll with the mouse pointer.

Ok, in that case, try adding:```


Section "Screen"
    Identifier     "Screen0-0"
    Device         "Videocard0-0"
    Monitor        "Monitor0-0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    **Virtual 1440 900**

EndSection
```

---

### Post by mailbinoy on 2007-05-16
> **heimo said:**
> Ok, in that case, try adding:```


Section "Screen"
    Identifier     "Screen0-0"
    Device         "Videocard0-0"
    Monitor        "Monitor0-0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    **Virtual 1440 900**

EndSection
```

Thanks man! works like a charm. only the virtual needs to be added in the Subsection

```


Section "Screen"
    Identifier     "Screen0-0"
    Device         "Videocard0-0"
    Monitor        "Monitor0-0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1280x1024" "1024x768" "800x600" "640x480"
    **Virtual 1440 900**
    EndSubSection


EndSection
```

---

