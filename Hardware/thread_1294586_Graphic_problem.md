---
title: "Graphic problem"
date: 2009-10-18
forum: Hardware
---

### Post by KriZo on 2009-10-18
Today i downlaoded the Football Manager 2010 demo, which should run in wine. Which it does, but only if I untick the "Allow Pixel Shader" in winecfg, which make FM lag.

If I haven't unticked the allow pixel shader, I get a black screen when I try to run Football Manager, and the folowing is what the terminal posts.

```
[email]kristoffer@kristoffer-laptop:~/.wine[/email]/drive_c/Program Files/Sports Interactive/Football Manager 2010 Demo$ wine fm.exe
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
ALSA lib pcm_dmix.c:1008:(snd_pcm_dmix_open) unable to open slave
fixme:powrprof:GetActivePwrScheme (0x32fb20) stub!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10032 0x00000000
fixme:win:EnumDisplayDevicesW ((null),0,0x305e374,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20034 0x00000000
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
```

I was able to run Football Manager 2009 under wine on ubuntu 9.04 without any problems. Currently i'm running 9.10.

This is my graphics .
```
kristoffer@kristoffer-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
```

---

