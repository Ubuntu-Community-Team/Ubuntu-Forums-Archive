---
title: "AMD/intel check swichable"
date: 2017-05-18
forum: Hardware
---

### Post by azim3 on 2017-05-18
Hello Everyone,
I`m new on intel/AMD laptops ( I byu Dell with intel+AMD) and install ubuntu gnome 17.04, everything is working fine, I don`t have problems, but I want to know:
[LIST]
[*] Whitch video card I use ?
[*] How to switch cards ?
[*] Is there have automatic switchable ?
[*]From where can I control wich application to use AMD  (If don`t have automatic swiching) ?
[/LIST]

When i type sudo cat /sys/kernel/debug/vgaswitcheroo/switch output is: 

```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch0:DIS: :DynOff:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0



```

Attached image show my system info on Gnome Details panel. (my system language is Bulgarian) 
[IMG]https://s24.postimg.org/651suogmd/amd.png[/IMG]
My Dell is with: 
intel core i5-7200U
GPU: AMD R7 M445 (4BG) + integradet INTEL
Sorry for my English guys :)
I hope you can help me.

---

### Post by Yellow Pasque on 2017-05-18
[https://wiki.archlinux.org/index.php/PRIME#PRIME_GPU_offloading](https://wiki.archlinux.org/index.php/PRIME#PRIME_GPU_offloading)

---

### Post by azim3 on 2017-05-19
Hello thanks for support, nice article from arch, but I can not understand is there have automatic swiching or I need to swiching cards manualy ?
Thank you !

---

### Post by Yellow Pasque on 2017-05-19
Look at output of:
```
DRI_PRIME=1 glxinfo | grep string
```
If it says Gallium on AMD, the discrete GPU should be setup correctly. 

So when you want to use the AMD GPU:
```
DRI_PRIME=1 programname
```

---

### Post by azim3 on 2017-05-19
Hello,
th output from [COLOR=#000000][FONT=&quot]DRI_PRIME=1 glxinfo | grep string[/FONT][/COLOR]

```
DRI_PRIME=1 glxinfo | grep stringserver glx vendor string: SGI
server glx version string: 1.4
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD ICELAND (DRM 3.9.0 / 4.10.0-21-generic, LLVM 4.0.0)
OpenGL core profile version string: 4.5 (Core Profile) Mesa 17.0.3
OpenGL core profile shading language version string: 4.50
OpenGL version string: 3.0 Mesa 17.0.3
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 17.0.3
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10



```

When I type DRI_PRIME=1 firefox
My firefox is going to start and work good. I thinks everything is good what do you think ?
 Something like bumlbebee on nVidia :) 
Is I'm right ?

---

### Post by Yellow Pasque on 2017-05-20
Yeah, like bumblebee. I've never had a laptop with switchable graphics, so I won' claim to be an expert, but it sounds like it's working as intended.

Mark the thread solved if you're satisfied (thread tools menu above first post).

---

### Post by azim3 on 2017-05-20
Yeah, Thanks again. God bless you!

---

