---
title: "Problem starting Compiz after upgrade to 8.10"
date: 2008-11-06
forum: General Help
---

### Post by silentstorm on 2008-11-06
After I upgraded to 8.10 Compiz won't start anymore.

compiz --replace is giving me

```
wim@Orion:~$ compiz --replace &
Checking for Xgl: [3] 9054
wim@Orion:~$ not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Aborted

```


although compiz-check is telling everything should be ok.

```
wim@Orion:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```

I used to run Compiz on 8.4 with Xgl but I don't think that is possible on 8.10, but shouldn't it work directly with the nvidia driver

current nvidia driver is 177.80-0ubuntu3  (I also tried 173)
and I'm using twinview

Does anyone has an idea how to solve this?
If more info is needed I'm happy to provide it.

thanks!

---

### Post by FerN(SA) on 2008-11-06
I think you have to wait for nvidia to bring out its new driver.  8.10 has a new Xorg.  I heard about it caused problems with PC using Nvidia and ATI graphic cards

---

### Post by mikeyfbi on 2008-11-06
Compiz won't start for me either:confused:

This is the output I get when I run 'compiz' in terminal
[PHP]Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
[/PHP]

I've googled it and found others with the same problem, but I haven't stumbled upon any solutions yet.

Mike

---

### Post by Izek on 2008-11-06
> **mikeyfbi said:**
> Compiz won't start for me either:confused:

This is the output I get when I run 'compiz' in terminal
[PHP]Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
[/PHP]

I've googled it and found others with the same problem, but I haven't stumbled upon any solutions yet.

Mike

You have not installed xorg-driver-fglrx or the "proper" nvidia driver.

---

### Post by sharkster2007 on 2008-11-06
I have 3d effects working on my Nvidia 6600GT hope my thread helps you [http://ubuntuforums.org/showthread.php?t=973038](http://ubuntuforums.org/showthread.php?t=973038) 

(I do have the grey titlebar window problem & some of the minor effects don't work but I have heard several times this is down to Nvidia's driver, the 3D desktop cube works however)

---

### Post by mikeyfbi on 2008-11-08
> **Izek said:**
> You have not installed xorg-driver-fglrx or the "proper" nvidia driver.

I installed xorg-driver-fglrx and xserver-xorg-video-vga

my output from lscpi | grep VGA is 
[PHP]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
[/PHP]

now my compiz output is
[PHP]Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity [/PHP]

:confused::confused:

---

### Post by Izek on 2008-11-08
You didn't tell me you had intel. That's a different driver.

---

### Post by mikeyfbi on 2008-11-08
Yeah, I didn't realize until this thread.  Any ideas?

---

### Post by mikeyfbi on 2008-11-10
bump

---

