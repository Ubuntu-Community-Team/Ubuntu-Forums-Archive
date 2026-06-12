---
title: "Nvidia GT650M graphics card not recognized in MSI GE60 laptop"
date: 2012-09-22
forum: Hardware
---

### Post by smeelkin on 2012-09-22
I recently got the MSI GE60 (0NC-084NE) laptop, and after dual-booting it with Ubuntu, I can't get Ubuntu to recognize the graphics card it contains. It has both the built in graphics and a Nvidia GT 650M card, but only the built in card is recognized.

I have tried installing the nvidia-current 295.59-0ubuntu1 package together with the nvidia-settings package, but it didn't work, and when I tried running the supplied X config for nvidia, it simply stopped using any graphics card, now I don't have an Xorg.conf file at all. I have also installed bumblebee, but I don't understand how it should work.

Furthermore I have checked the hardware on the computer using lshw -short, and it doesn't list the graphics card at all:
```
H/W path               Device      Class          Description
=============================================================
                                   system         GE60 0NC/GE60 0ND (To be filled by O.E.M.)
/0                                 bus            MS-16GA
/0/0                               memory         64KiB BIOS
/0/3d                              memory         512KiB L2 cache
/0/3e                              memory         64KiB L1 cache
/0/3f                              memory         3MiB L3 cache
/0/40                              memory         6GiB System Memory
/0/40/0                            memory         2GiB SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
/0/40/1                            memory         DIMM [empty]
/0/40/2                            memory         4GiB SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
/0/40/3                            memory         DIMM [empty]
/0/41                              processor      Intel(R) Core(TM) i5-3210M CPU @ 2.50GHz
/0/41/2.1                          processor      Logical CPU
/0/41/2.2                          processor      Logical CPU
/0/41/2.3                          processor      Logical CPU
/0/41/2.4                          processor      Logical CPU
/0/41/2.5                          processor      Logical CPU
/0/41/2.6                          processor      Logical CPU
/0/41/2.7                          processor      Logical CPU
/0/41/2.8                          processor      Logical CPU
/0/41/2.9                          processor      Logical CPU
/0/41/2.a                          processor      Logical CPU
/0/41/2.b                          processor      Logical CPU
/0/41/2.c                          processor      Logical CPU
/0/41/2.d                          processor      Logical CPU
/0/41/2.e                          processor      Logical CPU
/0/41/2.f                          processor      Logical CPU
/0/41/2.10                         processor      Logical CPU
/0/1                               processor      
/0/1/2.1                           processor      Logical CPU
/0/1/2.2                           processor      Logical CPU
/0/1/2.3                           processor      Logical CPU
/0/1/2.4                           processor      Logical CPU
/0/1/2.5                           processor      Logical CPU
/0/1/2.6                           processor      Logical CPU
/0/1/2.7                           processor      Logical CPU
/0/1/2.8                           processor      Logical CPU
/0/1/2.9                           processor      Logical CPU
/0/1/2.a                           processor      Logical CPU
/0/1/2.b                           processor      Logical CPU
/0/1/2.c                           processor      Logical CPU
/0/1/2.d                           processor      Logical CPU
/0/1/2.e                           processor      Logical CPU
/0/1/2.f                           processor      Logical CPU
/0/1/2.10                          processor      Logical CPU
/0/100                             bridge         Ivy Bridge DRAM Controller
/0/100/1                           bridge         Ivy Bridge PCI Express Root Port
/0/100/1/0                         generic        Illegal Vendor ID
/0/100/2                           display        Ivy Bridge Graphics Controller
/0/100/14                          bus            Panther Point USB xHCI Host Controller
/0/100/16                          communication  Panther Point MEI Controller #1
/0/100/1a                          bus            Panther Point USB Enhanced Host Controller #2
/0/100/1b                          multimedia     Panther Point High Definition Audio Controller
/0/100/1c                          bridge         Panther Point PCI Express Root Port 1
/0/100/1c.1                        bridge         Panther Point PCI Express Root Port 2
/0/100/1c.1/0          eth0        network        RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1c.2                        bridge         Panther Point PCI Express Root Port 3
/0/100/1c.2/0          scsi6       generic        RTS5116 PCI Express Card Reader
/0/100/1c.2/0/0.0.0    /dev/sdb    disk           xD/SD/M.S.
/0/100/1c.2/0/0.0.0/0  /dev/sdb    disk           
/0/100/1c.2/0.1                    generic        RTS5116 PCI Express Card Reader
/0/100/1c.3                        bridge         Panther Point PCI Express Root Port 4
/0/100/1c.3/0          wlan0       network        Centrino Wireless-N 135
/0/100/1d                          bus            Panther Point USB Enhanced Host Controller #1
/0/100/1f                          bridge         Panther Point LPC Controller
/0/100/1f.2            scsi0       storage        Panther Point 6 port SATA Controller [AHCI mode]
/0/100/1f.2/0          /dev/sda    disk           500GB WDC WD5000BPVT-2
/0/100/1f.2/0/1        /dev/sda1   volume         15GiB Windows NTFS volume
/0/100/1f.2/0/2        /dev/sda2   volume         100MiB Windows NTFS volume
/0/100/1f.2/0/3        /dev/sda3   volume         269GiB Windows NTFS volume
/0/100/1f.2/0/4        /dev/sda4   volume         179GiB Extended partition
/0/100/1f.2/0/4/5      /dev/sda5   volume         173GiB Linux filesystem partition
/0/100/1f.2/0/4/6      /dev/sda6   volume         6039MiB Linux swap / Solaris partition
/0/100/1f.2/1          /dev/cdrom  disk           DVD A  DS8A8SH
/0/100/1f.3                        bus            Panther Point SMBus Controller
/1                                 power          To Be Filled By O.E.M.

```

