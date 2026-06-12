---
title: "NVidia driver worked in Dapper but not Edgy"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by Avian00 on 2007-02-17
Hi,

I'm becoming quite frustrated by a particular issue.  I'll start by saying that I had absolutely NO issues with the Nvidia driver when using Dapper.  But when I switch to Edgy, everything just falls apart.  After installing using *apt-get install nvidia-glx* and then executing *nvidia-xconfig*, every time I try to start Xorg, it fails with the message "no screens found."  In order to use Xorg, I must change the "nvidia" driver back to simply "nv"

The output also claims it was unable to load the "wfb" module (not sure what this is) and that while screens were found, none of them have a "usable configuration."  I've attached what I believe to be the relevant portion of my Xorg log below:

```

(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(WW) Warning, couldn't open module wfb
(II) UnloadModule: "wfb"
(EE) Failed to load module "wfb" (module does not exist, 0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xd2102800 - 0xd21028ff (0x100) MX[B]
        [5] -1  0       0xd2101000 - 0xd2101fff (0x1000) MX[B]
        [6] -1  0       0xd2104000 - 0xd2107fff (0x4000) MX[B]
        [7] -1  0       0xd2102000 - 0xd21027ff (0x800) MX[B]
        [8] -1  0       0xd2200000 - 0xd2200fff (0x1000) MX[B]
        [9] -1  0       0xd2000000 - 0xd201ffff (0x20000) MX[B]
        [10] -1 0       0xd2504000 - 0xd25043ff (0x400) MX[B]
        [11] -1 0       0xd2500000 - 0xd2503fff (0x4000) MX[B]
        [12] -1 0       0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
        [13] -1 0       0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
        [14] -1 0       0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
        [15] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [16] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [17] -1 0       0x00003000 - 0x0000301f (0x20) IX[B]
        [18] -1 0       0x000018c0 - 0x000018df (0x20) IX[B]
        [19] -1 0       0x000018b0 - 0x000018bf (0x10) IX[B]
        [20] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [21] -1 0       0x00001840 - 0x0000185f (0x20) IX[B]
        [22] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [23] -1 0       0x00001800 - 0x0000181f (0x20) IX[B]
        [24] -1 0       0x00002000 - 0x0000207f (0x80) IX[B](B)
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xd2102800 - 0xd21028ff (0x100) MX[B]
        [5] -1  0       0xd2101000 - 0xd2101fff (0x1000) MX[B]
        [6] -1  0       0xd2104000 - 0xd2107fff (0x4000) MX[B]
        [7] -1  0       0xd2102000 - 0xd21027ff (0x800) MX[B]
        [8] -1  0       0xd2200000 - 0xd2200fff (0x1000) MX[B]
        [9] -1  0       0xd2000000 - 0xd201ffff (0x20000) MX[B]
        [10] -1 0       0xd2504000 - 0xd25043ff (0x400) MX[B]
        [11] -1 0       0xd2500000 - 0xd2503fff (0x4000) MX[B]
        [12] -1 0       0xd0000000 - 0xd0ffffff (0x1000000) MX[B](B)
        [13] -1 0       0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
        [14] -1 0       0xd1000000 - 0xd1ffffff (0x1000000) MX[B](B)
        [15] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [16] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [17] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [18] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [19] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [20] -1 0       0x00003000 - 0x0000301f (0x20) IX[B]
        [21] -1 0       0x000018c0 - 0x000018df (0x20) IX[B]
        [22] -1 0       0x000018b0 - 0x000018bf (0x10) IX[B]
        [23] -1 0       0x00001860 - 0x0000187f (0x20) IX[B]
        [24] -1 0       0x00001840 - 0x0000185f (0x20) IX[B]
        [25] -1 0       0x00001820 - 0x0000183f (0x20) IX[B]
        [26] -1 0       0x00001800 - 0x0000181f (0x20) IX[B]
        [27] -1 0       0x00002000 - 0x0000207f (0x80) IX[B](B)
        [28] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [29] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

I should mention that I am using a Toshiba Satellite P105-S9722 which has an Nvidia Go 7900 GS adapter.  And again, this configuration worked flawlessly in Dapper.  Thanks in advance for your help.

-Matt

---

### Post by taurus on 2007-02-17
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Avian00 on 2007-02-27
> **taurus said:**
> [http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

Thanks, but I already tried that.

---

### Post by Eigenwert on 2007-02-28
I have the exact same problem. I fixed it earlier, but then did a re-install and can't remember how I fixed this. I think what I did is downloaded the script directly from nVidia here [http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9746/NVIDIA-Linux-x86_64-1.0-9746-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/1.0-9746/NVIDIA-Linux-x86_64-1.0-9746-pkg2.run) (I'm on a amd64 by the way). I'm going to try it out and I'll get back with the results.

EW

---

### Post by Eigenwert on 2007-02-28
Okay, I got my problem fixed. Hopefully this helps you.

First I downloaded the Linux driver directly from the nVidia website. The selection of install scripts they have is here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html).

Second I did the following:
```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev

```
most of which was already installed. I then removed the previously installed nVidia stuff:
```

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*

```
Next you have to quit the x server to run the script
```

sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-1.0-9746-pkg2.run
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start
```

The script spit out a few strange messages at the beginning, but I continued with the install anyway. I also found that since I'm on a 64-bit machine I should not install the 32-bit OpenGL compatibility libraries (it asks, that's why I mention this.) 

After all that I checked my xorg.conf file, did a reboot and it worked.

You might also want to make sure that the default color depth in your xorg.conf file is set to 24 and not 16.

EW

---

### Post by signed on 2007-02-28
Thanks a lot, been having the exact same problem. Works fine now.

---

### Post by Yoooder on 2007-03-02
Eigenwert:

Thanks much for the instructions!  I had nvidial/Beryl running fine on Edgy, but the upgrade to Feisty gave me

> failed to load module "wfb"

Your instructions took care of it!  Thanks again

---

