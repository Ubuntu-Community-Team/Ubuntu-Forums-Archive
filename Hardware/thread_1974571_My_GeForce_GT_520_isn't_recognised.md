---
title: "My GeForce GT 520 isn't recognised"
date: 2012-05-06
forum: Hardware
---

### Post by Throne777 on 2012-05-06
Currently using the 'NVIDIA accelerated graphics driver (post-release updates) (version current-updates)'  in the additional drivers section. However, it isn't recognising my GeForce GT 520 card (Settings -> Graphics : Unknown). As such I'm not getting any 3D goodness and my card is going to waste.
Downloaded the latest off the NVIDIA website, but don't know how to kill X safely (other distros I'd either stop Slim or GDM, but Ubuntu isn't using either)
P.S. The other proprietary driver Ubuntu offers doesn't work either (Version current [recommended]).

---

### Post by Axxon95 on 2012-05-06
You should try this:

> 1st: Open Terminal and run "sudo add-apt-repository ppa:ubuntu-x-swat/x-updates"

2nd: Then run: "sudo apt-get purge nvidia*"
(to remove any unneeded nvidia packages that could interfere with the setup)

After that in the terminal type:
"sudo apt-get update"
then
"sudo apt-get install nvidia-current"

3rd: After it downloads the latest drivers and installs them, go to your Update Manager, refresh updates and get any Ubuntu-X team updates(then run "sudo nvidia-xconfig"), then restart.

You can run "sudo apt-get install mesa-utils", and then run "glxinfo | grep render" to see if they are correctly installed and supported.

---

### Post by Throne777 on 2012-05-07
> **Axxon95 said:**
> You should try this:



You can run "sudo apt-get install mesa-utils", and then run "glxinfo | grep render" to see if they are correctly installed and supported.

Followed everything, got the following:
```

throne777@theninthgate:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce GT 520/PCIe/SSE2
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, GL_OES_depth24, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
```

I assume that means everything is well and good?
If so, thanks :-)

---

### Post by Axxon95 on 2012-05-08
> **Throne777 said:**
> Followed everything, got the following:
```

throne777@theninthgate:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce GT 520/PCIe/SSE2
    GL_NV_conditional_render, GL_NV_copy_depth_to_color, GL_NV_copy_image, 
    GL_NV_parameter_buffer_object2, GL_NV_path_rendering, 
    GL_NVX_conditional_render, GL_NVX_gpu_memory_info, GL_OES_depth24, 
    GL_OES_fbo_render_mipmap, GL_OES_get_program_binary, GL_OES_mapbuffer, 
```I assume that means everything is well and good?
If so, thanks :-)

Yes, that looks as it should. No problem.

You can set the thread as Solved now. :)

---

### Post by mips on 2012-05-08
> **Throne777 said:**
> 
Downloaded the latest off the NVIDIA website, **but don't know how to kill X safely (other distros I'd either stop Slim or GDM, but Ubuntu isn't using either)**

Boot your system and login followed by Ctrl-Alt-F1 and execute **sudo service lightdm stop**

---

### Post by rodrigo.tufio on 2012-05-24
Hello, I could not run my card in Ubuntu 12.04 :( I have followed several instructions and so I have not yet achieved. My computer is a Dell XPS 14z and attached some information below:

```

rodrigo@dell:~$ uname -a
Linux dell 3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

rodrigo@dell:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520M] (rev a1)

rodrigo@dell:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1366x768       60.0*+   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)


```

It does not bother Unity 2D, but I urgently need to operate the Port MiniDisplay

Please help!

---

