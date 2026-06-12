---
title: "Thinkpad W530 nvidia"
date: 2012-06-20
forum: Hardware
---

### Post by Belrog on 2012-06-20
I'm trying to get the nvidia driver for the quadro k1000m to run, and have had no luck with any of the other threads. Help would be greatly appreciated.

Its an optimus setup, with the default X running on the intel graphics. I've added some command outputs at the bottom for context.

I have no xorg.conf at the moment, as the nvidia-xconfig file gives me an error referring me to the syslog, which only has the following entries about nvidia:

```

nvidia: module license 'NVIDIA' taints kernel.
nvidia 0000:01:00.0: power state changed by ACPI to D0
nvidia 0000:01:00.0: power state changed by ACPI to D0
nvidia 0000:01:00.0: enabling device (0004 -> 0007)
nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
nvidia 0000:01:00.0: setting latency timer to 64

```---
```

$ lsmod|grep nvidia
nvidia              10888310  0 

```--
```

# grep -r nvidia_current /etc
/etc/alternatives/x86_64-linux-gnu_nvidia_modconf:alias nvidia nvidia_current
/etc/modprobe.d/nvidia-graphics-drivers.conf:alias nvidia nvidia_current

```--
```

# find / -name nvidia.ko
/var/lib/dkms/nvidia-current/302.17/build/nvidia.ko
/lib/modules/3.2.0-25-generic/kernel/drivers/video/nvidia/nvidia.ko

```--
```

# find / -name nvidia_current.ko
/var/lib/dkms/nvidia-current/302.17/3.2.0-25-generic/x86_64/module/nvidia_current.ko
/lib/modules/3.2.0-25-generic/updates/dkms/nvidia_current.ko

```--
```

# lshw -short -class display
H/W path           Device      Class          Description
=========================================================
/0/100/1/0                     display        NVIDIA Corporation
/0/100/2                       display        Ivy Bridge Graphics Controller

```--
```

# lspci -vnn | grep '\''[030[02]\]'
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0ffc] (rev a1) (prog-if 00 [VGA controller])

```--
```

# cat /etc/modprobe.d/disable-nouveau.conf
blacklist nouveau
options nouveau modeset=0

```--
```

# uname -a
Linux snip 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```--
```

# xrandr
Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
LVDS1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1600x900       60.2*+   50.0  
   1440x900       59.9  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by kc1di on 2012-06-20
Don't know if you tried it yet by optimus requires the bumblebee driver set. here's a link to the ubuntu bumblebee page

[https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee")

---

### Post by Belrog on 2012-06-20
> **kc1di said:**
> Don't know if you tried it yet by optimus requires the bumblebee driver set. here's a link to the ubuntu bumblebee page

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

I'm trying to just get the nvidia working before I throw in the optimus side of things, unless I'm unable to get to the nvidia unless I go through optimus?

---

### Post by JanneM on 2012-06-21
Disclaimer: I'm still waiting for my T430 so this is not personal experience.

But from what I have read, if you want to use the NVIDIA card without Bumblebee, you normally need to explicitly select it as the sole graphics device in the BIOS setup. If you don't, the system will use the included graphics and ignore the NVIDIA card.

[COLOR=Silver] Which leads me to wonder, are you sure the live USB system actually uses the NVIDIA card? EDIT: I mixed up that part with a different thread. [/COLOR]

---

### Post by Rob_H on 2012-07-01
Yes, you need Bumblebee if you want to use the NVIDIA hardware unless your BIOS lets you disable the Intel adapter.

Please let us know how you do with this. I'm looking at this laptop, too.

---

### Post by Yellow Pasque on 2012-07-01
The last time I checked, Bumblebee wasn't working with Kepler-based nvidia cards yet. You should completely remove the nvidia driver and just use the Intel one for now.

---

### Post by Rob_H on 2012-07-01
> **Temüjin said:**
> The last time I checked, Bumblebee wasn't working with Kepler-based nvidia cards yet. You should completely remove the nvidia driver and just use the Intel one for now.

I ran across [this page]("http://www.linlap.com/wiki/lenovo+thinkpad+w530") on the Linux Laptop Wiki that says you can set the video to "Discrete" in the BIOS to get the NVIDIA card to work. Supposedly, then, you don't need Bumblebee.

---

### Post by Yellow Pasque on 2012-07-01
> **Rob_H said:**
> I ran across [this page]("http://www.linlap.com/wiki/lenovo+thinkpad+w530") on the Linux Laptop Wiki that says you can set the video to "Discrete" in the BIOS to get the NVIDIA card to work. Supposedly, then, you don't need Bumblebee.
That's nice. A lot of systems don't have a BIOS switch.

---

### Post by kripkenstein on 2012-07-24
I just tested a new W530 with Ubuntu 12.04. Sadly the NVidia GPU is not detected, even with it set up in the BIOS - all it sees is a low-res unaccelerated VGA-compatible driver. This is maybe not that surprising as NVidia's website does not list the K1000M as being supported by their linux drivers.

Switching to the Intel graphics in the BIOS works, they are detected and run properly. But of course performance is not on par with what the NVidia GPU could provide.

---

### Post by ineedtosleep on 2012-08-06
> **kripkenstein said:**
> I just tested a new W530 with Ubuntu 12.04. Sadly the NVidia GPU is not detected, even with it set up in the BIOS - all it sees is a low-res unaccelerated VGA-compatible driver. This is maybe not that surprising as NVidia's website does not list the K1000M as being supported by their linux drivers.<br />
<br />
Switching to the Intel graphics in the BIOS works, they are detected and run properly. But of course performance is not on par with what the NVidia GPU could provide.

I can also confirm this. For now it seems that the K1000M/2000M series of GPUs are *too* new, but the good news is that the Bumblebee installation is pretty painless and work well on my K2000M. The only major issue I have now is just the fact that I can't use multiple monitors just yet (since the external ports, including the ones on the ThinkPad docks, are all handled by the GPU). Never had a workflow to include workspace, but it seems like now's the time to adjust.

---

### Post by kalmos on 2012-08-07
I just want to contribute some links.

When I get around to installing and playing with settings, I'll let you know what happens. I'm using a Thinkpad W530 with K1000M. I expect that I'll have the same results as ineedtosleep and kripkenstein.


See the list of supported devices here: [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Quadro cards are listed but Quadro K (Kepler) cards are not listed for version 295.71 released 2012.08.07 for Linux 64-bit.


See a table of Quadro M cards here: [http://www.nvidia.com/object/IO_11761.html](http://www.nvidia.com/object/IO_11761.html)

Screenshot below shows the "Quadro Mobile Product Comparison". Notice that all cards with "K" are listed as "(New!)".

[[IMG]http://i.imgur.com/tDtrkl.png[/IMG]]("http://imgur.com/tDtrk")


The K1000M and K2000M cards are listed for beta NVIDIA drivers with versions 304.22, 304.30, and 304.32. See here: [http://www.nvidia.com/Download/Find.aspx?lang=en-us](http://www.nvidia.com/Download/Find.aspx?lang=en-us)

I haven't tried installing the beta drivers.

---

### Post by KidCoding on 2012-08-20
Bumblebee works "almost" fine for me on my W530. It allows me to run CUDA codes on the GPU using optirun.

Nevertheless, I still have problems with external monitors and my graphic card is not seen as a K2000M but a Q2100M :confused: (detected device when I launch optirun with a CUDA sample code fluidsGL  => CUDA device [Quadro 2100M].)

For the multi-screen/external desktop, you can get information there  [http://sagark.org/optimal-ubuntu-graphics-setup-for-thinkpads/ ]("http://sagark.org/optimal-ubuntu-graphics-setup-for-thinkpads/")    and there [http://sagark.org/thinkdisp-about-installation/ ]("http://sagark.org/thinkdisp-about-installation/")  . I hope this helps.

Kid

---

### Post by KidCoding on 2012-08-27
Any updates?

---

### Post by krismatth3 on 2012-08-27
K1000M on a Thinkpad W530 works perfectly for me in Ubuntu 12.04 and Fedora 17. Set to discrete graphics in BIOS, install the driver and good to go.

---

### Post by kalmos on 2012-08-27
I followed the instructions here: [http://sagark.org/optimal-ubuntu-graphics-setup-for-thinkpads/](http://sagark.org/optimal-ubuntu-graphics-setup-for-thinkpads/)

bumblebee and the thinkdisp widget seem to work ok most of the time. I can use an external monitor and turn it on/off with the widget controls.

It is not perfect, I've noticed three problems:

1. When I resume after locking screen or suspending, the external monitor refuses to be detected. A restart fixes the problem.

2. When I fullscreen a flash video like youtube or vimeo the video is enlarged and stretched so that half of the video is fullscreen on one monitor but the other monitor is not displaying the video.

3. The external monitor automatically turns off after not moving my mouse for some period. The caffeine widget does not keep the monitor from turning off, I must move the mouse.


I think I would prefer to do what krismatth3 did and just set graphics to discrete in the BIOS and call it done.

---

### Post by KidCoding on 2012-08-28
I have switched to discrete graphics (only gpu) in the BIOS. External display works perfectly!!!

But when i launch glxspheres, I have 60 fps.

With bumblebee, optirun glxspheres is running at +/- 200 fps. :confused:

Do you have the same problem/issue?

Optirun is supposed to force the system to use GPU. As I set the discrete graphics BIOS option, everything is supposed to be done on the GPU... So, in both case, evrything goes through the  GPU but I have 40% of the performances when I use the discrete  BIOS option.

weird...

---

### Post by kalmos on 2012-08-28
I am now on discrete in the BIOS and using newer nvidia drivers (304.43) from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/) that support K1000M. External monitor works perfectly as far as I'm concerned.

```
$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 304.43-0ubuntu1~precise~xup1
  Candidate: 304.43-0ubuntu1~precise~xup1
  Version table:
 *** 304.43-0ubuntu1~precise~xup1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/restricted amd64 Packages
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages

