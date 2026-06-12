---
title: "Latest Ubuntu 8.10 kernel update is messed up"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by ronaldv on 2009-04-07
Hi,

since the rollout of the latest 8.10 kernel update (2.6.27-11) my machine has been very messy. During the update the initrd was not building (showing errors). I managed to build the initrd manually and then it worked for a while.

But since a few days the kernel fails again completely. It looks like many kernel-modules are not loading BUT dmesg & syslog do not show relevant errors.

The result is:
- no networking
- no cpu frequency scaling
- no nvidia driver (nv drivers works normal)
- .......

I have been on Linux since 2003 but have never seen this before.

Does anybody have hints or is experiencing the same?

---

### Post by frodon on 2009-04-07
Try to reinstall the kernel packages through synaptic, it will re-run the neeeded initrd commands and check for errors then paste them here.

About nvidia drivers if you don't use the repo version it is normal that they don't work after kernel update, in this case you just need to install them again and will surely have to do so after each kernel update.

---

### Post by vanadium101 on 2009-04-07
The kernel updates lost sound for me. I've tried reinstalling every thing to do with sound but it didn't work. tried reinstalling the kernel too and I'm unable to force the previous version to be used

---

### Post by Mamitt on 2009-04-07
> **vanadium101 said:**
> The kernel updates lost sound for me. I've tried reinstalling every thing to do with sound but it didn't work. tried reinstalling the kernel too and I'm unable to force the previous version to be used

Got the same problem. Adept ended up with an error after security update. 
My onboard sound (Intel) was gone after required reboot. KMixer symbol is red-crossed.

Have no idea what to do. Looking for hours for a solution. In former Kubuntu-versions it worked fine, the sound driver was auto detected and no reason to worry about.

How can a security update cause something like that? :mad:

---

### Post by frodon on 2009-04-07
Any kernel update can cause this, if you know how to proceed please fill a launchpad bug report so that ubuntu developers can be aware of your issue.

---

### Post by ronaldv on 2009-04-08
I re-installed the kernel via synaptic.

No error, did not run long.

But still the same problems.

---

### Post by frodon on 2009-04-08
Have you installed anything manually about your sound drivers, graphic drivers and so on or have you always used synaptic ?

---

### Post by Najand on 2009-04-08
> **ronaldv said:**
> I re-installed the kernel via synaptic.

No error, did not run long.

But still the same problems.

Can you give us more information about your Devices and the Kernel you installed.

---

### Post by Zeedok on 2009-04-08
I think we are trying to solve the same problem over [here]("http://ubuntuforums.org/showthread.php?t=1119588"). We've lots of device and driver info over there - knock yourself out (and please find a solution)

Thanks

---

### Post by ronaldv on 2009-04-16
Well I hope somebody can make something out of this:

I only installed a non-ubuntu webcam driver (r5u870).

uname -r:

2.6.27-11-generic


lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86M [GeForce 8400M GT] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

---

