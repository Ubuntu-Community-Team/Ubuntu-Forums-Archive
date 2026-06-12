---
title: "Problem with graphic card"
date: 2017-11-03
forum: Hardware
---

### Post by samuele-zampini on 2017-11-03
Dear all,
I am Samuele. I am writing since I have some troubles with the graphic card.

I have a DELL Laptop, processor Intel i5, 4GB RAM, graphic card Intel Sandybridge Mobile and I have Ubuntu 16.04 installed.

It happens that when I am using the laptop (even if I am running the browser only) the laptop freezes for some seconds. I am pretty sure it is a matter of graphic card, since if - for example - I am writing a text, I don't see the the text on the screen, but some seconds later, everything appears.


Below the outputs of some commands:
```

lele@archimede:~$ lspci | grep -E 'VGA|Display'
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
lele@archimede:~$ sudo lshw -c display | grep driver
       configuration: driver=i915 latency=0
lele@archimede:~$ glxinfo | grep render
direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
Extended renderer info (GLX_MESA_query_renderer):
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
    GL_ARB_conditional_render_inverted, GL_ARB_copy_buffer, GL_ARB_copy_image, 
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_packed_depth_stencil, 
    GL_ARB_conditional_render_inverted, GL_ARB_copy_buffer, GL_ARB_copy_image, 
    GL_MESA_window_pos, GL_NV_blend_square, GL_NV_conditional_render, 
    GL_OES_element_index_uint, GL_OES_fbo_render_mipmap, 
lele@archimede:~$ glxinfo | grep "OpenGL version"
OpenGL version string: 3.0 Mesa 12.0.6
lele@archimede:~$ 

```


Can anyone help?
Thanks a lot,
Samuele

---

### Post by mörgæs on 2017-11-04
Hi, welcome to the fora.

Though Sandy Bridge is a semi-old processor Intel is still coding for it. I suggest that you try to see if the updated code solves the problem, for example by running a live boot of L/Xubuntu 17.10.

[https://www.phoronix.com/scan.php?page=news_item&px=Mesa-SNB-Gen6-FP64-RFC](https://www.phoronix.com/scan.php?page=news_item&px=Mesa-SNB-Gen6-FP64-RFC)

Your output shows OpenGL 3. According to the link you should be able to reach 4.


Tip of the hat to Intel for not abandoning customers who have bought a Sandy Brigde.

---

