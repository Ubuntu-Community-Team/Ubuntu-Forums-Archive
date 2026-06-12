---
title: "3D controller from 3DConnexion: 3DxWare?"
date: 2008-09-05
forum: Hardware
---

### Post by Keith_Beef on 2008-09-05
Well, I've been away from this for a long time, and decided to come back to try to get this controller working.

The original [thread]("http://ubuntuforums.org/showthread.php?t=387903") appears to have been archived and I can no longer post in it...

I downloaded the Deb package from [http://www.arakhne.org/3dxware/](http://www.arakhne.org/3dxware/) and added the Gnome applet to the panel, but can't see anything happening...

What should I expect to see? And should xcube now work? As it stands, I get this:
```
$ /opt/3DxWare/xcube
Magellan: xdrvlib.c 
MagellanMotionEvent = 0 
MagellanButtonPressEvent = 0 
MagellanButtonReleaseEvent = 0 
MagellanCommandEvent = 0 

No driver is running. Exit ... 
```

So either xcube is unhappy because it doesn't detect the 3DConnexion "official" driver, or else the applet is not launching a driver...

Any ideas?

K.

---

### Post by galland on 2008-09-07
> **Keith_Beef said:**
> Well, I've been away from this for a long time, and decided to come back to try to get this controller working.

The original [thread]("http://ubuntuforums.org/showthread.php?t=387903") appears to have been archived and I can no longer post in it...

I downloaded the Deb package from [http://www.arakhne.org/3dxware/](http://www.arakhne.org/3dxware/) and added the Gnome applet to the panel, but can't see anything happening...

What should I expect to see? And should xcube now work? As it stands, I get this:
```
$ /opt/3DxWare/xcube
Magellan: xdrvlib.c 
MagellanMotionEvent = 0 
MagellanButtonPressEvent = 0 
MagellanButtonReleaseEvent = 0 
MagellanCommandEvent = 0 

No driver is running. Exit ... 
```

So either xcube is unhappy because it doesn't detect the 3DConnexion "official" driver, or else the applet is not launching a driver...

Any ideas?

K.

Hi,

First we must be sure that the 3DxActiator is running. Please type:
```
ps -aux|grep 3dx
```
Something like the following output should appear:
```
root      5245  0.0  0.3   4952  3220 ?        S    09:15   0:00 /usr/bin/perl -w /usr/sbin/3dxactivator -d=usb --wakeup=1
```

If not, type: ```
/etc/init.d/3dxactivator start
``` and check again.

When the 3dxactivator is running, the gnome applet is able to launch the 3DxWare driver window, which is required to be connected to the device.
You can also launch the 3DxWare driver window with the "Start 3DxWare driver" from the 'System Tools' menu.

Then xcube should be connected to the 3DxWare driver and run properly.

Give feedback on any problem,
Stéphane.

---

