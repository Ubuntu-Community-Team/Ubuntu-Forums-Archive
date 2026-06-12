---
title: "Lenovo t500 with two (integrated and discrete) video cards"
date: 2009-10-16
forum: Hardware
---

### Post by sj_ on 2009-10-16
Hi, guys. I have Lenovo t500 laptop with two video cards
ATI Radeon HD 3650 256
and Integrated Intel GMA 4500HD
I'm running Ubuntu Karmic 9.10 with the latest FGLXR drivers 8.660 also i've installed xserver-xorg-video-intel 2:2.9.0-1ubuntu1 to use integrated video card sometimes for more battery time

I've found in that forum nice solution to pickup required Xorg config file on the boot time. Create script **xinit_conf** in the **/etc/init.d** directory and create a symlink in the **/etc/rc2.d** 
```

#!/bin/sh
VIDEO=`/usr/bin/lspci |/bin/grep -c ATI`

if [ "$VIDEO" = 1 ]; then
    cp -f /etc/X11/xorg.conf.ATI /etc/X11/xorg.conf
else
    cp -f /etc/X11/xorg.conf.INTEL /etc/X11/xorg.conf
fi

```

also i've created two different Xorg config files
**/etc/X11/xorg.conf.ATI**
```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
    Option      "VideoOverlay"  "off"
    Option      "OpenGLOverlay"  "on"
    Option      "TexturedVideo"  "off"
        Driver  "fglrx"
EndSection

```

**/etc/X11/xorg.conf.INTEL**
```

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
    Load    "dri"
    Load    "extmod"
    Load    "record"
    Load    "dbe"
    Load    "GLcore"
    Load    "xtrap"
    Load    "freetype"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver      "intel"
EndSection

Section "DRI"
    Mode 0666
EndSection

```

I have following issue here. When i boot Ubuntu with Integrated Intel video card i can't use OpenGL
**glxinfo**

```

name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16

```

It only starts when i removed FGLXR driver
```
sudo apt-get remove xorg-driver-fglrx
sudo reboot
```

But this is not solution cause i would like to use all of them.

Could anyone provide me with some solution or useful comment?

---

### Post by allbread on 2010-11-16
I'm interested in this as well; I currently have a Thinkpad w500 with  both integrated (Intel GMA 4500MHD) and discrete (FireGL v5700) graphics  and would like to be able to have a means of selecting one or the  other... preferably on the fly (yeah I know runtime support for  switchable graphics will likely never happen) but at the very least via  the BIOS at boot...

Did you ever get a working solution to this issue?

I  found someone attempting a similar workaround to the one you detail  above for an Intel 965GM and Nvidia 8400GS (integrated vs discrete) on a  Sony laptop:

[http://www.land-of-kain.de/docs/sony_vaio_sz61_mnb/](http://www.land-of-kain.de/docs/sony_vaio_sz61_mnb/)

and with a kernel patch on a T500;

[http://www.phoronix.com/forums/showthread.php?t=21979&highlight=w500](http://www.phoronix.com/forums/showthread.php?t=21979&highlight=w500)

However I haven't yet attempted either...

Any advice before I plunge in?

---

