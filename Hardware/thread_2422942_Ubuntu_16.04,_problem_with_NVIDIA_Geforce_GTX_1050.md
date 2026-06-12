---
title: "Ubuntu 16.04, problem with NVIDIA Geforce GTX 1050 ono HP pavillon 15-cs1025"
date: 2019-07-15
forum: Hardware
---

### Post by thefallen1971 on 2019-07-15
Hi due to matters i'll not mention i have to install Ubuntu 16.04.6 LTS on a HP Pavillon 15-cs1025 Geforce GTX 1050 with LVM
The installation works fine except the newly installed Ubuntu freezes on login.
Booting in nomodeset i managed to get in the desktop and install nvidia drivers, latest reccomended release, and now i'm able to login from lightdm.

trying to connect a second monitor i fund that it is not detected, nvidia utilities nvidia-settings and nvidia-smi were not working and looking into config i found typing "prime-select query" that the gpu in use was intel

switching with

prime-select nvidia

causes lighdm to freeze again on login, crash, restart, and sending me back to login screen.

some system informations follows

```
[COLOR=#555555][FONT=Monaco]utente@Ubuntu-HP:~$ nvidia-settings[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]ERROR: Unable to load info from any available system[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]utente@Ubuntu-HP:~$ nvidia-smi[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]NVIDIA-SMI couldn't find libnvidia-ml.so library in your system. Please make sure that the NVIDIA Display Driver is properly installed and present in your system.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Please also try adding directory that contains libnvidia-ml.so to your system PATH.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]utente@Ubuntu-HP:~$ prime-select query[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]intel[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]utente@Ubuntu-HP:~$ lsmod | grep nvidia[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]nvidia_uvm            819200  0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]nvidia_drm             45056  0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]nvidia_modeset       1110016  1 nvidia_drm[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]nvidia              18792448  2 nvidia_uvm,nvidia_modeset[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]drm_kms_helper        172032  2 nvidia_drm,i915[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]ipmi_msghandler        53248  2 ipmi_devintf,nvidia[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]drm                   401408  4 drm_kms_helper,nvidia_drm,i915[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]utente@Ubuntu-HP:~$ ubuntu-drivers devices[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]== /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0 ==[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]modalias : pci:v000010DEd00001C8Dsv0000103Csd0000856Abc03sc00i00[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]vendor   : NVIDIA Corporation[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]driver   : nvidia-430 - third-party free recommended[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]driver   : nvidia-410 - third-party free[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]driver   : nvidia-384 - distro non-free[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]driver   : nvidia-415 - third-party free[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]driver   : nvidia-418 - third-party free[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]driver   : xserver-xorg-video-nouveau - distro free builtin[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]driver   : nvidia-396 - third-party free[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]driver   : nvidia-390 - third-party free[/FONT][/COLOR]


```

```
[COLOR=#555555][FONT=Monaco]utente@Ubuntu-HP:~$ cat /var/log/Xorg.0.log | grep EE[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]   (WW) warning, (EE) error, (NI) not implemented, (??) unknown.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][     9.608] (EE) Failed to load module "nvidia" (module does not exist, 0)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][     9.608] (EE) Failed to load module "nvidia" (module does not exist, 0)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][     9.610] (EE) [drm] Failed to open DRM device for (null): -2[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][     9.610] (EE) Screen 0 deleted because of no matching config section.[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][     9.614] (EE) AIGLX: reverting to software rendering[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]utente@Ubuntu-HP:~$ [/FONT][/COLOR]
```

```
utente@Ubuntu-HP:~$ tail /var/log/Xorg.0.log[     9.814] (**) Option "xkb_layout" "it"
[     9.834] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[     9.834] (II) No input driver specified, ignoring this device.
[     9.834] (II) This device may have been added with another device file.
[     9.836] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event9)
[     9.836] (II) No input driver specified, ignoring this device.
[     9.836] (II) This device may have been added with another device file.
[     9.837] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[     9.837] (II) No input driver specified, ignoring this device.
[     9.837] (II) This device may have been added with another device file.
utente@Ubuntu-HP:~$ 



```

---

### Post by CatKiller on 2019-07-15
There have been several driver releases from the PPA that don't work with older releases of Ubuntu because of mismatches between what they use for building them and what comes with Ubuntu by default. In the future those drivers will be available through the same backporting process that browser releases go through, so they should go through a more robust building and testing process and the PPA will be unnecessary.

In the meantime you could try using the Hardware Enablement Stack to see if helps: that will give you a newer kernel and a newer version of X11, which may have fewer conflicts with the built modules.

---

### Post by thefallen1971 on 2019-07-15
you mean this i presume, 

[URL="https://wiki.ubuntu.com/Kernel/LTSEnablementStack"]
https://wiki.ubuntu.com/Kernel/LTSEnablementStack[/URL]

thank you i'll try immediatly

EDIT: already updated to latest available, nothing changed

---

