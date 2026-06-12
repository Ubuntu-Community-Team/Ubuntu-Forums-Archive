---
title: "Asus K50IN: Garbled resolution with Nvidia 185 driver"
date: 2009-08-22
forum: Hardware
---

### Post by DigitalJunkie on 2009-08-22
My brother bought a new laptop, and I'm trying to install Ubuntu for him. The newest restricted driver in the repos couldn't detect the GPU (a GeForce G102M), so I installed version 185.18.36 from the official Nvidia site.

It seems to detect the GPU properly, but it will only boot the desktop at a 6x tiled and garbled 640x480 resolution. The Nvidia Settings tool will not let me change the resolution to anything higher, and when I add the screen's native resolution (1366x768 ) to xorg.conf manually, it ignores this completely.
It looks like the same problem that hellkiller reported in this thread: [http://ubuntuforums.org/showthread.php?t=1230528](http://ubuntuforums.org/showthread.php?t=1230528)

Does anyone know how to solve this?

EDIT: SOLVED. Adding the following line to the "Device" section in xorg.conf fixed this for me:

```
Option "ModeValidation" "NoTotalSizeCheck"
```

Taken from [this thread at nvnews]("http://www.nvnews.net/vbulletin/showthread.php?t=137379"). Thanks to tuco penguin for posting this link in another thread, and to all the bug hunters in the original thread!

---

### Post by crypto_neo_freak on 2009-08-26
Hi,

I just bought an ASUS k50IN at newegg.com. I tried to follow the steps for installing the official nvidia drivers but nothing worked. Was there something I missed (i.e. additional 3rd party  libraries)?

Or more precisely, what was it that you did in order to get the display driver installed on your system?

Thanks.

---

### Post by tommcd on 2009-08-27
> **crypto_neo_freak said:**
>  I tried to follow the steps for installing the official nvidia drivers but nothing worked. Was there something I missed (i.e. additional 3rd party  libraries)?

To install the nvidia driver from nvidia.com you need the build-essential package, plus the linux-headers for your kernel. See this:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
There is also a program called **envyng** in the Ubuntu repos that can do this automatically. See this:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
You should completely purge the nvidia driver from the Ubuntu repos (if you have installed it) before installing the nvidia driver from nvidia.com.

And welcome to the Ubuntu forums!

---

### Post by crypto_neo_freak on 2009-08-27
It worked! It's funny that Nvidia has no drivers for the 102M line of cards and yet, the GE 102 driver worked like a charm on my K50IN.

Thank you, all!

---

### Post by zvezdogled on 2009-10-19
Thanks. It works for me.

---

### Post by Dynux on 2009-12-22
Hi all,
I've an Asus K50IN with GeForce g102m but i've still the 6 screens.
Can anyone upload the xorg.conf file that works with the proprietary drivers ( and the driver version) ?
Please help me, i'm going mad!

---

### Post by tommcd on 2009-12-23
> **Dynux said:**
> Hi all,
I've an Asus K50IN with GeForce g102m but i've still the 6 screens.
Can anyone upload the xorg.conf file that works with the proprietary drivers ( and the driver version) ?

First, install the nvidia driver from nvidia.com as I discussed in post #3 of this thread. Either use ** envyng** from the Ubuntu repos, or follow this:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)
If you are not familiar with installing the nvidia driver manually, I suggest you use envyng.
Then edit your xorg.conf file and add this to the "Device" section:
```
[Option "ModeValidation" "NoTotalSizeCheck"
```
... as was posted by DigitalJunkie at the top of this thread. This issue has been posted several places:
[http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg26479.html](http://www.mail-archive.com/ubuntu-x-swat@lists.launchpad.net/msg26479.html)
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/437637](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/437637)
Adding **Option "ModeValidation" "NoTotalSizeCheck"** to the device section of xorg.conf seems to be the way to fix it. 
If you still need help, post your xorg.conf after you have installed and enabled the nvidia driver and we can look at it.

---

### Post by Dynux on 2009-12-23
Still the same 6 screens, with all the drivers ( 180.xx 185.xx and 190.xx ). Please look at my xorg.conf file for any errors.

---

### Post by DigitalJunkie on 2009-12-24
Here is my working xorg.conf. I see yours is missing the following section:
```

Section "Module"
	Load	"glx"
EndSection

```
Does it make any difference if you add those lines?

Also, did you uninstall any older versions of the driver before installing the one from Nvidia's site? The Nvidia installer doesn't replace older drivers properly, and having two version installed at the same time is known to cause conflicts.

---

### Post by Dynux on 2009-12-26
Thank you so much!! It works!! The missing line has resolved the problem!!! Thank you all guys!

---

