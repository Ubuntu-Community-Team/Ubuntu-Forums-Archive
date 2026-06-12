---
title: "problem with a new graphic card (GeForce GT 710) in Kubuntu 18.04"
date: 2018-11-27
forum: Hardware
---

### Post by jduns on 2018-11-27
[SIZE=3][FONT=arial]As I said elsewhere, I have a problem with a new graphic card (GeForce GT 710), in Kubuntu 18.04. All seems right, but when [SIZE=3][FONT=arial]the screen[/FONT][/SIZE] turn off [SIZE=3][FONT=arial]automatically [/FONT][/SIZE](after 4 minutes) with the screen  saver active (system settings - desktop behavior - screen locking - appearance - slideshow), the screen is not definitively turned off, but after 3 seconds it  turns on again, and shows the slideshow with colors close to black, and  then goes off again, and then goes on again, and so on...
No problem deactivating the screen saver.

```
sudo lshw -C display
[sudo] password for duns: 
  *-display                 
       description: VGA compatible controller
       product: GK208 [GeForce GT 710B]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:125 memory:de000000-deffffff memory:d0000000-d7ffffff memory:d8000000-d9ffffff ioport:e000(size=128) memory:c0000-dffff
  *-display
       description: Display controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:123 memory:dd000000-ddffffff memory:c0000000-cfffffff ioport:f000(size=64)

```

(The bios is set for multi-monitor)

Any idea?
Thank you
[/FONT][/SIZE]

---

### Post by oldfred on 2018-11-27
Post this also:
dkms status

I did not know that there is a difference in drivers recommended for Fermi based (laptop?) chips.
It does not look like your is.
 Fermi based should use 390.xx not newer
[https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus](https://nvidia.custhelp.com/app/answers/detail/a_id/4656/~/list-of-fermi-series-geforce-gpus) 

You can check what is correct driver, but should only install from Ubuntu repository or ppa.


 Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 

If you have to install new driver, then be sure to totally purge old driver.

I just now got a new update to my nVidia driver in 18.04. You may want to check for updates.

---

### Post by jduns on 2018-11-27
Thank you!
```
$ dkms status
nvidia, 390.77, 4.15.0-39-generic, x86_64: installed
virtualbox, 5.2.18, 4.15.0-39-generic, x86_64: installed

```
The page of GeForce give the 410.78 as last, but the 390.77 one as correct as well.

How can I "be sure to totally purge old driver"?

Yesterday I tried to install new drivers from PPA (ppa:graphics-drivers/ppa), but I could not install them (via system settings): was always installed nouveau driver, until I removed the PPA and then I could install the distro driver.

But are we sure that the problem is the driver and not **some settings** (maybe on etc/default/grub)?

EDIT

Where search for the bug, witch **log**?

---

### Post by oldfred on 2018-11-27
I do not know vitualbox. It may have its own requirements for video.

Grub normally only comes into video settings when needing nomodeset. A few other cases, but not normally related to nVidia once installed.

 If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.
sudo apt-get remove --purge nvidia-*
sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
This xorg file may not exist, so if error that would be ok
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
      
 If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

### Post by jduns on 2018-11-27
Thank you! I will try, as you said, assuming the problem is the driver (I'm not so sure).
I will say something not next days, because I will be busy.

---

### Post by SeijiSensei on 2018-11-27
Virtual machines running under VirtualBox cannot address the video hardware directly.  The VM cannot see the NVIDIA card nor use the appropriate driver. VB does provide a proprietary video driver in the Extensions package.  That's the best you can do.

Can you disable the Intel video in the system's BIOS?  That's what I have done with these kinds of "hybrid" video systems.

---

### Post by jduns on 2018-11-28
This evening, in a new installation of the same PC, I installed PPA and the last not-beta nvidia driver the **410** one. But the bug remain, same as with the 390 driver (ubuntu, not PPA, nvidia driver): the same bug.
Moreover,  in the new installation where I installed the driver 410 I had the  black screen and I could access it *only in safe mode*.
@SeijiSensei: This bug was also *before* I added in BIOS the multi-screen option, that I project use with a e-ink boox monitor.
EDIT
Modified grub, so: GRUB_CMDLINE_LINUX_DEFAULT="quiet **splash nvidia-drm.modeset=1**", but the problem is still **not fixed**
Modified grub, so: GRUB_CMDLINE_LINUX_DEFAULT="**nomodeset**", but the problem is still [B]not fixed

[/B]EDIT```
$ inxi -GCS
System:    Host: sar-intel1 Kernel: 4.15.0-39-generic x86_64 bits: 64 Desktop: KDE Plasma 5.12.6
           Distro: Ubuntu 18.04.1 LTS
CPU:       Dual core Intel Core i3-7100 (-MCP-) cache: 3072 KB
           clock speeds: max: 3900 MHz 1: 800 MHz 2: 800 MHz
Graphics:  Card-1: Intel HD Graphics 630
           Card-2: NVIDIA GK208 [GeForce GT 710B]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1280x1024@75.02hz
           OpenGL: renderer: GeForce GT 710/PCIe/SSE2 version: 4.6.0 NVIDIA 390.77

```

---

### Post by jduns on 2018-12-05
Strange: with an other monitor (on the same PC) there is no problem. It **seems solved**.

---

### Post by jduns on 2018-12-10
Yes the problem was the hardware. With the new monitor no problem. Thank you!

---

