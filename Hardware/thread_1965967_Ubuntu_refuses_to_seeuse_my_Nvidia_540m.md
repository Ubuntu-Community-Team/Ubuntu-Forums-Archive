---
title: "Ubuntu refuses to see/use my Nvidia 540m"
date: 2012-04-26
forum: Hardware
---

### Post by skelooth on 2012-04-26
I'm running an ASUS all in one computer right now, and Ubuntu doesn't seem to want to recognize the graphic's card. 

Here's the output of glxinfo:
```


pavella@patrick:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

Here's the info from xorg.conf
```


Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I had to uninstall the (spelling?)nouvex driver before the NVidia driver would show up in the additional driver's dialog, but ubuntu doesn't seem to want to use it.

Does anyone have any help or ideas? I don't "Need" the nvidia card, but it sure would make the days at the office a lot nicer!

Thank you so much in advance.

---

### Post by lamb123 on 2012-04-26
I have Asus N53SV with same video card. I installed Bumblebee from PPA and got 3D working. Im not sure tho if it is using my nVidia card tho.

---

### Post by papibe on 2012-04-26
Hi skelooth.

Could you post the result of these commands?
```
lspci -nn | grep -i vga

sudo lshw -C display

lsmod | grep -i nvidia

apt-cache policy nvidia-current

grep -i glx /var/log/Xorg.0.log
```
Regards.

---

### Post by skelooth on 2012-04-26
> **papibe said:**
> Hi skelooth.

Could you post the result of these commands?
```
lspci -nn | grep -i vga

sudo lshw -C display

lsmod | grep -i nvidia

apt-cache policy nvidia-current

grep -i glx /var/log/Xorg.0.log
```
Regards.


```
pavella@patrick:~$ lspci -nn | grep -i vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 540M] [10de:0df4] (rev a1)

```
```
pavella@patrick:~$ sudo lshw -C display
[sudo] password for pavella: 
  *-display               
       description: VGA compatible controller
       product: GF108 [GeForce GT 540M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fa000000-faffffff memory:d0000000-d7ffffff memory:d8000000-d9ffffff ioport:e000(size=128) memory:fb000000-fb07ffff
  *-display
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:58 memory:fb400000-fb7fffff memory:c0000000-cfffffff ioport:f000(size=64)

```
```
pavella@patrick:~$ lsmod | grep -i nvidia
nvidia              12319264  0 

```
```
pavella@patrick:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 295.40-0ubuntu1
  Candidate: 295.40-0ubuntu1
  Version table:
 *** 295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
        100 /var/lib/dpkg/status
     295.33-0ubuntu1~precise~xup1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main amd64 Packages

```
```
pavella@patrick:~$ grep -i glx /var/log/Xorg.0.log
[    13.306] (II) LoadModule: "glx"
[    13.306] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    13.311] (II) Module glx: vendor="NVIDIA Corporation"
[    13.311] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
[    13.311] (II) Loading extension GLX
[    14.117] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

Does that help?

To the poster who mentioned bumble bee, I googled it and I'm not exactly sure what it is. I don't see it in the synaptic/apt repo, what's PPA?

Thanks friends!

---

### Post by haqking on 2012-04-26
I ran Ubuntu on my laptop with 540M and used propietary driver and  it worked fine as it does still with Debian.

Peace

---

### Post by skelooth on 2012-04-26
Question about the bumblebee thing. It says I need to use "optirun" to make things use the nvidia card... but that sucks, how can I get compiz et al working with bumble bee?

I might try the proprietary drivers.

---

### Post by papibe on 2012-04-26
You have an special configuration.

Your have Nvidia [Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux. Despite that fact, there are a couple of projects in progress that have some success to support it.

I would advice you to start reading a couple of useful threads. [This]("http://ubuntuforums.org/showthread.php?t=1657660") one to understand what it is (but a pessimist). And this [other]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") one (from post #7), with a more practical approach.

There are laptops that can either disable it, or simplify things by turning off the Nvidia card. Check your BIOS if you have any of those options.

I hope that helps,
Regards.

---

### Post by skelooth on 2012-04-26
Thank you much.

For posterity: I installed the proprietary NVIDIA driver from the NVIDIA website, and my pc slowed to a crawl and ultimately crashed until I put my xorg.conf back. 

Going to check bios now.

> **papibe said:**
> You have an special configuration.

Your have Nvidia [Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Which is a kind of new graphic architecture and it's just starting to be supported on Linux. Despite that fact, there are a couple of projects in progress that have some success to support it.

I would advice you to start reading a couple of useful threads. [This]("http://ubuntuforums.org/showthread.php?t=1657660") one to understand what it is (but a pessimist). And this [other]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia") one (from post #7), with a more practical approach.

There are laptops that can either disable it, or simplify things by turning off the Nvidia card. Check your BIOS if you have any of those options.

I hope that helps,
Regards.

---

### Post by skelooth on 2012-04-26
I think I'm going backwards here :3

Is there a way to get Ubuntu to just use the Intel card portion of the system to use compiz then? Compiz has a few usability features/shortcuts that I'm really missing, particularly zooming.

---

### Post by Yellow Pasque on 2012-04-26
You have to remove the nvidia proprietary driver before the intel GPU's 3D will work correctly...

---

### Post by skelooth on 2012-04-27
I went into Synaptic and uninstalled anything with the word NVIDIA in it.

Then I changed my xorg.conf to the intel driver instead of nvidia

Still no go on the 3d acceleration.

Anyone else have any ideas?

---

### Post by Yellow Pasque on 2012-04-27
Pastebin your /var/log/Xorg.o.log file

---

### Post by skelooth on 2012-04-27
> **Temüjin said:**
> Pastebin your /var/log/Xorg.o.log file

Here it is:
[http://pastebin.com/820JFhsN](http://pastebin.com/820JFhsN)

---

### Post by Yellow Pasque on 2012-04-27
```
[  5414.367] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  5414.375] (II) Module glx: vendor="NVIDIA Corporation"
[  5414.375]    compiled for 4.0.2, module version = 1.0.0
[  5414.375]    Module class: X.Org Server Extension
[  5414.375] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
```

You still have nvidia version of libgl(x) installed. Try:
```
sudo apt-get install --reinstall libgl1-mesa-glx xserver-xorg-core
```
Then log out/in.

---

### Post by skelooth on 2012-04-27
That did it, thank you so much!

> **Temüjin said:**
> ```
[  5414.367] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  5414.375] (II) Module glx: vendor="NVIDIA Corporation"
[  5414.375]    compiled for 4.0.2, module version = 1.0.0
[  5414.375]    Module class: X.Org Server Extension
[  5414.375] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:57:38 PDT 2012
```

You still have nvidia version of libgl(x) installed. Try:
```
sudo apt-get install --reinstall libgl1-mesa-glx xserver-xorg-core
```
Then log out/in.

---

