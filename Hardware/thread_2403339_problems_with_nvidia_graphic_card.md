---
title: "problems with nvidia graphic card"
date: 2018-10-10
forum: Hardware
---

### Post by c-bessem on 2018-10-10
Hi,

I installed unbuntu 18.04 on my laptop (Asus VivoBook) with an nvidia graphic card GeForce GTX 1050. Every time I logged, my laptop froze and the only way to get it to work was to add "nouveau.modeset=0" to the grub interface and this even after installing the nvidia drivers.
I run these series of command with the following results:
```

>lspci -vnn | grep -i VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:591b] (rev 04) (prog-if 00 [VGA controller])

>lspci -nnk | grep -iA2 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:591b] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1a10]
    Kernel driver in use: i915

>lspci -vnn | grep -i 3D
01:00.0 3D controller [0302]: NVIDIA Corporation GP107M [GeForce GTX 1050 Mobile] [10de:1c8d] (rev a1)

>sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001C8Dsv00001043sd00001A10bc03sc02i00
vendor   : NVIDIA Corporation
model    : GP107M [GeForce GTX 1050 Mobile]
driver   : nvidia-driver-390 - third-party free
driver   : nvidia-driver-396 - third-party free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

>sudo ubuntu-drivers list
nvidia-driver-396
nvidia-driver-390

```

So it seems that ubuntu sees the nvidia graphic card but is using the integrated one. Is there a way to solve the problem?
Can someone help me?

Thanks

---

### Post by Autodave on 2018-10-10
What driver did you install?  Where did you get the driver from?

---

### Post by c-bessem on 2018-10-10
Here are the commands I used for the installation:

```

[COLOR=#000000][FONT=menlo]> sudo add-apt-repository ppa:graphics-drivers/ppa
[/FONT][/COLOR][COLOR=#000000][FONT=menlo]> sudo apt update
[/FONT][/COLOR][COLOR=#000000][FONT=menlo]> [/FONT][/COLOR][COLOR=#000000][FONT=menlo]sudo apt install nvidia-396[/FONT][/COLOR][COLOR=#000000][FONT=menlo]
[/FONT][/COLOR]

```

---

### Post by Bashing-om on 2018-10-10
c-bessem; Hello =

I am of the opinion that " sudo apt install nvidia-396" had no result; as the packaging has been changed for the Nvidia install.

Take a look:
```

dpkg -l | grep -i nvidia

```

the driver is not installed ?

