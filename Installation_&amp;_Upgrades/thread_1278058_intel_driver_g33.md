---
title: "intel driver g33"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by linkingeek on 2009-09-29
please help i have intel g33 ,i downloaded "xf86-video-intel-2.8.1" and tried to install driver and received following errors(earlier ubuntu installed a xserver.xorg driver for i8xx,i9xx through updates)
- i used "  	 	 	 	 	[SIZE=4].[/SIZE]/configure 	--prefix=/usr  	 "command to configure
dolphin@ubuntu:~/Desktop/xf86-video-intel-2.8.1$ make install –directory ~/Desktop/xf86-video-intel-2.8.1
Making install in uxa
Making install in src
Making install in xvmc
Making install in shader
Making install in mc
Making install in vld
  CC    I810XvMC.o
In file included from I810XvMC.c:52:
I810XvMC.h:89: error: expected specifier-qualifier-list before ‘drm_handle_t’
I810XvMC.h:103: error: expected specifier-qualifier-list before ‘drm_context_t’
I810XvMC.h:147: error: expected specifier-qualifier-list before ‘drm_handle_t’
I810XvMC.h:167: error: expected specifier-qualifier-list before ‘drm_handle_t’
I810XvMC.c: In function ‘i810_free_privContext’:
I810XvMC.c:94: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:94: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c:94: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:97: error: ‘i810XvMCContext’ has no member named ‘ref’
I810XvMC.c:98: error: ‘i810XvMCContext’ has no member named ‘ref’
I810XvMC.c:100: error: ‘i810XvMCDrmMap’ has no member named ‘address’
I810XvMC.c:100: error: ‘i810XvMCDrmMap’ has no member named ‘size’
I810XvMC.c:101: error: ‘i810XvMCDrmMap’ has no member named ‘address’
I810XvMC.c:101: error: ‘i810XvMCDrmMap’ has no member named ‘size’
I810XvMC.c:108: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:108: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:108: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c: In function ‘XvMCCreateContext’:
I810XvMC.c:199: error: ‘i810XvMCContext’ has no member named ‘xv_colorkey’
I810XvMC.c:200: error: ‘i810XvMCContext’ has no member named ‘xv_colorkey’
I810XvMC.c:203: error: ‘i810XvMCContext’ has no member named ‘xv_colorkey’
I810XvMC.c:204: error: ‘i810XvMCContext’ has no member named ‘colorkey’
I810XvMC.c:208: error: ‘i810XvMCContext’ has no member named ‘xv_brightness’
I810XvMC.c:209: error: ‘i810XvMCContext’ has no member named ‘xv_saturation’
I810XvMC.c:210: error: ‘i810XvMCContext’ has no member named ‘xv_contrast’
I810XvMC.c:211: error: ‘i810XvMCContext’ has no member named ‘brightness’
I810XvMC.c:212: error: ‘i810XvMCContext’ has no member named ‘saturation’
I810XvMC.c:213: error: ‘i810XvMCContext’ has no member named ‘contrast’
I810XvMC.c:252: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c:253: error: ‘i810XvMCContext’ has no member named ‘fb_base’
I810XvMC.c:254: error: ‘i810XvMCDrmMap’ has no member named ‘offset’
I810XvMC.c:255: error: ‘i810XvMCDrmMap’ has no member named ‘size’
I810XvMC.c:256: error: ‘i810XvMCDrmMap’ has no member named ‘offset’
I810XvMC.c:257: error: ‘i810XvMCDrmMap’ has no member named ‘size’
I810XvMC.c:258: error: ‘i810XvMCContext’ has no member named ‘busIdString’
I810XvMC.c:259: error: ‘i810XvMCContext’ has no member named ‘busIdString’
I810XvMC.c:265: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:266: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:267: error: ‘i810XvMCContext’ has no member named ‘last_flip’
I810XvMC.c:268: error: ‘i810XvMCContext’ has no member named ‘dual_prime’
I810XvMC.c:294: error: ‘i810XvMCDrmMap’ has no member named ‘offset’
I810XvMC.c:295: error: ‘i810XvMCDrmMap’ has no member named ‘size’
I810XvMC.c:295: error: ‘i810XvMCDrmMap’ has no member named ‘address’
I810XvMC.c:297: error: ‘i810XvMCDrmMap’ has no member named ‘offset’
I810XvMC.c:297: error: ‘i810XvMCDrmMap’ has no member named ‘size’
I810XvMC.c:305: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:306: error: ‘i810XvMCDrmMap’ has no member named ‘address’
I810XvMC.c:309: error: ‘i810XvMCDrmMap’ has no member named ‘offset’
I810XvMC.c:310: error: ‘i810XvMCDrmMap’ has no member named ‘size’
I810XvMC.c:310: error: ‘i810XvMCDrmMap’ has no member named ‘address’
I810XvMC.c:323: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:323: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c:323: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:327: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:328: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:329: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:330: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:331: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:332: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:334: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:335: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:337: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:339: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:340: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:341: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:342: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:345: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:345: error: ‘i810XvMCContext’ has no member named ‘colorkey’
I810XvMC.c:345: error: ‘i810XvMCContext’ has no member named ‘colorkey’
I810XvMC.c:345: error: ‘i810XvMCContext’ has no member named ‘colorkey’
I810XvMC.c:346: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:349: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:350: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:351: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:352: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:354: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:357: error: ‘i810XvMCContext’ has no member named ‘ref’
I810XvMC.c:359: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:359: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:359: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c: In function ‘XvMCDestroyContext’:
I810XvMC.c:387: error: ‘i810XvMCContext’ has no member named ‘last_flip’
I810XvMC.c:388: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:388: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c:388: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:391: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:393: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:395: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:395: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:396: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:397: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:400: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:403: error: ‘i810XvMCContext’ has no member named ‘last_flip’
I810XvMC.c:406: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:408: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:408: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:408: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c: In function ‘XvMCCreateSurface’:
I810XvMC.c:449: error: ‘i810XvMCSurface’ has no member named ‘privContext’
I810XvMC.c:473: error: ‘i810XvMCDrmMap’ has no member named ‘address’
I810XvMC.c:474: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:474: error: ‘i810XvMCDrmMap’ has no member named ‘offset’
I810XvMC.c:493: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:494: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:501: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:502: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:506: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:507: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:511: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:511: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:513: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:523: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:530: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:531: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:533: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:534: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:536: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:537: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:553: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:554: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:555: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:556: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:557: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:558: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:564: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:565: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:578: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:579: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:582: error: ‘i810XvMCContext’ has no member named ‘ref’
I810XvMC.c: In function ‘XvMCDestroySurface’:
I810XvMC.c:606: error: ‘i810XvMCSurface’ has no member named ‘privContext’
I810XvMC.c: In function ‘dispatchYContext’:
I810XvMC.c:989: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:990: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c: In function ‘XvMCRenderSurface’:
I810XvMC.c:2490: error: ‘i810XvMCContext’ has no member named ‘dual_prime’
I810XvMC.c:2521: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:2521: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c:2521: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:2547: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:2548: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:2561: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:2562: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:2579: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:2580: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:2652: error: ‘i810XvMCContext’ has no member named ‘dual_prime’
I810XvMC.c:2653: error: ‘i810XvMCContext’ has no member named ‘dual_prime’
I810XvMC.c:2672: error: ‘i810XvMCContext’ has no member named ‘dual_prime’
I810XvMC.c:2674: error: ‘i810XvMCContext’ has no member named ‘dual_prime’
I810XvMC.c:2762: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:2763: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:2770: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:2771: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:2778: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:2779: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:2783: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:2783: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:2783: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c: In function ‘XvMCPutSurface’:
I810XvMC.c:2856: error: ‘i810XvMCSurface’ has no member named ‘privContext’
I810XvMC.c:2857: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:3092: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:3092: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c:3092: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:3100: error: ‘i810XvMCContext’ has no member named ‘last_flip’
I810XvMC.c:3101: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3104: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3104: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3127: error: ‘i810XvMCContext’ has no member named ‘contrast’
I810XvMC.c:3128: error: ‘i810XvMCContext’ has no member named ‘brightness’
I810XvMC.c:3129: error: ‘i810XvMCContext’ has no member named ‘saturation’
I810XvMC.c:3132: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:3132: error: ‘i810XvMCContext’ has no member named ‘colorkey’
I810XvMC.c:3132: error: ‘i810XvMCContext’ has no member named ‘colorkey’
I810XvMC.c:3132: error: ‘i810XvMCContext’ has no member named ‘colorkey’
I810XvMC.c:3135: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3136: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:3137: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:3138: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:3139: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:3140: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:3141: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:3144: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:3145: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:3146: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:3147: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:3148: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:3149: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:3164: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3178: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3193: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3218: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3237: error: ‘i810XvMCContext’ has no member named ‘last_flip’
I810XvMC.c:3239: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3246: error: ‘i810XvMCContext’ has no member named ‘last_flip’
I810XvMC.c:3247: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:3247: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:3247: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c: In function ‘XvMCGetSurfaceStatus’:
I810XvMC.c:3317: error: ‘i810XvMCSurface’ has no member named ‘privContext’
I810XvMC.c:3322: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:3322: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c:3322: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:3325: error: ‘i810XvMCContext’ has no member named ‘last_flip’
I810XvMC.c:3333: error: ‘i810XvMCContext’ has no member named ‘last_flip’
I810XvMC.c:3338: error: ‘i810XvMCContext’ has no member named ‘last_flip’
I810XvMC.c:3347: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3358: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:3358: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:3358: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c: In function ‘XvMCHideSurface’:
I810XvMC.c:3412: error: ‘i810XvMCSurface’ has no member named ‘privContext’
I810XvMC.c:3417: error: ‘i810XvMCContext’ has no member named ‘last_flip’
I810XvMC.c:3418: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:3418: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c:3418: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:3421: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3424: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:3426: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3426: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3427: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3428: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:3431: error: ‘i810XvMCContext’ has no member named ‘oregs’
I810XvMC.c:3438: error: ‘i810XvMCContext’ has no member named ‘last_flip’
I810XvMC.c:3442: error: ‘i810XvMCContext’ has no member named ‘current’
I810XvMC.c:3444: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:3444: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:3444: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c: In function ‘XvMCCreateSubpicture’:
I810XvMC.c:3524: error: ‘i810XvMCDrmMap’ has no member named ‘address’
I810XvMC.c:3525: error: ‘i810XvMCSubpicture’ has no member named ‘offset’
I810XvMC.c:3525: error: ‘i810XvMCDrmMap’ has no member named ‘offset’
I810XvMC.c:3528: error: ‘i810XvMCSubpicture’ has no member named ‘privContext’
I810XvMC.c:3549: error: ‘i810XvMCSubpicture’ has no member named ‘offsets’
I810XvMC.c:3550: error: ‘i810XvMCSubpicture’ has no member named ‘offsets’
I810XvMC.c:3558: error: ‘i810XvMCSubpicture’ has no member named ‘offsets’
I810XvMC.c:3565: error: ‘i810XvMCSubpicture’ has no member named ‘offset’
I810XvMC.c:3566: error: ‘i810XvMCSubpicture’ has no member named ‘offsets’
I810XvMC.c:3579: error: ‘i810XvMCSubpicture’ has no member named ‘offset’
I810XvMC.c:3580: error: ‘i810XvMCSubpicture’ has no member named ‘offsets’
I810XvMC.c:3587: error: ‘i810XvMCContext’ has no member named ‘ref’
I810XvMC.c: In function ‘XvMCClearSubpicture’:
I810XvMC.c:3623: error: ‘i810XvMCSubpicture’ has no member named ‘privContext’
I810XvMC.c:3638: error: ‘i810XvMCSubpicture’ has no member named ‘offsets’
I810XvMC.c: In function ‘XvMCCompositeSubpicture’:
I810XvMC.c:3679: error: ‘i810XvMCSubpicture’ has no member named ‘privContext’
I810XvMC.c:3702: error: ‘i810XvMCSubpicture’ has no member named ‘offsets’
I810XvMC.c: In function ‘XvMCDestroySubpicture’:
I810XvMC.c:3737: error: ‘i810XvMCSubpicture’ has no member named ‘privContext’
I810XvMC.c: In function ‘XvMCSetSubpicturePalette’:
I810XvMC.c:3783: error: ‘i810XvMCSubpicture’ has no member named ‘palette’
I810XvMC.c:3784: error: ‘i810XvMCSubpicture’ has no member named ‘palette’
I810XvMC.c:3785: error: ‘i810XvMCSubpicture’ has no member named ‘palette’
I810XvMC.c: In function ‘XvMCBlendSubpicture2’:
I810XvMC.c:3890: error: ‘i810XvMCSubpicture’ has no member named ‘privContext’
I810XvMC.c:3929: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:3929: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c:3929: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:3940: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:3940: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:3942: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:3942: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:3956: error: ‘i810XvMCSubpicture’ has no member named ‘palette’
I810XvMC.c:3963: error: ‘i810XvMCSubpicture’ has no member named ‘palette’
I810XvMC.c:4030: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:4030: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:4032: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:4032: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:4045: error: ‘i810XvMCSubpicture’ has no member named ‘palette’
I810XvMC.c:4052: error: ‘i810XvMCSubpicture’ has no member named ‘palette’
I810XvMC.c:4119: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:4119: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:4121: error: ‘i810XvMCSurface’ has no member named ‘offset’
I810XvMC.c:4121: error: ‘i810XvMCSurface’ has no member named ‘offsets’
I810XvMC.c:4135: error: ‘i810XvMCSubpicture’ has no member named ‘palette’
I810XvMC.c:4142: error: ‘i810XvMCSubpicture’ has no member named ‘palette’
I810XvMC.c:4209: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:4210: error: ‘i810XvMCContext’ has no member named ‘last_render’
I810XvMC.c:4213: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:4213: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:4213: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c: In function ‘XvMCGetSubpictureStatus’:
I810XvMC.c:4297: error: ‘i810XvMCSubpicture’ has no member named ‘privContext’
I810XvMC.c:4302: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:4302: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c:4302: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:4308: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:4308: error: ‘i810XvMCContext’ has no member named ‘lock’
I810XvMC.c:4308: error: ‘i810XvMCContext’ has no member named ‘drmcontext’
I810XvMC.c: In function ‘XvMCSetAttribute’:
I810XvMC.c:4414: error: ‘i810XvMCContext’ has no member named ‘xv_colorkey’
I810XvMC.c:4419: error: ‘i810XvMCContext’ has no member named ‘colorkey’
I810XvMC.c:4422: error: ‘i810XvMCContext’ has no member named ‘xv_brightness’
I810XvMC.c:4427: error: ‘i810XvMCContext’ has no member named ‘brightness’
I810XvMC.c:4430: error: ‘i810XvMCContext’ has no member named ‘xv_saturation’
I810XvMC.c:4435: error: ‘i810XvMCContext’ has no member named ‘saturation’
I810XvMC.c:4438: error: ‘i810XvMCContext’ has no member named ‘xv_contrast’
I810XvMC.c:4443: error: ‘i810XvMCContext’ has no member named ‘contrast’
I810XvMC.c: In function ‘XvMCGetAttribute’:
I810XvMC.c:4488: error: ‘i810XvMCContext’ has no member named ‘xv_colorkey’
I810XvMC.c:4489: error: ‘i810XvMCContext’ has no member named ‘colorkey’
I810XvMC.c:4492: error: ‘i810XvMCContext’ has no member named ‘xv_brightness’
I810XvMC.c:4493: error: ‘i810XvMCContext’ has no member named ‘brightness’
I810XvMC.c:4496: error: ‘i810XvMCContext’ has no member named ‘xv_saturation’
I810XvMC.c:4497: error: ‘i810XvMCContext’ has no member named ‘saturation’
I810XvMC.c:4500: error: ‘i810XvMCContext’ has no member named ‘xv_contrast’
I810XvMC.c:4501: error: ‘i810XvMCContext’ has no member named ‘contrast’
make[3]: *** [libI810XvMC_la-I810XvMC.lo] Error 1
make[2]: *** [install-recursive] Error 1
make[1]: *** [install-recursive] Error 1
make: *** [install-recursive] Error 1


