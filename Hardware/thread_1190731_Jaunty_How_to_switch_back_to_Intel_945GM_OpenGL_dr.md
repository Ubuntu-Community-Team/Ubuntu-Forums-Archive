---
title: "Jaunty How to switch back to Intel 945GM OpenGL drivers"
date: 2009-06-18
forum: Hardware
---

### Post by lootsd on 2009-06-18
I had Compiz working fine on Jaunty. One day I connected a second monitor to my HP Compaq nx7400 laptop. Had to struggle a bit to get the resolutions okay. Now that all works fine.

But it seems as if my OpenGL drivers / settings had been messed up badly. I cannot get Compiz to work any more (even when I have no external monitor connected). OpenGL performance in general looks bad, even 2D performance. At some stage I could not even watch videos on my laptop.

After trying a couple of ideas from ubuntuforums, I got slightly better performance and video is working. But Compiz is still not working.

**My Current Drivers / settings**:
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
``````
$ glxinfo | grep OpenGL
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.4
OpenGL shading language version string: 1.20
OpenGL extensions:
``````

$ tail -21 /etc/X11/xorg.conf
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 2560 1024
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"                   "uxa"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
        Option          "Tiling"                        "true"
EndSection
```**Another working HP Laptop (identical hardware)**.
A colleague also installed Jaunty on his HP Compaq nx7400 and Compiz is still working fine. I asked him for his glxinfo and found a different "OpenGL vendor string" and "OpenGL renderer string".

```
OpenGL vendor string: Tungsten Graphics, Inc 
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20090326 2009Q1 RC2 x86/MMX/SSE2 
OpenGL version string: 1.4 Mesa 7.4 
OpenGL extensions: 

```I suspect getting my laptop from "Mesa Project" back to the "Tungsten Grpahics, Inc" vendor string, will solve my problems. But I have no idea how to do it.

Assistance, as always, will be much appreciated.

---

### Post by lootsd on 2009-06-19
Just after posting this, I restarted GDM and it would not come back. I got a black screen with a message box that said something like:Ubuntu is running in low-graphics mode. (EE) intel(0): Cannot support DRI with framebuffer width > 2048". Next I'm presented with a couple of options and I select "Reconfigure Graphics", then "Use default(generic) configuration".

After this GDM came up again (after another restart) and everything was okay again. Compiz worked and glxinfo reported the old settings:
> OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.4
OpenGL extensions:

I thought everything is good and great again. Then this morning I connected the second display. Initially it comes up with Mirrored Display. This still works fine. But then I selected to have the two monitors (laptop and external) as different screens. It told me that the Virtual Resolution (or something) was updated and I had to log out and back in again.

Comiz was not working anymore and glxinfo again shows the slower settings:
> OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.4
OpenGL shading language version string: 1.20
OpenGL extensions:

If I want to re-create the whole situation, I edit /etc/X11/xorg.conf and change the Device section to:
> Section "Device"
        Identifier      "Configured Video Device"
        Option          "AccelMethod"                   "uxa"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
        Option          "Tiling"                        "true"
EndSection

When I restart gdm, I get the same thing.
"Ubuntu is running in low-graphics mode....
"Reconfigure Graphics"
"Use default (generic) configuration"
glxinfo shows "OpenGL vendor string: Tungsten Graphics, Inc" and Compiz works fine.
Two screens are Mirrored.
I change to expanded.
After re-login, glxinfo shows "OpenGL vendor string: Mesa Project" and Compix does not work anymore.

I really hope there is someone that understands these problems. If someone can assist, I would appreciate quite a bit. Even if someone just tells me the command to revert to the original configuration.

---

### Post by s_baramov on 2009-06-19
Well as far as the dual monitor configuration goes, you and me and many other are out luck. From the [http://intellinuxgraphics.org/dualhead.html](http://intellinuxgraphics.org/dualhead.html) page 

*"There is a known issue that DRI doesn't work on pre-965 if maximum is larger than 2048x2048."*

So you can't me Compiz or any other 3d engine work with dual head on intel 945 unless you go under 2048. 

Still i have lived with this problem for more then a year now. However, after upgrading to Jaunty the performance degrades significantly. I have the feeling I am back on those days of i386 with Windows 3.1. So after digging around ([https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4/](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4/)) I made this change in my xorg.conf and it runs. Note, I have not downgraded my driver.

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver          "Intel"
	Option		"AccelMethod"	"XAA"
EndSection

```

hope it works for you too.

---

### Post by lootsd on 2009-06-20
Your advise is quite help full, thank you. My problem is still how to switch back to the default configuration, equivalent to the error handler I described earlier? Is there a command I can run? A file I can edit?

---

### Post by lootsd on 2009-06-20
I suspect that I found the way to return to the default settings. I only have to remove the following lines from xorg.conf and restart:
>         SubSection "Display"
                Virtual 2560 1024
        EndSubSectionI suspect, what happens is it (?) tries to start with my settings (Display...) and the Intel 945GM prevents that, it then reverts to the Generic MESA driver.

Just adding "Driver Intel" to the "Device" section does not solve this problem. Removing the mentioned lines, solves the problem. By the way, these settings works like a charm. OpenGL works better than ever on my laptop. Thank you s_baramov. Much appreciated.

> ```
Section "Device"
    Identifier    "Configured Video Device"
    Driver          "Intel"
    Option        "AccelMethod"    "XAA"
EndSection
```

---

