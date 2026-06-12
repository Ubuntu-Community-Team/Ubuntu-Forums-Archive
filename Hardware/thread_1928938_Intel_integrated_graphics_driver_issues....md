---
title: "Intel integrated graphics driver issues..."
date: 2012-02-21
forum: Hardware
---

### Post by LiteDrive on 2012-02-21
And I have no idea how to fix this. First off, I'll display my lspci for my vga controller:

    VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])

And then my glxinfo:

```

    name of display: :0
    display: :0  screen: 0
    direct rendering: Yes
    server glx vendor string: Brian Paul
    server glx version string: 1.4 Mesa 8.1-devel
    server glx extensions:
        GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
        GLX_MESA_release_buffers, GLX_ARB_get_proc_address, 
        GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
        GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
    client glx vendor string: Brian Paul
    client glx version string: 1.4 Mesa 8.1-devel
    client glx extensions:
        GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
        GLX_MESA_release_buffers, GLX_ARB_get_proc_address, 
        GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
        GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
    GLX version: 1.4
    GLX extensions:
        GLX_MESA_copy_sub_buffer, GLX_MESA_pixmap_colormap, 
        GLX_MESA_release_buffers, GLX_ARB_get_proc_address, 
        GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
        GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
    OpenGL vendor string: Brian Paul
    OpenGL renderer string: Mesa X11
    OpenGL version string: 2.1 Mesa 8.1-devel (git-6e738d3 oneiric-oibaf-ppa)
    OpenGL shading language version string: 1.20
```

Yet, when I try to render my window in GLUT, all I get is an invisible screen which the user can literally see through (with a window border around it). 

What is the issue behind this? When I try to do a glutInitContextVersion( 2, 0 ), I get the following error message:
```

    Mesa: Initializing x86-64 optimizations
    X Error of failed request:  BadRequest (invalid request code or no such operation)
      Major opcode of failed request:  34 (X_UngrabKey)
      Serial number of failed request:  33
      Current serial number in output stream:  33
```

How and why this is happening I have no idea. 

**My Code**

   ```
 void InitializeGlut( int winwidth, int winheight )
    {
    	glutInitContextVersion( 2, 0 );
    	glutInitWindowPosition( 0, 0 );
    	glutInitWindowSize( winwidth, winheight );
    
    	glutCreateWindow( "Engine C Lib Rendering Test" );
    
    	glutMainLoop();
    }
```

I already have glutInit() called in the main function, so I know it has nothing to do with that.


Is there any solution to this?

I think it may be because I did a distro upgrade and that caused me to download both ATI AND nVidia drivers, but I'm not sure...

---

