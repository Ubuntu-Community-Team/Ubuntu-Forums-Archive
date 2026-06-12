---
title: "wine rants about different nVidia kernel modules"
date: 2008-10-31
forum: General Help
---

### Post by kung fu buntu on 2008-10-31
I'm trying to use VirtualDub in wine, but it's crashing when I open an .avi file.
> $ wine VirtualDub.exe
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:volume:GetVolumePathNameW (L"Z:\\...", 0x8abdf8, 260), stub!
fixme:commdlg:GetFileName95 Flags 0x00800000 not yet implemented
fixme:volume:GetVolumePathNameW (L"Z:\\...", 0x8b2ba0, 260), stub!
fixme:volume:GetVolumePathNameW (L"Z:\\...", 0x8b2d88, 260), stub!
fixme:volume:GetVolumePathNameW (L"Z:\\....", 0x8b2dc0, 260), stub!

Error: API mismatch: the NVIDIA kernel module has version 173.14.09,
but this NVIDIA driver component has version 100.14.11.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
Error: API mismatch: the NVIDIA kernel module has version 173.14.09,
but this NVIDIA driver component has version 100.14.11.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
fixme:win:EnumDisplayDevicesW ((null),0,0x32ee1c,0x00000000), stub!


I have a Debian amd64 system.
Kernel 2.6.26-1-amd64
nVidia drivers 173.14.09
wine 1.0.0-1.1


$ nvidia-settings -q NvidiaDriverVersion
Attribute 'NvidiaDriverVersion' (stardust:0.0): 173.14.09

$ glxinfo | grep -i rendering
direct rendering: Yes


Is there any way to check the version of my nvidia kernel module? There is the possibility that the problems lies there... but I REALLY doubt it...
modinfo didn't help


Thanks for any help.

---

### Post by kung fu buntu on 2008-11-05
bump ):P

---

