---
title: "GLXGears has very slow frame rate with nvidia GeForce GPU"
date: 2013-02-19
forum: Hardware
---

### Post by Mr Kipling on 2013-02-19
System:
PC: Dell Inspiron 530
CPU: Intel® Core™2 Duo CPU E8500 @ 3.16GHz × 2
RAM: 3GB
OS: Ubuntu 12.04 (32-bit)
GPU: EVGA nvidia GeForce 210
Dirver: 304.64
Direct Rendering: Yes

When running glxgears with gnome classic the window pops up but the gears do not display, the framerate is extremely slow:
glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
3 frames in 13.0 seconds =  0.230 FPS
2 frames in 13.1 seconds =  0.153 FPS
2 frames in 13.1 seconds =  0.153 FPS
2 frames in 13.1 seconds =  0.153 FPS
2 frames in 13.1 seconds =  0.153 FPS
2 frames in 13.1 seconds =  0.153 FPS

Running glxinfo also takes a while to complete and freezes the system for 30 seconds.

When running in gnome classic no effects, glxinfo completes instantly but glxgears still shows the same behaviour.

I installed the nvidia drivers using:
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update 
sudo apt-get install nvidia-current

I also purged the old nvidia drivers before running this.

---

### Post by The Cog on 2013-02-19
It may be worth trying the latest "experimental" nvidia drivers (nvidia-experimental-310). I've seen several posts saying that this fixes problems, and it fixed problems for me too (but I didn't have your problem). 

You could also run nvidia-settings and turn the sync to vertical refresh off in case that's the issue. On my PC, doing that changes the frame rate to Ludicrous Speed.

---

### Post by Mr Kipling on 2013-02-19
I unchecked the sync to vblank option in nvidia settings and it is now working :-).

Thanks very much for your help, mu kids can now play minecraft and leave me alone.

---

