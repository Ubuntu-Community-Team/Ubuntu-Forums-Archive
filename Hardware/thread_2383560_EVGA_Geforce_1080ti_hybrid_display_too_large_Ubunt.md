---
title: "EVGA Geforce 1080ti hybrid display too large Ubuntu 14.04"
date: 2018-01-26
forum: Hardware
---

### Post by marseille2 on 2018-01-26
Hello, I've seen similar questions to mine online but there's so many different directions, I don't know which to follow.

I'm still using Trusty LTS and my desktop is ICEWM (previously I ran XFCE with ATI on an AMD ... then transferred my harddrive onto an Intel system). I tried to change resolutions through xrandr but it doesn't seem to pick up the size of my screen, and I have no xorg file (except very old backup files for the ATI).

BTW the nouveau drivers (currently blacklisted) worked perfectly, so the font size only got huge after installing nvidia-390 binary. I do have nomodset for boot, so no black screen problems ... I just can't figure out how to change the font size.

Also in the nvidia settings... I have no idea what to do since all the tabs are labeled but there's nothing to choose from and I don't know what I should do as I'm an NVIDIA n00b.

[B]$ gksudo nvidia-settings
[/B]```
ERROR: Error querying enabled displays on GPU 0 (Missing Extension).



ERROR: Error querying connected displays on GPU 0 (Missing Extension).


** Message: PRIME: No offloading required. Abort
** Message: PRIME: is it supported? no


ERROR: nvidia-settings could not find the registry key file. This file
       should have been installed along with this driver at
       /usr/share/nvidia/nvidia-application-profiles-key-documentation. The
       application profiles will continue to work, but values cannot be
       prepopulated or validated, and will not be listed in the help text.
       Please see the README for possible values and descriptions.
```

Tried to hunt for keys ... found these two files are located in '/usr/share/nvidia' and '/usr/share/nvidia-390':
-- nvidia-application-profiles-390.12-key-documentation
-- nvidia-application-profiles-390.12-rc

**$ lspci -nnk | grep -iA2 vga**
```
65:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1b06] (rev a1)
        Subsystem: eVga.com. Corp. Device [3842:6598]
65:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:10ef] (rev a1)
        Subsystem: eVga.com. Corp. Device [3842:6598]
        Kernel driver in use: snd_hda_intel
b2:05.0 System peripheral [0880]: Intel Corporation Device [8086:2034] (rev 04)
```

**$ glxinfo**
```
name of display: :0
Error: couldn't find RGB GLX visual or fbconfig
Error: couldn't find RGB GLX visual or fbconfig
```

**$ xrandr -q**
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        73.0*
```

**UPDATE**: I got rid of the Nvidia driver; restored Nouveau drivers; and reconfigured xorg ... but it doesn't make a difference. Xrandr is still telling me the same thing about gamma; and the screen resolution is still off the charts. I've tried a lot of stuff over the past few days but this is tricky.

---

### Post by marseille2 on 2018-01-29
bump

---

### Post by oldfred on 2018-01-29
How did you install nVidia driver, from nVidia with .run or with ppa and directly into Ubuntu.
Only the ppa is recommended.

Did you purge all old drivers before installing new driver?

 #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 


 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices 
   If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
   sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by marseille2 on 2018-01-30
Oldfred, thank-you for being so kind to help me. I did originally install from the PPA but I also failed to remove all drivers before that. My bad!

But I think I finally got it but I'm going to give it a couple days before I mark the thread solved, just in case the settings flake on me again (that happened before).

Just a quick run-down. I have no idea how I got it to work. But I did do a full purge of nvidia-390 before I reverted back to the Nouveau driver. After I saw your post, I went back and noticed that the system did not give me the 390 option any more ... only 384. But in Synaptic I see 310 experimental. So I decided to try the 384 and installed it. ... There was no xorg file (same as 390), so I just put one in /etc/X11. 

BTW ... I also switched kernels and dropped down from 4.14x low-latency to 4.4x. I'm a little suspicious about the way I installed the 4.14 because it did not work with VirtualBox (dkms issues) and I'm not sure what was going on with Mesa and some other stuff before I dropped my drive into the new PC.

**$ uname -a**
```
Linux av 4.4.0-111-lowlatency #134~14.04.1-Ubuntu SMP PREEMPT Mon Jan 15 16:35:19 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

I have some other problems going on with dual boot (I have windows on another drive and have no idea how to fix grub), so I needed to shutdown. After booting back into Ubuntu, I was surprised that the resolution is correct and looks good. 

The major difference is that now I have an nvidia-settings window that is actually populated with information. It was completely empty before this last boot. 