try as :
```

sudo apt install nvidia-driver-396

```
be aware that Nvidia recommends the 390 version driver for your card:
[https://www.nvidia.com/Download/driverResults.aspx/137276/en-us](https://www.nvidia.com/Download/driverResults.aspx/137276/en-us)

[INDENT]my bit to try and help
[/INDENT]

---

### Post by c-bessem on 2018-10-12
Hi Bashing-om,

Thanks for the advice,
when I use the first command i get this results
```

>dpkg -l | grep -i nvidia

ii  libnvidia-cfg1-396:amd64                   396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-396                       396.54-0ubuntu0~gpu18.04.1              all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-390:amd64                390.77-0ubuntu0~gpu18.04.1              amd64        NVIDIA libcompute package
rc  libnvidia-compute-390:i386                 390.77-0ubuntu0~gpu18.04.1              i386         NVIDIA libcompute package
ii  libnvidia-compute-396:amd64                396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA libcompute package
ii  libnvidia-compute-396:i386                 396.54-0ubuntu0~gpu18.04.1              i386         NVIDIA libcompute package
ii  libnvidia-decode-396:amd64                 396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-396:i386                  396.54-0ubuntu0~gpu18.04.1              i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-396:amd64                 396.54-0ubuntu0~gpu18.04.1              amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-396:i386                  396.54-0ubuntu0~gpu18.04.1              i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-396:amd64                   396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-396:i386                    396.54-0ubuntu0~gpu18.04.1              i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-396:amd64                     396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-396:i386                      396.54-0ubuntu0~gpu18.04.1              i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-396:amd64                   396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-396:i386                    396.54-0ubuntu0~gpu18.04.1              i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
rc  nvidia-compute-utils-390                   390.77-0ubuntu0~gpu18.04.1              amd64        NVIDIA compute utilities
ii  nvidia-compute-utils-396                   396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA compute utilities
rc  nvidia-dkms-390                            390.77-0ubuntu0~gpu18.04.1              amd64        NVIDIA DKMS package
ii  nvidia-dkms-396                            396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA DKMS package
ii  nvidia-driver-396                          396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA driver metapackage
rc  nvidia-kernel-common-390                   390.77-0ubuntu0~gpu18.04.1              amd64        Shared files used with the kernel module
ii  nvidia-kernel-common-396                   396.54-0ubuntu0~gpu18.04.1              amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-396                   396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA kernel source package
ii  nvidia-prime                               0.8.8.1                                 all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            396.54-0ubuntu0~gpu18.04.1              amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-396                           396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-396              396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA binary Xorg driver

``` 

Then as you advised I installed the nvidia driver 390 using 
```

sudo apt install nvidia-driver-390

```

The installation seems to have worked and the 390 is intalled but when I check which graphic card is used, i still get the same results as the first time (first post). also when I restarted the laptop and did not use the nouveau.modeset=0 in the GRUB start page, ubuntu froze at the loggin step and I had to restart it again using the nouveau.modeset=0.
Is there a way to make the nouveau.modeset=0 permanent and not having to input it every time at the GRUB page?

Thank you for your help

---

### Post by Bashing-om on 2018-10-12
c-bessem; Well -

Need to see current info as to what is installed, and what the system expects.
post back:
```

dpkg -l | grep -i nvidia
cat /var/log/gpu-manager.log

```
where I do anticipate that there exist a driver conflict between 390 and 396.
Booting nomodeset is not an optimum solution as then Kernel Mode Setting is defeated.

[INDENT][INDENT]do the right thing
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2018-10-14
See if this page helps: [https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu](https://www.linuxbabe.com/desktop-linux/switch-intel-nvidia-graphics-card-ubuntu)
```
prime-select query
sudo prime-select nvidia
```

> **Bashing-om said:**
> be aware that Nvidia recommends the 390 version driver for your card

Just curious - How did you come to that conclusion? Both the 390.xx and 396.xx drivers support the GPU.

> Is there a way to make the nouveau.modeset=0 permanent and not having to input it every time at the GRUB page?
You edit /etc/default/grub and add it to the "GRUB_CMDLINE_LINUX_DEFAULT=" line. When you're done, you run:
```
sudo update-grub2
```

---

### Post by SeijiSensei on 2018-10-14
If you only want to use the NVIDIA card, see if there's an option in the BIOS to turn off the Intel adapter.

---

### Post by Bashing-om on 2018-10-14
@ Temüjin -

> 
&#65532; Originally Posted by Bashing-om &#65532;
be aware that Nvidia recommends the 390 version driver for your card
//
Just curious - How did you come to that conclusion? Both the 390.xx and 396.xx drivers support the GPU.

> 
model    : GP107M [GeForce GTX 1050 Mobile]

My reference is:
[https://www.nvidia.com/Download/driverResults.aspx/137276/en-us](https://www.nvidia.com/Download/driverResults.aspx/137276/en-us)

[INDENT]I bow to your knowledge
[/INDENT]

---

### Post by dannydcrespo on 2018-10-14
Did you download the driver from official site?

---

### Post by Yellow Pasque on 2018-10-15
> **Bashing-om said:**
> My reference is:
[https://www.nvidia.com/Download/driverResults.aspx/137276/en-us](https://www.nvidia.com/Download/driverResults.aspx/137276/en-us)
Well, 396.54 also supports GTX1050/M: [https://www.nvidia.com/Download/driverResults.aspx/137211/en-us](https://www.nvidia.com/Download/driverResults.aspx/137211/en-us)
The 390.xx driver is the "long-lived" branch while the 396.xx driver is the "short-lived" branch. See: [https://www.phoronix.com/scan.php?page=news_item&px=OTkxOA](https://www.phoronix.com/scan.php?page=news_item&px=OTkxOA)

> I bow to your knowledge
Thanks, but I don't consider myself that knowledgeable about Optimus laptops seeing as how I've never owned one.

[QUOTE=dannydcrespo]Did you download the driver from official site? [/QUOTE]
No, the OP was using this excellent PPA for the latest version: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Downloading directly from Nvidia is not a good idea when properly packaged alternatives are available.

---

### Post by c-bessem on 2018-10-17
Hi bashing-om 

Sorry I was able to open the laptop only now. I tried your commands and here is the results
```

>dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-390:amd64                   390.87-0ubuntu0~gpu18.04.1              amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390                       390.87-0ubuntu0~gpu18.04.1              all          Shared files used by the NVIDIA libraries
ii  libnvidia-common-396                       396.54-0ubuntu0~gpu18.04.1              all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-390:amd64                390.87-0ubuntu0~gpu18.04.1              amd64        NVIDIA libcompute package
ii  libnvidia-compute-390:i386                 390.87-0ubuntu0~gpu18.04.1              i386         NVIDIA libcompute package
rc  libnvidia-compute-396:amd64                396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA libcompute package
rc  libnvidia-compute-396:i386                 396.54-0ubuntu0~gpu18.04.1              i386         NVIDIA libcompute package
ii  libnvidia-decode-390:amd64                 390.87-0ubuntu0~gpu18.04.1              amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-390:i386                  390.87-0ubuntu0~gpu18.04.1              i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-390:amd64                 390.87-0ubuntu0~gpu18.04.1              amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-390:i386                  390.87-0ubuntu0~gpu18.04.1              i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-390:amd64                   390.87-0ubuntu0~gpu18.04.1              amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-390:i386                    390.87-0ubuntu0~gpu18.04.1              i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-390:amd64                     390.87-0ubuntu0~gpu18.04.1              amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-390:i386                      390.87-0ubuntu0~gpu18.04.1              i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-390:amd64                   390.87-0ubuntu0~gpu18.04.1              amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-390:i386                    390.87-0ubuntu0~gpu18.04.1              i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-390                   390.87-0ubuntu0~gpu18.04.1              amd64        NVIDIA compute utilities
rc  nvidia-compute-utils-396                   396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA compute utilities
ii  nvidia-dkms-390                            390.87-0ubuntu0~gpu18.04.1              amd64        NVIDIA DKMS package
rc  nvidia-dkms-396                            396.54-0ubuntu0~gpu18.04.1              amd64        NVIDIA DKMS package
ii  nvidia-driver-390                          390.87-0ubuntu0~gpu18.04.1              amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-390                   390.87-0ubuntu0~gpu18.04.1              amd64        Shared files used with the kernel module
rc  nvidia-kernel-common-396                   396.54-0ubuntu0~gpu18.04.1              amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-390                   390.87-0ubuntu0~gpu18.04.1              amd64        NVIDIA kernel source package
ii  nvidia-prime                               0.8.8.1                                 all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                            396.54-0ubuntu0~gpu18.04.1              amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-390                           390.87-0ubuntu0~gpu18.04.1              amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-390              390.87-0ubuntu0~gpu18.04.1              amd64        NVIDIA binary Xorg driver

```

and 
```

>cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-36-generic/updates/dkms
Found nvidia module: nvidia.ko
Looking for amdgpu modules in /lib/modules/4.15.0-36-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? yes
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:591b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1c8d
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver.
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
Intel IGP detected
Desktop system detected
or laptop with open drivers
Nothing to do

```

I am new to this but from the gpu manager log it seems that the OS is not loading the nvidia. Is there a way to force it to do so?

I know that using the nouveau.modeset=0 is not the ideal solution but I need to start using the laptop soon and having it freezing at every start due to a problem with the graphic card is not helping.

@Temujin

I tried your commands and here is the results

```

>prime-select query
nvidia

>sudo prime-select nvidia
Info: the nvidia profile is already set

```

Thank you for your help.

---

### Post by Yellow Pasque on 2018-10-17
> Found nvidia module: nvidia.ko
Is nvidia loaded? no

Try this to see what response you get:
```
sudo modprobe -v nvidia
```

---

### Post by Bashing-om on 2018-10-17
c-bessem; Hummmm ...

See the above, I also note:> 
ii  libnvidia-common-390                       390.87-0ubuntu0~gpu18.04.1              all          Shared files used by the NVIDIA libraries
ii  libnvidia-common-396                       396.54-0ubuntu0~gpu18.04.1              all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-390:amd64                390.87-0ubuntu0~gpu18.04.1              amd64        NVIDIA libcompute package
ii  libnvidia-compute-390:i386                 390.87-0ubuntu0~gpu18.04.1              i386         NVIDIA libcompute package

where the 396 Shared files are still in existence.
Maybe purge all nvidia and try and install again ?
Where is ( if any ) the graphic's config file located ?
```

sudo find / -name Xorg.conf

```
As we do want to insure that the old config file is removed.

[INDENT][INDENT]shedding light in some dark place
[/INDENT][/INDENT]

---

### Post by c-bessem on 2018-10-18
@Temujin

Here is the response to the commad
```

>sudo modprobe -v nvidia
insmod /lib/modules/4.15.0-36-generic/updates/dkms/nvidia.ko 
modprobe: ERROR: could not insert 'nvidia': Required key not available

```

@Bashing-om
I got this response when trying to locate the config file
```

>sudo find / -name Xorg.conf
find: ‘/run/user/1000/gvfs’: Permission denied

```

I will try to purge and re-install the driver (the 390) and let you know.

---

### Post by c-bessem on 2018-10-18
I think the problem was not with the nvidia drivers. I purged them but then discovered that the nouveau driver for nvidia xserver-xorg-video-nouveau was also installed. I removed it and reinstalled the nvidia driver. It has been 30 min since the reboot and the laptop hasn't froze yet.
I'll keep you updated, but I think the problem is solved.
I will wait till tomorrow before changing the status of the thread to solved and thank you for your help Temujin and Bashing-om

---

### Post by Yellow Pasque on 2018-10-18
> modprobe: ERROR: could not insert 'nvidia': Required key not available

Suggests an issue with SecureBoot. Check BIOS/EFI settings to see if you can disable it.

---

