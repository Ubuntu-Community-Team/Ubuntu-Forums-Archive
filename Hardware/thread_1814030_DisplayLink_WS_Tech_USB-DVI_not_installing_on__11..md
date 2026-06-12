---
title: "DisplayLink WS Tech USB-DVI not installing on  11.04 64 bit"
date: 2011-07-28
forum: Hardware
---

### Post by sehson on 2011-07-28
I have a DisplayLink WS Tech USB-DVI
trying to get it to work on Ubuntu 11.04 x86_64, kernel 2.6.38-9 generic.

I rather new to linux ~ 2 months work related, I need an 3rd monitor for work and I already have the aforementioned usb-dvi adapter.

I've looked over here. [http://ubuntuforums.org/showthread.php?t=1759006](http://ubuntuforums.org/showthread.php?t=1759006)

compared to the Displaylink recommended site [http://mulchman.org/blog/?tag=displaylink](http://mulchman.org/blog/?tag=displaylink)

Tried, tried again Wiped tried yet again fail every time. trying to get it down pat on a test machine so I don't nuke my work machine.

Google is only returning results for setting up this dang thing in versions of Ubuntu earlier then 10.x at the latest and typically 9.x

according to [http://libdlo.freedesktop.org/wiki/](http://libdlo.freedesktop.org/wiki/) libdlo has been replaced by the kernal driver udlfb in kernals 2.6.31 and later

I have apt-get install libusb-dev xserver-xorg-video-displaylink

even modified/ added

/etc/gdm/Init/Default
XRANDR=`gdmwhich xrandr`
if [ "x$XRANDR" != "x" ] ; then
$XRANDR -o 0
fi


make modifications to xorg.conf as recommended via various sites listed and many others using the /usr/share/doc/xserver-xorg-video-displaylink as a template.


I have even tried installing the Libdlo, and best I can get is the adapter to display with the make check.

The adapter will only show green or after the xorg.conf is configured cause the machine to lock in boot. remove everything associated with the adapter in xorg.conf and the system will boot fine.

Is there anyone who has installed this adapter on Ubuntu 11.04 and gotten it working, that can tell me how.  Or point me to some sites that have the instructions.

Google is failing me.

Thanks

Logan Seh

---

### Post by poppe076 on 2011-07-31
I'm in the exact same boat. Frustrating.

---

