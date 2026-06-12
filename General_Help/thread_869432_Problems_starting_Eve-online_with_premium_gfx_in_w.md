---
title: "Problems starting Eve-online with premium gfx in wine"
date: 2008-07-24
forum: General Help
---

### Post by UbFido on 2008-07-24
ey guys.
I just got Ubuntu on my machine again cause i got sick and tired of vista :P
 - I got sad when i saw that they only have the linux client working with normal gfx but googled and found out that lots of ppl are running premium under wine.

So i decided to do so..

Installation of EvE went smooth, no problems there.

But on startup, the splashscreen shows (woot) and then the screen blinks black one time, returns to the desktop BUT with the EvE cursor and eve blocking the desktop. i have to turn to a new desktop area and terminate the eve process to get it away...

I ran it in terminal and got:

```
zeiler@Liderbamsen:~/.wine/drive_c/Program Files/CCP/EVE$ wine eve.exe
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8d7, disabling mixer
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
err:threadpool:iocp_poller NtRemoveIoCompletion failed: 0xc0000008
fixme:win:EnumDisplayDevicesW ((null),0,0x33ad84,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3554
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x30026 0x00000000
fixme:imm:ImmReleaseContext (0x30026, 0x1427c0): stub
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
fixme:d3d_surface:IWineD3DSurfaceImpl_BltOverride >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ surface.c / 3345
wine: Unhandled page fault on execute access to 0x7c093e48 at address 0x7c093e48 (thread 001a), starting debugger...
zeiler@Liderbamsen:~/.wine/drive_c/Program Files/CCP/EVE$
```

Any ideas ppl?

Running Ubuntu Hardy Heron x64 on:

Processors: AMD Athlon 64 X2 Dual Core Processor 6400+
GFX card: Asus EAH3870top

- UbFido

---

### Post by UbFido on 2008-07-25
Anyone?

---

### Post by UbFido on 2008-07-25
Noone? ...

---

### Post by deep.tinker77 on 2008-07-25
Hiya, I also recently installed EVE on my lappy. Did you install the 32 bit dependancies? And also check out this thread on the subject. Good luck.

[http://ubuntuforums.org/showthread.php?t=860807&highlight=Eve+online](http://ubuntuforums.org/showthread.php?t=860807&highlight=Eve+online)

---

