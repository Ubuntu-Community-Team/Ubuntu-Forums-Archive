---
title: "Ubuntu 8.04 no puede reproducir .avi y se cuelga"
date: 2009-07-21
forum: Hardware
---

### Post by donmatas on 2009-07-21
Estimad@s:

adquirí un dell 15. Lo primero que hice fue instalarle jaunty, pero tuve que buscar otra alternativa, pues no funcionaba bien el audio (estaba muy despacio y no capturaba sonido). Instalé un viejo conocido 8.04. Hasta aquí todo bien, pero hoy intenté ver una película en .avi y simplemente se cuelga. Pensé que podía ser awn o los efectos del compiz, pero no es eso, porque intenté reproducirlo en una sesión de invitado y también se colgó. No sé qué hacer. He googleado la solución pero no encuentro nada:confused: Lo peor es que me obliga a resetear

lanzo un lspci para que le den un vistazo

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

pd: como se llega a este foro desde la página principal?

---

### Post by Patriciologico on 2009-07-22
¿Que reproductor estas usando? lanza el reproductor desde un terminal y cuando este reproduciendo ve que mensajes lanza. Ademas revisa los sucesos del sistema en el menu sistema/administracion. De ahi lograras mas datos para que sea mas facil encontrar la solucion.

Saludos.

Pd:Ubuntu Forums > The Ubuntu Forum Community > Other Community Discussions > Ubuntu LoCo Team Forums > International LoCo Teams > Chile Team

---

### Post by donmatas on 2009-07-23
Gracias patricio por tu respuesta.

la situación acontecía con cualquier reproducto (vlc, mplayer y totem). Solucioné parcialmente el asunto desinstalando vlc y totem y confiurando mplayer de la siguiente manera:

fui preferencias y en la solapa video desmarqué el driver xv x11/xv y marqué el Gl2 x11 (openGL) mutitexture-video.

esto me permite ver avi, pero mplayer no se comporta muy bien (al apretar botón derecho para desplegar los comandos todo tirita y es dificil de operar). 

ahora lo lanzo de un terminal y me manda esto:

matias@matias-laptop:~$ gmplayer
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz (Family: 6, Model: 23, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/matias/Vídeos/25th Hour (2002)/25th Hour (2002).avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  608x256  12bpp  25.000 fps  592.0 kbps (72.3 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.4.1 (build 2178/release)
SUB: Detected subtitle file format: subviewer
SUB: Read 1612 subtitles.
SUB: Added subtitle file (1): /home/matias/Vídeos/25th Hour (2002)/25th Hour (2002).srt
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 608 x 256 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.38:1 - prescaling to correct movie aspect.
[swscaler @ 0x89348f0]SwScaler: using unscaled yuv420p -> bgr24 special converter
VO: [gl2] 608x256 => 608x256 BGR 24-bit 
[gl2] You have OpenGL >= 1.2 capable drivers, GOOD (16bpp and BGR is ok!)
[gl2] antialiasing off
[gl2] bilinear linear
A:   2.3 V:   2.0 A-V:  0.217 ct:  0.028  52/ 52  9% 83%  1.5% 36 0             
GNOME screensaver enabled

Playing /home/matias/Vídeos/25th Hour (2002)/25th Hour (2002).avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  608x256  12bpp  25.000 fps  592.0 kbps (72.3 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.4.1 (build 2178/release)
SUB: Detected subtitle file format: subviewer
SUB: Read 1612 subtitles.
SUB: Added subtitle file (1): /home/matias/Vídeos/25th Hour (2002)/25th Hour (2002).srt
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 608 x 256 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 2.38:1 - prescaling to correct movie aspect.
VO: [gl2] 608x256 => 608x256 BGR 24-bit 
[gl2] You have OpenGL >= 1.2 capable drivers, GOOD (16bpp and BGR is ok!)
[gl2] antialiasing off
[gl2] bilinear linear
A:   2.2 V:   1.6 A-V:  0.676 ct:  0.064  40/ 40  8% 101%  1.8% 31 0            
GNOME screensaver enabled

Exiting... (Quit)

---

### Post by lokiju on 2009-09-27
No tengo mucha información sobre el asunto sólo que en los últimos días empecé a tener el mismo problema. Pensé que podría ser algún problema con algún codec asi que procedí a instalar los restringidos con:

sudo aptitude install ubuntu-restricted-extras

En mi caso funcionó. Sé que no es una solución muy ortodoxa pero por probar...

---

