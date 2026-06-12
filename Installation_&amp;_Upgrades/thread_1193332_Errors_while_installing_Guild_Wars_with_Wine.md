---
title: "Errors while installing Guild Wars with Wine"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by brossartr1 on 2009-06-21
Hello, I'm kind of inexperienced with Linux. I've only been using it for a couple of years (mostly in class). I just installed it on my new desktop and am trying to get Guild Wars working on it. Can anybody help me to troubleshoot these issues? The download screen pops up and starts downloading, but then these errors come up in the terminal and the download screen disappears. Thanks for your help. Ryan

root@ryan-desktop:/home/ryan# wine ./GwSetup.exe 
fixme:shdocvw:IEParseDisplayNameWithBCW stub: 0x0 L"http://www.guildwars.com" 0x147010 0x33f5cc
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:shdocvw:IEParseDisplayNameWithBCW stub: 0x0 L"http://www.guildwars.com/support/support.html" 0x13a100 0x33f5cc
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:shell:DllCanUnloadNow stub
root@ryan-desktop:/home/ryan# fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D9 is not available without opengl
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D8 is not available without opengl
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D8 is not available without opengl
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D9 is not available without opengl
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D8 is not available without opengl
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D8 is not available without opengl
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.

---

### Post by brossartr1 on 2009-06-21
Does anyone have any ideas?

---

### Post by brossartr1 on 2009-06-23
Please assist? :(

---

### Post by aihtdikh on 2009-08-24
Hi brossartr1

I see that it's been a few months, but in case it still might help you (or other googlers) :

This looks like you do not have 3D-hardware drivers installed (the "Xlib:  extension "GLX" missing" error).
Have a look at the install instructions at
[https://help.ubuntu.com/.../Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Installation")  for NVidia cards, or
[https://help.ubuntu.com/.../ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20Ubuntu%20repositories%20%28easier%29")   for ATI cards.

If :
*  you do already have the 3D drivers installed and native Linux 3D games work; and
*  you're running a 64bit version of Linux;
then the "err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat" problem
happens if you don't have the 32bit drivers installed as well.
On Debian and (I presume) Ubuntu, the package required to fix this is nvidia-glx-ia32 for nvidia cards, or fglrx-glx-ia32 for ATI cards.

---

### Post by Mark Phelps on 2009-08-25
Caution! If you're using an ATI card DO NOT force the installation of fglrx drivers!  Unless you have one of the new HD 3x or HD 4x series, forcing that driver will result in no video on your machine.

---

