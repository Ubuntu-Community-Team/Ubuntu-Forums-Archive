---
title: "How to disable onboard intel graphics permanently?"
date: 2014-04-04
forum: Hardware
---

### Post by beerninja on 2014-04-04
I have a Dell GX520 here with onboard intel graphics and sadly the Dell BIOS is so poorly made that it will not even allow me to disable the onboard graphics now that I have installed a PCI Nvidia Quadro NVS 280.  In windows, I had to use the device manager to disable them.  In linux, no such device manager exists so I've been trying various CLI commands attempting to disable it but with no success.

I need to disable it before linux boots because it is causing infinite boot loop in linux.  I'm 99% sure the intel graphics with the nvidia card at the same time is breaking linux and causing boot loop.  (posts about it [http://ubuntuforums.org/archive/index.php/t-2131784.html](http://ubuntuforums.org/archive/index.php/t-2131784.html) and [http://ubuntuforums.org/showthread.php?t=2210348&p=12968491#post12968491](http://ubuntuforums.org/showthread.php?t=2210348&p=12968491#post12968491))

If I use nomodeset it will boot up in software rendering mode who allows me to install various drivers but I am never able to use said drivers since I can't get into ubuntu or any linux distro without using nomodeset or i915.modeset=0.  Both put me into software rendering mode.

Here is what I've tried to disable the intel graphics:

```
sudo nano -w /etc/modprobe.d/blacklist
```
```
blacklist i915
```
then save, then...
```
sudo update-initramfs -u
```
Unfortunately this had no effect.

Then I tried adding this after "quiet splash" in the boot options:
GRUB_CMDLINE_LINUX_DEFAULT="agp=off"
Nothing changed.  I found that on some debian forum so maybe it doesn't work with unbuntu?

Then I found this:  [http://www.dslreports.com/forum/r25280447-How-to-disable-graphics-card-via-sysfs](http://www.dslreports.com/forum/r25280447-How-to-disable-graphics-card-via-sysfs) which talks about how to power off a device.
So I tried these commands from that thread (as root):
```
echo -n "auto" > /sys/devices/pci0000:00/0000:00:02.0/power/control
```
```
echo -n "0000:00:02.0" > /sys/bus/pci/drivers/i915/unbind
```
The second line said directory does not exist.  I took a look and found no such i915 directory even though i915 is showing up in my lsmod.

Here is my lsmod in regards to video stuff:

nvidia               7108418  0 
nouveau               968899  0 
mxm_wmi                12893  1 nouveau
wmi                    18673  2 mxm_wmi,nouveau
ttm                    72698  1 nouveau
video                  18856  2 i915,nouveau
drm_kms_helper         46907  2  i915,nouveau
drm                   243663  4  ttm,i915,drm_kms_helper,nouveau
i2c_algo_bit           13197  2  i915,nouveau
ptp                    18445  1 tg3

here is my lspci:

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev  02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root  Port (rev 02)
00:02.0 Display controller: Intel Corporation 82945G/GZ  Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel  Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1c.0 PCI  bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev  01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2  (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI  Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7  Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel  Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB  controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev  01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI  Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge  (rev e1)
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7  Family) AC'97 Audio Controller (rev 01)
00:1f.0 ISA bridge: Intel Corporation  82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface:  Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE  interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev  01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev  01)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751  Gigabit Ethernet PCI Express (rev 01)
04:00.0 VGA compatible controller:  NVIDIA Corporation NV34GL [Quadro NVS 280 PCI] (rev a1)

If anyone know how to disable the onboard graphics before linux starts up, I would greatly appreciate some help :)

---

### Post by tgalati4 on 2014-04-04
I would work the problem a different way.  Remove the nVidia card.  Clean out the machine and reseat all cards and cables.  Then try to boot.  If you are still getting a boot-loop, then you may have a motherboard problem since the Intel graphics are part of the motherboard.  The i915 driver has been around a long time and is pretty stable, so the inability to boot with it as the primary graphics card could indicate a serious hardware problem.  If you can't get it to boot with the on-board graphics, then trying to troubleshoot with the nVidia card will be difficult.

---

