---
title: "Nvidia 7800GTX SLI setup help"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by godmode0 on 2007-11-30
Hello got some buggy sli when activate sli ..
here my specs 

[debian lenny/sid 32bit] [Kernel: Linux 2.6.22-14-generic i686] [Uptime: 1h 7min 33.68s] [Cpu Name: AMD Athlon(tm) 64 X2 D Proce or 4400+] [Total RAM: 2027MB] [NVIDIA Corporation GeForce xfx7800 GTX
ASus nforce 4   A8n sli premium (latest bios )
aka ubuntu 7.10 


all updated en latest !fresh install



When use single card i have these fps ->>

46398 frames in 5.0 seconds = 9279.520 FPS
45294 frames in 5.0 seconds = 9058.639 FPS
45824 frames in 5.0 seconds = 9164.712 FPS
44397 frames in 5.0 seconds = 8879.363 FPS
45417 frames in 5.0 seconds = 9082.379 FPS
46291 frames in 5.0 seconds = 9258.074 FPS
46187 frames in 5.0 seconds = 9237.333 FPS
42564 frames in 5.0 seconds = 8512.649 FPS

when activate sli with the  "sli nvidia-xconfig --sli=" command
and i run glxgears . its a total disaster and pfs go down to maybey 2000 and my desktop hangs ... realy crappy (

I started loving ubuntu kuz its realy nice and finaly runs great .. tweaked and all eyecandy... but like i said want to have my slii to have work.!  would be so nice :P


if i need to provide to some debug logs tell me how .. and i wil do

ps: i searched the forums and could not find a solution, if this is double posted or there is solution for it plzz linke me ... if no sorry for this post !

xX

---

### Post by multi on 2007-12-01
I have the same problems with 2 7900GTO cards in SLI. ET Quake Wars crashes the complete system when the limbomenu is loaded, I can play Enemy Territory but performance is worse then with single card. I tried with different drivers but all seem to give the same problems: 100.14.19 / 100.14.23 and 169.04. Also I've tried different settings for SLI option in /etc/xorg.conf but none of them seem to make a difference: AFR / SFR / Auto. I realy hope these performance issues will be fixed 'cause I've grown kinda fond of Ubuntu.

I found this quote from [here](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-w.html)

[i]Why is glxgears slower when SLI is enabled?
	
When SLI is enabled, the NVIDIA driver must coordinate the operations of both GPUs when each new frame is swapped (made visible). For most applications, this GPU synchronization overhead is negligible. However, because glxgears renders so many frames per second, the GPU synchronization overhead consumes a significant portion of the total time, and the framerate is reduced.[/i]

At least that explains why glxgears is slower.

---

