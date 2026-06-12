---
title: "Drivers radeon R7 m370"
date: 2016-07-19
forum: Hardware
---

### Post by alejandroperezcosio on 2016-07-19
Hello there, a month ago I bought a new Lenovo e560 laptop with a radeon R7 M370 video card. Everything works really fast and well with Windows (great! the card is working! but windows.. no thanks..), I started to have issues when installed the last version of Ubuntu (16.04) with gnome (downloaded from this [link]("https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME/LTS")). 

I didn't realize that the dedicated video drivers were not installed until the day where the screen froze and some 'radeon' error messages appeared. That was where I started to search if I had the drivers installed.

```
$ lspci -vnn
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 520 [8086:1916] (rev 07) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Skylake Integrated Graphics [17aa:5049]
    Flags: bus master, fast devsel, latency 0, IRQ 127
    Memory at e0000000 (64-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

[...]

03:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Mars [Radeon HD 8670A/8670M/8750M] [1002:6600] (rev ff) (prog-if ff)
    !!! Unknown header type 7f
    Kernel driver in use: radeon
    Kernel modules: radeon

```

This makes me think that Ubuntu doesn't recognize the video card, I tried to search the drivers to compile myself but, there is no option for the 16.04 version ([link]("http://support.amd.com/en-us")).

So, it would be really nice if someone who had the same issue and found a workaround could share its experience.

Regards
--
Alejandro

---

### Post by howefield on 2016-07-19
Have a look at the release notes for 16.04, scroll down near the bottom of the page... to Graphics and Display.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

There are a ton of threads in the forums that you can browse for more information

---

### Post by alejandroperezcosio on 2016-07-19
Thank you @howefield, but I tried to do a dist-upgrade, I have also installed libllvm3.8, but nothing changed.. Maybe if I reinstall Ubuntu with the instructions in the post it could work (allowing to download third-party software while installing), but for now it's impossible for me.

---

### Post by servius314 on 2016-07-20
Hi I am having the exact same issue as Alejandro. I was expecting my graphics card (Radeon R7 M370) to be supported by the open source Radeon Drivers pre-installed with Ubuntu 16.04 but when I transferred the graphics control using VGAswitcheroo I got a black screen. With closer inspection of the kern.log this error appeared "vgaarb: this pci device is not a vga device". I also have the exact same readout from the "lspci" command. Is AMD going to provide support for this series of graphics cards soon?

Thanks,
John

---

### Post by dpcole72 on 2016-07-22
Hopefully in time, servius314.  I too have the R7 M370 with Intel 530.  

Command line utilities pick up something that sees AMD (save for very specific model info) but it's clear there's no AMD driver running, just Intel.  The R7 is new, so it should be supported at some point. Until then I'm enabling 3D hardware acceleration for the Intel 530.  I really don't want to put in 14.04 or OpenSUSE (assuming it works and I probably won't do a liveCD boot demo), having spent the time to deal with Ubuntu though I adore both distros.

If I find anything I'll update this thread, but suspect we're all going to be actively looking with bated breath nonetheless. :)

---

### Post by km14hixepo on 2016-08-28
The lspci command is based off a database of IDs. Unluckily the R7 M370 card reuses an ID from another card. But you can safely ignore the output from that command.

First of all the Lenovo e560 has what's called a hybrid graphics system, specifically the muxless kind. Some interesting reading:
[https://01.org/linuxgraphics/gfx-docs/drm/gpu/vga-switcheroo.html](https://01.org/linuxgraphics/gfx-docs/drm/gpu/vga-switcheroo.html)

Anyway in an Ubuntu 16.04 fresh install this kinda works already. First check the output of:
```
$ xrandr --listproviders
Providers: number : 3
Provider 0: id: 0x6b cap: 0x9, Source Output, Sink Offload crtcs: 4 outputs: 6 associated providers: 2 name:Intel
Provider 1: id: 0x41 cap: 0x6, Sink Output, Source Offload crtcs: 2 outputs: 0 associated providers: 2 name:OLAND @ pci:0000:03:00.0
Provider 2: id: 0x41 cap: 0x6, Sink Output, Source Offload crtcs: 2 outputs: 0 associated providers: 2 name:OLAND @ pci:0000:03:00.0
```
Should show both, the Intel card and Radeon (OLAND) card. If the radeon one doesn't show then there's probably something wrong with the driver (in kernel or in X server).

You can  also test it by installing mesa-utils package and then running:
```
DRI_PRIME=1 glxgears
```

Except it doesn't work for more than a few seconds before crashing, or even completely locking up the OS.

To solve the crashes I had to take two steps:
[LIST]
[*]Enable DRI3 
[*]Enable Dynamic Power Management (DPM) 
[/LIST]

I read that enabling DRI3 on the Intel card helped fix the crashes from here:
[https://wiki.archlinux.org/index.php/PRIME#Kernel_crash.2Foops_when_using_PRIME_and_switching_windows.2Fworkspaces](https://wiki.archlinux.org/index.php/PRIME#Kernel_crash.2Foops_when_using_PRIME_and_switching_windows.2Fworkspaces)

So I enabled DRI3 on both the Intel and Radeon cards. For that I created the file /usr/share/X11/xorg.conf.d/20-gpu.conf with the following contents:
```
Section "Device"
        Identifier "intel"
        Driver "intel"
        Option "DRI" "3"
EndSection

Section "Device"
        Identifier "RADEON"
        Driver "radeon"
        Option "DRI3" "1"
EndSection
```
[https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/open-source-amd-linux/886614-radeon-x-org-driver-now-only-uses-dri3-by-default-with-glamor](https://www.phoronix.com/forums/forum/linux-graphics-x-org-drivers/open-source-amd-linux/886614-radeon-x-org-driver-now-only-uses-dri3-by-default-with-glamor)

Once you reboot (or restart X) you should see the following lines in /var/log/Xorg.0.log:
```
$ grep 'DRI3' /var/log/Xorg.0.log
[    36.468] (**) RADEON(G0): Option "DRI3" "1"
[    37.649] (**) RADEON(G0): DRI3 enabled
[    37.901] (II) intel(0): direct rendering: DRI2 DRI3 enabled
```

Next step is to enable DPM. Do this by adding a **radeon.dpm=1** parameter to your kernel boot line. Edit /etc/default/grub and modify add it linux command line like so:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.dpm=1"
```

Then update grub menu:
```
sudo update-grub
```

Now try running again:
```
DRI_PRIME=1 glxgears
```

Should be able to run without crashing.

One last issue is that the Radeon card will power off after being idle for only 5 seconds:
```
$ cat /sys/class/drm/card0/device/power/autosuspend_delay_ms 
5000
```
 For program that's continually rendering it might not be much of an issue but some programs use the OpenGL intermittently and the card takes like 5~10 seconds to power back on after powering off. This will adjust it to 60 seconds delay instead:
```
echo 60000 > /sys/class/drm/card0/device/power/autosuspend_delay_ms
```

---

### Post by myroslav-tkachenko on 2016-10-16
Thank you for the instructions. this is exactly what I've been looking for! I have a new lenovo thinkpad e560 and now I can use its discrete card. had issues with the driver though, but after install of kernel 4.8 and new firmware I was able to complete the steps provided, so everything is working fine now: can run "Don't Starve" either using integrated or discrete card.

---

