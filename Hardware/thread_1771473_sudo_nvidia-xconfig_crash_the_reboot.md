---
title: "sudo nvidia-xconfig crash the reboot"
date: 2011-05-30
forum: Hardware
---

### Post by fred_gavin on 2011-05-30
Dear All, 

My installation of Ubuntu 11.04 didin't come up with Unity desktop as nvidia driver installed with the installation.  So when I tried to configure resolution, etc, , 
the message appeared: you are not to be using nvidia x driver (edit nvidia-xconfi and restart x server). 

So when I did "sudo nvidia-xconfig" and restart x by ctrl+alt+blackspace, then it freezed in a blank black window. 

I reboot the computer, the normal reboot didn't work, so I have to reboot through recovery mode via failsafe graphic model to reconfigure graphics first.

That's basically the problem I encountered. Even I removed nvidia and re-installed, the problem is exact the same. 

So I removed all nvidia, including the one in the additional driver. This time Unity back. As checked, xserver-xorg-video-nouveau is still there. Is that the major support for the unity desktop? 

Now my question is:

---

### Post by fred_gavin on 2011-05-30
Now my question is: 

I am using Thinkpad T520 with 15.6 FHD(1920x1080(16:9)) screen. And graphics is NVIDIA Quadro NVS4200M Optimus (1GB). 

If set up the full 1920x1080 resolution, everything is small (font size can change, I know, but there are others still remains small). The "Monitor" setting only provides 1920X1080 and  1360X768 that I can use for 16:9 screen.  The former too small, the later seems OK, but web pages make me eye uncomfortable. 

Is there anyone know how I can set up resolution or refresh rate that could utilise 1920X1080 while maintaining font, icon, or everything in a normal size ? 

Thank you very much.

---

