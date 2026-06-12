---
title: "VIA Chrome9 drivers and glxinfo crash (8.04)"
date: 2009-01-21
forum: Hardware
---

### Post by ijb99 on 2009-01-21
Hi,

I'm using Ubuntu Server 8.04 and I'm having trouble getting 3D acceleration working on an Epia SN board with Chrome 9 integrated graphics.

I installed the OpenChrome driver but had no luck (I think it doesn't yet support Chrome 9), so I tried using the patches provided by VIA at [http://linux.via.com.tw/support](http://linux.via.com.tw/support).

After following the instructions in the patch archive I ended up with via_chrome9 and drm modules which load without error.  Unfortunately, while I can run glxgears (at 135 fps - a speed which was reached with the OpenChrome driver) I can't run glxinfo without a crash:

Program received signal SIGSEGV, Segmentation fault.
0xb7d5a9bc in memcpy () from /lib/tls/i686/cmov/libc.so.6
(gdb) bt
#0  0xb7d5a9bc in memcpy () from /lib/tls/i686/cmov/libc.so.6
#1  0xaf47391e in _mesa_initialize_context (ctx=0x84b6850, visual=0x18,
    share_list=0x0, driverFunctions=0xbfa0da4c, driverContext=0x84b6840)
    at context.c:1069
#2  0xaf5c00a0 in XMesaCreateContext (v=0x18, share_list=0x0) at xm_api.c:1504
#3  0xb7b9c10c in __glXMesaScreenCreateContext (screen=0x828a4e8,
    modes=0x843c898, baseShareContext=0x0) at ../../../GL/glx/glxglcore.c:246
#4  0xb7b998ff in DoCreateContext (cl=0x843e4e8, gcId=27262979, shareList=0,
    visual=72, screen=0, isDirect=0 '\0') at ../../../GL/glx/glxcmds.c:206
#5  0xb7b99af4 in __glXDisp_CreateContext (cl=0x843e4e8,
    pc=0x842ea08 "*\003\006") at ../../../GL/glx/glxcmds.c:249
#6  0xb7b9b996 in __glXDispatch (client=0x843c658)
    at ../../../GL/glx/glxext.c:561
#7  0x081506ee in XaceCatchExtProc (client=0x843c658) at ../../Xext/xace.c:299
#8  0x0808d8df in Dispatch () at ../../dix/dispatch.c:502
#9  0x0807471b in main (argc=3, argv=0xbfa0e374, envp=Cannot access memory at address 0x3c
) at ../../dix/main.c:452

I'm guessing glxgears is still running in software and glxinfo crashes on trying to use the hardware.

Looking on the forums other people seem to have problems with OpenChrome as well.

- Has anyone managed to get the VIA-provided drivers to work?
- Is there any 3D code in X that would need rebuilding after the VIA patches?

Iain

---

