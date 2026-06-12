---
title: "Hardy upgrade to Ubuntu Studio, X server fails to start"
date: 2008-07-31
forum: Hardware
---

### Post by timothiasthegreat on 2008-07-31
Hello, please forgive my noobness, but I try :) . So I decided I wanted to try Ubuntu Studio and upgraded my Hardy install to the realtime kernel while installing the audio workstation packages. I have had my Hardy system up and running for a while with all the appropriate drivers and everything functional. Using synaptic I selected the Ubuntu Studio packages I wanted and installed them.  I was then prompted for a reboot after it finished.  

When it rebooted Grub now shows two Linux kernels, the original kernel and the RT kernel.  Booting to the RT kernel leads me to an "X server has failed to start" dialog  while the original kernel still boots properly.

I have a NVIDIA 9600GT video card with the proprietary drivers installed.

Here is the last portion of the log file from the failed boot;
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
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
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

So it appears the RT kernel does not like my proprietary drivers.  Any input on how to correct this?

---

### Post by timothiasthegreat on 2008-07-31
Bump?

---

### Post by LowSky on 2008-07-31
boot th eRT kernel into safe mode
and reset you drivers using

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by timothiasthegreat on 2008-07-31
So that worked in the sense that I am now able to boot into the rt kernel, however I have lost 3d and openGL functionality (a result of disabling the NVIDIA driver?)   An attempt at reinstaling the NVIDIA driver says that i do not have the appropriate kernel source tree installed and it cannot buld the package.  Is there a different driver i should be using for the RT kernel, or where can i get the proper source tree for this kernel?

Thanks.

---

