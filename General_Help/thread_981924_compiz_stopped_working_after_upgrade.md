---
title: "compiz stopped working after upgrade"
date: 2008-11-14
forum: General Help
---

### Post by scicode on 2008-11-14
After upgrading to interpid compiz stopped working

here are some things i tested compiz-check from [http://forlong.blogage.de/entries/pages/Compiz-Check]("http://forlong.blogage.de/entries/pages/Compiz-Check")

```
$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
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

```
$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1366x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present.
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity
```

so I checked glxifo

```
$ glxinfo 
name of display: :0.0                         
display: :0  screen: 0                        
direct rendering: Yes                         
server glx vendor string: SGI                 
server glx version string: 1.2                
server glx extensions:                        
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,      
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer        
client glx vendor string: SGI                                                 
client glx version string: 1.4                                                
client glx extensions:                                                        
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,    
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory,     
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control,                          
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control,     
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync,      
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,                
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap                 
GLX version: 1.2                                                              
GLX extensions:                                                               
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context,    
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method,          
    GLX_SGIS_multisample, GLX_SGIX_fbconfig                                   
OpenGL vendor string: Mesa Project                                            
OpenGL renderer string: Software Rasterizer                                   
OpenGL version string: 2.1 Mesa 7.2                                           
OpenGL shading language version string: 1.10  
```

this is the output after doing a

```
sudo aptitude install libgl1-mesa-dri
```

which was already installed

i also checked 

```
$ less /var/log/Xorg.0.log|grep AIGLX
(==) AIGLX enabled
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
```

now i am tired and hope that someone can help me to get it right

---

### Post by bonfire89 on 2008-11-16
I'm having the same issues with my 940gml on my thinkpad x60 tablet

---

### Post by binbash on 2008-11-16
try sudo dpkg-reconfigure xserver-xorg and report back if it still occurs

---

### Post by bonfire89 on 2008-11-16
nope, no go :(

I'm getting better at linux, but not quite there yet. I suspect it is a driver issue. I have not done anything regarding installing drivers or anything.

But here is the relevant information on my card

[PHP]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
[/PHP]

I also previously had my external monitor working with intrepid, however, in the process of attempting to fix things, I have lost it. heh










update


definitely driver issues

me@meezcomp:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y 

 The vesa driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 



if I fix it I will post back

---

### Post by scicode on 2008-11-18
thank you binbash

this was much easier than i thought

... now let me bang my head against the screen for not trying this earlier

---

### Post by thread on 2009-01-19
binbash's command didn't seem to help my issue... and it's very similar to the one being discussed. Check this other thread for the details:

[http://ubuntuforums.org/showthread.php?t=1033566](http://ubuntuforums.org/showthread.php?t=1033566)

---

### Post by jmcvetta on 2009-05-07
Try adding this directive to your xorg.conf in the "Device" section:

```
Option          "AccelMethod"     "UXA"
```

That worked on my Thinkpad X60 with Intel 945GM graphics.

---

### Post by bonfire89 on 2009-05-07
> **jmcvetta said:**
> Try adding this directive to your xorg.conf in the "Device" section:

```
Option          "AccelMethod"     "UXA"
```

That worked on my Thinkpad X60 with Intel 945GM graphics.

Interesting. Although it did improve performance, I would get system crashes which I believe were linked to fast motion on the screen. It seemed like it happened a few times when I'd quickly scroll up a web page... possibly with flash. I have a thinkpad x60tablet. I am also using an external monitor.

---