I tried this earlier but never gave me a problem since i never updated it but now ...

---

### Post by rreese6 on 2009-09-29
So you want to know why this happened besides you not using sudo with the "make install" command ;)

try like this:
```
sudo make install &#8211;directory ~/Desktop/xf86-video-intel-2.8.1
```

I am also curious of why you want to install an Xfree86 Driver instead of the More advanced Xorg..
Of course I may have missed something here....
here is a good post to look at:

[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

---

### Post by linkingeek on 2009-09-29
xf86 driver was published on intel's website which is for g33 too but as you said x.org is much advanced then why ubuntu repositories show xorg driver for i8xx,i9xx ?
-Also, i m new to linux.

---

### Post by rreese6 on 2009-09-29
> **linkingeek said:**
> xf86 driver was published on intel's website which is for g33 too but as you said x.org is much advanced then why ubuntu repositories show xorg driver for i8xx,i9xx ?
-Also, i m new to linux.

Basically the xorg driver from the repository is correct for the chipset you have on the motherboard. basically the chipset on the motherboard (i810 in your case) talks to the video card or on board video..
The Xorg Driver Ubuntu put in is correct for your system.
no, because the "generic" video dive might not give you all you could get from the video card (like hardware 3D) then you might want to install a driver from the company that makes the main chip on the card, such as Intel, ATI , or Nvidia, to name the more popular ones.

Tell us why you feel you need another driver so we can understand why you want to do what you are attempting to do..

---