So is there a way to make my graphics card recognized? Help would be greatly appreciated.

---

### Post by nu11ifier on 2012-09-23
Hiya,  I have exactly the same problem when I tried to install Ubuntu 12.04 LTS. When trying Ubuntu 12.10 beta1, I had the NVIDIA GT650M listed in my output of lspci.    Anyway, I had no success on installing the Nvidia drivers and getting them to work with 12.10. The blacklisting of the intel_agp module (thus forcing the nvidia driver to be used for X) results in compiz not loading. So after logging in on the lightdm greeter, I only see the background image. No Unity bar gets started, no Alt+F2 or anything else giving me an xterm worked.   Can anyone help here? nu11

---

### Post by nu11ifier on 2012-09-23
Hi again!

I found a way how to enable that Nvidia GT650M on the MSI GE60 Laptop. 

After searching the net for a while - and after finding out I needed the 3.5.x Kernel for the card to be recognized, I hit this thread:

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

So, what I did was:

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia

--> You see your Turbo switch go dark! *hint hint*

sudo reboot

After reboot, I had a working X server with working Compiz again. Oh, Turbo switch is dark!

Then I tested:

glxspheres
--> 60 fps, Turbo switch dark

optirun glxspheres
--> 236 fps, Turbo switch lit, when exiting program, it goes dark again.

So this workaround seems to do well.

Cheers so much guys for bringing us bumblebee!!! CUDA@linux, here I come... ;)

o/

---

### Post by smeelkin on 2012-09-24
Nice to see it working! I tried installing the bumblebee packages as instructed, then using optirun, but now I get a new error message, saying: ```
[ 2388.303821] [ERROR]Cannot access secondary GPU - error: You need to change the ConnectedMonitor setting in /etc/bumblebee/xorg.conf.nvidia to 

[ 2388.303863] [ERROR]Aborting because fallback start is disabled.

```

I've tried changing the ConnectedMonitor between TV, CTR and DFP, but with the same error message. Interestingly, when I tried to run: ```
/usr/lib/nvidia-current/bin/nvidia-xconfig --query-gpu-info --nvidia-cfg-path=/usr/lib/nvidia-current
```I got ```
Number of GPUs: 1

GPU #0:
  Name      : GeForce GT 650M
  PCI BusID : PCI:1:0:0

  Number of Display Devices: 0

```
Maybe it has something to do with the 0 display devices.

Did you install a 3.5.x kernel? I have no idea where to go from here, except the usual excessive googling. Oh well, at least my card is recognized now :D




...I have no idea what I'm doing...

---

### Post by nu11ifier on 2012-09-24
Hi,

as I stated in my above post, I'm running Ubuntu 12.10 Beta1 which builds on linux-3.5.3. 

I installed Ubuntu 12.10, then left the xorg.conf untouched! Do install bumblebee as shown, this should also install the nvidia drivers you need. You don't need to reconfigure X for this. I had no problems using optirun then.

Using CUDA is another bit of nasty homework, I'm just on it. 

Good luck!

EDIT: 

For your reference, I post my output of "sudo lshw -short"

```

H/W path               Device      Class          Description
=============================================================
                                   system         GE60 0NC (To be filled by O.E.M.)
