---
title: "No 3D Hardware Acceleration"
date: 2014-03-09
forum: Hardware
---

### Post by fadyfadlallah on 2014-03-09
Hello, 
I have a problem where I have no 3D hardware acceleration 
LIBGL_DEBUG=verbose glxinfo | grep -i -A 5 -B 5 directIt 
 
gave me:
name of display: :0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap,  
GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,
 
 no displays nor anything. What could be the problem ?

---

### Post by Mark Phelps on 2014-03-09
Run the following command "lspci", look for the line containing "VGA" and post the results back here.

Also, need to know what version of Ubuntu you are running.

---

