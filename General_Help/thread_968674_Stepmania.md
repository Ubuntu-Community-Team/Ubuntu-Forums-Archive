---
title: "Stepmania"
date: 2008-11-02
forum: General Help
---

### Post by Qloor on 2008-11-02
Hey guys, I'm trying to get StepMania 3.9 up and running on Ubuntu 8.10. When I try to run ./stepmania I get the song loading screen and the following output in my Terminal window (don't mind the random song errors and such, they're not the cause of the problem):

```
drew@Drew-MacBook:~/Desktop/StepMania$ ./stepmania
StepMania 3.9
Log starting 2008-11-02 23:02:37
Loading window: gtk
OS: Linux ver 020627
Crash backtrace component: x86 custom backtrace
Crash lookup component: dladdr
Crash demangle component: cxa_demangle
Runtime library: glibc 2.8.90
Threads library: NPTL 2.8.90
TLS is available
ALSA: Advanced Linux Sound Architecture Driver Version 1.0.17.
ALSA Driver: 0: HDA Intel [Intel], device 0: ALC885 Analog [ALC885 Analog], 1/1 subdevices avail
ALSA Driver: 0: HDA Intel [Intel], device 1: ALC885 Digital [ALC885 Digital], 1/1 subdevices avail
Couldn't load driver ALSA: Not enough substreams for hardware mixing, using software mixing
ALSA: Software mixing at 44100hz
Sound driver: ALSA-sw
/////////////////////////////////////////
WARNING: Couldn't find any SM, DWI, BMS, or KSF files in 'Songs/SMGpack 2/This Is Sensation (Dj_Ossa)/'.  This is not a valid song directory.
/////////////////////////////////////////

(stepmania:370): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
Video renderers: 'opengl'
The program 'stepmania' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 11 error_code 1 request_code 143 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb799e7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb799e96e]
#2 /usr/lib/libX11.so.6 [0xb7ebf619]
#3 /usr/lib/libX11.so.6(XSync+0x25) [0xb7eb3625]
#4 /usr/lib/libSDL-1.2.so.0 [0xb7fbfb25]
#5 /usr/lib/libSDL-1.2.so.0 [0xb7fc8bbb]
#6 /usr/lib/libSDL-1.2.so.0(SDL_VideoQuit+0x50) [0xb7fb6940]
#7 /usr/lib/libSDL-1.2.so.0(SDL_QuitSubSystem+0x55) [0xb7f8b7d5]
#8 /usr/lib/libSDL-1.2.so.0(SDL_Quit+0x1e) [0xb7f8b85e]
#9 /lib/tls/i686/cmov/libc.so.6(exit+0x89) [0xb7b1cd69]
#10 /usr/lib/libgdk-x11-2.0.so.0 [0xb6d656b7]
#11 /usr/lib/libSDL-1.2.so.0 [0xb7fc84f6]
#12 /usr/lib/libX11.so.6(_XError+0x109) [0xb7eb7ef9]
#13 /usr/lib/libX11.so.6(_XReply+0x22e) [0xb7ec046e]
#14 /usr/lib/libGL.so.1 [0xb7e44337]
#15 /usr/lib/libGL.so.1 [0xb7e25ab4]
#16 /usr/lib/libGL.so.1(glXChooseVisual+0x37) [0xb7e22b97]
#17 /usr/lib/libSDL-1.2.so.0 [0xb7fc4ce1]
#18 /usr/lib/libSDL-1.2.so.0 [0xb7fcb046]
#19 /usr/lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1f0) [0xb7fb7900]
Segmentation fault

```

Any help?

---

### Post by Qloor on 2008-11-02
Also, any help on installing libavcodec1d would be appreciated.

---

