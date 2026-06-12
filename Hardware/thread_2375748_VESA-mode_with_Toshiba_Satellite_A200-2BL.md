---
title: "VESA-mode with Toshiba Satellite A200-2BL"
date: 2017-10-27
forum: Hardware
---

### Post by stn021 on 2017-10-27
Hello,

due to thermal problems with the GPU I would like to run to Toshiba Satellite A200-2BL on Ubuntu 17.10 in VESA-mode.
The graphics adapter according to lspci is 01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV610/M72-S [Mobility Radeon HD 2400].
The LCD-screen has a resolution of 1280x800.

In principle VESA works. I just need some settings in /etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset xforcevesa"
GRUB_GFXMODE="1280x800x32"
GRUB_GFXPAYLOAD_LINUX=keep
```
and then of course
```
sudo update-grub
```
That solves the thermal problem but the resolution is 1024x768 instead of 1280x800.
How can I configure the correct resolution?
THX, stn

---

### Post by mörgæs on 2017-10-27
If you click the link in my signature you will find some advice about Vesa.

Though, for GPU which is not ancient I don't think Vesa should be necessary. Have you cleaned the fan and radiator for accumulated dust bunnies?

---

### Post by stn021 on 2017-10-27
> **mörgæs said:**
>  ... I don't think Vesa should be necessary. Have you cleaned the fan and radiator for accumulated dust bunnies?

Yes, I have taken out the fan and cleaned everything. The fan is huge, compared to other fans I have seen. There was almost no dust in the fan or the coolers.

Also I have tried several desktops, for example lubuntu and cinnamon with software rendering. That did not help, unfortunately.

I think that this notebook is one with bad solderspots or maybe the GPU+cooling was badly designed. It is a definitely problem with the hardware and happens with windows, ubuntu live, ubuntu installed, different distributions. After a while lines or other artifacts appear on the screen and nothing works anymore.

VESA on the other hand works fine. I am at this computer right now and have not had any problems since I set up VESA.
Except for the resolution :-|

---

### Post by stn021 on 2017-10-28
> **mörgæs said:**
> If you click the link in my signature you will find some advice about Vesa.

I checked that and tried vga=791:

```
$ cat /proc/cmdline 
BOOT_IMAGE=/vmlinuz-4.13.0-16-generic root=UUID=51c48684-2d0c-4437-a884-03ea47dbe3d9 ro quiet splash vga=791 vt.handoff=7
```

I believe that should have at least changed the resolution to something lower.

It did not change anything though. The resolution is OK @ 1280x800 but the thermal problem remains and the radeon driver is still being used, according to lsmod. Seems like "vga=791" was simply ignored :(

Is there anything else I can try? Maybe use xorg.conf or switch to fbdev?

---

### Post by mörgæs on 2017-10-29
The guide also has a suggestion for avoiding overheating with Radeon drivers. Did that help?

---

### Post by Yellow Pasque on 2017-10-29
This may not work with vesa:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

---

### Post by stn021 on 2017-10-29
> **mörgæs said:**
> The guide also has a suggestion for avoiding overheating with Radeon drivers. Did that help?

Right, thank you, I missed that one. It is a long article :oops:

Testing now. It will take a while to see if it works because it takes some time before the GPU overheats.

/etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.dpm=1"
```

after reboot:
```
$ cat /proc/cmdline 
BOOT_IMAGE=/vmlinuz-4.13.0-16-generic root=UUID=51c48684-2d0c-4437-a884-03ea47dbe3d9 ro quiet splash radeon.dpm=1 vt.handoff=7
```

I am using Cinnamon-Desktop, standard version. 

Up to now I used Cinnamon "with software rendering". That already helps to minimize overheating. The only small drawback here is that I watch youtube-videos on another computer.

Lubuntu-Desktop did not solve the problem. Apparently that still uses too much GPU even though it is declared to save resources.

---

### Post by stn021 on 2017-10-29
> **Temüjin said:**
> This may not work with vesa:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

I tried the method with xrandr only, it really does not seem to work.

But I may have made some other mistake on some detail. 
The following script works in the mode with the radeon-driver but not with VESA.
Also it does not work for 800x600 in VESA-mode. According to VESA-standard that resolution should be possible while 1280x800 is not part of the VESA-standard. So it is not a matter of the resolution but of VESA and xrandr in general.
The device in VESA-mode according to xrandr is "default":

```
cvt 1280 800 60
# # 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
# Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
xrandr --addmode default        "1280x800_60.00"
xrandr --output default --mode "1280x800_60.00"
```

There is no change of resolution, instead:
```
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
```

---

### Post by stn021 on 2017-11-14
Hello, 

thank you for all the input.

I have tested for a while now. Unfortunately powering down the GPU only worked at very low room temperatures. But "radeon.dpm=1" plus cinnamon-desktop in mode software-rendering works fine. Not fit for videos of course but that is not a problem for me. No blackouts or colorful patterns anymore O:)

Only cinnamon with software-rendering without "radeon.dpm=1" did **not** work. In that configuration the thermal problems were still there.

I also found that I can power the GPU even further down with 
```
echo "battery" > /sys/class/drm/card0/device/power_dpm_state
```

The current powerstate and the clock-frequencies can then be checked with
```
cat /sys/class/drm/card0/device/power_dpm_state
cat /sys/kernel/debug/dri/0/radeon_pm_info
```

No help with thermal problem at this point but still interesting.

---

### Post by stn021 on 2017-11-20
Lubuntu also works after powering down the GPU to "battery"-mode.
See above.

---

