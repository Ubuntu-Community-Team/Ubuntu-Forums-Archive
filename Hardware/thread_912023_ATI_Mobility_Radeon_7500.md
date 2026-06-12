---
title: "ATI Mobility Radeon 7500"
date: 2008-09-06
forum: Hardware
---

### Post by fraktalek on 2008-09-06
Hi, does someone know how to get this card working in Hardy, please?
I have IBM Thinkpad T42 with ATI Mobility Radeon 7500

I tried to follow this thread [http://ubuntuforums.org/showthread.php?t=122094&page=12](http://ubuntuforums.org/showthread.php?t=122094&page=12) but Hardy apparently has quite different xorg.conf - rather minimalistic and if I add the "Modules" section, etc., then the X just crash.
I've read that Hardy already supports this card by default via the radeon_dri driver but I'm not sure whether it is loaded (can that be determined by lsmod or its some separate X modules?) and if it is then it doesn't work that well because glxgears shows FPS only around 600 although it should be more than double that.

and 
```
~$ LIBGL_DEBUG=verbose glxinfo | grep direct
libGL: XF86DRIGetClientDriverName: 5.3.0 radeon (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/radeon_dri.so
libGL error: dlopen /usr/lib/dri/radeon_dri.so failed (/usr/lib/dri/radeon_dri.so: undefined symbol: _glapi_Dispatch)
libGL error: unable to load driver: radeon_dri.so
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

any ideas?

---

