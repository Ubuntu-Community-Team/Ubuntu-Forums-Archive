---
title: "trouble with graphic card on TOSHIBA Protegé R500"
date: 2009-04-25
forum: Hardware
---

### Post by sontags on 2009-04-25
Hi

I just installed ubuntu 9.04 on my TOSHIBA Protegé R500. Everything works fine except of the damn graphic chip (Intel Graphics Media Accelerator 950). I get this nasty "Desktop effects could not be enabled"-message when I try to turn on "Normal" visual effects via System > Preferences > Appearance. And when I launch any graphical app such as VLC and start playing any movie, the app just dies.

Booting the ubuntu 9.04 live cd, even this works perfect (which i do not really understand). 

A few infos:

```

daniel@makbooc:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
03:0b.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:0b.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
03:0b.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

``````

daniel@makbooc:~$ hal-device
...
156: udi = '/org/freedesktop/Hal/devices/pci_8086_27a6'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27a6'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1'  (string)
  info.product = 'Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller'  (string)
  pci.product_id = 10150  (0x27a6)  (int)
  pci.vendor_id = 32902  (0x8086)  (int)
  pci.subsys_product_id = 34  (0x22)  (int)
  pci.subsys_vendor_id = 4473  (0x1179)  (int)
  pci.device_class = 3  (0x3)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  info.vendor = 'Intel Corporation'  (string)
  pci.product = 'Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller'  (string)
  pci.subsys_vendor = 'Toshiba America Info Systems'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  info.subsystem = 'pci'  (string)

157: udi = '/org/freedesktop/Hal/devices/pci_8086_27a2'
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27a2'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  info.product = 'Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller'  (string)
  pci.product_id = 10146  (0x27a2)  (int)
  pci.vendor_id = 32902  (0x8086)  (int)
  pci.subsys_product_id = 34  (0x22)  (int)
  pci.subsys_vendor_id = 4473  (0x1179)  (int)
  pci.device_class = 3  (0x3)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  info.vendor = 'Intel Corporation'  (string)
  pci.product = 'Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller'  (string)
  pci.subsys_vendor = 'Toshiba America Info Systems'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  info.subsystem = 'pci'  (string)
...

```Running hal-device while working with the live cd I get one more video device: 

```

udi = '/org/freedesktop/Hal/devices/pci_8086_27a2_drm_i915_card0'
  access_control.file = '/dev/dri/card0'  (string)
  access_control.type = 'video'  (string)
  drm.dri_library = 'i915'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'drm', 'access_control'} (string list)
  info.category = 'drm'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27a2'  (string)
  info.product = 'Direct Rendering Manager Device'  (string)
  info.subsystem = 'drm'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27a2_drm_i915_card0'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.device_file = '/dev/dri/card0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'drm'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/drm/card0'  (string)

```And some lsmod output (first on my installed system, second on the booted live cd):

```

daniel@makbooc:~$ lsmod | grep agpgart 
agpgart                42696  2 intel_agp

``````

daniel@makbooc:~$ cat lsmod_cdrom | grep agpgart
agpgart                42696  3 drm,intel_agp

```Does anybody have an idea how to fix this issue?

---

### Post by coffeecat on 2009-04-25
This wiki page gives you some background as to why there are a lot of Intel problems at the moment:

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance?](https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance?)

There are some ideas on this thread that may help:

[http://ubuntuforums.org/showthread.php?t=1134984](http://ubuntuforums.org/showthread.php?t=1134984)

---

### Post by sontags on 2009-04-25
Thanks for your help coffeecat!

I just reverted my drivers as described by Jai Harrison, but sadly this did not work for me. Still the same issues...

Is there a way to force Ubuntu to load the missing device (which is loaded when I boot the live cd)? It is pretty weird that the drivers are working fine when using the cd.

---

### Post by coffeecat on 2009-04-26
Sorry I can't help further. I just happened to find those two links and hoped they might be of use. I'm in the lucky position of my two laptops (an older one with the 915GM chipset and a new one with a recent Intel graphics) working fine with compiz in Jaunty. Or, at least, so far. I'm watching upgrades with trepidation. :(

I've bumped your thread for you so perhaps someone else might notice and be able to help.

The only other thing to say is that, according to the first link, the complete rewriting of the Intel drivers is clearly a work in progress, so hopefully bug-squashed versions might be trickling down from upstream sooner or later.

---

### Post by mikeypizano on 2009-04-26
I too have the same issue with my Toshiba A205-S5859, but I installed "Compiz Icon" and right click the tray icon and hit "reload" and it will work.

---

### Post by sontags on 2009-04-26
Thank you mikey

The compiz-icon (package is named fusion-icon) did non fix my problem neither. I tried it with both original intel driver shipped with ubuntu 9.04 and the old version (2.4).

The result was nothing bis a white screen and a mouse curser. I had the same effect when turning on the compiz-manager blacklist skip flag:

```

SKIP_CHECKS=yes compiz-manager

```

Seems like I have to wait for the rewritten driver...

---

### Post by mikeypizano on 2009-04-26
> **sontags said:**
> Thank you mikey

The compiz-icon (package is named fusion-icon) did non fix my problem neither. I tried it with both original intel driver shipped with ubuntu 9.04 and the old version (2.4).

The result was nothing bis a white screen and a mouse curser. I had the same effect when turning on the compiz-manager blacklist skip flag:

```

SKIP_CHECKS=yes compiz-manager

```

Seems like I have to wait for the rewritten driver...

Sorry, I may just put Vista back on mine and keep Ubuntu on my desktop... I am waiting for the iPod sync support to be added to Rhythmbox anyway.

---

### Post by sontags on 2009-05-02
Hey There!

I just installed the 2.7 Driver from Stefan Glasenhardt ([https://launchpad.net/~glasen/+archive/ppa]("https://launchpad.net/%7Eglasen/+archive/ppa")). Did not made any difference... Just as info.

---

### Post by sontags on 2009-05-05
The problem is: [http://www.h-online.com/open/Ubuntu-9-04-and-Intel-graphics--/features/113196](http://www.h-online.com/open/Ubuntu-9-04-and-Intel-graphics--/features/113196) (found via delicious.com)

[FONT=Arial]Thanks to [/FONT]Dr. Oliver Diedrich, interesting article to me as a not-that-deep-into-X11-and-kernel-guy.

By the way: People with the same problem should have a look at the Fedora 11 feature list ([http://fedoraproject.org/wiki/Releases/11/FeatureList](http://fedoraproject.org/wiki/Releases/11/FeatureList)). Eventually (or hopefully) they took some lessons learned from Ubuntu 9.04 and got those issued describe by Diedrich fixed. This would make me switch. Just because everything (such as scrolling, moving windows, just everything) sucks if the graphic drivers don't work properly.

---

