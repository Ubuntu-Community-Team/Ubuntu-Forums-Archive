---
title: "GeForce GTX 1650 Ti Max-Q Vulkan not working"
date: 2020-10-03
forum: Hardware
---

### Post by somamint on 2020-10-03
Hello Guys,

i just bought the new Razer Blade Stealth 2020 and installed Kubuntu. 

                 [                             Intel Core i7-1065G7]("https://www.idealo.de/preisvergleich/ProductCategory/3751F3035300.html")                                       16 GB RAM                   512 GB SSD                   nVidia 

Everything works out of the box. But once i install the newest Nvidia Driver i can't get vulkan working.

Vulkan installation seems to work, but i get texture pop up ingame.

Can anybody help me to install the Nvidia Driver? 

I tried now vkcube and i guess the cube should be turn around  smooth but its stuck on one place and tried to turn without succes and  it creates kind of the same texture popup as i have in prey. So i guess  there so something wrong with vulkan.

Also found another error:

lspci | grep 3D && vulkaninfo | grep deviceName
58:00.0 3D controller: NVIDIA Corporation Device 1f95 (rev a1)
ERROR: [Loader Message] Code 0 : /usr/lib/i386-linux-gnu/libvulkan_radeon.so: wrong ELF class: ELFCLASS32
ERROR: [Loader Message] Code 0 : /usr/lib/i386-linux-gnu/libvulkan_intel.so: wrong ELF class: ELFCLASS32
deviceName = GeForce GTX 1650 Ti with Max-Q Design

Thanks in advance :)

---

