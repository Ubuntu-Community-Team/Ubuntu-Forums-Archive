---
title: "I want to extract uncompressed AVI from DV camcorder through IEEE1394 board"
date: 2019-04-06
forum: Hardware
---

### Post by kazu755 on 2019-04-06
I am trying to extract video (uncompressed AVI) from DV camcorder (Panasonic NV-MX3000) through firewire on Ubuntu 18.04.2 LTS 64bit. It is the first time to use Ubuntu and also post article here.  The IEEE1394 board (PCI express x1) is attached to the motherboard. The DV camcorder and IEEE1394 port is connected with DV cable(both 4pins). I tried to extract video either dvgrab or kino, but I could not extract anything yet. So I want advices and comments to resolve this issue.

What I did is described as follows:



(1) from hardware side:
I got following message as I tried "# lspci -v":

04:00.0 Firewire (IEEE 1394): VIA technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI controller (rev 0)(prog-if 10 [OHCI]
subsystem: VIA technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI controller
Flags: bus master, medium devsel, latency 32, IRQ 18
Memory at f7100000 (32-bit, non-prefetchable) [size=2K]
I/O ports at e000 [size=128]
Capabilities : [50] Power Management version 2
Kernel driver in use : firewire_ohci
Kernel module : firewire_ohci

I also got following result as I tried "# ls -l fw*" at /dev:

crw------- 1 root root 244, 0 April 6 13:41 fw0

From what I got above, I understand the IEEE1394 board is recognized by Ubuntu system.



(2) from software side:

The website at ([https://ubuntu.pkgs.org/18.04/ubuntu-universe-i386/dvgrab_3.5+git20160707.1.e46042e-1_i386.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-universe-i386/dvgrab_3.5+git20160707.1.e46042e-1_i386.deb.html)) requires several libraries to make dvgrab work. So I tried to install all of them as follows:

- libavc1394 ([https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libavc1394-0_0.5.4-4build1_i386.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libavc1394-0_0.5.4-4build1_i386.deb.html)) : apt-get install libavc1394-0:

- libc6 ([https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libc6_2.27-3ubuntu1_i386.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libc6_2.27-3ubuntu1_i386.deb.html)) :apt-get install libc6:

- libdv4 ([https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libdv4_1.0.0-11_i386.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libdv4_1.0.0-11_i386.deb.html)) : apt-get install libdv4:

- libgcc1 ([https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libgcc1_8-20180414-1ubuntu2_i386.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libgcc1_8-20180414-1ubuntu2_i386.deb.html)) : apt-get install libgcc1:

- libiec61883 ([https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libiec61883-0_1.2.0-2_i386.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libiec61883-0_1.2.0-2_i386.deb.html)) :apt-get install libiec61883-0

- libjpeg8 ([https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libjpeg8_8c-2ubuntu8_i386.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libjpeg8_8c-2ubuntu8_i386.deb.html)) : apt-get install libjpeg8:

- libquicktime2 ([https://ubuntu.pkgs.org/18.04/ubuntu-universe-i386/libquicktime2_1.2.4-11build1_i386.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-universe-i386/libquicktime2_1.2.4-11build1_i386.deb.html)) : apt-get install libquicktime2:

- libraw1394-11 ([https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libraw1394-11_2.1.2-1_i386.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libraw1394-11_2.1.2-1_i386.deb.html)) : apt-get install libraw1394-11:

- libstdc++6 ([https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libstdc++6_8-20180414-1ubuntu2_i386.deb.html](https://ubuntu.pkgs.org/18.04/ubuntu-main-i386/libstdc++6_8-20180414-1ubuntu2_i386.deb.html)) : apt-get install libstdc++6:


Those libraries are successfully installed, then I load OHCI1394 driver as follows:
# /sbin/modprobe ohci1394
(nothing was displayed)


Finally I tried to install dvgrab as follows:
# apt-get install dvgrab:

I launched dvgrab from console as root, but the system says as follows, off course DV camcorder is playing:
# Error : no camera exists.


Also I tried to install kino as follows:
# apt-get install kino

I launched kino from console as root as follows: 
# kino
UI of kino is shown on the screen, off course DV camcorder is also playing, but kino says, "No AV/C compliant cam connected or not switched on ?" I also checked kino's preference, nothing is listed in AV/C device pull-down menu at "IEEE1394".


The issue seems to be in the software configuration or settings because hardware itself is properly installed and recognized by the Ubuntu system.

What should I do to capture video through Firewire interface ?

Thank you for reading my article.

---

### Post by akg-bruggeman on 2020-03-11
been a while...
any progress ?

---

### Post by brianthefolksinger on 2020-04-02
I don;t know if I can help as I don;t know much about this all, at least any more, did 20 years ago, knew it well, but haven't kept up, just use it and make it work, get under the hood if I have to.
I have the original SOny PD-150 dvcam, and have used it with various firewire interfaces. At this point, I can still make it work, but only with Kino and dvgrab, no um real problem, though Kino doesn't ID my actual model, it shows a camera, and then it works.
But did copy the manual from the Kino site years ago, , that doesn't seem to be there any more, but here is a paste of the capture page, which has critical distinction between how to manage which module you have. btw I am running U-18-LTS, and the raw1394 module.
Though I can't seem to get anything else to recognize and capture except Kino and dvgrab, though found some utilities for patching into V4Li they seem to depend on using the old dv1394 module., and beyond that, though it works, the device files aren't in any of the old places, a quick look seems they might be dev/fw1  no trace of 1394.. anyway, haven't done any of simplest terminal device discovery commands, umm, it has been working, has for years, kept working as I switched machines, upgraded, etc, never bothered to find the files.
And, I am here looking for help on something else.. want to use my camera as a live streaming feed, but can't find an app that will recognize it, though made an ugly workaround with Kino in capture mode and OBS source as screen, both on my other monitor, line it up right and well, have a feed. But ugly way, and seems there should be a right way.

but here is the page from the manual, in case it helps, a little ugly as it is just the text copied and pasted off the save webpage. Theres an intro at top and the pertinent info at the middle and end. Since you don't see an AV/C device, then the module might be the problem
peace, keep searching for an answer to my problem

Kino can capture from a DV device over IEEE 1394, also known as FireWire or iLink. The most popular form of DV device is a MiniDV camcorder. but it could be a VTR, analog converter, or other. Kino does not support capturing of DVCPRO50, DVCPROHD, or HDV. Neither does it support Video4Linux or USB for a capture interface. If you can only use Video4Linux on your system, we recommend using another program to capture from V4L, and then let Kino import the file.

Before attempting to capture video, it is good to understand the Linux IEEE 1394 and Kino configuration. Linux IEEE 1394 configuration can be tricky due to changes in the kernel interfaces and various distributions' default support for setup of the device files. Next, it is good to understand that there are three concepts to understand: device discovery, device control, and DV capture.
[Caution] 	Caution

The dv1394 kernel interface is deprecated in Kino, but it is still offered as a build-time configure option for legacy transition.

Kino prefers the raw1394 kernel module interface. Nearly all kernel versions load the raw1394 module when you plug in and DV device and turn it on. With raw1394, device discovery, device control, and DV capture are seamless! Since the raw1394 device file is a well established standard at /dev/raw1394, there is no need to configure it. You just need to make sure your user account has read and write access to /dev/raw1394. With raw1394, if your system has more than one IEEE 1394 interface, Kino discovers your DV device regardless of which interface your device is plugged into. If you have more than one DV device, then choose Edit->Preferences->IEEE 1394 and use the AV/C Device option menu to choose the device. Kino attempts to read the name of the device, but displays the devices universally unique identifier in Base64 when a name is not available.

To determine which kernel module your version of Kino is using for DV Capture choose Edit->Preferences->IEEE 1394 . If there is a dv1394 device field, then it is using dv1394 and not raw1394 for DV capture.
[Note] 	About dv1394 (skip if not relevant)

dv1394 does not offer any device control , and Kino does not fully support device discovery when using dv1394. However, when configured to use dv1394 for DV capture , Kino still tries to use raw1394 for device control. In other words, Kino can still use raw1394 for device control to supplement dv1394. However, without raw1394 and lacking device control, one can still manually control the device using its physical buttons. With dv1394, it is important to ensure the kernel module is loaded (using lsmod and modprobe, if not loaded). Some kernel versions automatically load dv1394 when a DV device is plugged in and turned on. Next, you need to locate the device file under /dev. It might be /dev/dv1394-N, /dev/dv1394/N, or under /dev/ieee1394/dv/hostN/.... If you have only one IEEE 1394 interface, then N = 0; otherwise, there are multiple-numbered files--one for each interface (host). If you have more than one interface, it can be tricky to determine into which one your DV device is plugged. This is how dv1394 makes full support for device discovery difficult. If you can not find a file under /dev corresponding to dv1394, then you must create it manually . Next, you must make sure that your user account has read and write access to the dv1394 device files. Finally, you must enter the correct device file name in Kino by choosing Edit->Preferences->IEEE 1394->dv1394 device

---

### Post by coffeecat on 2020-04-03
Back to sleep, old thread.

The OP has not logged in for nearly a year!

---

