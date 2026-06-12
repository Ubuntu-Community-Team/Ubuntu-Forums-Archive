---
title: "Image not centered with screen"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by Pulka on 2005-04-12
Hi!

I have a problem with my Philips 170S  17'.
My image is not centered with the screen. It's a little bit to the right, and for example, i can't see the cross to close the firefox and other apps.

I already checked Vert Refresh and Horiz Sync, but it seems alright with what the manufacturer says. Can anyone help me with this? If i ajust the position of the screen manually, then, when i go to windows, the same happens. If i ajust in windows, then, in linux, is not centered...and so on.
Here is the XF86Config-4:

Section "Device"
        Identifier      "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        ModelName    "Philips 170S"
        DisplaySize     340     270
        HorizSync    30.0 - 82.0
        VertRefresh 56.0 - 76.0
        option          "dpms"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Monitor         "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640$        EndSubSection
        SubSection "Display"
                Depth           4
       Modes           "1280x1024" "1024x768" "800x600" "720x400" "640$        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640$        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640$        EndSubSection
  SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640$        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640$        EndSubSection
EndSection

---

### Post by c_dog on 2005-04-12
Is this using Warty or Hoary? Warty uses XF86Config-4, but Hoary uses xorg.conf . Otherwise you  might try commenting out the DisplaySize line. You shouldn't need it unless you're trying to force the screen dpi to close to 96dpi which is 338 270. If want to check your dpi :

```
xdpyinfo | grep resolution
```

The reason for the screen shift is because if you're displaying Windows and Linux at 1280x1024 you may not have both of them set for the same refresh rate. The ranges you gave will Linux 1280x1024 at 75Hz (refresh rate) if you tell it the montior to specfically to use 75Hz. It's going to probably try to sync at 60Hz if you don't give XFree or xorg a modeline that discribes 75Hz to your monitor.
To do this you'd put this in the Monitors section of your XFree or xorg config file.

```
Modeline "1280x1024@75" 156.43 1280 1312 1904 1936 1024 1043 1056 1076
``` 

Set the modes at whatever bit setting in the Screen section with  1280x1024@75 instead of just 1280x1024

---

### Post by Pulka on 2005-04-13
it worked! Many thanks!

Many people says that in Hoary is not XF86Config-4, but i have Hoary and i don't have the xorg.conf. Just the XF86. Is it normal?

Anyway, here it is the new XF86 with the changes. Please see if everything is alright.

Thanks again


Section "Monitor"
        Identifier   "Monitor0"
        ModelName    "Philips 170S"
        DisplaySize     340     270
        HorizSync    30.0 - 82.0
        VertRefresh 56.0 - 76.0
        option          "dpms"
        Modeline "1280x1024@75" 156.43 1280 1312 1904 1936 1024 1043 1056 1076
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Monitor         "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
EndSection

---

### Post by shmk on 2005-06-09
I have the same problem but I'm using 1024 x 768 @ 85 ,
my monitor is an LG studioworks 700s,
someone can give me the right "modeline" ? (Not understood what numbers on it mean... :roll: )

---

### Post by PryGuy on 2005-06-09
And yet, have you enabled the native nVidia driver with 3D acceleration? If not, [enable it](http://ubuntuguide.org/#installnvidiadriver) cause the ubuntu's own driver causes such things

---

### Post by shmk on 2005-06-11
[QUOTE=PryGuy]And yet, have you enabled the native nVidia driver with 3D acceleration? If not, [enable it](http://ubuntuguide.org/#installnvidiadriver) cause the ubuntu's own driver causes such things[/QUOTE]
 THX !
The problem is solved :)

---

### Post by SandmanXC on 2008-02-04
I have the same problem on 7.10. I've done the edits to xorg.conf, but it's the same. Any advice?

Edit: Using the nVidia drivers does help indeed. Sorry :D

---