So let me take it for a test drive and see if it's stable. If it is I will mark the thread solved in a few days.

If anyone else wants to chime in and give me some tips that I might need later, I'd appreciate it. 

To answer questions about what's currently installed ...

**$ dpkg -l | grep nvidia**
```
ii  nvidia-384                                                  384.111-0ubuntu0.14.04.1                                    amd64        NVIDIA binary driver - version 384.111
ii  nvidia-cg-dev:amd64                                         3.1.0013-1                                                  amd64        Cg Toolkit- GPU Shader Authoring Language (headers)
ii  nvidia-cg-toolkit                                           3.1.0013-1                                                  amd64        Cg Toolkit- GPU Shader Authoring Language
ii  nvidia-opencl-icd-384                                       384.111-0ubuntu0.14.04.1                                    amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                                0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             331.20-0ubuntu8                                             amd64        Tool for configuring the NVIDIA graphics driver
```

**$ dkms status**
```
bbswitch, 0.7, 4.4.0-111-lowlatency, x86_64: installed
nvidia-384, 384.111, 4.4.0-111-lowlatency, x86_64: installed
```

NOTE: Do I need to remove bbswitch, even though the 384 driver seems to work?



**$ lsmod | grep nvidia**
```
nvidia_uvm            647168  0
nvidia_drm             45056  1
nvidia_modeset        860160  5 nvidia_drm
nvidia              13144064  382 nvidia_modeset,nvidia_uvm
drm_kms_helper        151552  2 i915_bpo,nvidia_drm
drm                   360448  6 ttm,i915_bpo,drm_kms_helper,nvidia_drm
```

---

### Post by oldfred on 2018-01-30
I do not know about bbswitch.
It was my original understanding that it was only for those laptops that have one video port but can autoswitch between Intel & nVidia driver/output.

But bbswitch seems to get installed just about all the time. Maybe they cannot tell if needed or not so always install it?

---

### Post by marseille2 on 2018-01-30
I just tried booting into the 4.14x kernel and found that the resolution was still huge. Strange thing... I then rebooted into the 4.4x kernal and the resolution looks great. Maybe I should remove the 4.14x kernel?

---

### Post by oldfred on 2018-01-30
Was this kernel left over from an upgrade?
Dpkg manages the integration of the nVidia driver into the kernel, but if not part of current Ubuntu then not in dpkg list to run updates on.

If you manually added kernel, you probably have to manage the install of the nVidia driver into kernel yourself. This would be like what you have to do with the .run version of driver directly from nVidia as it is then up to user to manage.

---

### Post by marseille2 on 2018-01-30
Ok that's starting to make some sense for me. I manually added that kernel and I think it's causing me more grief than it's worth. My initial hope was that 4.14x would help me with a device but it did not, so it's really not needed.

Also... I'm in synaptic and marked bbwitch for removal but it wants to remove nvidia-prime. I'm not sure how to proceed. I'm just starting to look at the [Nvidia page explanation]("https://devtalk.nvidia.com/default/topic/957814/linux/prime-and-prime-synchronization/") and it looks long and grueling. But I did spot that nvidia-prime needs kernel 4.6x+ to work.

---

### Post by oldfred on 2018-01-30
Found this which then is Prime also is for support of the hybrid graphics.
[https://wiki.archlinux.org/index.php/PRIME](https://wiki.archlinux.org/index.php/PRIME)
> PRIME is a technology used to manage hybrid graphics found on recent laptops ([Optimus for NVIDIA]("https://wiki.archlinux.org/index.php/NVIDIA_Optimus"), AMD Dynamic Switchable Graphics for Radeon). PRIME GPU offloading and Reverse PRIME is an attempt to support muxless hybrid graphics in the Linux kernel. 

---

### Post by marseille2 on 2018-02-01
Oldfred, I'm marking this thread solved. I'm fairly certain that the way I installed the 4.14x kernel caused me problems when I wrecklessly installed the nvidia-390 driver. Although the latter might have been too much of a gamble, since I'm getting excellent results with the 384.

I logged in and out of that manually installed 4.14.x kernel a few more times and the resolution was always huge; there was nothing in nvidia-settings and xrandr kept reporting the gamma problem (with or without the 390 binary driver).

When I log into the 4.4.x kernel (from synaptic), I have no problems and the resolution is terrific!

And so ... I've gotten rid of the 4.14x and have decided to wait for Ubuntu 18.x LTS to be released to upgrade my kernel. I also removed bbswitch (which automatically removed prime), since I'm running a custom desktop.

Thank-you for being patient with me:)

---

