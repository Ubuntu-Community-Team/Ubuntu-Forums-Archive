---
title: "Need help with NVidia 9600GT on 15.10"
date: 2016-04-17
forum: Hardware
---

### Post by nskirov on 2016-04-17
Hello Ubuntu community,

Last Friday, I unwisely went for a dist upgrade from 15.04 to 15.10. I am not stuck with the infamous "The System is running in low-graphics mode" error.

I'm using the nvidia-340 driver and have done a bunch of research already but nothing has helped yet. Could someone give me a hand, I will be ready to post more info about my system/drivers/installs etc.?

---

### Post by oldfred on 2016-04-17
When you upgrade you have to remove proprietary driver, upgrade, and then readd proprietary driver from repository. 
In between you normally have to use nomodeset to get into low graphics mode so you can install nVidia driver from Ubuntu's repository.

Post this from terminal:
 sudo lshw -c display
      
 dkms status

 sudo ubuntu-drivers devices

If dkms status just comes back then driver is not installed with upgrade.

---

### Post by nskirov on 2016-04-17
Hello Oldfred,

I actually already purged and reinstalled the driver, I used nvidia-340 since that worked in 15.04. Just fyi. Here is the info you requested:

sudo lshw -c display

```

  *-display
       description: VGA compatible controller
       product: G94 [GeForce 9600 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:30 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f4000000-f5ffffff ioport:dc80(size=128) memory:f7e00000-f7e7ffff

```

dkms status

```

bbswitch, 0.7, 4.2.0-35-generic, x86_64: installed
nvidia-340, 340.96, 4.2.0-35-generic, x86_64: installed
virtualbox, 5.0.14, 3.19.0-51-generic, x86_64: installed
virtualbox, 5.0.14, 4.2.0-35-generic, x86_64: installed

```

sudo ubuntu-drivers devices

```

== /sys/devices/pci0000:00/0000:00:03.0/0000:02:00.0 ==
modalias : pci:v000010DEd00000622sv00003842sd0000C868bc03sc00i00
vendor   : NVIDIA Corporation
model    : G94 [GeForce 9600 GT]
driver   : nvidia-304 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-340 - distro non-free recommended
driver   : nvidia-340-updates - distro non-free
driver   : nvidia-304-updates - distro non-free

== cpu-microcode.py ==
driver   : intel-microcode - distro non-free

```

---

### Post by nskirov on 2016-04-17
The nvidia-340 driver seems to work correctly so I started exploring other possible issues...

In particular I noticed that lightdm was not starting correctly, so I decided to try using gdm instead by running:

```
sudo dpkg-reconfigure lightdm
```

and selecting gdm as the display manager.

I was still stuck at the "The System is running in low-graphics mode" error message so I used the information here:

[http://askubuntu.com/questions/689570/gdm-not-working-with-ubuntu-15.10]("http://askubuntu.com/questions/689570/gdm-not-working-with-ubuntu-15.10")

to get things working with gdm.

That said, if anyone is interested in getting more information about my issues with lightdm, I'd be more than happy to explore that further with you.

Cheers.

---

