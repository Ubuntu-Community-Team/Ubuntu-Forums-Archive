---
title: "Running after installing"
date: 2008-09-26
forum: General Help
---

### Post by Deten on 2008-09-26
I installed privateer gold which came as a *.bz2.bin with chmod then ./filename

It installed the game to ~/privateergold/

inside there are a bunch of .sh files, and when I double click them nothing happens, furthermore theres no launch program anywhere.  How do I get this game running?

Thanks

---

### Post by Deten on 2008-09-26
I discovered that to launch the game, I have to type "privgold" in terminal

this is the output

```
deten@deten-laptop:~$ privgold
a
b
c
Vega Strike  
See http://www.gnu.org/copyleft/gpl.html for license details.

GOT SUBDIR ARG = 
Found data in ..
Using /home/deten/privateerGold as data directory
Using .privgold100 as the home directory
Found MODDIR = /home/deten/privateerGold/mods
USING HOMEDIR : /home/deten/.privgold100 As the home directory 
CONFIGFILE - Found a config file in home directory, using : /home/deten/.privgold100/vegastrike.config
DATADIR - No datadir specified in config file, using ; /home/deten/privateerGold
SIMULATION_ATOM: 0.06
MISSION_NAME is empty using : main_menu.mission
Could not find platform independent libraries <prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
running import sys
print sys.path
sys.path = [r"/home/deten/privateerGold/modules/builtin/",r"/home/deten/privateerGold/modules/",r"/home/deten/privateerGold/bases/"]
['/usr/local/lib/python24.zip', '/usr/local/lib/python2.4/', '/usr/local/lib/python2.4/plat-linux2', '/usr/local/lib/python2.4/lib-tk', '/usr/lib/python2.4/lib-dynload']
testing VS randomrunning import sys
print sys.path
['/home/deten/privateerGold/modules/builtin/', '/home/deten/privateerGold/modules/', '/home/deten/privateerGold/bases/']
open /dev/[sound/]dsp: Device or resource busy
open /dev/[sound/]dsp: Device or resource busy
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7152767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb71528b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7cdf1bd]
#3 ./vegastrike(SDL_XF86VidModeQueryVersion+0x8f) [0x8b16cd7]
#4 ./vegastrike(X11_GetVideoModes+0x161) [0x8b158c1]
#5 ./vegastrike [0x8af1bb0]
#6 ./vegastrike(SDL_VideoInit+0x286) [0x8aee596]
#7 ./vegastrike(SDL_InitSubSystem+0x4b) [0x8ae6afb]
#8 ./vegastrike(SDL_Init+0x25) [0x8ae6bf5]
#9 ./vegastrike(winsys_init+0x6cd) [0x89a4f4d]
#10 ./vegastrike(GFXInit__FiPPc+0x1f) [0x8991927]
#11 ./vegastrike(Init__12GameUniverseiPPcPCc+0x25) [0x86d10a1]
#12 ./vegastrike(__12GameUniverseiPPcPCc+0x3a) [0x86d116e]
#13 ./vegastrike(main+0xed1) [0x89a6a7d]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d9c450]
#15 ./vegastrike [0x81b1851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7152767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb715281e]
#2 /usr/lib/libX11.so.6 [0xb7cde518]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb7cd4f70]
#4 ./vegastrike [0x8b15653]
#5 ./vegastrike(X11_GetVideoModes+0x407) [0x8b15b67]
#6 ./vegastrike [0x8af1bb0]
#7 ./vegastrike(SDL_VideoInit+0x286) [0x8aee596]
#8 ./vegastrike(SDL_InitSubSystem+0x4b) [0x8ae6afb]
#9 ./vegastrike(SDL_Init+0x25) [0x8ae6bf5]
#10 ./vegastrike(winsys_init+0x6cd) [0x89a4f4d]
#11 ./vegastrike(GFXInit__FiPPc+0x1f) [0x8991927]
#12 ./vegastrike(Init__12GameUniverseiPPcPCc+0x25) [0x86d10a1]
#13 ./vegastrike(__12GameUniverseiPPcPCc+0x3a) [0x86d116e]
#14 ./vegastrike(main+0xed1) [0x89a6a7d]
#15 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d9c450]
#16 ./vegastrike [0x81b1851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7152767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb71528b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7cdf1bd]
#3 ./vegastrike(SDL_XineramaIsActive+0x77) [0x8b1b433]
#4 ./vegastrike(X11_GetVideoModes+0x669) [0x8b15dc9]
#5 ./vegastrike [0x8af1bb0]
#6 ./vegastrike(SDL_VideoInit+0x286) [0x8aee596]
#7 ./vegastrike(SDL_InitSubSystem+0x4b) [0x8ae6afb]
#8 ./vegastrike(SDL_Init+0x25) [0x8ae6bf5]
#9 ./vegastrike(winsys_init+0x6cd) [0x89a4f4d]
#10 ./vegastrike(GFXInit__FiPPc+0x1f) [0x8991927]
#11 ./vegastrike(Init__12GameUniverseiPPcPCc+0x25) [0x86d10a1]
#12 ./vegastrike(__12GameUniverseiPPcPCc+0x3a) [0x86d116e]
#13 ./vegastrike(main+0xed1) [0x89a6a7d]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d9c450]
#15 ./vegastrike [0x81b1851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7152767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb715281e]
#2 /usr/lib/libX11.so.6 [0xb7cde518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb7cb4e76]
#4 ./vegastrike [0x8af1cdd]
#5 ./vegastrike(SDL_VideoInit+0x286) [0x8aee596]
#6 ./vegastrike(SDL_InitSubSystem+0x4b) [0x8ae6afb]
#7 ./vegastrike(SDL_Init+0x25) [0x8ae6bf5]
#8 ./vegastrike(winsys_init+0x6cd) [0x89a4f4d]
#9 ./vegastrike(GFXInit__FiPPc+0x1f) [0x8991927]
#10 ./vegastrike(Init__12GameUniverseiPPcPCc+0x25) [0x86d10a1]
#11 ./vegastrike(__12GameUniverseiPPcPCc+0x3a) [0x86d116e]
#12 ./vegastrike(main+0xed1) [0x89a6a7d]
#13 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d9c450]
#14 ./vegastrike [0x81b1851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7152767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb71528b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7cdf1bd]
#3 ./vegastrike(SDL_XF86VidModeGetGamma+0x94) [0x8b16f94]
#4 ./vegastrike [0x8b13d81]
#5 ./vegastrike(X11_SaveVidModeGamma+0x37) [0x8b13e23]
#6 ./vegastrike [0x8af1d68]
#7 ./vegastrike(SDL_VideoInit+0x286) [0x8aee596]
#8 ./vegastrike(SDL_InitSubSystem+0x4b) [0x8ae6afb]
#9 ./vegastrike(SDL_Init+0x25) [0x8ae6bf5]
#10 ./vegastrike(winsys_init+0x6cd) [0x89a4f4d]
#11 ./vegastrike(GFXInit__FiPPc+0x1f) [0x8991927]
#12 ./vegastrike(Init__12GameUniverseiPPcPCc+0x25) [0x86d10a1]
#13 ./vegastrike(__12GameUniverseiPPcPCc+0x3a) [0x86d116e]
#14 ./vegastrike(main+0xed1) [0x89a6a7d]
#15 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d9c450]
#16 ./vegastrike [0x81b1851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7152767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb715281e]
#2 /usr/lib/libX11.so.6 [0xb7cde518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb7cd5616]
#4 ./vegastrike [0x8af1775]
#5 ./vegastrike [0x8af1d8e]
#6 ./vegastrike(SDL_VideoInit+0x286) [0x8aee596]
#7 ./vegastrike(SDL_InitSubSystem+0x4b) [0x8ae6afb]
#8 ./vegastrike(SDL_Init+0x25) [0x8ae6bf5]
#9 ./vegastrike(winsys_init+0x6cd) [0x89a4f4d]
#10 ./vegastrike(GFXInit__FiPPc+0x1f) [0x8991927]
#11 ./vegastrike(Init__12GameUniverseiPPcPCc+0x25) [0x86d10a1]
#12 ./vegastrike(__12GameUniverseiPPcPCc+0x3a) [0x86d116e]
#13 ./vegastrike(main+0xed1) [0x89a6a7d]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d9c450]
#15 ./vegastrike [0x81b1851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7152767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb71528b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7cdf1bd]
#3 ./vegastrike(SDL_XF86VidModeQueryVersion+0x8f) [0x8b16cd7]
#4 ./vegastrike(SDL_XF86VidModeGetModeLine+0x5d) [0x8b17071]
#5 ./vegastrike [0x8b154c7]
#6 ./vegastrike(X11_EnterFullScreen+0x76) [0x8b16192]
#7 ./vegastrike [0x8af2919]
#8 ./vegastrike [0x8af2aca]
#9 ./vegastrike(SDL_SetVideoMode+0x1a5) [0x8aeed7d]
#10 ./vegastrike [0x89a45ad]
#11 ./vegastrike(winsys_init+0x752) [0x89a4fd2]
#12 ./vegastrike(GFXInit__FiPPc+0x1f) [0x8991927]
#13 ./vegastrike(Init__12GameUniverseiPPcPCc+0x25) [0x86d10a1]
#14 ./vegastrike(__12GameUniverseiPPcPCc+0x3a) [0x86d116e]
#15 ./vegastrike(main+0xed1) [0x89a6a7d]
#16 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d9c450]
#17 ./vegastrike [0x81b1851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7152767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb715281e]
#2 /usr/lib/libX11.so.6 [0xb7cde518]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb7cb4165]
#4 ./vegastrike(X11_EnterFullScreen+0xca) [0x8b161e6]
#5 ./vegastrike [0x8af2919]
#6 ./vegastrike [0x8af2aca]
#7 ./vegastrike(SDL_SetVideoMode+0x1a5) [0x8aeed7d]
#8 ./vegastrike [0x89a45ad]
#9 ./vegastrike(winsys_init+0x752) [0x89a4fd2]
#10 ./vegastrike(GFXInit__FiPPc+0x1f) [0x8991927]
#11 ./vegastrike(Init__12GameUniverseiPPcPCc+0x25) [0x86d10a1]
#12 ./vegastrike(__12GameUniverseiPPcPCc+0x3a) [0x86d116e]
#13 ./vegastrike(main+0xed1) [0x89a6a7d]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d9c450]
#15 ./vegastrike [0x81b1851]
vegastrike: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted
```

---

