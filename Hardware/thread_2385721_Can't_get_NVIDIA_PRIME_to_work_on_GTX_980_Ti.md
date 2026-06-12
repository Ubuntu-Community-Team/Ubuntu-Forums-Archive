---
title: "Can't get NVIDIA PRIME to work on GTX 980 Ti"
date: 2018-02-23
forum: Hardware
---

### Post by 2*@uG%9~ on 2018-02-23
I have been over the course of a few days to get nvidia-prime to work, and cant for the life of me.

I have a GTX 980 Ti, I'm running Xubuntu as dual boot (Xubuntu on one ssd, Windows on other). 

Things I've tried:

- followed instructions on threads such as these: [https://askubuntu.com/questions/457446/ubuntu-14-04-nvidia-prime-is-it-supported-no](https://askubuntu.com/questions/457446/ubuntu-14-04-nvidia-prime-is-it-supported-no)
commands like 
$ sudo apt-get purge bumblebee*$ sudo apt-get purge nvidia-*
(then reinstalling nvidia drivers either through Software and Updates or sudo apt-get install nvidia-xxx)

- tried running the prop 384.111/389/390 (iirc) drivers
- reinstalling Ubuntu
- running Kubuntu
- removing Ubuntu, installing Xubuntu from scratch
Maybe some other steps I forgot.

I would really like to get nvidia-prime working for the desktop gpu acceleration.
Even though I have a gtx 980 in my system and a good enough CPU, my machine feels underpowered and laggy, which forced me to go over from something like cinnamon to XFCE to make it tolerable.

On my laptop, which has a gtx 960m, nvidia prime is supported and things like dragging around windows, scrolling through webpages etc feels smooth.
Another note, the graphics card works fine in the windows boot.

A screenshot:
[https://i.imgur.com/6ORKIEi.jpg](https://i.imgur.com/6ORKIEi.jpg)

Thank You for your time.

---

### Post by wildmanne39 on 2018-02-23
Please use the attachment facility by clicking on the paperclip or url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by Bashing-om on 2018-02-23
ehaasdfasdfasdf; Hello; Welcome to the forum.

Strange and odd sloppyation...,,,,

Let's see what we can make of it.
Post back - Between Code Tags - the outputs of terminal commands:
```

lsb_release -a
dpkg -l | grep -i nvidia*
cat /var/log/gpu-manager.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
As working from text files is much easier/complete than that of an image.

[INDENT]gotta be a reason why - not
[/INDENT]

---

### Post by Yellow Pasque on 2018-02-24
nvidia-prime is not for desktop Nvidia cards (which is why nvidia-settings tells you it's unsupported). Your question doesn't make sense to me.

---

### Post by 2*@uG%9~ on 2018-02-24
Oh wow, silly me.

Thanks for you time anyway.

But is it possible to use gpu acceleration in a DE such as cinnamon with my card then? Or should it be using it already by default? (I'm pretty new to linux, trying to learn but getting stuck on this one)

---

### Post by sccman on 2018-02-24
As long as Linux can detect the graphics card and use its drivers it will work. Graphics drivers are managed and booted before the desktop environment boots.

Your Nvidia drivers version supports GTX 980 Ti. Run the commands and paste the output here so we can check that Nvidia is running the drivers fine:

```
lspci -k | grep -A 2 -i "VGA"
modinfo nvidia | grep version
glxinfo | grep -i nvidia
```

---

### Post by 2*@uG%9~ on 2018-02-24
> **sccman said:**
> As long as Linux can detect the graphics card and use its drivers it will work. Graphics drivers are managed and booted before the desktop environment boots.

Your Nvidia drivers version supports GTX 980 Ti. Run the commands and paste the output here so we can check that Nvidia is running the drivers fine:

```
lspci -k | grep -A 2 -i "VGA"
modinfo nvidia | grep version
glxinfo | grep -i nvidia
```

```
####eha@eha-mainframe:~$ lspci -k | grep -A 2 -i "VGA"

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller: NVIDIA Corporation GM200 [GeForce GTX 980 Ti] (rev a1)
    Subsystem: CardExpert Technology GM200 [GeForce GTX 980 Ti]
    Kernel driver in use: nvidia

####eha@eha-mainframe:~$ modinfo nvidia | grep version

modinfo: ERROR: Module nvidia not found.
eha@eha-mainframe:~$ glxinfo | grep -i nvidia
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
OpenGL core profile version string: 4.5.0 NVIDIA 384.111
OpenGL core profile shading language version string: 4.50 NVIDIA
OpenGL version string: 4.5.0 NVIDIA 384.111
OpenGL shading language version string: 4.50 NVIDIA
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 384.111

####eha@eha-mainframe:~$ 

```

And for:

> **Bashing-om said:**
> ehaasdfasdfasdf; Hello; Welcome to the forum.

Strange and odd sloppyation...,,,,

Let's see what we can make of it.
Post back - Between Code Tags - the outputs of terminal commands:
```

lsb_release -a
dpkg -l | grep -i nvidia*
cat /var/log/gpu-manager.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
As working from text files is much easier/complete than that of an image.[INDENT]gotta be a reason why - not
[/INDENT]



```
####eha@eha-mainframe:~$ lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

####eha@eha-mainframe:~$ dpkg -l | grep -i nvidia*

ii  bbswitch-dkms                               0.8-3ubuntu1                               amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-384                                384.111-0ubuntu0.16.04.1                   amd64        NVIDIA CUDA runtime library
ii  nvidia-384                                  384.111-0ubuntu0.16.04.1                   amd64        NVIDIA binary driver - version 384.111
ii  nvidia-opencl-icd-384                       384.111-0ubuntu0.16.04.1                   amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.2                                      amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             361.42-0ubuntu1                            amd64        Tool for configuring the NVIDIA graphics driver

####eha@eha-mainframe:~$ cat /var/log/gpu-manager.log

log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-fglrx-was-loaded file
Looking for fglrx modules in /lib/modules/4.13.0-36-generic/updates/dkms
Looking for nvidia modules in /lib/modules/4.13.0-36-generic/updates/dkms
Found nvidia module: nvidia_384_drm.ko
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is fglrx kernel module available? no
Is nvidia kernel module available? yes
Vendor/Device Id: 8086:412
BusID "PCI:0@0:2:0"
Is boot vga? no
Vendor/Device Id: 10de:17c8
BusID "PCI:1@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card1", driven by "i915"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card1", driven by "i915"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card1", driven by "i915"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Found "/dev/dri/card1", driven by "i915"
Number of connected outputs for /dev/dri/card1: 0
Does it require offloading? no
last cards number = 2
Has amd? no
Has intel? yes
Has nvidia? yes
How many cards? 2
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/nvidia-384/ld.so.conf
Current core alternative: (null)
Current egl alternative: /usr/lib/nvidia-384/ld.so.conf
Is nvidia enabled? yes
Is nvidia egl enabled? yes
Is fglrx enabled? no
Is mesa enabled? no
Is mesa egl enabled? no
Is pxpress enabled? no
Is prime enabled? no
Is prime egl enabled? no
Is nvidia available? yes
Is nvidia egl available? no
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is mesa egl available? yes
Is pxpress available? no
Is prime available? yes
Is prime egl available? no

####eha@eha-mainframe:~$ 

```

Also, things like CUDA work for deep learning, but my desktop seems to be definitely running off the cpu. (When I drag around a window fast, the cpu usage increases, etc.)
Update: Tested a bit more with CUDA, its very weird, my cpu is 100% usage as well as my gpu (heating up and all), but it seems that the speeds are as slow as if they were running only on the cpu? Really weird things going on here, even weirder is that it sometimes happens and othertimes doesnt.

---

### Post by Bashing-om on 2018-02-25
ehaasdfasdfasdf; Hummmm ...

The only thing I can point too is a discrepancy with the installed version of nvidia-settings:
yours:
> 
ii  nvidia-settings                             361.42-0ubuntu1


I also tun the 384 version nvidia driver and for nvidia settings I have :
> 
  nvidia-settings                             390.25-0ubuntu0~gpu16.04.1

with the difference that my driver is from our trusted PPA.

Maybe purge your present nvidia driver and re-install ? See then if you pick up a newer nvidia-settings tool .
If applies, make sure that secure boot is disabled in the EFI firmware
```

sudo apt purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo ubuntu-drivers autoinstall

```
where the system will choose the driver to install .

Re-boot to see the effect.

[INDENT][INDENT]maybe Yes
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2018-02-25
I don't see any problem with the nvidia driver info. One thing that confuses me is why the onboard Intel GPU is enabled. For a desktop system, I would think it should be disabled in BIOS/EFI and not show up in lspci.

> **Bashing-om said:**
> Maybe purge your present nvidia driver and re-install ? See then if you pick up a newer nvidia-settings tool.

I would not recommend it. It is okay for nvidia-settings to be a different version. The OP has the correct version of nvidia-settings for 16.04.x assuming no nvidia driver PPA: [https://launchpad.net/ubuntu/+source/nvidia-settings](https://launchpad.net/ubuntu/+source/nvidia-settings)

---

### Post by 2*@uG%9~ on 2018-02-25
I tried reinstalling, removed with the first command, ran the second command (which returned "rm: cannot remove '/etc/X11/xorg.conf': No such file or directory", I checked, indeed I don't have such a file in that directory.
I then went ahead and used the auto install to install the drivers:
```

eha@eha-mainframe:~$ sudo rm /etc/X11/xorg.conf
[sudo] password for eha: 
Sorry, try again.
[sudo] password for eha: 
rm: cannot remove '/etc/X11/xorg.conf': No such file or directory
eha@eha-mainframe:~$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  iucode-tool libcuda1-384 nvidia-opencl-icd-384 nvidia-prime nvidia-settings
The following NEW packages will be installed:
  intel-microcode iucode-tool libcuda1-384 nvidia-384 nvidia-opencl-icd-384 nvidia-prime
  nvidia-settings
0 upgraded, 7 newly installed, 0 to remove and 128 not upgraded.
Need to get 1 019 kB/82,4 MB of archives.
After this operation, 363 MB of additional disk space will be used.
Get:1 http://ee.archive.ubuntu.com/ubuntu xenial-updates/main amd64 iucode-tool amd64 1.5.1-1ubuntu0.1 [33,8 kB]
Get:2 http://ee.archive.ubuntu.com/ubuntu xenial-updates/main amd64 intel-microcode amd64 3.20180108.0+really20170707ubuntu16.04.1 [985 kB]
Fetched 1 019 kB in 0s (4 061 kB/s)      
Selecting previously unselected package iucode-tool.
(Reading database ... 340907 files and directories currently installed.)
Preparing to unpack .../iucode-tool_1.5.1-1ubuntu0.1_amd64.deb ...
Unpacking iucode-tool (1.5.1-1ubuntu0.1) ...
Selecting previously unselected package nvidia-384.
Preparing to unpack .../nvidia-384_384.111-0ubuntu0.16.04.1_amd64.deb ...
Unpacking nvidia-384 (384.111-0ubuntu0.16.04.1) ...
Selecting previously unselected package libcuda1-384.
Preparing to unpack .../libcuda1-384_384.111-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libcuda1-384 (384.111-0ubuntu0.16.04.1) ...
Selecting previously unselected package nvidia-opencl-icd-384.
Preparing to unpack .../nvidia-opencl-icd-384_384.111-0ubuntu0.16.04.1_amd64.deb ...
Unpacking nvidia-opencl-icd-384 (384.111-0ubuntu0.16.04.1) ...
Selecting previously unselected package nvidia-prime.
Preparing to unpack .../nvidia-prime_0.8.2_amd64.deb ...
Unpacking nvidia-prime (0.8.2) ...
Selecting previously unselected package nvidia-settings.
Preparing to unpack .../nvidia-settings_361.42-0ubuntu1_amd64.deb ...
Unpacking nvidia-settings (361.42-0ubuntu1) ...
Selecting previously unselected package intel-microcode.
Preparing to unpack .../intel-microcode_3.20180108.0+really20170707ubuntu16.04.1_amd64.deb ...
Unpacking intel-microcode (3.20180108.0+really20170707ubuntu16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up iucode-tool (1.5.1-1ubuntu0.1) ...
Setting up nvidia-384 (384.111-0ubuntu0.16.04.1) ...
update-alternatives: using /usr/lib/nvidia-384/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-384/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-384/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-384/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/share/nvidia-384/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-384
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Adding system user `nvidia-persistenced' (UID 121) ...
Adding new group `nvidia-persistenced' (GID 129) ...
Adding new user `nvidia-persistenced' (UID 121) with group `nvidia-persistenced' ...
Not creating home directory `/'.
Loading new nvidia-384-384.111 DKMS files...
First Installation: checking all kernels...
Building only for 4.13.0-36-generic
Building for architecture x86_64
Building initial module for 4.13.0-36-generic
Done.


nvidia_384:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-36-generic/updates/dkms/


nvidia_384_modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-36-generic/updates/dkms/


nvidia_384_drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-36-generic/updates/dkms/


nvidia_384_uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-36-generic/updates/dkms/


depmod....


DKMS: install completed.
Setting up libcuda1-384 (384.111-0ubuntu0.16.04.1) ...
Setting up nvidia-opencl-icd-384 (384.111-0ubuntu0.16.04.1) ...
Setting up nvidia-prime (0.8.2) ...
Setting up nvidia-settings (361.42-0ubuntu1) ...
Setting up intel-microcode (3.20180108.0+really20170707ubuntu16.04.1) ...
update-initramfs: deferring update (trigger activated)
intel-microcode: microcode will be updated at next boot
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.13.0-36-generic
Processing triggers for shim-signed (1.33.1~16.04.1+13-0ubuntu2) ...
Secure Boot not enabled on this system.
Processing triggers for ureadahead (0.100.0-19) ...

```

I can see that it installs the 361.42 nvidia settings once again.
But something odd I noticed was that once I uninstalled the gpu drivers and restarted my machine, everything felt much smoother than before, even though it still ran on the CPU (didn't even have gpu drivers installed), dragging windows around and so on didn't have any issues at all. Kind of odd.

If my GPU drivers were properly installed and everything was working well/as intended, does Xubuntu/Xfce even use your gpu to accelerate desktop activites? Does cinnamon/unity/gnome use gpu acceleration as well? From my searching, I'm not exactly sure.

Update: okay I reinstalled the drivers as well, and I feel like the jitters when moving a chrome window up and down/resizing it for example are back again, even though its still using the cpu.
And I also monitored my gpu this time whilst moving windows, it actually does definitely use the gpu as well, just not very well it seems.



Also, videos for proof of concept:

Resizing window with nvidia drivers INSTALLED:
[https://drive.google.com/open?id=1sXrSbRihsF5NqkYgPLK4AKvDyDhaMuAC](https://drive.google.com/open?id=1sXrSbRihsF5NqkYgPLK4AKvDyDhaMuAC)

Resizing window with nvidia drivers NOT installed:
[https://drive.google.com/open?id=13mAai8V0DgHP0TlmUaSCApX28Rwdwj6V](https://drive.google.com/open?id=13mAai8V0DgHP0TlmUaSCApX28Rwdwj6V)

Without drivers its clearly a lot smoother for some reason.

---

### Post by Yellow Pasque on 2018-02-25
Get the /var/log/Xorg.0.log file when you boot without the nvidia driver installed. Then get one when you boot with the nvidia driver installed and post both logs so we can compare.
Do you have any sort of switch in the BIOS to disable the integrated GPU or choose which order the GPU's get initialized in?

> does Xubuntu/Xfce even use your gpu to accelerate desktop activites?

Yes. xfce can use 2D acceleration.

---

### Post by Bashing-om on 2018-02-25
ehaasdfasdfasdf; Well -

we have hybrid graphics:

> 
####eha@eha-mainframe:~$ lspci -k | grep -A 2 -i "VGA"

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller: NVIDIA Corporation GM200 [GeForce GTX 980 Ti] (rev a1)
    Subsystem: CardExpert Technology GM200 [GeForce GTX 980 Ti]
    Kernel driver in use: nvidia


And as such that /etc/X11/Xorg.conf config file is requited to enable the ability to switch graphic's sets . I can not imagine what is not going on that the file was not generated when the nvidia driver was formerly installed.

Is the file now present ?
```

ls -al /etc/X11/Xorg.conf config

```


Else, As a thought:
Can you now activate nvidia-settings and have nvidia generate the config file, see then what results .. ?
( or that file can be generated from terminal ) .

[INDENT]gotta be a reason
[/INDENT]

---

### Post by Yellow Pasque on 2018-02-25
> **Bashing-om said:**
> Well - we have hybrid graphics

I see no indication that this is a laptop. Logs will tell us more though..

---

### Post by 2*@uG%9~ on 2018-02-28
Sorry for the late reply, I didn't get any notifications suddenly anymore. I'll get on my machine in about 7 hoursish, but I'll try to reply with the details I know right now.

Yes, I don't have a laptop, I at first thought that nvidia-prime is just something that allows for better desktop graphics acceleration on any machine, not only laptops.
> Get the /var/log/Xorg.0.log file when you boot without the nvidia driver installed. Then get one when you boot with the nvidia driver installed and post both logs so we can compare.
Do you have any sort of switch in the BIOS to disable the integrated GPU or choose which order the GPU's get initialized 
[COLOR=#000000]

[/COLOR]
When I checked the bios a few days ago, I didn't notice anything that would mention the dedicated graphics card, there might have been something mentioned about the intel hd graphics, I'm not sure right now.
I'll try all the things mentioned above when I get on my machine, but at least here are some of my components:

GTX 980 Ti
GA-H81-D3
i5-4570
12gb of ram (1600mhz ddr3)
[COLOR=#000000]
[/COLOR]

---

### Post by Yellow Pasque on 2018-02-28
Looking at the manual, there is an "Intel Processor Graphics" setting to enable/disable the IGP under the "Peripherals" menu.
[http://download.gigabyte.us/FileList/Manual/mb_manual_ga-h81-d3_e.pdf](http://download.gigabyte.us/FileList/Manual/mb_manual_ga-h81-d3_e.pdf)

---

### Post by 2*@uG%9~ on 2018-02-28
> **Temüjin said:**
> Looking at the manual, there is an "Intel Processor Graphics" setting to enable/disable the IGP under the "Peripherals" menu.
[http://download.gigabyte.us/FileList/Manual/mb_manual_ga-h81-d3_e.pdf](http://download.gigabyte.us/FileList/Manual/mb_manual_ga-h81-d3_e.pdf)


I am home now, I indeed disabled it now, I can't notice a difference.


> 
And as such that /etc/X11/Xorg.conf config file is requited to enable the ability to switch graphic's sets . I can not imagine what is not going on that the file was not generated when the nvidia driver was formerly installed.


Is the file now present ?



```

eha@eha-mainframe:~$ ls -al /etc/X11/Xorg.conf config
ls: cannot access '/etc/X11/Xorg.conf': No such file or directory
ls: cannot access 'config': No such file or directory

```


Even though I can access nvidia-settings, the Xorg.conf file still doesn't seem to be present.
The only place I found a Xorg.conf file was in '/usr/share/doc/xserver-xorg-video-intel-hwe-16.04', but I'm not sure if that is even relevant at all.


> 
Get the /var/log/Xorg.0.log file when you boot without the nvidia driver installed. Then get one when you boot with the nvidia driver installed and post both logs so we can compare.
Do you have any sort of switch in the BIOS to disable the integrated GPU or choose which order the GPU's get initialized in?



Xorg.0.log with GPU driver installed, intelhd graphics disabled from bios: [https://hastebin.com/bucewiloga.scala](https://hastebin.com/bucewiloga.scala)
Xorg.0.log with GPU driver installed, intelhd graphics enabled from bios: [https://hastebin.com/otamatomod.scala](https://hastebin.com/otamatomod.scala)
Xorg.0.log with GPU driver uninstalled, intelhd graphics enabled from bios: [https://hastebin.com/iyufuwajiq.scala](https://hastebin.com/iyufuwajiq.scala)

---

### Post by 2*@uG%9~ on 2018-03-01
I'm looking at some search results, and there are people with similar problems, yet none of them have fixes, or at least the fixes don't work.

examples:
[https://askubuntu.com/questions/882956/ubuntu-16-04-1-live-window-resize-lags-a-lot-on-gtx-1080](https://askubuntu.com/questions/882956/ubuntu-16-04-1-live-window-resize-lags-a-lot-on-gtx-1080)

[https://devtalk.nvidia.com/default/topic/1005676/gtx-1080-compiz-wtf/](https://devtalk.nvidia.com/default/topic/1005676/gtx-1080-compiz-wtf/)

[https://askubuntu.com/questions/828026/1080-gtx-slow-performance-ubuntu-16-04](https://askubuntu.com/questions/828026/1080-gtx-slow-performance-ubuntu-16-04) (tried installing cuda, trying different chrome options, none of them make a difference)

[https://github.com/linuxmint/Cinnamon/issues/2465](https://github.com/linuxmint/Cinnamon/issues/2465)

---

### Post by Yellow Pasque on 2018-03-01
I see some complaints about the "Razer Deathadder" mouse in the Cinnamon thread you link to. So if you have a different mouse to try, do so. Or, you can try lowering the polling rate using something like: [http://www.webupd8.org/2016/06/configure-razer-mice-in-linux-with.html](http://www.webupd8.org/2016/06/configure-razer-mice-in-linux-with.html)

---

### Post by 2*@uG%9~ on 2018-03-01
> **Temüjin said:**
> I see some complaints about the "Razer Deathadder" mouse in the Cinnamon thread you link to. So if you have a different mouse to try, do so. Or, you can try lowering the polling rate using something like: [http://www.webupd8.org/2016/06/configure-razer-mice-in-linux-with.html](http://www.webupd8.org/2016/06/configure-razer-mice-in-linux-with.html)

I actually do have that same mouse. I tried to change the polling rate with some commands, but maybe I'll try again with that tool tomorrow to see what happens. Will update then.

---

### Post by 2*@uG%9~ on 2018-03-02
Tried it, even when changing to 125hz (the lowest), changed nothing sadly. This is getting pretty hopeless.

---

