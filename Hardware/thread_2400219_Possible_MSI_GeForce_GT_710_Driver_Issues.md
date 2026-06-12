---
title: "Possible MSI GeForce GT 710 Driver Issues"
date: 2018-09-03
forum: Hardware
---

### Post by hennmann on 2018-09-03
I just completed an installation of the latest version of Ubuntu on my Gigabyte GA-M68MT-S2 with an Athlon AMD 640x4 CPU running an MSI GeForce GT 710 video card and I'm having possible driver issues?? 
As per this discussion:

[https://ubuntuforums.org/showthread.php?t=2380061&highlight=MSI+GT+710](https://ubuntuforums.org/showthread.php?t=2380061&highlight=MSI+GT+710)

I entered the suggested commands in the terminal and it appears I have version 340.104 for drivers installed and not the 384 driver.
Otherwise on
[https://www.geforce.com/drivers/results/137276](https://www.geforce.com/drivers/results/137276)

they list the following and 384 is the earliest version shown. Also this is a dual boot setup where Windows 7 64 is installed and this card is working fine on Windows. The problems on the latest version of Ubuntu is I have squares and rectangles speckled on my screens (dual monitors otherwise working fine) and on a white screen image these squares and rectangles are yellow and in the terminal with a black screen they are blue. Please bear with me being new to LInux and mainly used to the "Device Manager" in windows which is used to check the status of hardware and drivers and update them as required. I'm open to suggestions and if need be I can copy and paste commands in the terminal to bumble along being a Windows GUI slave. I have downloaded and saved both the 384 and 390.87 drivers and just need a bit of advice on how to install and if required remove the 340.104 driver if required to do so? Below is a bit of info on the 2nd latest 390 driver and the latest is a BETA version. Any help would be greatly appreciated. 



[TABLE]
[TR]
[TD]390.87
[/TD]
                            [/TR]
                            [TR]
                             [TD]Release Date[/TD]
                             [TD]Mon Aug 27, 2018[/TD]
                           [/TR]
	                            [TR]
                             [TD]Operating System[/TD]
                             [TD]Linux 64-bit
[/TD]
                           [/TR]
                            [TR]
                             [TD]Language[/TD]
                             [TD]English (US)
[/TD]
                           [/TR]
                                            [TR]
                             [TD]File Size
[/TD]
                             [TD]78.86 MB








[/TD]
[/TR]
[/TABLE]

---

### Post by Bashing-om on 2018-09-03
hennmann; Hello -

I too run that card on an AMD platform - I have no issues with this card.
> 
sysop@x1810:~$ sudo lshw -C display
[sudo] password for sysop: 
  *-display                 
       description: VGA compatible controller
       product: GK208B [GeForce GT 710]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fb000000-fbffffff memory:d8000000-dfffffff memory:e6000000-e7ffffff ioport:4c00(size=128) memory:c0000-dffff

sysop@x1810:~$ dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-390:amd64              390.87-0ubuntu1                       amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-390                  390.87-0ubuntu1                       all          Shared files used by the NVIDIA libraries
ii  libnvidia-compute-390:amd64           390.87-0ubuntu1                       amd64        NVIDIA libcompute package
ii  libnvidia-compute-390:i386            390.87-0ubuntu1                       i386         NVIDIA libcompute package
ii  libnvidia-decode-390:amd64            390.87-0ubuntu1                       amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-390:i386             390.87-0ubuntu1                       i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-390:amd64            390.87-0ubuntu1                       amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-390:i386             390.87-0ubuntu1                       i386         NVENC Video Encoding runtime library
ii  libnvidia-fbc1-390:amd64              390.87-0ubuntu1                       amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-390:i386               390.87-0ubuntu1                       i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-390:amd64                390.87-0ubuntu1                       amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-390:i386                 390.87-0ubuntu1                       i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-390:amd64              390.87-0ubuntu1                       amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  libnvidia-ifr1-390:i386               390.87-0ubuntu1                       i386         NVIDIA OpenGL-based Inband Frame Readback runtime library
ii  nvidia-compute-utils-390              390.87-0ubuntu1                       amd64        NVIDIA compute utilities
ii  nvidia-dkms-390                       390.87-0ubuntu1                       amd64        NVIDIA DKMS package
ii  nvidia-driver-390                     390.87-0ubuntu1                       amd64        NVIDIA driver metapackage
ii  nvidia-kernel-common-390              390.87-0ubuntu1                       amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-390              390.87-0ubuntu1                       amd64        NVIDIA kernel source package
ii  nvidia-prime                          0.8.9                                 all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                       390.77-0ubuntu1                       amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-390                      390.87-0ubuntu1                       amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-390         390.87-0ubuntu1                       amd64        NVIDIA binary Xorg driver
sysop@x1810:~$ 


Installing the driver from Nvidia is the means of last resort - even Nvidia says do not do this, but get the driver from the distro's software archive.
In your case try terminal commands::
```

sudo rm /etc/X11/Xorg.conf  ## just in case this file should exist
cat /usr/share/X11/xorg.conf.d/10-nvidia.conf ##see what this config file looks like
sudo apt purge nvidia
sudo ubuntu-drivers autoinstall

```

reboot to see the effect.

[INDENT][INDENT]all better now ?
[/INDENT][/INDENT]

---

### Post by hennmann on 2018-09-04
While reading your reply it would appear you have the 390.386 driver installed? Sorry I'm reading and responding on my tiny smartphone without my reading glasses.  Otherwise where your 390,386 is listed I see 340 so I probably have the wrong or improper driver. Otherwise I also have an MSI 970A SLI Krait with an MSI Armor 570OC and it worked fantastic right away. When I get my Gigabyte working I will install Ubuntu back on the Krait running Win 7 as a a dual boot seeing now how easy this is to accomplish on the Gigabyte.

---

### Post by Bashing-om on 2018-09-04
hennmann; Yup -

You have the right of it all . I do have the 390 version driver installed, and yes - that is the driver you do want installed.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by hennmann on 2018-09-04
Okay thanks for your help so far! I would take a guess that the incorrect driver has to be removed and the correct installed but removing it will be a guess to me. Can one install the correct driver first and remove the 340 after or does it need to be purged out of the OS first? This is one reason why I ran away from Linux at 90 miles per hour with my hair on fire over 12 years ago due to that archaic CLI and of course if you don't know the commands is the same as getting behind the wheel of your car and not knowing how to turn the ignition key to even start the engine. The device manager on Windows at least lets you browse for a directory of the driver and then select it.

---

### Post by Bashing-om on 2018-09-04
hennmann; Welp -

Me I am the opposite - I avoid the GUI as I am terminally minded.
ubuntu GUI way: software sources -> additional drivers.

[INDENT][INDENT]else we do do this in terninal
[/INDENT][/INDENT]

---

### Post by hennmann on 2018-09-05
At least things have improved in a positive way such as when I installed Kodi it was click on the selection and it downloaded and installed complete with an Icon on the desktop to select it. It wasn't even that long ago one needed a command just to do this!! I can think of only two people who use Linux or should I say count on my fingers who uses it with many left over. It is no wonder the amount of users is dropping off. The CLI reminds me of DOS and who uses that now? As for the CLI unless you know the commands (of many) you are SOL

---

### Post by hennmann on 2018-09-05
Also another thing puzzles me?? Why is the driver from the actual manufacturer a last resort?

---

### Post by hennmann on 2018-09-05
Where are the drivers on this site?? If the drivers in this latest version of Ubuntu for this card are obviously incorrect why are they not updated?? I have the drivers from the manufacturer but they are just there to sit and look at! Don't forget if people are thinking of making the transition from Crapple or Windoze perhaps the transition could be made a bit more user or should I say NOOB friendly?

---

### Post by oldfred on 2018-09-05
If you install the drivers directly from nVidia, you have to in effect reinstall with every kernel update. The drivers are reconfigured to auto work with new kernels if you install directly from Ubuntu repository.

NVidia has multiple drivers. Older cards do not have features that new cards have, so the freeze a driver and then may only do security updates to that series of drivers. Newest cards keep getting newer drivers until they are older and driver is then frozen. Installing too new of a driver can lead to issues, just as installing too old of a driver.

This should be all you have to do, if newer driver required. If older card you do not even have to add ppa.
       # Shows standard repository versions, which is the same as gui list here:
System Settings, Software & Updates icon, Additional drivers tab,         With 18.04, the only way I can get to this now is with Software Updater & Settings. 
    
Shows drivers:
ubuntu-drivers devices 
And you should get a recommended driver like this for my GeForce GT 620:
driver   : nvidia-driver-390 - distro non-free recommended

Link to where ppa is showing what it has, not required to look at, just add ppa as below.
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

 # make sure system is up to date
sudo apt-get update
sudo apt-get upgrade
sudo apt-add-repository ppa:graphics-drivers/ppa  <--optional only if newer card/chip
sudo apt-get update 
            # should show newest versions available in addition, if ppa added
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX  

    Ubuntu  tries to offer current driver by model of nVidia card, but ISO is frozen and only will have versions available when ISO released. Newer versions will in repository, but you must purge old version or incorrect version, otherwise drivers conflict. Installing new driver does not automatically remove all of old driver.

For those with very new nVidia cards/chips, there is a ppa that is like an updated repository and makes it easy to install nVidia driver. But you need to know version you need.

       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)
Fermi based should use 390.xx not newer
[https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus](https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus) 
    
       If wrong nVidia driver or upgrade, you must purge & install correct driver, more details:
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by Yellow Pasque on 2018-09-06
> **hennmann said:**
> Also another thing puzzles me?? Why is the driver from the actual manufacturer a last resort?

Because different Linux distros do things differently, such as having different package management systems, putting/expecting files in different places, etc.
Nvidia's installer doesn't try to account for all of those differences. Nvidia's installer is not meant to be used directly by end users of major distros. It is mainly for distro packagers, or maybe power users who don't run a traditional distro.

> Where are the drivers on this site?? 
What site?

> If the drivers in this latest version of Ubuntu for this card are obviously incorrect why are they not updated??
They're not "obviously incorrect." The 340.104 and the 340.xx legacy branch in general supports the GT710. See the 'Supported Products' list here: [https://www.nvidia.com/Download/driverResults.aspx/123703/en-us](https://www.nvidia.com/Download/driverResults.aspx/123703/en-us)

You don't mention what "issues" you are having in the first place that makes you want to change/upgrade driver.

---

### Post by oldfred on 2018-09-06
If you use this nVidia site, it shows the newest drivers work.
[https://www.geforce.com/drivers](https://www.geforce.com/drivers)

I think the 340.xx was the current driver back when the GT710 was released. But the 340.xx also is a driver that was frozen for older cards/chips and newer cards needed  newer drivers.

There may not be much difference between 340 & 390 or even 396 as the 710 does not have the newer hardware the newer driver supports.  Probably some minor improvement.
So then you can install any nVidia driver from 340 thru 396 and it should work. But you must uninstall any previous driver or you get conflicts and driver will not work.

---

### Post by hennmann on 2018-09-06
Thanks oldfred & Bashing-OM
I downloaded the latest  390.87 from ppa and it is now sitting in my downloads directory.
I have the improper 340 driver and could you please post the proper CLI command so I can copy, paste, and purge the improper driver properly? I kind of used commands from the other threads you posted but the result is it lists:

 ```
'bumblebee' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'primus' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-libopencl1-331' is not installed, so not removed
Package 'nvidia-libopencl1-331-updates' is not installed, so not removed
Package 'nvidia-libopencl1-340' is not installed, so not removed
Package 'nvidia-libopencl1-340-updates' is not installed, so not removed
Package 'nvidia-libopencl1-346' is not installed, so not removed
Package 'nvidia-libopencl1-346-updates' is not installed, so not removed
Package 'nvidia-libopencl1-352' is not installed, so not removed
Package 'nvidia-libopencl1-352-updates' is not installed, so not removed
Package 'nvidia-libopencl1-361' is not installed, so not removed
Package 'nvidia-libopencl1-361-updates' is not installed, so not removed
Package 'nvidia-libopencl1-367' is not installed, so not removed
Package 'nvidia-libopencl1-375' is not installed, so not removed
Package 'nvidia-libopencl1-384' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-nsight' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-331' is not installed, so not removed
Package 'nvidia-opencl-icd-331-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-340-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-346' is not installed, so not removed
Package 'nvidia-opencl-icd-346-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-352' is not installed, so not removed
Package 'nvidia-opencl-icd-352-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-361' is not installed, so not removed
Package 'nvidia-opencl-icd-361-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-367' is not installed, so not removed
Package 'nvidia-opencl-icd-375' is not installed, so not removed
Package 'nvidia-opencl-icd-384' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 100 not upgraded.
```
```
sudo] password for don: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'nvidia-325-updates' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-binary' for glob 'nvidia*'
Note, selecting 'nvidia-331-dev' for glob 'nvidia*'
Note, selecting 'nvidia-384-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-cg-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-driver-libs-i386:i386' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-common-390' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-384-updates' for glob 'nvidia*'
Note, selecting 'nvidia' for glob 'nvidia*'
Note, selecting 'nvidia-driver' for glob 'nvidia*'
Note, selecting 'nvidia-367-updates' for glob 'nvidia*'
Note, selecting 'nvidia-modprobe' for glob 'nvidia*'
Note, selecting 'nvidia-texture-tools' for glob 'nvidia*'
Note, selecting 'nvidia-utils' for glob 'nvidia*'
Note, selecting 'nvidia-387-updates' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-vdpau-driver' for glob 'nvidia*'
Note, selecting 'nvidia-349-updates' for glob 'nvidia*'
Note, selecting 'nvidia-310-updates' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-352-dev' for glob 'nvidia*'
Note, selecting 'nvidia-vdpau-driver' for glob 'nvidia*'
Note, selecting 'nvidia-346-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-utils-390' for glob 'nvidia*'
Note, selecting 'nvidia-smi' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-313-updates' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-334-updates' for glob 'nvidia*'
Note, selecting 'nvidia-331-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-prime' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-390' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-current-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-dev' for glob 'nvidia*'
Note, selecting 'nvidia-nsight' for glob 'nvidia*'
Note, selecting 'nvidia-common' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-headless-no-dkms-390' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-compute-utils-390' for glob 'nvidia*'
Note, selecting 'nvidia-355-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-libs-nonglvnd' for glob 'nvidia*'
Note, selecting 'nvidia-375-dev' for glob 'nvidia*'
Note, selecting 'nvidia-current' for glob 'nvidia*'
Note, selecting 'nvidia-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-375-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-390' for glob 'nvidia*'
Note, selecting 'nvidia-337-updates' for glob 'nvidia*'
Note, selecting 'nvidia-358-updates' for glob 'nvidia*'
Note, selecting 'nvidia-367-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-304xx-driver' for glob 'nvidia*'
Note, selecting 'nvidia-driver-libs' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source' for glob 'nvidia*'
Note, selecting 'nvidia-378-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-319-updates' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-visual-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-persistenced' for glob 'nvidia*'
Note, selecting 'nvidia-361-dev' for glob 'nvidia*'
Note, selecting 'nvidia-settings-binary' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-331' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-346' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-352' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-361' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-367' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-375' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-384' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-headless-390' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-driver' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-doc' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-dev' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-dev' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-304xx-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-cg-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cg-doc' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-381-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-331' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-346' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-352' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-361' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-367' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-375' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-gdb' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-304' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-384' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-310' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-313' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-319' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-325' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-331' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-334' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-337' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-340' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-343' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-346' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-349' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-352' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-355' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-358' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-361' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-364' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-367' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-375' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-378' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-381' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-384' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-387' for glob 'nvidia*'
Note, selecting 'nvidia-343-updates' for glob 'nvidia*'
Note, selecting 'nvidia-364-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304' for glob 'nvidia*'
Note, selecting 'nvidia-310' for glob 'nvidia*'
Note, selecting 'nvidia-313' for glob 'nvidia*'
Note, selecting 'nvidia-319' for glob 'nvidia*'
Note, selecting 'nvidia-325' for glob 'nvidia*'
Note, selecting 'nvidia-331' for glob 'nvidia*'
Note, selecting 'nvidia-334' for glob 'nvidia*'
Note, selecting 'nvidia-337' for glob 'nvidia*'
Note, selecting 'nvidia-340' for glob 'nvidia*'
Note, selecting 'nvidia-343' for glob 'nvidia*'
Note, selecting 'nvidia-346' for glob 'nvidia*'
Note, selecting 'nvidia-349' for glob 'nvidia*'
Note, selecting 'nvidia-352' for glob 'nvidia*'
Note, selecting 'nvidia-355' for glob 'nvidia*'
Note, selecting 'nvidia-358' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-source-390' for glob 'nvidia*'
Note, selecting 'nvidia-361' for glob 'nvidia*'
Note, selecting 'nvidia-364' for glob 'nvidia*'
Note, selecting 'nvidia-367' for glob 'nvidia*'
Note, selecting 'nvidia-375' for glob 'nvidia*'
Note, selecting 'nvidia-378' for glob 'nvidia*'
Note, selecting 'nvidia-381' for glob 'nvidia*'
Note, selecting 'nvidia-384' for glob 'nvidia*'
Note, selecting 'nvidia-387' for glob 'nvidia*'
Note, selecting 'nvidia-dkms-kernel' for glob 'nvidia*'
Note, selecting 'nvidia-390' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-settings' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd' for glob 'nvidia*'
Package 'nvidia-304' is not installed, so not removed
Note, selecting 'nvidia-settings' instead of 'nvidia-settings-binary'
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia-vdpau-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-vdpau-driver' is not installed, so not removed
Package 'nvidia-390' is not installed, so not removed
Note, selecting 'nvidia-kernel-common-390' instead of 'nvidia-kernel-common'
Note, selecting 'nvidia-kernel-source-390' instead of 'nvidia-kernel-source'
Note, selecting 'nvidia-utils-390' instead of 'nvidia-smi'
Note, selecting 'nvidia-utils-390' instead of 'nvidia-utils'
Package 'nvidia-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-driver' is not installed, so not removed
Package 'nvidia-legacy-304xx-driver' is not installed, so not removed
Package 'nvidia-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-340xx-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-304xx-kernel-dkms' is not installed, so not removed
Package 'nvidia' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-304-updates' is not installed, so not removed
Package 'nvidia-experimental-304' is not installed, so not removed
Package 'nvidia-310' is not installed, so not removed
Package 'nvidia-310-updates' is not installed, so not removed
Package 'nvidia-experimental-310' is not installed, so not removed
Package 'nvidia-313' is not installed, so not removed
Package 'nvidia-313-updates' is not installed, so not removed
Package 'nvidia-experimental-313' is not installed, so not removed
Package 'nvidia-319' is not installed, so not removed
Package 'nvidia-319-updates' is not installed, so not removed
Package 'nvidia-experimental-319' is not installed, so not removed
Package 'nvidia-325' is not installed, so not removed
Package 'nvidia-325-updates' is not installed, so not removed
Package 'nvidia-experimental-325' is not installed, so not removed
Package 'nvidia-experimental-331' is not installed, so not removed
Package 'nvidia-334' is not installed, so not removed
Package 'nvidia-334-updates' is not installed, so not removed
Package 'nvidia-experimental-334' is not installed, so not removed
Package 'nvidia-337' is not installed, so not removed
Package 'nvidia-337-updates' is not installed, so not removed
Package 'nvidia-experimental-337' is not installed, so not removed
Package 'nvidia-experimental-340' is not installed, so not removed
Package 'nvidia-343' is not installed, so not removed
Package 'nvidia-343-updates' is not installed, so not removed
Package 'nvidia-experimental-343' is not installed, so not removed
Package 'nvidia-experimental-346' is not installed, so not removed
Package 'nvidia-349' is not installed, so not removed
Package 'nvidia-349-updates' is not installed, so not removed
Package 'nvidia-experimental-349' is not installed, so not removed
Package 'nvidia-experimental-352' is not installed, so not removed
Package 'nvidia-355' is not installed, so not removed
Package 'nvidia-355-updates' is not installed, so not removed
Package 'nvidia-experimental-355' is not installed, so not removed
Package 'nvidia-358' is not installed, so not removed
Package 'nvidia-358-updates' is not installed, so not removed
Package 'nvidia-experimental-358' is not installed, so not removed
Package 'nvidia-experimental-361' is not installed, so not removed
Package 'nvidia-364' is not installed, so not removed
Package 'nvidia-364-updates' is not installed, so not removed
Package 'nvidia-experimental-364' is not installed, so not removed
Package 'nvidia-367-updates' is not installed, so not removed
Package 'nvidia-experimental-367' is not installed, so not removed
Package 'nvidia-375-updates' is not installed, so not removed
Package 'nvidia-experimental-375' is not installed, so not removed
Package 'nvidia-378' is not installed, so not removed
Package 'nvidia-378-updates' is not installed, so not removed
Package 'nvidia-experimental-378' is not installed, so not removed
Package 'nvidia-381' is not installed, so not removed
Package 'nvidia-381-updates' is not installed, so not removed
Package 'nvidia-experimental-381' is not installed, so not removed
Package 'nvidia-384-updates' is not installed, so not removed
Package 'nvidia-experimental-384' is not installed, so not removed
Package 'nvidia-387' is not installed, so not removed
Package 'nvidia-387-updates' is not installed, so not removed
Package 'nvidia-experimental-387' is not installed, so not removed
Note, selecting 'libnvtt-bin' instead of 'nvidia-texture-tools'
Package 'nvidia-driver-libs' is not installed, so not removed
Package 'nvidia-driver-libs-nonglvnd' is not installed, so not removed
Package 'nvidia-driver-libs-i386:i386' is not installed, so not removed
Package 'nvidia-prime' is not installed, so not removed
Package 'nvidia-settings' is not installed, so not removed
Package 'nvidia-331' is not installed, so not removed
Package 'nvidia-331-dev' is not installed, so not removed
Package 'nvidia-331-updates' is not installed, so not removed
Package 'nvidia-331-updates-dev' is not installed, so not removed
Package 'nvidia-331-updates-uvm' is not installed, so not removed
Package 'nvidia-331-uvm' is not installed, so not removed
Package 'nvidia-340' is not installed, so not removed
Package 'nvidia-340-dev' is not installed, so not removed
Package 'nvidia-340-updates' is not installed, so not removed
Package 'nvidia-340-updates-dev' is not installed, so not removed
Package 'nvidia-340-updates-uvm' is not installed, so not removed
Package 'nvidia-340-uvm' is not installed, so not removed
Package 'nvidia-346' is not installed, so not removed
Package 'nvidia-346-dev' is not installed, so not removed
Package 'nvidia-346-updates' is not installed, so not removed
Package 'nvidia-346-updates-dev' is not installed, so not removed
Package 'nvidia-352' is not installed, so not removed
Package 'nvidia-352-dev' is not installed, so not removed
Package 'nvidia-352-updates' is not installed, so not removed
Package 'nvidia-352-updates-dev' is not installed, so not removed
Package 'nvidia-361' is not installed, so not removed
Package 'nvidia-361-dev' is not installed, so not removed
Package 'nvidia-361-updates' is not installed, so not removed
Package 'nvidia-361-updates-dev' is not installed, so not removed
Package 'nvidia-367' is not installed, so not removed
Package 'nvidia-367-dev' is not installed, so not removed
Package 'nvidia-375' is not installed, so not removed
Package 'nvidia-375-dev' is not installed, so not removed
Package 'nvidia-384' is not installed, so not removed
Package 'nvidia-384-dev' is not installed, so not removed
Package 'nvidia-compute-utils-390' is not installed, so not removed
Package 'nvidia-dkms-390' is not installed, so not removed
Package 'nvidia-driver-390' is not installed, so not removed
Package 'nvidia-headless-390' is not installed, so not removed
Package 'nvidia-headless-no-dkms-390' is not installed, so not removed
Package 'nvidia-kernel-common-390' is not installed, so not removed
Package 'nvidia-kernel-source-390' is not installed, so not removed
Package 'nvidia-opencl-icd-340' is not installed, so not removed
Package 'nvidia-utils-390' is not installed, so not removed
Package 'bbswitch-dkms' is not installed, so not removed
Package 'bumblebee' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'primus' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-libopencl1-331' is not installed, so not removed
Package 'nvidia-libopencl1-331-updates' is not installed, so not removed
Package 'nvidia-libopencl1-340' is not installed, so not removed
Package 'nvidia-libopencl1-340-updates' is not installed, so not removed
Package 'nvidia-libopencl1-346' is not installed, so not removed
Package 'nvidia-libopencl1-346-updates' is not installed, so not removed
Package 'nvidia-libopencl1-352' is not installed, so not removed
Package 'nvidia-libopencl1-352-updates' is not installed, so not removed
Package 'nvidia-libopencl1-361' is not installed, so not removed
Package 'nvidia-libopencl1-361-updates' is not installed, so not removed
Package 'nvidia-libopencl1-367' is not installed, so not removed
Package 'nvidia-libopencl1-375' is not installed, so not removed
Package 'nvidia-libopencl1-384' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-nsight' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-331' is not installed, so not removed
Package 'nvidia-opencl-icd-331-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-340-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-346' is not installed, so not removed
Package 'nvidia-opencl-icd-346-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-352' is not installed, so not removed
Package 'nvidia-opencl-icd-352-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-361' is not installed, so not removed
Package 'nvidia-opencl-icd-361-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-367' is not installed, so not removed
Package 'nvidia-opencl-icd-375' is not installed, so not removed
Package 'nvidia-opencl-icd-384' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 100 not upgraded.
```

BTW this is the "tail end" of all that spewed out in my terminal otherwise the post would be a mile or KM long

If need be post the command to display what is installed so we can use this information for a proper and total purge and once I attempt to complete this purge, then the command for installing:
nvidia-graphics-drivers-390_390.87.orig-amd64.tar.gz
as it is labeled as in the downloads directory please and thank you. It lists this at the ppa and highlighted in blue newest version so this is what I selected and downloaded

---

### Post by wildmanne39 on 2018-09-06
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

In the future please include all code in one post using code tags.

Thanks

---

### Post by Bashing-om on 2018-09-06
hennmann; Whoahhh //
> 
0 upgraded, 0 newly installed, 0 to remove and 100 not upgraded.


Get this system updated and then see what we can do.

```

sudo apt update
sudo apt full-upgrade

```

[INDENT]maybe push can come to shove
[/INDENT]

---

### Post by Bashing-om on 2018-09-06
hennmann; Whoahhh //
> 
0 upgraded, 0 newly installed, 0 to remove and 100 not upgraded.


Get this system updated and then see what we can do.

```

sudo apt update
sudo apt full-upgrade

```

[INDENT]maybe push can come to shove
[/INDENT]

---

### Post by hennmann on 2018-09-06
This is the result
100 packages can be upgraded. Run 'apt list --upgradable' to see them.
After I entered your posted command and how do we get the upgrade going?
never mind with that last question as I reread and entered 
sudo apt full-upgrade
and now it is rattling away upgrading. Thanks again Bashing-OM

---

### Post by hennmann on 2018-09-06
I have upgraded the system, rebooted and back on again. Okay I need to purge the 340 driver and install the latest and greatest (I hope) driver. Next I entered 
sudo apt-get remove --purge nvidia-* which I found using your posted link to look
and got the same result as posted above which is "is not installed, so not removed"
and I guess the 340 must be purged first from what I read earlier

---

### Post by Bashing-om on 2018-09-07
hennmannl Ho Kay ...

Run terminal commands:
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```

reboot to see the effect - where I expect you to come up on the 390 driver.

[INDENT] Maybe Yes
[/INDENT]

---

### Post by Yellow Pasque on 2018-09-07
^^ If that doesn't work, maybe Synaptic would help you. It has certainly helped me manage and learn over the years.
I'm fairly sure you can install it through the software center, or just:
```
sudo apt-get install synaptic
```
Then it should be in your menu. (I use xubuntu/xfce, so I'm sorry if that's not very specific.)

Once you start it, you can search for "nvidia" (no quotes) and click the "installed version" column header twice to see what packages you have installed with nvidia in the name, and you can remove them all. Remember that you can use Shift to highlight multiple package names.


> Then the command for installing: nvidia-graphics-drivers-390_390.87.orig-amd64.tar.gz as it is labeled as in the downloads directory please and thank you. It lists this at the ppa and highlighted in blue newest version so this is what I selected and downloaded

No, that is not what you want. Delete that file. If you want to use the PPA, follow the instructions on its page.
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-driver-390
```

---

### Post by hennmann on 2018-09-08
I have the POS file but of course it is in my download directory and I probably have to direct to the directory using a command? See what I mean about archaic CLI, I would have had this done an hour later using the device manager! You can delete, browse and select the drivers you want to try whereas CLI is literally spoon feeding, begging for a command and continued spoon feeding. Sorry for bashing and flaming but as I mentioned before I can count on one hand how many Linux users I know and have fingers left over. I will give these commands a try later but the command to install will probably not work unless the directory is found? Also these drivers on POS are probably not an exe file so just "clicking" on them will probably not work. If the directory needs to be directed to lol do I add downloads to the command?

---

### Post by Yellow Pasque on 2018-09-08
> I have the POS file but of course it is in my download directory and I probably have to direct to the directory using a command?

Huh? No. Use the file manager. It's that thing like Windows Explorer.

---

### Post by hennmann on 2018-09-12
Yes I have used File Manager but obviously this directory has to be steered or directed to the terminal to install? Remember this driver is NOT an EXE file that one clicks onto for a self installing driver like the driver utilities many manufacturers have. Also the driver directly from the manufacturer isn't recommended.
1)Purge the lousy 340 driver
2)Install new 390.87 driver I downloaded from this web site. 
I haven't purged the old driver yet and I HAVE updated the system as per previous members so the system is up to date.
Unless I get proper commands I'm quite simply dead in the water

