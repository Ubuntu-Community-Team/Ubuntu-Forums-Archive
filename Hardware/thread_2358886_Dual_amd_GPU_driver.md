---
title: "Dual amd GPU driver"
date: 2017-04-18
forum: Hardware
---

### Post by milan225 on 2017-04-18
Hello, I got a problem with my PC. My pc got 2. GPU:
1. AMD RADEON R5 SERIES (From amd apu CPU)
2. AMD RADEON R7 M360 (Dedicated)
I want to play some games, but I don´t know how to switch from R5 to R7.
My PC:
HP PAVILION 15ab081nc

ps: sorry for my bad english

---

### Post by Mark Phelps on 2017-04-18
You probably can't.  You have what is known as Switchable Graphics and Linux drivers for that are very, very hard to find.  The drivers from AMD do not support switchable graphics, so basically, you are stuck.

---

### Post by milan225 on 2017-04-22
Is there any other ways? Or to play I need to get back to Win 10?

---

### Post by Mark Phelps on 2017-04-22
Switchable graphics have changed over the years.  Originally, it was a mixture of AMD/Intel video chips and there were workarounds in Linux that sometimes got those working:  [http://ubuntuforums.org/showthread.php?t=1930450&highlight=switchable+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=switchable+graphics)

But with the newer AMD/AMD chipsets, I personally know of no way to get those working properly in Linux.

---

### Post by fredwntr1 on 2017-04-22
you need to disable the apu from the bios of your computer that will do it

---

### Post by milan225 on 2017-04-23
My bios does not support this function...

---

### Post by Yellow Pasque on 2017-04-23
See if xrandr recognizes both GPU's:
```
xrandr --listproviders
```

---

### Post by milan225 on 2017-04-26
Providers: number : 2
Provider 0: id: 0x73 cap: 0x9, Source Output, Sink Offload crtcs: 2 outputs: 2 associated providers: 1 name:MULLINS @ pci:0000:00:01.0
Provider 1: id: 0x3f cap: 0x4, Source Offload crtcs: 0 outputs: 0 associated providers: 1 name:TOPAZ @ pci:0000:01:00.0

---

### Post by milan225 on 2017-04-26
> Providers: number : 2
Provider 0: id: 0x73 cap: 0x9, Source Output, Sink Offload crtcs: 2 outputs: 2 associated providers: 1 name:MULLINS @ pci:0000:00:01.0
Provider 1: id: 0x3f cap: 0x4, Source Offload crtcs: 0 outputs: 0 associated providers: 1 name:TOPAZ @ pci:0000:01:00.0

This?

---

### Post by Yellow Pasque on 2017-04-26
Set the integrated card to offload todiscrete card:
```
xrandr --setprovideroffloadsink 1 0
```

Test it:
```
DRI_PRIME=1 glxinfo | grep renderer
```
Command should return something like "Gallium 0.4 on AMD Topaz"

So now, when you want to use the discrete GPU to run "someprogram":
```
DRI_PRIME=1 someprogram
```

---

### Post by milan225 on 2017-04-27
ok, but tow I can play minecraft. I change java path to: "DRI_PRIME=1 java" but the game not started.

and test code: > ~$ DRI_PRIME=1 glxinfo | grep renderer
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
Extended renderer info (GLX_MESA_query_renderer):
OpenGL renderer string: Gallium 0.4 on AMD ICELAND (DRM 3.3.0 / 4.8.0-46-generic, LLVM 3.8.0)



---

### Post by milan225 on 2017-04-27
Sorry, but my internet is so buggy

---

### Post by milan225 on 2017-04-27
Ok, But how o play minecraft? I tryed to change path but game not started

---

