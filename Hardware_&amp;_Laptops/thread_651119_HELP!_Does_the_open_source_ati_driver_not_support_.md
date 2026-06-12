---
title: "HELP! Does the open source ati driver not support opengl?"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by CHNdonny on 2007-12-27
a problem occurred when i was launching the game  --- etqw
it showed  ------- Initializing renderSystem --------
----- R_InitOpenGL -----
...using GL_ARB_multitexture
...using GL_ARB_texture_cube_map
X..GL_ARB_texture_non_power_of_two not found
...using GL_ARB_texture_compression
X..GL_EXT_texture_compression_s3tc not found
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
X..GL_EXT_texture_lod not found
X..GL_1.4_texture_lod_bias not found
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_ARB_texture_rectangle
...using GL_EXT_texture_rectangle
...using GL_EXT_stencil_wrap
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
X..GL_EXT_depth_bounds_test not found
X..GL_ARB_point_sprite not found
X..GL_ARB_occlusion_query not found
X..GL_EXT_framebuffer_object not found
X..GL_EXT_packed_depth_stencil not found
...using GL_EXT_blend_minmax
...using GL_ARB_multisample
X..GL_ARB_shader_objects not found
X..GL_ARB_vertex_shader not found
X..GL_ARB_fragment_shader not found
X..GL_ARB_fragment_program_shadow not found
X..GL_ARB_shadow not found
X..GL_ARB_depth_texture not found
...using GL_EXT_gpu_program_parameters
0x0
[0x082d1151]
[0x0819e8bf]
[0x0810a1b4]
[0x0810aadf]
[0x0819c86c]
[0x0819ce12]
[0x0819cfee]
[0x083f60ce]
[0xb7b89ebc]
[0x0804c8b1]
********************
ERROR: The current video card / driver combination does not support the necessary features: GL_ARB_occlusion_query
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
Sys_Error: Error during initialization

which indicated my open source ati driver doesn't support opengl

but the restricted driver seems not to run my compiz-fusion well

Is there any good method can be used to make the open source ati driver support opengl

or Is there any method can be used to make etqw and compiz-fusion co-exist

it is appreciated if you can help me

---

### Post by zhouxing on 2007-12-27
Have you tried Envy?

[HTML]http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu4_all.deb[/HTML]

---

### Post by CHNdonny on 2007-12-28
i dont mean i cant install ati driver.   i mean the xgl cant works well under the restricted driver

---

### Post by Yellow Pasque on 2007-12-28
It might mean that the open-source driver doesn't support that particular function of OpenGL (GL_ARB_occlusion_query). Personally, I value functionality over eye candy, so I would use the restricted drivers and forget about the Compiz stuff, but that's just my opinion. You may feel differently.

---

### Post by CHNdonny on 2007-12-28
Temüjin  , thank you for your opinion . i dont know which is the important . maybe two both have the   problem . the game is always down . when i have played several minutes. and the xgl cant run well under the restricted driver

---

