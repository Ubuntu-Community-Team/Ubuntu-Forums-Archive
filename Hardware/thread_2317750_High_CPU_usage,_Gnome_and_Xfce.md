---
title: "High CPU usage, Gnome and Xfce"
date: 2016-03-19
forum: Hardware
---

### Post by nigro.orlando on 2016-03-19
Hi! 
I recently installed xubuntu 15.10 and I also installed the kernel 4.4 since I had problems with my radeon r9 390 card and I read the the newest kernel should fix those problems. 
The problems were that the desktop froze suddenly giving me no choice then hard reboot, both with open source and proprietary drivers. I tried several things like different distributions and also debian Debian, where one of the problem was that the GPU:s fan was all the time on. 

Now I thought that I managed to solve the problem with the new kernel but it frooze again. I also noticed that now the GPU is not overheated and the fans aren't on but the CPU is overloaded, if I use Gnome, then gnome-shell takes 70-80% out of the CPU.
Same occurs in xfce where the process "xorg" takes up the 30%. Much better then Gnome yes, but still unusual. I have read several threads about similar issues but I couldn't find a solution.

This maybe can help:
```
glxinfo | grep render
direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
    GL_MESA_ycbcr_texture, GL_NV_blend_square, GL_NV_conditional_render, 


```

On xfce this is the result from Top:
```
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 6992 root      20   0  428792 192372  21896 S  22,6  0,6   2:31.58 Xorg        
 7826 orlando   20   0  770140  69096  58324 S   5,6  0,2   0:09.80 gnome-syst+ 
 8399 orlando   20   0  791184  27436  22520 S   1,3  0,1   0:00.45 xfce4-term+ 
 7607 orlando   20   0  253356  23840  18068 S   1,0  0,1   0:11.75 panel-10-w+ 
 7409 orlando   20   0  174616  21992  15944 S   0,7  0,1   0:06.03 xfwm4       
 8432 orlando   20   0   33372   3236   2632 R   0,7  0,0   0:00.04 top         
  110 root      20   0       0      0      0 S   0,3  0,0   0:00.88 kworker/6:1 
 7413 orlando   20   0  652732  23492  18504 S   0,3  0,1   0:00.32 xfce4-panel 
 7650 orlando   20   0  340416   6500   5636 S   0,3  0,0   0:00.04 indicator-+ 
 7877 orlando   20   0 1676860 441176  96344 S   0,3  1,3   2:34.65 firefox     
    1 root      20   0   33900   4512   2728 S   0,0  0,0   0:01.41 init        
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.00 kthreadd    
    3 root      20   0       0      0      0 S   0,0  0,0   0:00.01 ksoftirqd/0 
    5 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:+ 
    7 root      20   0       0      0      0 S   0,0  0,0   0:01.33 rcu_sched   
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh      
    9 root      rt   0       0      0      0 S   0,0  0,0   0:00.02 migration/0 

```

What should I do? Right now I'm using the open source drivers.


How do I edit the thread's title? I feel like is more then that.

---

### Post by Edison_James on 2016-03-19
You can ask a moderator to edit the thread title for you.

---

