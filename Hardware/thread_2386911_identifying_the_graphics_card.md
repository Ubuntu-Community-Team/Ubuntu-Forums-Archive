---
title: "identifying the graphics card"
date: 2018-03-12
forum: Hardware
---

### Post by redy2 on 2018-03-12
Hi all,

I problem i am having is that on my laptop i have an AMD Radeon 530 which apparenantly has no drivers for Linux, only windows 10 . 

so ..
running lspci i get the two following lines:
00:02.0 VGA compatible controller: Intel Corporation Device 5917 (rev 07)
01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265] (rev ff)

if the VGA controller is the video i am using , aka the onboard thing.
then what is the Display Controller all about and why is it detecting another video card ?  

running: sudo lspci -v -s 01:00.0 will give me: 

01:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Topaz XT [Radeon R7 M260/M265] (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel driver in use: amdgpu
	Kernel modules: amdgpu




I am not sure what to make of this . Can this be the result of linux trying to associate my videocard with a driver available to him ? (I assume i did not receive another videocard with the laptop  than i have burgened for :) )

And the important one :Is there like any way to get the videocard to run on linux ? :(

thanks, much appreciated ! 
Adrian

---

### Post by Yellow Pasque on 2018-03-12
You have a hybrid graphics laptop. There is a lower-power integrated GPU in the Intel CPU and a higher-power discrete AMD GPU.

Run this:
```
sudo update-pciids
```
Then, look at lspci again, as well as the output of:
```
glxinfo -B
DRI_PRIME=1 glxinfo -B
```

You may already have the AMD GPU working and not even know it. To use it, you have to run commands with DRI_PRIME=1 like in the example above.

---

### Post by redy2 on 2018-03-12
thanks !

I have ran the above commands and received the beelow so i asume i don't hve the dedicated one . :(

adi@adi-Inspiron-5570:~$ glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Intel Open Source Technology Center (0x8086)
    Device: Mesa DRI Intel(R) Kabylake GT1.5  (0x5917)
    Version: 17.2.8
    Accelerated: yes
    Video memory: 3072MB
    Unified memory: yes
    Preferred profile: core (0x1)
    Max core profile version: 4.5
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Kabylake GT1.5 
OpenGL core profile version string: 4.5 (Core Profile) Mesa 17.2.8
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile


OpenGL version string: 3.0 Mesa 17.2.8
OpenGL shading language version string: 1.30
OpenGL context flags: (none)


OpenGL ES profile version string: OpenGL ES 3.2 Mesa 17.2.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20


adi@adi-Inspiron-5570:~$ DRI_PRIME=1 glxinfo -B
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: Intel Open Source Technology Center (0x8086)
    Device: Mesa DRI Intel(R) Kabylake GT1.5  (0x5917)
    Version: 17.2.8
    Accelerated: yes
    Video memory: 3072MB
    Unified memory: yes
    Preferred profile: core (0x1)
    Max core profile version: 4.5
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.2
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Kabylake GT1.5 
OpenGL core profile version string: 4.5 (Core Profile) Mesa 17.2.8
OpenGL core profile shading language version string: 4.50
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile




OpenGL version string: 3.0 Mesa 17.2.8
OpenGL shading language version string: 1.30
OpenGL context flags: (none)


OpenGL ES profile version string: OpenGL ES 3.2 Mesa 17.2.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20

---

### Post by Yellow Pasque on 2018-03-12
Hmm. I was expecting the DRI_PRIME output to refer to the AMD GPU instead of the Intel one.
What model laptop is this? Can you also check:
```
xrandr --listproviders
```

---

### Post by redy2 on 2018-03-12
The laptop is: 

[B]Laptop Dell Inspiron 5570 
Intel Core Kaby Lake R 8th Gen i5-8250U 
AMD Radeon 530 2GB FullHD FPR di5570i54256530ru[/B]


This is the result igete:
adi@adi-Inspiron-5570:~$ xrandr --listproviders
Providers: number : 2
Provider 0: id: 0x66 cap: 0x9, Source Output, Sink Offload crtcs: 3 outputs: 4 associated providers: 1 name:modesetting
Provider 1: id: 0x3f cap: 0x4, Source Offload crtcs: 0 outputs: 0 associated providers: 1 name:TOPAZ @ pci:0000:01:00.0

---

### Post by Yellow Pasque on 2018-03-12
```
xrandr --setprovideroffloadsink 1 0
DRI_PRIME=1 glxinfo -B
```

If that doesn't work and glxinfo still refers to Intel GPU, I'm out of ideas.

---

### Post by redy2 on 2018-03-12
Thanks but i am getting the same . Still not showing anything about any radeon :(

---

### Post by redy2 on 2018-03-13
any other ideas please ? :(

---

### Post by kc1di on 2018-03-13
try installing inxi```
sudo apt install inxi
```
then run this command: 
```
inxi -G
``` What does that say?

---

### Post by eeshanmulye2 on 2018-03-13
I have the same problem I have HP pavilion wave which has hybrid r9 m470 but all is get is Intel integrated graphics

---

### Post by redy2 on 2018-03-13
Hi  kc1di and thanks ! 
[COLOR=#000000]I have ran [/COLOR][COLOR=#000000][FONT=&quot]inxi -G and i can also find a video card in here . Is this good news ? 

[/FONT][/COLOR]adi@adi-Inspiron-5570:~$ inxi -G
Graphics:  Card-1: Intel UHD Graphics 620
           Card-2: Advanced Micro Devices [AMD/ATI] Topaz XT [Radeon R7 M260/M265 / M340/M360 / M440/M445]
           Display Server: X.Org 1.18.4 drivers: amdgpu (unloaded: radeon)
           Resolution: 1920x1080@60.05hz
           GLX Renderer: Mesa DRI Intel Kabylake GT1.5
           GLX Version: 3.0 Mesa 17.2.8

---

### Post by eeshanmulye2 on 2018-03-14
For Ubuntu the solution is quite simple

[https://m.youtube.com/watch?v=7-ckiKQotNw](https://m.youtube.com/watch?v=7-ckiKQotNw)

Follow the steps in the video. I want to know a permanent solution for all distros.

---

### Post by Yellow Pasque on 2018-03-14
> **eeshanmulye2 said:**
> For Ubuntu the solution is quite simple [https://m.youtube.com/watch?v=7-ckiKQotNw](https://m.youtube.com/watch?v=7-ckiKQotNw)

This is exactly what I had OP do above (I used the provider number instead of the hex ID, but it shouldn't make a difference).

> I want to know a permanent solution for all distros. 

There is nothing Ubuntu-specific about the commands used, so you should be more specific about what isn't working. In fact, if DRI_PRIME is working correctly for you, then you probably have a different issue than the OP, and you may want to consider a new thread.

---

### Post by Yellow Pasque on 2018-03-14
> **Temüjin said:**
> This is exactly what I had OP do above (I used the provider number instead of the hex ID, but it shouldn't make a difference).

@OP: You may want to try again using hex ID just to make sure:
```
xrandr --setprovideroffloadsink 0x3f 0x66
DRI_PRIME=1 glxinfo -B
```

Also, consider that if you don't play games or do anything that demands more 3D power than the Intel GPU provides, it may not be worth the time/frustration it takes to get PRIME working.

---

### Post by deadflowr on 2018-03-14
Is it just me or do the X driver and the mesa driver seem off.
X is amdgpu, but the glx mesa are intel? (from the inxi -G output in post #11)
Seems like an odd mixture.
Is that normal for this?

(I don't have hybrid, so can't tell)

---

### Post by Yellow Pasque on 2018-03-14
> **deadflowr said:**
> Is it just me or do the X driver and the mesa driver seem off.

It's probably a peculiarity of inxi with hybrid graphics.

---

### Post by redy2 on 2018-03-14
Thank you all ! 
Temujin, I have followed the instructions in the video . The output i got is the below . Does this mean that i am actualy using the dedicated gpu ? 

adi@adi-Inspiron-5570:~$ DRI_PRIME=1 glxinfo | grep "OpenGL renderer"
OpenGL renderer string: AMD ICELAND (DRM 3.1.0 / 4.4.0-116-generic, LLVM 6.0.0)

---

### Post by Yellow Pasque on 2018-03-14
Yes, that is what you want to see.

> Does this mean that i am actually using the dedicated gpu ?

Only when you run programs with DRI_PRIME=1

---

### Post by redy2 on 2018-03-16
Thanks ! 
Unfortunately when i try to open for example Starcraft2 with DRI_PRIME=1 it crashes . I have given up and made a dual boot with windows for whenever i want to play . 
Since there is no driver for it i assume that's it . Another thing is Linux did detect the video correctly , it's an R7 i have so basically i was given a different laptop which hopefully i will be able to give back . :)
Thanks a lot for all the time and effort !

---