---

### Post by hennmann on 2018-09-12
> **Bashing-om said:**
> hennmannl Ho Kay ...

Run terminal commands:
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```

reboot to see the effect - where I expect you to come up on the 390 driver.
[INDENT] Maybe Yes
[/INDENT]


I'm trying this again and the only difference is I extracted the driver in the same directory as the original ppa driver and right now I used the same commands as you listed and it seems to be rattling away in the terminal like a virus opening up in Windows OS LOL 
I will give an update of the results after this is finished. Also I never purged the the 340 driver due to lack of knowledge so I will bumble along here.

---

### Post by hennmann on 2018-09-12
Something did happen after rebooting but all that  happened is the monitors exchanged (multiple monitors) and the purple spots remained. Otherwise before the log in screen appears there is a clean solid purple with none of these purple spots. I would say possibly the old 340 must be purged. I will again attempt to purge and see what happens.

---

### Post by oldfred on 2018-09-12
If you have not purged, you will have issues.

 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 

Then you can install as posted above and really in post #2.

---

### Post by Yellow Pasque on 2018-09-13
> **hennmann said:**
> Remember this driver is NOT an EXE file that one clicks onto for a self installing driver like the driver utilities many manufacturers have. Also the driver directly from the manufacturer isn't recommended.

I know. That's why I told you to DELETE the .tar.gz file you downloaded and use the PPA in the way it is intended (with the three commands I gave in post #20). 

You seem to be having a very difficult time following directions and you insist on doing things your own way. I don't have anything else to offer here. Good luck.

---

### Post by hennmann on 2018-09-15
As per the installation of the drivers it seemed to find the driver in my downloaded directory after I extracted the driver so this is probably required first.
Then as per Bashing-om's instructions
sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

It installed the driver and after I rechecked what was installed for drivers, the 340 seemed to become purged (don't ask me how) and the 390 driver installed, the monitors reversed I.E. the main monitor became the secondary monitor and the crappy old VGA became the primary monitor.
The colored squares remained but when all is said and done the video card is defective, with the problems being barely noticeable on Win 7 Pro 64 but worse on Ubuntu with the DVI-D port not working at all just the HDMI and VGA on both OS. The DVI-D port cuts on and off as well so I took it back to where I purchased it and they tested it and as it turns out the VGA port isn't working with Win 10 but this is probably a driver issue for 10 as the VGA works on 7 and Ubuntu. I exchanged it but upgraded to a GeForce GT1030 2GB DDR5 and it is working just fine without any additional steps required other than just installing the hardware and turning on. My only problem is this newer card doesn't have a VGA port so I'm typing this on a single monitor for the time being until I upgrade monitors and throw out the VGA boat anchors!!At the end of the day I have learned a few procedures and the problem is solved

---

### Post by Bashing-om on 2018-09-15
hennmann - :)

Sometimes it is hardware at fault !
Thanks for providing what the root cause if the issue was.

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]we do something different next time
[/INDENT][/INDENT]

---

### Post by hennmann on 2018-09-15
How do I mark this thread solved?

---

### Post by Bashing-om on 2018-09-15
hennmann -

1st post -> thread tools :)
see the provided link.

[INDENT][INDENT]all a process of learning
[/INDENT][/INDENT]

---

