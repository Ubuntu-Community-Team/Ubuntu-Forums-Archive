---
title: "msi GP62 6QE leopard with  ubuntu 15.10 and Intel/nvidia GPU not working"
date: 2016-03-15
forum: Hardware
---

### Post by Giulio_Rigoni on 2016-03-15
Hi...i know, there is a great number of post like mine, and i alredy read/tried every one of them...NO ONE WORKING FOR ME. So please, try help me make my notebook working cause i need it for university XD. (im not english, and i suck at english ..sry !! ) Rigth now i can use the notebook but i can use only the NVIDIA GPU, and  my battery last like 45 minuts and the notebook is really hot, as if plaing games. So i want make use of Intel gpu, i dont care about nvidia at all.

I started with nvidia-prime  coming from drivers like : 352-355-358-361.....no one works, all have the same xserver-settings control panel broken (see attachments). Plus using shell command : prime-select , i can only choose nvidia or nvidia-prime (so no nvidia and itel ) and only one of them works but 

I tried 3 different bumblebee guide but no one worked. After first reboot, i cant get past login .... only revory mode works !!

All standard approch doesnt works...i think i have some kind of "hidden" error or "weird" configuration .... dont know how to explain it better, cause following various guides i found missing .conf files or placed in wrong places O.o (im not a pro Ubuntu user, but i dont think this is normal >_> ). c

Here some shell outputs :
```

giulio@Giulio-Pc:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 191b (rev 06)


giulio@Giulio-Pc:~$ sudo lshw -c display
[sudo] password di giulio: 
  *-display UNCLAIMED     
       description: 3D controller
       product: GM107M [GeForce GTX 950M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:dd000000-ddffffff memory:b0000000-bfffffff ioport:f000(size=64)


giulio@Giulio-Pc:~$ lshw -c display | grep driver
WARNING: you should run this program as super-user.
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


giulio@Giulio-Pc:~$ glxinfo | grep render
direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_query_renderer, GLX_OML_swap_method, GLX_SGIS_multisample, 
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.7, 256 bits)
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth, 
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_depth_clamp, 



```


Thank you in advance ^^ !

---