### Post by Yellow Pasque on 2020-10-04
[https://ubuntuforums.org/showthread.php?t=2450147&p=13985186#post13985186](https://ubuntuforums.org/showthread.php?t=2450147&p=13985186#post13985186)

---

### Post by somamint on 2020-10-04
Ok wow this helped a lot, Prey got no more texture pop ups. But after playing it 15 mit it crashed and how me the error

Prey.exe has stoped working
"Attempt to read from adress 0xFFFFFFFFFFFFFFFFFFFF
The memory could not be read.

but this could be also a prey problem itself according to protondb. Will try some other games i had problems yesterday!

---

### Post by somamint on 2020-10-05
Ok i tried Star Wars Fallen Order and Prey with different Proton and it just works! I'm so grateful :) 

But could you explain, what helped? I mean yes it fixed it, but what was the problem?

---

### Post by Yellow Pasque on 2020-10-05
> **somamint said:**
> But could you explain, what helped? I mean yes it fixed it, but what was the problem?

So you are using "prime-run" for these games, correct? I would guess that you were trying to run them on the Intel GPU before and there are bugs there. I don't know though. I don't have the hardware you have.

---

### Post by somamint on 2020-10-05
Yes i use "prime run". So is it like a special driver? Just wanna understand whats the difference to the normal driver.

---

### Post by Yellow Pasque on 2020-10-05
No, prime-run uses the Nvidia GPU. Everything else runs on the integrated Intel GPU.

---

### Post by somamint on 2020-10-05
Ahhh is it because my laptop has like two graphic cards?

---

### Post by Yellow Pasque on 2020-10-05
> **somamint said:**
> Ahhh is it because my laptop has like two graphic cards?

Yes.

---

### Post by somamint on 2020-10-08
Ok its really strange, If i play Linux Native games i need "performance mode" and for vulkan i need to change to "on demand"

---

### Post by Yellow Pasque on 2020-10-08
> **somamint said:**
> Ok its really strange, If i play Linux Native games i need "performance mode" and for vulkan i need to change to "on demand"

No, I'm not sure where you got that idea.
You should always be in on-demand mode, and use prime-run on games/apps that need serious 3D power. It does not matter whether those apps use Vulkan or OpenGL. It does not matter whether those apps are Linux native or run in something like wine.

---

### Post by somamint on 2020-10-09
I switched to performance mode as native linux games won't even start on demand mode. If i start native games with proton in worked on demand. But native no change.

---

### Post by Yellow Pasque on 2020-10-09
First, check that these work correctly in on-demand mode (copy/paste the output).
```
glxinfo -B
prime-run glxinfo -B
```

Then, try starting a game in on-demand mode:
```
prime-run <gamecommand>
```
What is the output?

---

### Post by somamint on 2020-10-09
```
[FONT=monospace][COLOR=#000000]glxinfo -B [/COLOR]
name of display: :0 
display: :0  screen: 0 
direct rendering: Yes 
Extended renderer info (GLX_MESA_query_renderer): 
    Vendor: Intel (0x8086) 
    Device: Mesa Intel(R) Iris(R) Plus Graphics (ICL GT2) (0x8a52) 
    Version: 20.0.8 
    Accelerated: yes 
    Video memory: 3072MB 
    Unified memory: yes 
    Preferred profile: core (0x1) 
    Max core profile version: 4.6 
    Max compat profile version: 4.6 
    Max GLES1 profile version: 1.1 
    Max GLES[23] profile version: 3.2 
OpenGL vendor string: Intel 
OpenGL renderer string: Mesa Intel(R) Iris(R) Plus Graphics (ICL GT2) 
OpenGL core profile version string: 4.6 (Core Profile) Mesa 20.0.8 
OpenGL core profile shading language version string: 4.60 
OpenGL core profile context flags: (none) 
OpenGL core profile profile mask: core profile 

OpenGL version string: 4.6 (Compatibility Profile) Mesa 20.0.8 
OpenGL shading language version string: 4.60 
OpenGL context flags: (none) 
OpenGL profile mask: compatibility profile 

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 20.0.8 
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20


[/FONT]
```

the second one, not sure what i should type in in "gamecommand"

---

### Post by Yellow Pasque on 2020-10-09
You didn't give the output of:
```
prime-run glxinfo -B
```

> the second one, not sure what i should type in in "gamecommand" 
What games are you haveing problems with?

---

### Post by somamint on 2020-10-09
I try to play Kubifaktorium Native.

---

### Post by Yellow Pasque on 2020-10-11
> **somamint said:**
> I try to play Kubifaktorium Native.

I have no idea what that is. Try starting it from the command line.
And you still haven't show the output of:
```
prime-run glxinfo -B
```

---

### Post by somamint on 2020-10-11
```
[FONT=monospace][COLOR=#000000] prime-run glxinfo -B [/COLOR]
name of display: :0 
display: :0  screen: 0 
direct rendering: Yes 
Memory info (GL_NVX_gpu_memory_info): 
    Dedicated video memory: 4096 MB 
    Total available memory: 4096 MB 
    Currently available dedicated video memory: 3700 MB 
OpenGL vendor string: NVIDIA Corporation 
OpenGL renderer string: GeForce GTX 1650 Ti with Max-Q Design/PCIe/SSE2 
OpenGL core profile version string: 4.6.0 NVIDIA 450.66 
OpenGL core profile shading language version string: 4.60 NVIDIA 
OpenGL core profile context flags: (none) 
OpenGL core profile profile mask: core profile 

OpenGL version string: 4.6.0 NVIDIA 450.66 
OpenGL shading language version string: 4.60 NVIDIA 
OpenGL context flags: (none) 
OpenGL profile mask: (none) 

OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 450.66 
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
[/FONT]
```

Kubifaktorium is a game on steam " [https://store.steampowered.com/app/898720/Kubifaktorium/](https://store.steampowered.com/app/898720/Kubifaktorium/)

---

### Post by Yellow Pasque on 2020-10-11
^Okay, thanks. It looks like prime-run is working correctly.
So, if you're trying to run a game on Steam, here are Steam's directions:
> To make a game run using the discrete GPU, use these simple steps:
    Select a game - that you want to run using your discrete Nvidia card - from the Library page of the Steam client, right-click, and select Properties.
    Click the SET LAUNCH OPTIONS... button and specify prime-run %command% for the command line.
    Save your changes.This method allows you to pick when the discrete NVidia GPU should be used on a per-game basis.


---

### Post by somamint on 2020-10-11
thanks.

so i put "prime-run %command%" (without") in  LAUNCH OPTIONS, click on play wait for a few seconds, game not even starting, i can click play again, but nothing happens.

---

### Post by Yellow Pasque on 2020-10-11
I don't use Steam on Linux and I don't have the hardware to replicate this, so I don't know what to tell you. Maybe ask on their forum.

---

