---
title: "Radeon mobility x700 and fglrx 3d acceleration problem"
date: 2006-09-08
forum: Hardware &amp; Laptops
---

### Post by lassegs on 2006-09-08
Hi,

I've had a couple of Ubuntu installations on this laptop (asus a6v) and everything has always been working fine, after some configuration.

Now im having huge troubles getting opengl direct rendering and 3d acceleration to work. I've installed xorg-driver-fglrx, run aticonfig --initial, got a succesfull config and xorg.conf looks good to me. Tested opengl direct rendering and 3d acceleration, and it doesnt work. tested with cedega and with screensaver. Cedega gives me a failed message, and opengl screensaver lags.

fgl_glxgears gives this error message:
lasse@cylinder:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  32
  Current serial number in output stream:  32

I think it might have something to do with a failed xgl install i did a while back ago, that I just left broken. Since I installed it with a different session it hasnt affected my regular use. 
I've tried reinstalling xorg-driver-fglrx and doing aticonfig --initial again, but nothing seems to work.

Here is my xorg.conf
[http://pastebin.ca/164634](http://pastebin.ca/164634)

Please, please, pretty please, someone help me, im desperate!
Thanx

EDIT: 
xglrinfo shows this:

lasse@cylinder:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

---

### Post by Tingvan on 2006-09-09
my opinion is reinstalling your ATI driver. 
you can visit the ati website to get the lastest ati dirver for your X700 and install it.

---

### Post by lassegs on 2006-09-11
I've tried that, only using sudo apt-get remove, sudo apt-get install. 

Please someone. This is killing me!

---

### Post by lassegs on 2006-09-13
I cant see why noone is answering. Is it is too little information, because one cannot see the problem, or what. I hate this problem, please help me.

---

### Post by Alendit on 2006-09-23
Hi,

i have right this problem and worst thing is i can't use ati opensource driver because Xorg doesn't show anything with it.

Alendit.

---

### Post by lassegs on 2006-09-23
what you need to do is add these lines at the end of your xorg.conf

Section "Extensions"
        Option  "Composite" "0"
EndSection

Thats what did it for me

---

### Post by lH)4~mK0e on 2006-09-23
The old driver doesn't have the correct delivery of libGL.so.1.2 into the /usr/lib directory.  You will need to download the 8.28.8 driver from ati.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.29.6.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.29.6.run)

Then follow this how-to (remembering to change the deb installed to the current filename).  It's explained more in detail in the how-to:

[http://ubuntuforums.org/showthread.php?t=204910&highlight=fglrx](http://ubuntuforums.org/showthread.php?t=204910&highlight=fglrx)

Then add this line to replace the section that says:

```
Driver "ati"
```

with this:

```
Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "UseInternalAGPGART" "on"
	Option "no_accel"                   "no"
    	Option "no_dri"                     "no"
    	Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
    	Option "DesktopSetup"               "(null)" 
    	Option "ScreenOverlap"              "0" 
    	Option "GammaCorrectionI"           "0x00000000"
    	Option "GammaCorrectionII"          "0x00000000"
    	Option "Capabilities"               "0x00000000"
    	Option "CapabilitiesEx"             "0x00000000"
    	Option "CenterMode"                 "off"
    	Option "PseudoColorVisuals"         "off"
    	Option "Stereo"                     "off"
    	Option "StereoSyncEnable"           "1"
    	Option "FSAAEnable"                 "no"
    	Option "FSAAScale"                  "1"
    	Option "FSAADisableGamma"           "no"
    	Option "FSAACustomizeMSPos"         "no"
    	Option "FSAAMSPosX0"                "0.000000"
    	Option "FSAAMSPosY0"                "0.000000"
    	Option "FSAAMSPosX1"                "0.000000"
    	Option "FSAAMSPosY1"                "0.000000"
    	Option "FSAAMSPosX2"                "0.000000"
    	Option "FSAAMSPosY2"                "0.000000"
    	Option "FSAAMSPosX3"                "0.000000"
   	Option "FSAAMSPosY3"                "0.000000"
    	Option "FSAAMSPosX4"                "0.000000"
    	Option "FSAAMSPosY4"                "0.000000"
    	Option "FSAAMSPosX5"                "0.000000"
    	Option "FSAAMSPosY5"                "0.000000"
   	Option "UseFastTLS"                 "0"
    	Option "BlockSignalsOnLock"         "on"
    	Option "ForceGenericCPU"            "no"
    	BusID  "PCI:1:0:0"
	Option "DynamicClocks"	            "on"
```

---

