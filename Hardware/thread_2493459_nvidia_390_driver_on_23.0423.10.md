---
title: "nvidia 390 driver on 23.04/23.10"
date: 2023-12-15
forum: Hardware
---

### Post by dltech on 2023-12-15
The debian team throws away the 390 driver from debian stable and advised to install it from sid repository. Therefore ubuntu 23 haven't got 390 driver in it's repositories too, only 525 like a debian stable. Trying to install 390 package leads to black screen. So I ask ubuntu team to add 390 package in the ubuntu 23 repository. Otherwise, the simplest way to install 390 driver on ubuntu is to delete him, and then install debian 12. 

links:
[https://wiki.debian.org/NvidiaGraphicsDrivers#Installation](https://wiki.debian.org/NvidiaGraphicsDrivers#Installation)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2046098](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2046098)
[https://packages.ubuntu.com/search?keywords=nvidia-driver-390&searchon=names&suite=all&section=all](https://packages.ubuntu.com/search?keywords=nvidia-driver-390&searchon=names&suite=all&section=all)

---

### Post by Bashing-om on 2023-12-15
dltech ; Hey --

May I suggest that you are a bit short on research ?

Our trusted PPA still maintains the Nvidia 390 driver up to 23.04 release:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Cheers

---

### Post by deadflowr on 2023-12-16
> The debian team throws away the 390 driver from debian stable and advised to install it from sid repository. Therefore ubuntu 23 haven't got 390 driver in it's repositories too, only 525 like a debian stable.

What Debian does with those drivers is unrelated to what Ubuntu has done with those drivers.
The drivers aren't from Debian anyway.
That said, Ubuntu removed them for having reached EOL upstream: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/2035189]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/2035189")

You mentioned in your bug report that Ubuntu ships the 340 driver but that's not true.
They ship a package called nvidia-340 but it's only a transitional package that installs the open source nouveau driver.

What to do? what to do?

You might have to look into this [https://github.com/MeowIce/nvidia-legacy]("https://github.com/MeowIce/nvidia-legacy")
Says it's patched up to the latest kernels.

---

### Post by dltech on 2023-12-16
> **Bashing-om said:**
>  Our trusted PPA still maintains the Nvidia 390 driver up to 23.04 release: 
Sorry, forgot that trying to install driver from ppa caused to error while kernel modules building.
```
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; nvidia-dkms-390 (390.157-0ubuntu7) …
update-initramfs: deferring update (trigger activated)
Loading new nvidia-390.157 DKMS files...
Building for 6.5.0-14-generic
Building for architecture x86_64
Building initial module for 6.5.0-14-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/nvidia-dkms-390.0.crash'
Error! Bad return status for module build on kernel: 6.5.0-14-generic (x86_64)
Consult /var/lib/dkms/nvidia/390.157/build/make.log for more information.
dpkg: &#1086;&#1096;&#1080;&#1073;&#1082;&#1072; &#1087;&#1088;&#1080; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; nvidia-dkms-390 (--configure): &#1087;&#1086;&#1076;&#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089; &#1080;&#1079; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; nvidia-dkms-390 &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085; &#1089;&#1094;&#1077;&#1085;&#1072;&#1088;&#1080;&#1081; post-installation &#1074;&#1086;&#1079;&#1074;&#1088;&#1072;&#1090;&#1080;&#1083; &#1082;&#1086;&#1076; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080; 10

```

> [COLOR=#000000]You might have to look into this [/COLOR][https://github.com/MeowIce/nvidia-legacy](https://github.com/MeowIce/nvidia-legacy) 
They uses semi-working git-lfs, I can't download installer, because of authentication error.

As I understood there is a problem in building of nvidia module for new 6.5 kernel? [Build log.]("https://drive.google.com/file/d/1E4Ypw8gmWxf6P0tKz0pw0z2rQoG6gPPj/view?usp=sharing")

---

### Post by Yellow Pasque on 2023-12-16
> **deadflowr said:**
> You might have to look into this [https://github.com/MeowIce/nvidia-legacy]("https://github.com/MeowIce/nvidia-legacy")
Says it's patched up to the latest kernels.

They only kept up with nvidia 340 branch. For nvidia 390, they still have an old upstream version 350.151 and only have patches for kernel 5.18.

---

### Post by Yellow Pasque on 2023-12-16
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/2028165](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/2028165)
Okay, so there is a version that works with 6.5 kernel in Ubuntu 23.10 in the mantic-proposed repository. Remember to disable the proposed repo after you install the nvidia packages. You probably don't want to install everything in there..

---

### Post by dltech on 2023-12-17
Where I could find this hidden package? There isn't any nvidia-driver-390=390.157-0ubuntu8 in mantic-proposed and in graphics-drivers/ppa. Only nvidia-driver-390=390.157-0ubuntu7. Why this new package is not visible on repository web page? I even could not download it manually.

upd: I manually downloaded archives from [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/390.157-0ubuntu8](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/390.157-0ubuntu8) . Manually unpacked them, manually installed them, using commands:
```
sudo apt-src build nvidia-graphics-drivers-390
sudo apt install ./*.deb

```
It works! but I do not know, how to make it automatically.

---

### Post by dltech on 2023-12-17
Driver nvidia-driver-390=390.157-0ubuntu8 installs successfully, but with blackscreen after reload. xorg.conf, generated by nvidia-xconfig looks adequate. Where is an error?
In Xorg log I found "malloc(): unaligned tcache chunk detected".

---

### Post by SeijiSensei on 2023-12-17
I have a pretty old NVIDIA card

```
01:00.0 VGA compatible controller: NVIDIA Corporation GP108 [GeForce GT 1030] (rev a1)
```

It runs fine with driver 535.129.03 which was installed by default. Why would you want to use the 390-series driver?

---

### Post by dltech on 2023-12-17
> **SeijiSensei said:**
> Why would you want to use the 390-series driver?
[B]Black screen.
[/B][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293213&stc=1[/IMG]

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293213&stc=1[/IMG]
My xorg log. I do not found here something strange[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293213&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293213&stc=1[/IMG][ATTACH]293213[/ATTACH]. But in lightdm x log it ends with "malloc(): unaligned tcache chunk detected" message, and ligthtdm writes that "Process 1435 terminated with signal 11.  XServer 0: X server stopped". 
Sorry, new fixed driver crashes with segfault.

---

### Post by Yellow Pasque on 2023-12-17
I don't see anything wrong with the Xorg log.

> **SeijiSensei said:**
> I have a pretty old NVIDIA card

Pascal isn't that old. Anyway, the OP has a Fermi, "NVIDIA GPU GeForce GT 430 (GF108)", which is only supported up to 390.xx

---

### Post by SeijiSensei on 2023-12-17
> **Yellow Pasque said:**
> Pascal isn't that old.
I bought it refurbished over eight years ago. I think of that as "old" in the video adapter market since it's dominated by gamers.

---

### Post by dltech on 2023-12-17
> **Yellow Pasque said:**
> I don't see anything wrong with the Xorg log.
"Using 6144.00 MB of virtual memory for indirect memory access." - is it normal? It is not too much? Maybe this 6GB is the reason of segfault? Maybe wrong default xorg config?
If it normal, I will generate yet another bug with nvidia driver segfault error.
What tools I could use in order to catch the binary or library, which crashes the xorg?

---

### Post by scottbomb on 2024-02-10
I'm having the same issue. My laptop, which was running 390, recently booted to a black screen full of cryptic kernel output. I reinstalled Kubuntu and now I can only start it with nouveau.modeset=0 on the grub command line. Every time I try to install the drivers (the card calls for 390), it errors out...

> INFO:Enable nvidia
Removing old nvidia-390.157 DKMS files...
Deleting module nvidia-390.157 completely from the DKMS tree.
Loading new nvidia-390.157 DKMS files...
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/nvidia-dkms-390.0.crash'
Consult /var/lib/dkms/nvidia/390.157/build/make.log for more information.
dpkg: error processing package nvidia-dkms-390 (--configure):
 installed nvidia-dkms-390 package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent configuration of nvidia-driver-390:
 nvidia-driver-390 depends on nvidia-dkms-390 (<= 390.157-1); however:
  Package nvidia-dkms-390 is not configured yet.
 nvidia-driver-390 depends on nvidia-dkms-390 (>= 390.157); however:
  Package nvidia-dkms-390 is not configured yet.
dpkg: error processing package nvidia-driver-390 (--configure):
 nvidia-dkms-390
 nvidia-driver-390


---

### Post by scottbomb on 2024-02-10
apt install -f and nothing else I have tried with apt or dpkg works. Now I have to boot with nouveau.modeset=0

---

### Post by MAFoElffen on 2024-02-10
Backup...

The Ubuntu Graphics Team's "Propiertary GPU Drivers PPA", which I am a beta tester for: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=)

Still has NVidia Driver 390 built through Noble...

---

### Post by scottbomb on 2024-02-11
I tried that and got the same error. It looks like the repo is enabled alright.
```
scottbomb@laptop:/etc/apt/sources.list.d$ cat grap*
deb https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/ jammy main

```

In case this is helpful...
```
scottbomb@laptop:/etc/apt/sources.list.d$ sudo lshw -C display;
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: GK107GLM [Quadro K1100M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:b0000000-b0ffffff memory:80000000-8fffffff memory:90000000-91ffffff ioport:4000(size=128) memory:b1080000-b10fffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       logical name: /dev/fb0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom fb
       configuration: depth=32 driver=i915 latency=0 resolution=1920,1080
       resources: irq:35 memory:b1400000-b17fffff memory:a0000000-afffffff ioport:5000(size=64) memory:c0000-dffff

```

```

scottbomb@laptop:/etc/apt/sources.list.d$ sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000FF6sv000017AAsd0000221Ebc03sc00i00
vendor   : NVIDIA Corporation
model    : GK107GLM [Quadro K1100M]
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-390 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin


```

---

### Post by Yellow Pasque on 2024-02-11
> **MAFoElffen said:**
> The Ubuntu Graphics Team's "Propiertary GPU Drivers PPA", which I am a beta tester for: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa?field.series_filter=)
Still has NVidia Driver 390 built through Noble...

It's out of date though, as it only works up to kernel 6.4.
I made a PPA specifically to fix the issue. See: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/2051436](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/2051436)

---

### Post by MAFoElffen on 2024-02-11
Here is the problem:
```

scottbomb@laptop:/etc/apt/sources.list.d$ cat grap*
deb https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/ [COLOR=#ff0000]jammy[/COLOR] main

Is for Jammy, you were all talking about newer releases sand where it was dropped, which is a different issue altogether than to make it work for Jammy.

```
Read the second half of this: [https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164](https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164)

The 6.5.0 kernel was compile with gcc-12... Jammy has gcc-11. You will see, by the bug-report, changing the compiler in the work-around still doesn't work for NVidia's legacy drivers. Therefore the second half of that post is the work-around for legacy drivers... Uninstall the 6.5.0 series kernels and pin the kernels to 6.2.0 or remove the HWE stack so the kernels are at the 5.15 series.

Canonical & Launchpad is trying to work on a fix for legacy drivers working with 6.5.0 and newer kernels, but they are not there yet

---

### Post by Yellow Pasque on 2024-02-11
> **MAFoElffen said:**
> Here is the problem:
...
Canonical & Launchpad is trying to work on a fix for legacy drivers working with 6.5.0 and newer kernels, but they are not there yet

I've had multiple people tell me that the Jammy version of 390 in my PPA worked for them with 6.5, and while I don't have an Nvidia card to fully test it, I was able to verify that it builds/installs correctly in a Jammy VM.
As for the Mantic version, I just  straight copied the binaries from the Jammy version and didn't test it, so I wouldn't be surprised if that doesn't work.

---

### Post by scottbomb on 2024-02-11
That would explain why it was working just fine for a year and then just gave up the ghost.

---

### Post by scottbomb on 2024-02-11
Thank you. I was doing some internet searching but should have checked launchpad. I'll subscribe to that bug. This works perfectly, thanks again.

> **MAFoElffen said:**
> Here is the problem:
```

scottbomb@laptop:/etc/apt/sources.list.d$ cat grap*
deb https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu/ [COLOR=#ff0000]jammy[/COLOR] main

Is for Jammy, you were all talking about newer releases sand where it was dropped, which is a different issue altogether than to make it work for Jammy.

```
Read the second half of this: [https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164](https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164)

The 6.5.0 kernel was compile with gcc-12... Jammy has gcc-11. You will see, by the bug-report, changing the compiler in the work-around still doesn't work for NVidia's legacy drivers. Therefore the second half of that post is the work-around for legacy drivers... Uninstall the 6.5.0 series kernels and pin the kernels to 6.2.0 or remove the HWE stack so the kernels are at the 5.15 series.

Canonical & Launchpad is trying to work on a fix for legacy drivers working with 6.5.0 and newer kernels, but they are not there yet

---

### Post by MAFoElffen on 2024-02-12
> **Yellow Pasque said:**
> I've had multiple people tell me that the Jammy version of 390 in my PPA worked for them with 6.5, and while I don't have an Nvidia card to fully test it, I was able to verify that it builds/installs correctly in a Jammy VM.
As for the Mantic version, I just  straight copied the binaries from the Jammy version and didn't test it, so I wouldn't be surprised if that doesn't work.
I have a laptop that is stuck at nvidia-driver-390. I can test and verify that... I might have some time tonight to do that. BRB

---

### Post by MAFoElffen on 2024-02-12
@Yellow Pasque:

It built and worked just fine:
```

mafoelffen@Mikes-ThinkPad-T520:~$ nvidia-smi
Mon Feb 12 18:28:58 2024       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.157                Driver Version: 390.157                   |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  NVS 4200M           Off  | 00000000:01:00.0 N/A |                  N/A |
| N/A   71C    P0    N/A /  N/A |    181MiB /   964MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0                    Not Supported                                       |
+-----------------------------------------------------------------------------+
mafoelffen@Mikes-ThinkPad-T520:~$ uname -r
6.5.0-17-generic

```
I added it as a fix to my work-around post in Installations & Updates, credited to you: [https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164](https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164)

Which is also linked from post #2 of my ["Graphics Resolution" sticky]("https://ubuntuforums.org/showthread.php?t=1743535&p=10740087#post10740087")

---