/0                                 bus            MS-16GA
/0/0                               memory         64KiB BIOS
/0/3d                              memory         1MiB L2 cache
/0/3e                              memory         128KiB L1 cache
/0/3f                              memory         6MiB L3 cache
/0/40                              memory         8GiB System Memory
/0/40/0                            memory         4GiB SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
/0/40/1                            memory         DIMM [empty]
/0/40/2                            memory         4GiB SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
/0/40/3                            memory         DIMM [empty]
/0/41                              processor      Intel(R) Core(TM) i7-3610QM CPU @ 2.30GHz
/0/100                             bridge         3rd Gen Core processor DRAM Controller
/0/100/1                           bridge         Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port
/0/100/1/0                         generic        Illegal Vendor ID
/0/100/2                           display        3rd Gen Core processor Graphics Controller
/0/100/14                          bus            7 Series/C210 Series Chipset Family USB xHCI Host Controller
/0/100/16                          communication  7 Series/C210 Series Chipset Family MEI Controller #1
/0/100/1a                          bus            7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2
/0/100/1b                          multimedia     7 Series/C210 Series Chipset Family High Definition Audio Controller
/0/100/1c                          bridge         7 Series/C210 Series Chipset Family PCI Express Root Port 1
/0/100/1c.1                        bridge         7 Series/C210 Series Chipset Family PCI Express Root Port 2
/0/100/1c.1/0          eth0        network        RTL8111/8168B PCI Express Gigabit Ethernet controller
/0/100/1c.2                        bridge         7 Series/C210 Series Chipset Family PCI Express Root Port 3
/0/100/1c.2/0          scsi7       generic        RTS5209 PCI Express Card Reader
/0/100/1c.2/0/0.0.0    /dev/sdc    disk           xD/SD/M.S.
/0/100/1c.2/0/0.0.0/0  /dev/sdc    disk           
/0/100/1c.2/0.1                    generic        RTS5209 PCI Express Card Reader
/0/100/1c.3                        bridge         7 Series/C210 Series Chipset Family PCI Express Root Port 4
/0/100/1c.3/0          wlan0       network        Centrino Wireless-N 135
/0/100/1d                          bus            7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1
/0/100/1f                          bridge         HM76 Express Chipset LPC Controller
/0/100/1f.2                        storage        7 Series Chipset Family 6-port SATA Controller [AHCI mode]
/0/100/1f.3                        bus            7 Series/C210 Series Chipset Family SMBus Controller
/0/1                   scsi0       storage        
/0/1/0.0.0             /dev/sda    disk           750GB WDC WD7500BPVT-2
/0/1/0.0.0/1           /dev/sda1   volume         12GiB Windows NTFS volume
/0/1/0.0.0/2           /dev/sda2   volume         97GiB EXT4 volume
/0/1/0.0.0/3           /dev/sda3   volume         15GiB Linux swap volume
/0/2                   scsi2       storage        
/0/2/0.0.0             /dev/cdrom  disk           CDDVDW SN-208AB
/0/3                   scsi6       storage        
/0/3/0.0.0             /dev/sdb    disk           4004MB SCSI Disk
/0/3/0.0.0/1           /dev/sdb1   volume         3818MiB Linux filesystem partition
/1                                 power          To Be Filled By O.E.M.

```

---

### Post by smeelkin on 2012-09-24
I got mine to work too now :D I tried following the instructions at the page you linked before and upgrading the drivers and programs, installing bumblebee-nvidia and all those things, then rebooting. I also reconfigured xorg.conf back to the normal, but I don't think it changed anything.

I think the driver upgrade ( to 304.43-0ubuntu1~precise~xup1 ) was the thing that did it. Also, my turbo switch is staying on constantly.

I only got a 190 fps in the glxspheres on optirun, but I suppose your quad core i7 processor and 8 gigs of ram do help a bit ;)

Good luck with the CUDA thing, report back if you get any results with it, and thanks for the help!


take some reward popcorn, you deserve it :popcorn:

---

### Post by vela3 on 2012-10-02
Thanks a lot for this great instructions.
It works now, though I did it slightly different, because I use the Dream Studio distribution, which I think I will like. 

I installed the distro, updated, and then installed the 3.5 kernel like described [here]("http://www.howopensource.com/2012/07/how-to-install-linux-kernel-3-5-quantal-in-ubuntu-12-04-11-10-11-04-10-10-and-10-04/")

Works well, thanks again and do have the popcorn.

---

### Post by Kranium31 on 2013-05-20
Thank you for the answer. This helped me wih my new laptop and Mint 14 mate 64bit. The first time i missed  the sudo reboot and just rebooted and it didnt work.

The second time around it worked. I had no sound before and now it works perfectly with bumblebee installed.

Thanks again

Ps: Im not sure if it matters but my turbo button stays on all the time for some reason.

---

