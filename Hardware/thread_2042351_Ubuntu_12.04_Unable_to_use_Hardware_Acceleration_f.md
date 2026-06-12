---
title: "Ubuntu 12.04: Unable to use Hardware Acceleration for Radeon HD 6490M card"
date: 2012-08-14
forum: Hardware
---

### Post by giogziro95 on 2012-08-14
I've followed steps in [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI/"). Here is output of 'vainfo' command:
```
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```
What's wrong?! I have Catalyst 12.6 driver installed (from debs). Also I've fixed switchable graphics bug, using [this guide]("http://ubuntuforums.org/showthread.php?t=1930450") (STEP 2). PLEASE HELP!! :]

P.S.: I tried to add ```
LIBVA_DRIVER_NAME=xvba LIBVA_DRIVERS_PATH=/usr/lib/va/drivers
``` to /etc/environment and rebooted system ([source]("http://askubuntu.com/questions/87395/how-can-i-enable-hardware-acceleration-for-an-ati-radeon-hd")), but the result was same :\

---

### Post by QIII on 2012-08-14
Were you running on the ATI card when you attempted to activate the hardware acceleration?

Can you try again after using the Catalyst Control Center to switch to your ATI GPU and rebooting?

Did you follow the instructions at the end of the hardware acceleration section for creating/correcting the symlink?

I am not going to suggest that the askubuntu answer is wrong, but I do think that the symlink approach is more satisfactory than changing an environmental setting.

Of course all of this is moot if the Intel/ATI hybrid graphics setup poses problems of its own.

---

### Post by giogziro95 on 2012-08-14
Hello, QIII!
> **QIII said:**
> Were you running on the ATI card when you attempted to activate the hardware acceleration?

Yes (:D).

> **QIII said:**
> 
Can you try again after using the Catalyst Control Center to switch to your ATI GPU and rebooting?

It's already switched to ATI. I tried to switch to Sandybridge and then back to ATI - no difference between.

> **QIII said:**
> 
Did you follow the instructions at the end of the hardware acceleration section for creating/correcting the symlink?

I am not going to suggest that the askubuntu answer is wrong, but I do think that the symlink approach is more satisfactory than changing an environmental setting.

I'm getting the same command output despite the symlink exists or not:
```
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```
I'm getting following on changing environmental setting:
```
libva: VA-API version 0.32.0
libva: User requested driver 'xvba LIBVA_DRIVERS_PATH=/usr/lib/va/drivers'
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/xvba LIBVA_DRIVERS_PATH=/usr/lib/va/drivers_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```

THERE IS NO TARGET FOR SYMLINK! The folder /usr/lib/va does NOT exist in the system (I think some libraries are missing..)!

---

### Post by QIII on 2012-08-14
Remember that  you changed /etc/environment.  That is overriding anything else.

The target would normally be /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so on a 64 bit system, provided you installed via the instructions in the ATI Driver Wiki.

See if /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so exists.  If it does, try commenting out the line you added to /etc/environment.

However, it looks like as you have it set up, it is trying to find the Intel acceleration (i965_drv_video.so), so this may be a hybrid difficulty.

---

### Post by giogziro95 on 2012-08-14
> **QIII said:**
> 
The target would normally be /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so on a 64 bit system, provided you installed via the instructions in the ATI Driver Wiki.

See if /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so exists.  If it does, try commenting out the line you added to /etc/environment.

Nope!
It exists, but it is not a driver file, it's a broken link (to non-existent file). It's created by following command and its target is non-existent /usr/lib/va/drivers/fglrx_drv_video.so file:
```
sudo ln -s /usr/lib/va/drivers/fglrx_drv_video.so /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
```

> **QIII said:**
> 
However, it looks like as you have it set up, it is trying to find the Intel acceleration (i965_drv_video.so), so this may be a hybrid difficulty.

I don't think so. Because I've restored the 10fglrx file and rebooted system, after that hybrid graphics was no longer working, but nothing has changed. Then I've changed it back and rebooted system.

But! After that I found out, that the file xvba_drv_video.so (in same folder) is the one, which must be used instead i965_drv_video.so. So, I've created link (I have no idea why I needed to do that):
```
sudo ln -s /usr/lib/x86_64-linux-gnu/dri/xvba_drv_video.so /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
```
Executed vainfo and I got:
```
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
```
And it works! Problem solved! :D

P.S.: Please excuse me for my bad English... :oops:

---

### Post by QIII on 2012-08-15
This means that with Intel/ATI integrated graphics the process differs.  I will have to do some research and add a new section to the instructions in the wiki for hybrid graphics.

---

### Post by RIPAciD on 2012-08-21
Same problem and I only have a dedicated card amd hd7870, I followed [this guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") , any help?

--edit--

Uninstalled using 'Synaptic '
> 
libva-egl1
libva-glx1
libva-x11-1
libva1
varinfo
xvba-va-driver
Re-installed using 'Synaptic'

Fixed 
> 
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD
But Synaptic uninstalled the latest drivers from AMD and installed the version available in 'Additional Drivers' (4.2.11627)

I will try to re-install the latest drivers from AMD to see if this problem will occur again...

--edit--

I'm a noob, installed the drivers following the wrong tutorial, reinstalled and now is fixed.

---

