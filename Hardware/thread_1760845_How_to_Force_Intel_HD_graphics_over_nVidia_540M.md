---
title: "How to Force Intel HD graphics over nVidia 540M"
date: 2011-05-17
forum: Hardware
---

### Post by glomerulus on 2011-05-17
Hello everyone,

I have a Dell XPS 15(L502X) with :

[LIST]
[*]Intel core i5 2410M (Sandy bridge) processor
[*]nVidia GeForce 540M with Optimus
[/LIST]
I just did a fresh install of Ubuntu 11.04 64-bit. Visual effects, Compiz etc all worked out of the box.
However, I want to use the Intel HD graphics instead of the nVidia gpu to conserve battery life (and also because for some reason the laptop fan always keeps running)

To disable the nVidia card, i did:
```
sudo apt-get remove nVidia-* xserver-xorg-video-nouveau
```Then I added the following lines to **/etc/modprobe.d/blacklist.conf**
```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```.. followed by a reboot.

Trouble is that the fan is still constantly running even when it has no reason to.
And i'm not sure i have disabled the nVidia card

**lspci** still gives:
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
```For reference, **lshw** gives:
```
sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:f1000000-f107ffff
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
       resources: irq:49 memory:f1400000-f17fffff memory:e0000000-efffffff ioport:4000(size=64)
```What does the** "UNCLAIMED"** against the nVidia card mean?

Any remarks, suggestions will be appreciated!

---

### Post by Zogg on 2011-05-20
More and more people receive laptops with dual GPUs and linux is royally f***ed in this department. :(

Here is how you may disable nvidia card:
[http://ubuntuforums.org/showthread.php?t=1753473](http://ubuntuforums.org/showthread.php?t=1753473)
It would be great if you reported on the success or failure of that method.

You may search for "Optimus" in ubuntu forums for extensive information.

---

### Post by Meikrekel on 2011-09-18
I think I've disabled my Nvidia gt540m, but I'm not sure. Can someone tell me if I have succesfully managed to disable my gt540m, so my battery will last longer? My battery life is now around 2 hours, may be a bit less or more. 

Here is the output of a couple of commands I did:
```
wouter@wouter-ubuntu:~$ cd acpi_call
wouter@wouter-ubuntu:~/acpi_call$ lspci -vnnn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: nVidia Corporation GF106 [GeForce GT 555M] [10de:0df4] (rev ff) (prog-if ff)
wouter@wouter-ubuntu:~/acpi_call$ sh test_off.sh
Trying \_SB.PCI0.P0P1.VGA._OFF: failed
Trying \_SB.PCI0.P0P2.VGA._OFF: failed
Trying \_SB_.PCI0.OVGA.ATPX: failed
Trying \_SB_.PCI0.OVGA.XTPX: failed
Trying \_SB.PCI0.P0P3.PEGP._OFF: failed
Trying \_SB.PCI0.P0P2.PEGP._OFF: failed
Trying \_SB.PCI0.P0P1.PEGP._OFF: failed
Trying \_SB.PCI0.MXR0.MXM0._OFF: failed
Trying \_SB.PCI0.PEG1.GFX0._OFF: failed
Trying \_SB.PCI0.PEG0.GFX0.DOFF: failed
Trying \_SB.PCI0.PEG1.GFX0.DOFF: failed
Trying \_SB.PCI0.PEG0.PEGP._OFF: works!
wouter@wouter-ubuntu:~/acpi_call$ lspci -vnnn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: nVidia Corporation GF106 [GeForce GT 555M] [10de:0df4] (rev ff) (prog-if ff)
wouter@wouter-ubuntu:~/acpi_call$ sh test.sh
sh: Can't open test.sh
wouter@wouter-ubuntu:~/acpi_call$ sh test_on.sh
sh: Can't open test_on.sh
wouter@wouter-ubuntu:~/acpi_call$ ^C
wouter@wouter-ubuntu:~/acpi_call$ cd
wouter@wouter-ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce GT 555M] (rev ff)
wouter@wouter-ubuntu:~$ sudo lshw -C display
[sudo] password for wouter: 
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
       resources: irq:52 memory:f1400000-f17fffff memory:e0000000-efffffff ioport:4000(size=64)

```

---

### Post by .... on 2011-09-18
[http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/](http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/)
This allows you to use the nvidia card if you want and automatically turns it off when not in use.

---

### Post by Meikrekel on 2011-09-19
I know, I've installed ironhide. My question is, have I configured it right? My battery life is still only 2 hours, compared to windows 7, where it has around 5 hours of battery life

---

### Post by .... on 2011-09-19
The Linux kernel has problems with battery life as of late. One thing you can try is to boot with pcie_aspm=force. Some systems are known to have issues with this (which is why it's disabled by default). Try it once by manually editing the grub/boot line. If your system is okay, make the change permanent: [http://dickmcjohnnson.wordpress.com/2011/07/02/linux-kernel-power-problems-solved/](http://dickmcjohnnson.wordpress.com/2011/07/02/linux-kernel-power-problems-solved/)

---

