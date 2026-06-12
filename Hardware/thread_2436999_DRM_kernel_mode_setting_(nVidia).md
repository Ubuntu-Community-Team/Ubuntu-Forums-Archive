---
title: "DRM kernel mode setting (nVidia)"
date: 2020-02-17
forum: Hardware
---

### Post by lasermouse on 2020-02-17
I use Ubuntu 19.10. I followed the instructions but nothing helps. I always get a blank (black, purple or Asus ROG logo) screen. 
But when I tried POP! _OS (19.10) in live mode, modesetting is worked:
/sys/module/nvidia_drm/parameters/modeset
Y
How to achieve the same thing on Ubuntu?

---

### Post by vidtek on 2020-02-17
More details please, use your signature to detail your machine setup, what you have tried what you are trying to achieve?

Tony

---

### Post by lasermouse on 2020-02-17
I did not find such an option like "Signature" in my settings. Therefore, I will write here. But I think for my question, this is not important. Because this should work for all modern nVidia adapters.
Asus ROG CROSSHAIR VI HERO, AMD Ryzen 7 1800X, nVidia GTX 680, Ubuntu 19.10.

[https://wiki.archlinux.org/index.php/NVIDIA#DRM_kernel_mode_setting](https://wiki.archlinux.org/index.php/NVIDIA#DRM_kernel_mode_setting)
[https://devtalk.nvidia.com/default/topic/1027337/linux/how-to-enable-prime-synchronization-/](https://devtalk.nvidia.com/default/topic/1027337/linux/how-to-enable-prime-synchronization-/)

With the parameter "modeset=1" I always get a blank (purple or Asus ROG logo) screen.

---

### Post by vidtek on 2020-02-18
> **lasermouse said:**
> I did not find such an option like "Signature" in my settings. Therefore, I will write here. But I think for my question, this is not important. Because this should work for all modern nVidia adapters.
Asus ROG CROSSHAIR VI HERO, AMD Ryzen 7 1800X, nVidia GTX 680, Ubuntu 19.10.

[https://wiki.archlinux.org/index.php/NVIDIA#DRM_kernel_mode_setting](https://wiki.archlinux.org/index.php/NVIDIA#DRM_kernel_mode_setting)
[https://devtalk.nvidia.com/default/topic/1027337/linux/how-to-enable-prime-synchronization-/](https://devtalk.nvidia.com/default/topic/1027337/linux/how-to-enable-prime-synchronization-/)

With the parameter "modeset=1" I always get a blank (purple or Asus ROG logo) screen.

Go to settings next to logoff on the top header, then scroll down to my settings-> edit signature.

You have given us very little to go on, what driver are you using? Nouveau, nvidia proprietary, wayland?

If you are using the proprietary driver, you could do this and create an old-style xorg.conf.

as root: ```
nvidia-xconfig
```

then

```
nano /etc/X11/xorg.conf
```

insert these in the monitor section:
```
  HorizSync       15.0 - 81.0
              VertRefresh     24.0 - 75.0
              Option         "DPMS"
              Option         "UseEdidDpi" "FALSE"
              Option         "DPI" "100 x 100"
``` 

The vert and horizontal refresh rates are for my monitor, you need to check your documentation to see what your monitor supports.

Let us know, Tony.

---

### Post by lasermouse on 2020-02-18
I already use it (xorg.conf) with such settings. I also tried not to use this configuration file at all. There was no difference. It does not help. 
Of course I use the proprietary driver from nVidia (not wayland). [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=eoan](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=eoan)

---

### Post by mörgæs on 2020-02-20
I would not recommend to waste signature space on a hardware description. 

[LIST]
[*]If one asks a question it's a good idea to post the description in  initial post (as opposed to repeated all over) but it should be  more detailed than two lines. 
[*]If one answers a question it's only noise.
[/LIST]
 @lasermouse, please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and paste lshw.txt in CODE tags. It will give all needed details in one go.

---

