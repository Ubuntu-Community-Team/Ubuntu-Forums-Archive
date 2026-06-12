---
title: "Dazzle DVC 80"
date: 2010-02-01
forum: Hardware
---

### Post by NickCis on 2010-02-01
Hola, tengo una dazzle DVC 80 (usb). Y la verdad estoy mas perdido de como usarlo en linux =S.
Intente con el vlc pero la verdad cuando entro en "Abrir Aparato de Captura" ya no se que mas hacer. Dsp si hago mplayer tv:// me sale esto:
```

newpc@newpc:~$ mplayer tv://
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Dazzle Fusion Model DVC-80 Rev 
 Capabilites:  video capture  audio  read/write  streaming
 supported norms: 0 = NTSC; 1 = NTSC-M; 2 = NTSC-M-JP; 3 = NTSC-M-KR; 4 = PAL; 5 = PAL-BG; 6 = PAL-H; 7 = PAL-I; 8 = PAL-DK; 9 = PAL-M; 10 = SECAM; 11 = SECAM-B; 12 = SECAM-G; 13 = SECAM-H; 14 = SECAM-DK; 15 = SECAM-L; 16 = SECAM-Lc;
 inputs: 0 = Composite Video Input; 1 = S-Video Input;
 Current input: 0
 Current format: YVU420
Selected input hasn't got a tuner!
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 320x240 => 320x240 Planar YV12 
Selected video codec: [rawyv12] vfm: raw (RAW YV12)
==========================================================================
Audio: no sound
Starting playback...
V:   0.0  22/ 22 ??% ??% ??,?% 0 0 

```

Al parecer detecta bien la placa, pero me da una pantalla verde sin sonido =S.
Si pongo en consola lsusb me devulve esto:
```

newpc@newpc:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 07d0:0004 Dazzle DVC-800 (PAL) Grabber
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
newpc@newpc:~$ 

```

Alguna ayuda/idea?.
Saludos y gracias =p

---

### Post by NickCis on 2010-02-02
Alguna ayuda?

---

