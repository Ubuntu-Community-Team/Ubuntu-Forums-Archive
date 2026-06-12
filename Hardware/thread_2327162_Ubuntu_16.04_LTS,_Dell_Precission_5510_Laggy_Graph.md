---
title: "Ubuntu 16.04 LTS, Dell Precission 5510 Laggy Graphics with NVIDIA"
date: 2016-06-08
forum: Hardware
---

### Post by artur20 on 2016-06-08
Hi,

I have been trying to get my graphics to work for the past 2 days and I am not really sure how/where to continue. I will start by posting (as much) of my configuration as I know how to find :) 

I bought a new Dell Precission 5510, with this setup: (Note: Dell sells these laptops as ubuntu ready)

```
artur@pandaadb:~$ lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)
	DeviceName:  Onboard IGD
	Subsystem: Dell Skylake Integrated Graphics
--
01:00.0 3D controller: NVIDIA Corporation GM107GLM [Quadro M1000M] (rev ff)
	Kernel modules: nvidiafb, nouveau, nvidia_361
02:00.0 Network controller: Intel Corporation Wireless 8260 (rev 3a)

artur@pandaadb:~$ uname -a
Linux pandaadb 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux




```

I installed the Additional Drivers with this version of NVIDIA: 
V 361.42 from nvidia-361 (proprietary, tested) 

The other card runs on: 
"Using Processor microcode firmware for Intel CPUs from intel microcode (proprietary)" - Note, I am not sure what this means. 

Maybe the lshw output gives some more information: 

```
artur@pandaadb:~$ sudo lshw -numeric -C display
  *-display               
       description: VGA compatible controller
       product: Intel Corporation [8086:191B]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:126 memory:db000000-dbffffff memory:70000000-7fffffff ioport:f000(size=64

```

Now I managed to install the nvidia drivers by following the tutorials. I had to disable Secure Boot (NVIDIA setup actually prompts for that), for I was stuck in the log-in loop. The nvidia settings showed up correct (in the control center). I set it to Performant mode and started working when I noticed a few things.

* Laggy screens. When scrolling or switching between windows, the screen would have weird pixeling, it would lag behind, the words would overlap. Sadly this goes away quite quickly so I can't take a screenshot to demonstrate. I hope the description is okay.
* Terminal is lagging behind. Even a few ll commands would force the screen to its knees. 
* Typing in the browser, sometimes the typing would lag about 1-2 letters behind. 
* Streaming netflix would appear laggy and have picture problems (same with youtube) 

I started researching and I ended up finding a lot of people saying they install CompizConfig Manager and enable a workaround to force redraws. I did the same and installed it, and there was no change. 

Now here's the kicker though. I got desperate and was not sure what else to do, so I went to the NVIDIA settings and enable the power-safe-mode. (I believe that is why it only shows 1 graphics card for the lshw output). This fixed it (mostly, as I believe my mouse is a bit slow, but then again I've been chasing this for so long that this could be a red herring/a **** mouse/me being tired). 

But: My terminal now works fine, my netflix/youtube has no issues/ my scrolling is fixed.

Now the question is: Is that the correct thing to do? I seem to have this quite good nvidia chip in my laptop and I would like to use it. Now it seems I simply disabled it and it seems to work. 

Other info:

* I manually installed the NVIDIA driver using the purge + reinstall method that I have found multiple times online
* I never installed any other drivers (for the intel graphics). 
* Orriginally the additional drivers where not using the options that I am using now. I had 2 options on each, I chose the others (saying the non default) 

Please let me know if you need any more info - I am very happy to support and help as much as I can. I have *some* experience using ubuntu, however I have rather little with regards to hardware config. 

Thanks! 

Artur

---

### Post by Jan_Drewes on 2016-06-12
Hi Artur,

if you search this forum a little, you will find a very extensive thread about the XPS 15 9550, which is nearly identical in hardware to the Precision 5510. I have a precision too, I found my solutions in the XPS15 thread.

