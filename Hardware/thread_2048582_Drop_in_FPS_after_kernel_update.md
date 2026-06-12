---
title: "Drop in FPS after kernel update"
date: 2012-08-26
forum: Hardware
---

### Post by finitybeyond on 2012-08-26
I am running Ubuntu 12.04 x86_64 with the latest nvidia-current drivers (304.37). After updating the kernel from 3.2.0-32 to 3.2.0-39, I noticed a very significant drop in graphics performance. Unity 3D still works, but the FPS is noticeably lower. Before the upgrade, the fps count in glxgears was consistently in the 11200 fps ballpark. However, after upgrading, glxgears only rendered around 60 fps and output:

```

Running synchronized to the vertical refresh. The framerate should be approximately the same as the monitor refresh rate.
299 frames in 5.0 seconds = 59.690 FPS
300 frames in 5.0 seconds = 59.953 FPS
...

```

Yes, knowing that glxgears is not a benchmark, I also installed the Phoronix Test Suite and ran the Lightsmark benchmark which, to my dismay, also only ran around 60 FPS.

I also tried to reinstall the nvidia driver so that it would be built against the 3.2.0-29 kernel:

```

sudo apt-get remove --purge nvidia-current nvidia-settings
sudo apt-get install nvidia-current nvidia-settings
nvidia-xconfig

```

But I am still getting 60 FPS. Is there something that is preventing the graphics card from pushing more frames than 60 FPS?

My card is NVIDIA GeForce GTX 680. Some more info:

```

$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1180 (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 0e0a (rev a1)

$ glxinfo | grep -i direct
direct rendering: Yes
    GL_AMD_multi_draw_indirect, GL_AMD_seamless_cubemap_per_texture
    GL_ARB_draw_indirect, GL_ARB_draw_elements_base_vertex,
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_direct_state_access,

```

---

### Post by Yellow Pasque on 2012-08-27
> Running synchronized to the vertical refresh. The framerate should be approximately the same as the monitor refresh rate.

Don't worry about the glxgears numbers. 60 fps means vsync is turned on (60fps = monitor is 60Hz) to prevent tearing. That is probably what you want.

If you're curious about the number without vsync, disable vsync in the nvidia control panel (but you probably don't want to leave that off).

---