```

I also get 60fps on glxspheres, but that doesn't matter to me. Performance seems to be great in any app I've tried. Haven't tried 3D games.

```
$ glxspheres
Polygons in scene: 62464
Visual ID of window: 0x27
Context is Direct
OpenGL Renderer: Quadro K1000M/PCIe/SSE2
58.311433 frames/sec - 65.075559 Mpixels/sec
```

---

### Post by KidCoding on 2012-08-29
from here [https://github.com/Bumblebee-Project/Bumblebee/issues/243](https://github.com/Bumblebee-Project/Bumblebee/issues/243),

You can get better perf by disabling vertical sync in the nvidia settings gui ( uncheck sync to vblank option under OpenGL settings). But this causes sync glitch (horizontal lines appears in the OpenGl window).

KiD

---

### Post by krismatth3 on 2012-09-04
But since your display is not refreshing at more than 60hz, greater than 60 fps is completely pointless. :)

---

### Post by hgroover on 2012-12-14
This may also be covered elsewhere but I thought I'd add this. I also have a new Lenovo Thinkpad W530. Installed Ubuntu 12.10 Secure Remix over a Windows 7 installation and created a dual boot configuration. No problems, boots every time.

I upgraded the memory to 16gb and it hangs on boot, sometimes with part of an [OK] boot message showing. Apparently a video problem, and similar to some of the problems people have seen on the Thinkpad with Nvidia using external monitors.

I tried adding acpi=noirq to the boot command line which worked sometimes (but is not recommended due to various performance issues).

Finally I added rootdelay=2 to the boot command line (using Grub customizer [http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183) )

Now it boots every time (and solves my problem). I only mention this here because there seems to be an initialization timing issue and the rootdelay (which we often use on embedded systems to allow multithreaded initialization of storage devices used for the root filesystem) seems to work around it. Waiting an extra 2 seconds on the rare occasions when I need to reboot is a perfectly acceptable workaround for me.

---