Cheers,

Jan

---

### Post by artur20 on 2016-06-13
Hi Jan,

thanks for pointing that out. I assume you meant this thread: [http://ubuntuforums.org/showthread.php?t=2301071&page=8](http://ubuntuforums.org/showthread.php?t=2301071&page=8) ?

I am still reading through it but it seems that this one is sadly also not fixing my issue. I wanted to update this threads with things I have tried that have not worked for me so far: 

1. Installing new Nvidia drivers. I have now tried 361, 364 and 367 from the nvidia repos, however the screen tearing still consists to be present. (I believe however that the new drivers did fix things like the terminal lagging. Browser scrolling and video input is still broken) 
2. running 

nvidia-settings --assign CurrentMetaMode="nvidia-auto-select +0+0 { ForceCompositionPipeline = On }

This was recommended by someone ob the official ubuntu IRC channel as a fix. I have also seen this in multiple forums. It did not do anything for me. 
3. Updating /etc/X11/xorg.cong 

I have done: 

artur@pandaadb:~$ cat /etc/X11/xorg.conf.backup 
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "None"
EndSection


Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection


Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
    Option "RegistryDwords" "PerfLevelSrc=0x2233"
    Option "TripleBuffer" "True"
    OPTION "TearFree"     "True"
EndSection


Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection

Non of these have changed anything. I believe some of these have actually caused my system to crash and I had to reverse them in recovery mode.

4. Adding -bs flag to /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf 
Also no effect. It broke my system and I had to crash it.

Apart from that I made sure that I have all dell firmware installed and the latest drivers as well as an up to date BIOS. Dell is conveniently ignoring all my requests for any support so no idea if they have actually make this work or they are just advertising this laptop as ubuntu-ready-to-go. The orginial laptop came with a ubuntu 14 pre-installed. I ran into the nvidia-screen-freeze bug and had to upgrade to ubuntu 16.04 (I did a fresh install, not an update) 

I am still looking and hoping, but I am close to admitting defeat and just keep using the power-safe-mode and intel since that one at least let's me watch a movie and scroll a website. I also opened:

[https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/1591260](https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/1591260)

Thanks 

Artur

---

### Post by i2000s2 on 2016-07-25
Hi,


I saw the nouveau driver installed in parallel with the nvidia driver. I remember when I was installing the nvidia driver on my thinkpad P50, I uninstalled/disabled the nouveau driver first, and I didn't use the nvidia driver from the additional driver interface. Plus, when you install the nvidia driver (367 should work now), please read the installation process log on your bash window. If it fails to in cope with the kernel, there will be some error. Feel free to try the debugging steps in the other thread.

Here is my setting for now:
```
$ lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)
    Subsystem: Lenovo Skylake Integrated Graphics
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller: NVIDIA Corporation GM107GLM [Quadro M1000M] (rev a2)
    Subsystem: Lenovo GM107GLM [Quadro M1000M]
    Kernel driver in use: nvidia



```

Good luck!

---

### Post by artur20 on 2016-07-26
Hi,

I am going through the other thread to provide as much info as possible. 

1. I think I got rid of the [COLOR=#000000]nouveau driver. I purged all nvidia drivers and installed the 367. However, I did not install it from scratch, but rather added a page to my repositories that found the dirvers. So I installed them using apt-get (I believe). I am using: 

[/COLOR]graphics-drivers-ubuntu-ppa-xenial.list ( I think this is the right one) 

Question: is it wrong to use these repos and should I install the nvidia driver from the nvidia page? 

Apart from that, here are the outputs that are requested in the other thread:

```
artur@pandaadb:~$ lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06)
    DeviceName:  Onboard IGD
    Subsystem: Dell Skylake Integrated Graphics
--
01:00.0 3D controller: NVIDIA Corporation GM107GLM [Quadro M1000M] (rev a2)
    Subsystem: Dell GM107GLM [Quadro M1000M]
    Kernel driver in use: nvidia

``````

artur@pandaadb:~$ sudo lshw -C display


  *-display               
       description: 3D controller
       product: GM107GLM [Quadro M1000M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:dc000000-dcffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:e000(size=128) memory:dd000000-dd07ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:126 memory:db000000-dbffffff memory:70000000-7fffffff ioport:f000(size=64)


```

This is the Xorg config. This (I believe) is currently disabled because I am running in Power save mode. So at the moment I think Intel integrated is the only thing running on my system. 

```
artur@pandaadb:~$ ls /etc/X11/
app-defaults  default-display-manager  rgb.txt  xkb                 xorg.conf.06102016  xorg.conf.06132016  xorg.conf.backup  Xreset    Xresources  Xsession.d        xsm
cursors       fonts                    xinit    xorg.conf.06072016  xorg.conf.06122016  xorg.conf.07072016  xorg.conf.faulty  Xreset.d  Xsession    Xsession.options  Xwrapper.config

```

My Nvidia XServer Settings is available and I can enable the NVIDIA chip. The box does start up (it usually crashes after immidiate switch, unless I power down/up again - e.g. log in/out does not work)


These are the requested values from the first page: 

```
artur@pandaadb:~$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                              0.8-3ubuntu1                                                amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  bumblebee                                  3.2.1-10                                                    amd64        NVIDIA Optimus support for Linux
ii  bumblebee-nvidia                           3.2.1-10                                                    amd64        NVIDIA Optimus support using the proprietary NVIDIA driver
ii  libcuda1-364                               364.19-0ubuntu0~gpu16.04.6                                  amd64        NVIDIA CUDA runtime library
rc  nvidia-361                                 361.42-0ubuntu2                                             amd64        NVIDIA binary driver - version 361.42
ii  nvidia-364                                 364.19-0ubuntu0~gpu16.04.6                                  amd64        NVIDIA binary driver - version 364.19
rc  nvidia-367                                 367.18-0ubuntu0~gpu16.04.3                                  amd64        NVIDIA binary driver - version 367.18
rc  nvidia-opencl-icd-361                      361.45.11-0ubuntu0~gpu16.04.1                               amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-364                      364.19-0ubuntu0~gpu16.04.6                                  amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-367                      367.18-0ubuntu0~gpu16.04.3                                  amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                               0.8.2                                                       amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                            367.35-0ubuntu0~gpu16.04.1                                  amd64        Tool for configuring the NVIDIA graphics driver
ii  primus                                     0~20150328-1                                                amd64        client-side GPU offloading for NVIDIA Optimus



```

```
artur@pandaadb:~$ dkms status
bbswitch, 0.8, 4.4.0-24-generic, x86_64: installed
bbswitch, 0.8, 4.4.0-28-generic, x86_64: installed
bbswitch, 0.8, 4.4.0-31-generic, x86_64: installed
nvidia-364, 364.19, 4.4.0-24-generic, x86_64: installed
nvidia-364, 364.19, 4.4.0-28-generic, x86_64: installed
nvidia-364, 364.19, 4.4.0-31-generic, x86_64: installed



```

```
artur@pandaadb:~$ lsmod | grep nvidia
nvidia_drm             45056  0
nvidia_modeset        753664  1 nvidia_drm
nvidia              10203136  1 nvidia_modeset
drm_kms_helper        147456  2 i915_bpo,nvidia_drm
drm                   360448  8 i915_bpo,drm_kms_helper,nvidia_drm



```


```
artur@pandaadb:~$ dpkg -l | grep linux-
ii  linux-base                                 4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                             1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                              4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-24                     4.4.0-24.43                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-24-generic             4.4.0-24.43                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-28                     4.4.0-28.47                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic             4.4.0-28.47                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31                     4.4.0-31.50                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic             4.4.0-31.50                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.6.0-040600                 4.6.0-040600.201606100558                                   all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600-generic         4.6.0-040600.201606100558                                   amd64        Linux kernel headers for version 4.6.0 on 64 bit x86 SMP
ii  linux-headers-generic                      4.4.0.31.33                                                 amd64        Generic Linux kernel headers
rc  linux-image-4.4.0-21-generic               4.4.0-21.37                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-22-generic               4.4.0-22.40                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-24-generic               4.4.0-24.43                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic               4.4.0-28.47                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic               4.4.0-31.50                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-generic         4.4.0-21.37                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-22-generic         4.4.0-22.40                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-24-generic         4.4.0-24.43                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic         4.4.0-28.47                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic         4.4.0-31.50                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                        4.4.0.31.33                                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                       4.4.0-31.50                                                 amd64        Linux Kernel Headers for development
ii  linux-signed-generic                       4.4.0.31.33                                                 amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-4.4.0-22-generic        4.4.0-22.40                                                 amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-24-generic        4.4.0-24.43                                                 amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-28-generic        4.4.0-28.47                                                 amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-31-generic        4.4.0-31.50                                                 amd64        Signed kernel image generic
ii  linux-signed-image-generic                 4.4.0.31.33                                                 amd64        Signed Generic Linux kernel image
ii  linux-sound-base                           1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
ii  syslinux-common                            3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                            2:3.63+dfsg-2ubuntu8                                        amd64        Bootloader for Linux/i386 using MS-DOS floppies



```



Generally I was of the opinion that my drivers were correctly installed. I got the repository (rather than using the nvidia driver) from #ubuntu on irc. They recommended switching the drivers. Updating the drivers did fix some crashes it appeared, however it did not fix my screen tearing/waving (I am not sure of the correct word for this effect).

---

### Post by mheidt on 2016-08-12
arthur,

How did you manage to install a nvidia driver? 
Via Driver Manager, it stalls. Only in Linux safe mode I am asked to disable UEFI Safe Mode, when starting driver manager. This time selecting an nvidia driver, asks me to reboot.
But after the reboot i get a black screen.

Kind regards,
Markus

---

### Post by artur20 on 2016-08-17
I used the drivers ppa. There is a discription here:

[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

then I think I simply did: 

[COLOR=#111111][FONT=Consolas] sudo apt-get purge nvidia-*
[/FONT][/COLOR]sudo add-apt-repository ppa:graphics-drivers/ppa[COLOR=#111111][FONT=Ubuntu] and then [/FONT][/COLOR]sudo apt-get update[COLOR=#111111][FONT=Ubuntu].
[/FONT][/COLOR]sudo apt-get install nvidia-367 

I think I had to turn off the UEFI Safe mode in the bios. 

There is some info here: [http://askubuntu.com/questions/760934/graphics-issues-after-installing-ubuntu-16-04-with-nvidia-graphics](http://askubuntu.com/questions/760934/graphics-issues-after-installing-ubuntu-16-04-with-nvidia-graphics)


I install it in tty. 

> **mheidt said:**
> arthur,

How did you manage to install a nvidia driver? 
Via Driver Manager, it stalls. Only in Linux safe mode I am asked to disable UEFI Safe Mode, when starting driver manager. This time selecting an nvidia driver, asks me to reboot.
But after the reboot i get a black screen.

Kind regards,
Markus

---

### Post by artur20 on 2016-08-24
I know believe this to be a Xorg server / vsync issue - lacking the ability to sync the 2 gpus together. 

See: [https://devtalk.nvidia.com/default/topic/775691/linux/vsync-issue-nvidia-prime-ux32vd-with-gt620-m-/1](https://devtalk.nvidia.com/default/topic/775691/linux/vsync-issue-nvidia-prime-ux32vd-with-gt620-m-/1)

However, I upgrade to driver 370 and it does improve the situation somewhat.

---

