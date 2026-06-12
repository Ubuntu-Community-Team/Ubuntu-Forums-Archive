---
title: "Nvidia Xorg complaining EDID file is wrong format"
date: 2013-04-10
forum: Hardware
---

### Post by Jamie_Edwards on 2013-04-10
Hi guys,

I've got a little bit of a problem with Nvidia and it's driver ( which is 310.14 ) where I've got it using my xorg.conf file.

When I entered the following command:
```

-$ sudo nvidia-xconfig --custom-edid=DFP-1:/etc/X11/technika_edid.bin

```

and then reboot my computer, my screen stays at 800x600 ( when it's actually supposed to be at 1920x1080 )

I then had a look in my Xorg.0.log file and found this:
```

[    17.756] (WW) NVIDIA(GPU-0): Unable to use EDID file '/etc/X11/technika_edid.bin': file
[    17.756] (WW) NVIDIA(GPU-0):     format not recognized
[    17.785] (WW) NVIDIA(GPU-0): The EDID read for display device DFP-1 is invalid:
[    17.785] (WW) NVIDIA(GPU-0):     unrecognized EDID Header.

```

Any ideas in how I can get this to work as I need to be able to use the CUDA function of the card with Blender 3D.

Thanks.

---

### Post by Jamie_Edwards on 2013-04-13
Anyone got any ideas?

---

### Post by Jamie_Edwards on 2013-04-20
Gonna give this one another go, anyone got any idea's I need my second monitor working...

---

