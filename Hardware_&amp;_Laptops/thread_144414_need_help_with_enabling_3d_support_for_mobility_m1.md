---
title: "need help with enabling 3d support for mobility m1 please"
date: 2006-03-14
forum: Hardware &amp; Laptops
---

### Post by carny on 2006-03-14
Gday, I recently installed Ubuntu 5.10 and its bloody awesome so far, however it does not seem to recognize my graphics card as being capable of 3d acceleration (dri). I have googled and researched and found out how to enable it.. however when i am trying to install the driver, it comes up with the following error message: 

/home/carny/Desktop/mach64-20060311-linux.i386/drm/linux-core/Makefile:289: *** CONFIG_X86_CMPXCHG needs to be enabled in the kernel.  Stop.
make[2]: *** [_module_/home/carny/Desktop/mach64-20060311-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'

Also in my xorg.conf file.. it says that it loads dri and all the opengl crap.. but it just does not work. I think the ati driver that i am trying to install is already installed but just not configured properly and i have no clue of howto get it working.. here is are some extracts from my xorg.conf file:

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Rage Mobility P/M (AGP)"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "DRI"
        Mode    0666
EndSection

So i dont know what is wrong and i would appreciate greatly any advice on how i can go about getting dri working and opengl working. Do i need to recompile my kernel?? reconfigure my xorg.conf file?? Here is my system config if its any help:
Dell latitude cpx:
p3500
8mb ati mobility m1 (uses mach64 chipset.. is definetly 3d capable)
6gb hdd
ubuntu 5.10

Thankyou,
carny

---

