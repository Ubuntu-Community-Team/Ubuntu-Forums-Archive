---
title: "How to upgrade your OpenGL implementation"
date: 2011-03-30
forum: Hardware
---

### Post by bornbyforce on 2011-03-30
Ok I have looked for this enough but I don't see how I can do this. May be I am looking for the wrong thing anyway.

I have a laptop with an old Integrated Intel Graphics.
The version of Ubuntu out of the box shows it as Mesa 7.9 and OpenGL 1.4
So far so good.
Now, Isn't mesa supposed to provide the latest version of OpenGL interface for the programs?
I mean when I am programming with OpenGL, shouldn't I be able to receive the OpenGL 2 functions (for example) and all the hardware compatibility issues be behind the scene?
If a Graphics card is not supporting certain functions they can be implemented in software and run by CPU. Naturally they are not as fast but code will be portable. Is there a way to upgrade the version of OpenGL interface that Mesa provides?
And if Mesa is not meant to do this does anyone know of anything else?

The question may be a little out of the scope of UbuntuForums but I'd be happy to go and read the manual first if I know what manual exactly I need to read! : p

---

### Post by xandercage17 on 2011-03-31
Delete My account

---

### Post by bornbyforce on 2011-04-01
[LEFT]Thanks  xandercage17 but that is not the problem. I am already on mesa 7.9 as I  said above. And it supports opengl2.1 as well. My OpenGL version string  is 1.4 Mesa 7.9-devel.
The question is how can I get access to opengl2.1 api. Of course my  graphic card does not support functions of 2.1. But the interface must  be there and must work at software level and executed by CPU. I don't  know how to set this up.
  [/LEFT]

---

### Post by IcarusR on 2011-04-01
> I have a laptop with an old Integrated Intel Graphics.

Depending on what your graphics is & how old it may not be supported by the intel module (driver) for your h/w

---

### Post by bornbyforce on 2011-04-01
:( I don't know why nobody gets what I mean...
I know my hardware does not support OpenGL above 1.4. I don't need to look for that. I know the driver support is necessary for hardware rendering. I know I can not go above OpenGL 1.4 with this card. 
OpenGL is not code itself. It is just a standard. And Mesa and others have implemented that standard. What I want is NOT hardware rendering. I want to be able to send commands as defined in opengl2.1. Then Mesa using some sort of software implementation as a replacement of graphic card's shortcomings, renders it as if the card does support OpenGL2.1. Naturally this will be quite slow compared to real 2.1 which is alright.

---

### Post by Yellow Pasque on 2011-04-01
Turn off hardware rendering and use the Mesa software rasterizer. You can probably do this in xorg.conf with:
```
Section "Module"
        Disable    "dri"
EndSection
```

---

### Post by bornbyforce on 2011-04-05
Thanks Temujin. I actually could not get your suggestion to work. When I don't load DRI the GUI doesn't load.

I However found the answer which probably will be helpful for people who come and read this later.
When your hardware does not support certain functionality if you use wrappers like GLEW to provide you with a unique interface, they will leave out the functions that are not supported. However Mesa 7.9 on my machine DOES support things like Vertex Buffers although they are not supported by Intel's driver provided for Windows.
The trick is to use the ARB functions directly. For example for glGenBuffers just use glGenBuffersARB. As far as I could understand you can use all the functionality that your Mesa version has implemented regardless of your hardware's ability.
I personally have not tested all the functionality. But I can confirm that there are some cases at least that I can use functions in OpenGL1.5 (for example) with Mesa under Ubuntu that are not available to me with Intel driver's OpenGL1.4 implementation under Windows in the same machine.
Of course my main concern here is code portability rather than runtime performance.

---

