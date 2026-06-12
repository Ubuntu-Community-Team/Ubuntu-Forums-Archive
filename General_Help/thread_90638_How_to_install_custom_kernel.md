---
title: "How to install custom kernel"
date: 2005-11-15
forum: General Help
---

### Post by beijingjj on 2005-11-15
I downloaded the 2.6.14 kernel from kernel.org, untarred it into /usr/src and configured it with make xconfig as I have done many times before with other distros.  This seems to have mostly worked but it seems that some of my hardware is broken now.  For example, I have compiled the module for my wireless card, and it is even loaded automatically, but the device is not created in the operating system.  I believe the same thing is happening for my sound card.  When I login I get a HAL error message.  Is HAL somehow responsible for loading the hardware?  Did I screw something up in the kernel to cause this HAL to fail (or whatever it is)?  How can I troubleshoot this further?

FYI after running make xconfig I used the command 
make-kpkg buildpackage -rev Custom.1 kernel_image
and then
dpkg -i /usr/src/*.deb
to install the kernel, which successfully installed it.

Thanks in advance for any help

---

### Post by hw-tph on 2005-11-15
If you *must* build a custom kernel image, you are probably better off starting with the Ubuntu configuration so you have a good working config to start with. Copy the config you want to use from /boot/config-${VERSION} to /usr/src/linux/.config and then run menuconfig or however you want to configure the kernel. Chances are you're missing essential things like event interface and other things that Debian/Ubuntu rely on but other distros can do without.


Håkan

---

### Post by antidrugue on 2005-11-15
1) You will need certain packages, so

```

$ sudo apt-get install build-essential debhelper devscripts dh-make module-assistant xserver-xorg kernel-package libncurses5-dev libqt3-mt-dev libxtst-dev xlibs-dev rpm bzip2 fakeroot 
``` 
2) Then download a kernel (as of 15/11/05 the latest is 2.6.14.2) from:
[ftp://ftp.kernel.org/pub/linux/kernel/v2.6/]("ftp://ftp.kernel.org/pub/linux/kernel/v2.6/")

3) Then...

```

$ cd /usr/src
$ sudo tar jxf /path/to/linux-image-2.6.14.2.tar.bz2
$ cd linux-2.6.14.2
$ sudo cp /boot/config-2.6.x-y-686 .config
$ sudo make menuconfig
  - enable Code maturity level options -> Select only drivers expected to compile cleanly
  - set Processor type and features -> Processor family (Pentium 4, or your CPU)

$ sudo make-kpkg clean
$ sudo make-kpkg --append-to-version "-<suffix>" --revision "<revision>" --initrd kernel_image
$ sudo make-kpkg --append-to-version "-<suffix>" --revision "<revision>" modules_image
$ cd ..
# sudo dpkg -i kernel-image-2.6.14.2-<suffix>_<revision>_i386.deb

``` 
Of course, you don't type the "$" sign !

Remember, if you want to install NVIDIA or ATI drivers, you will have to compile the kernel modules for it too.

This come from [http://www.atworkonline.it/~bibe/sarge/]("http://www.atworkonline.it/%7Ebibe/sarge/")

But take a look at [http://www.atworkonline.it/~bibe/breezy]("http://www.atworkonline.it/%7Ebibe/breezy")

If you have any doubts, maybe you are better off, just doing this (instead of custom kernel):

```

$ sudo apt-get install linux-686

``` 
Just reboot, and then remove the old kernel:

```

$ sudo apt-get remove --purge linux-image-2.6.12-9-386

```

---

### Post by tseliot on 2005-11-16
[QUOTE=beijingjj]I downloaded the 2.6.14 kernel from kernel.org, untarred it into /usr/src and configured it with make xconfig as I have done many times before with other distros.  This seems to have mostly worked but it seems that some of my hardware is broken now.  For example, I have compiled the module for my wireless card, and it is even loaded automatically, but the device is not created in the operating system.  I believe the same thing is happening for my sound card.  When I login I get a HAL error message.  Is HAL somehow responsible for loading the hardware?  Did I screw something up in the kernel to cause this HAL to fail (or whatever it is)?  How can I troubleshoot this further?

FYI after running make xconfig I used the command 
make-kpkg buildpackage -rev Custom.1 kernel_image
and then
dpkg -i /usr/src/*.deb
to install the kernel, which successfully installed it.

Thanks in advance for any help[/QUOTE]
Try my guide please: [http://www.ubuntuforums.org/showthread.php?t=85064]("http://www.ubuntuforums.org/showthread.php?t=85064")

---

### Post by beijingjj on 2005-11-17
I tried these suggestions, the main difference being that this time I started with the original ubuntu .config file (from /boot).  I have the same results though.  I think there is something special about the way the original config loads modules.  Take this example:

I believe the ipw2200 driver was not included in the kernel until 2.6.14, however the module is part of my 2.6.12-9-386 kernel modules:

**/lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/ipw2200/ipw2200.ko**

Not also that for the new kernel the driver is located in a different directory:

**/lib/modules/2.6.14.2/kernel/drivers/net/wireless/ipw2200.ko**

Furthermore, when the system tries to insmod this 2.6.14.2 module it is looking for the ipw2200 firmware files on the system, which don't exist until I download and install them.  But if there are no ipw2200 firmware files here then how did the original kernel load them?  It would seem that it is not using the driver from sourceforge or the one built into the kernel.  I believe something similar is going on for the synaptics touchpad driver.

What gives here??

---

### Post by leechin on 2005-12-02
I have just install ubuntu 5.10 and am trying to update my kernel to linux-686.
I can't seem to be able to do it either through the console or synaptic manager.
The option does not even show up in the synaptic manager.(i.e. linux-686)

My system has a P4 processor. 

Some data that might help analyse the problem.(thanx to google)

sidhanti@localhost:~$ sudo uname -a
Linux localhost 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux

sidhanti@localhost:~$ apt-cache show linux-686
W: Unable to locate package linux-686
E: No packages found
sidhanti@localhost:~$ apt-cache show linux-386
Package: linux-386
Priority: optional
Section: restricted/base
Installed-Size: 48
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.12.16
Depends: linux-image-386, linux-restricted-modules-386
Filename: pool/restricted/l/linux-meta/linux-386_2.6.12.16_i386.deb
Size: 22434
MD5Sum: 870fea541ab79d30161bf53826be71fb
Description: Complete Linux kernel on 386.
 This package will always depend on the latest complete Linux kernel available
 for 386.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-minimal

sidhanti@localhost:~$ apt-cache show linux-686
W: Unable to locate package linux-686
E: No packages found

sidhanti@localhost:~$ sudo apt-get install linux-686
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-686

---

### Post by Drifter on 2005-12-02
Snaptic had the 686 kernel in it, just go search and then install it.

---

### Post by RAOF on 2005-12-02
If I remember correctly, the kernels later than 2.6.13 have removed support for something, devfs maybe?, and replaced it with only udev.  Maybe these newer kernels just won't work totally correctly with Breezy, at least not without a bit of work.

---

### Post by goombah88 on 2006-01-04
[QUOTE=leechin]I have just install ubuntu 5.10 and am trying to update my kernel to linux-686.
I can't seem to be able to do it either through the console or synaptic manager.
The option does not even show up in the synaptic manager.(i.e. linux-686)

My system has a P4 processor. 

Some data that might help analyse the problem.(thanx to google)

sidhanti@localhost:~$ sudo uname -a
Linux localhost 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux

sidhanti@localhost:~$ apt-cache show linux-686
W: Unable to locate package linux-686
E: No packages found
sidhanti@localhost:~$ apt-cache show linux-386
Package: linux-386
Priority: optional
Section: restricted/base
Installed-Size: 48
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-meta
Version: 2.6.12.16
Depends: linux-image-386, linux-restricted-modules-386
Filename: pool/restricted/l/linux-meta/linux-386_2.6.12.16_i386.deb
Size: 22434
MD5Sum: 870fea541ab79d30161bf53826be71fb
Description: Complete Linux kernel on 386.
 This package will always depend on the latest complete Linux kernel available
 for 386.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-minimal

sidhanti@localhost:~$ apt-cache show linux-686
W: Unable to locate package linux-686
E: No packages found

sidhanti@localhost:~$ sudo apt-get install linux-686
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-686[/QUOTE]
leechin,

if you're using the command line use 'sudo apt-cache search linux-image'

if you're using synaptic just click search and search for 'linux-image'.  scroll down through the results and you'll see the kernel you're looking for.  you'll most likely want the 686-smp kernel.  the -smp is for P4 processors which have hyperthreading.

---

### Post by zasf on 2006-01-07
[QUOTE=antidrugue]3) Then...

```

$ cd /usr/src
$ sudo tar jxf /path/to/linux-image-2.6.14.2.tar.bz2
$ cd linux-2.6.14.2
$ sudo cp /boot/config-2.6.x-y-686 .config
$ sudo make menuconfig
  - enable Code maturity level options -> Select only drivers expected to compile cleanly
  - set Processor type and features -> Processor family (Pentium 4, or your CPU)

```[/QUOTE]

hum.. I experience the same as beijingjj talking about ipw2200 dir

moreover when i do ```
matteo@ubuntu:/usr/src/linux$ sudo cp /boot/config-2.6.12-10-386 .config
Password:
matteo@ubuntu:/usr/src/linux$ sudo make menuconfig
scripts/kconfig/mconf arch/i386/Kconfig
#
# using defaults found in .config
#
.config:147: trying to assign nonexistent symbol ACPI_BOOT
.config:148: trying to assign nonexistent symbol ACPI_INTERPRETER
.config:163: trying to assign nonexistent symbol ACPI_SONY
.config:164: trying to assign nonexistent symbol ACPI_DEV
.config:165: trying to assign nonexistent symbol ACPI_I2C
.config:167: trying to assign nonexistent symbol ACPI_PCC
.config:169: trying to assign nonexistent symbol ACPI_BUS
.config:172: trying to assign nonexistent symbol ACPI_PCI
.config:176: trying to assign nonexistent symbol ACPI_INITRD
.config:177: trying to assign nonexistent symbol ACPI_TC1100
.config:250: trying to assign nonexistent symbol PCI_NAMES
.config:383: trying to assign nonexistent symbol MTD_ELAN_104NC
.config:504: trying to assign nonexistent symbol BLK_DEV_CLOOP
.config:517: trying to assign nonexistent symbol BLK_DEV_GNBD
.config:718: trying to assign nonexistent symbol SCSI_PCI2000
.config:719: trying to assign nonexistent symbol SCSI_PCI2220I
.config:879: trying to assign nonexistent symbol IP_TCPDIAG
.config:880: trying to assign nonexistent symbol IP_TCPDIAG_IPV6
.config:1392: trying to assign nonexistent symbol SK98LIN_NAPI
.config:1445: trying to assign nonexistent symbol IEEE80211_CRYPT
.config:1446: trying to assign nonexistent symbol IEEE80211_WPA
.config:1450: trying to assign nonexistent symbol IPW2100_DEBUG
.config:1452: trying to assign nonexistent symbol IPW2100_FS_AMILO_M7400
[B].config:1454: trying to assign nonexistent symbol IPW2200_MONITOR
.config:1455: trying to assign nonexistent symbol IPW2200_QOS
.config:1456: trying to assign nonexistent symbol IPW2200_DEBUG[/B]
.config:1457: trying to assign nonexistent symbol WLAN_NG
.config:1458: trying to assign nonexistent symbol PRISM2
.config:1459: trying to assign nonexistent symbol PRISM2_USB
.config:1460: trying to assign nonexistent symbol ADM8211
.config:1462: trying to assign nonexistent symbol ACX100
.config:1463: trying to assign nonexistent symbol RT2500
.config:1464: trying to assign nonexistent symbol RT2400
.config:1592: trying to assign nonexistent symbol PPP_MPPE_MPPC
.config:1602: trying to assign nonexistent symbol NDISWRAPPER
.config:1824: trying to assign nonexistent symbol INPUT_ACERHK
.config:1825: trying to assign nonexistent symbol INPUT_CPAD
.config:1842: trying to assign nonexistent symbol GAMEPORT_VORTEX
.config:1844: trying to assign nonexistent symbol GAMEPORT_CS461X
.config:1881: trying to assign nonexistent symbol SERIAL_WACOM_ACPI
.config:1887: trying to assign nonexistent symbol SERIAL_8250_MULTIPORT
.config:2011: trying to assign nonexistent symbol DRM_GAMMA
.config:2088: trying to assign nonexistent symbol I2C_SENSOR
.config:2147: trying to assign nonexistent symbol AVERATEC_5100P
.config:2148: trying to assign nonexistent symbol PACKARDBELL_E5
.config:2234: trying to assign nonexistent symbol DVB_DIBUSB
.config:2235: trying to assign nonexistent symbol DVB_DIBUSB_MISDESIGNED_DEVICES.config:2236: trying to assign nonexistent symbol DVB_DIBCOM_DEBUG
.config:2252: trying to assign nonexistent symbol DVB_B2C2_SKYSTAR
.config:2312: trying to assign nonexistent symbol DXR3
.config:2313: trying to assign nonexistent symbol EM8300
.config:2314: trying to assign nonexistent symbol EM8300_LOOPBACK
.config:2315: trying to assign nonexistent symbol EM8300_UCODETIMEOUT
.config:2316: trying to assign nonexistent symbol EM8300_DICOMFIX
.config:2317: trying to assign nonexistent symbol EM8300_DICOMCTRL
.config:2318: trying to assign nonexistent symbol EM8300_DICOMPAL
.config:2319: trying to assign nonexistent symbol ADV717X
.config:2320: trying to assign nonexistent symbol ADV717X_SWAP
.config:2321: trying to assign nonexistent symbol ADV717X_PIXELPORT16BIT
.config:2322: trying to assign nonexistent symbol ADV717X_PIXELPORTPAL
.config:2323: trying to assign nonexistent symbol BT865
.config:2441: trying to assign nonexistent symbol SND_GENERIC_PM
.config:2549: trying to assign nonexistent symbol SND_VXP440
.config:2555: trying to assign nonexistent symbol BT_ALSA
.config:2728: trying to assign nonexistent symbol USB_SPCA5XX
.config:2729: trying to assign nonexistent symbol USB_QC
.config:2746: trying to assign nonexistent symbol USB_GENESYS
.config:2747: trying to assign nonexistent symbol USB_NET1080
.config:2748: trying to assign nonexistent symbol USB_PL2301
.config:2749: trying to assign nonexistent symbol USB_KC2190
.config:2756: trying to assign nonexistent symbol USB_ZAURUS
.config:2757: trying to assign nonexistent symbol USB_CDCETHER
.config:2762: trying to assign nonexistent symbol USB_AX8817X
.config:2764: trying to assign nonexistent symbol USB_ZD1211
.config:2765: trying to assign nonexistent symbol USB_ATMEL
.config:2823: trying to assign nonexistent symbol USB_EAGLE
.config:2905: trying to assign nonexistent symbol OCFS2_FS
.config:2945: trying to assign nonexistent symbol DEVFS_FS
.config:2946: trying to assign nonexistent symbol DEVFS_MOUNT
.config:2947: trying to assign nonexistent symbol DEVFS_DEBUG
.config:2948: trying to assign nonexistent symbol DEVPTS_FS_XATTR
.config:2949: trying to assign nonexistent symbol DEVPTS_FS_SECURITY
.config:2951: trying to assign nonexistent symbol TMPFS_XATTR
.config:2952: trying to assign nonexistent symbol TMPFS_SECURITY
.config:2956: trying to assign nonexistent symbol CONFIGFS_FS
.config:2957: trying to assign nonexistent symbol FUSE
.config:2965: trying to assign nonexistent symbol ASFS_FS
.config:2966: trying to assign nonexistent symbol ASFS_DEFAULT_CODEPAGE
.config:2967: trying to assign nonexistent symbol ASFS_RW
.config:2979: trying to assign nonexistent symbol JFFS2_FS_NAND
.config:2980: trying to assign nonexistent symbol JFFS2_FS_NOR_ECC
.config:2986: trying to assign nonexistent symbol SQUASHFS
.config:2987: trying to assign nonexistent symbol SQUASHFS_EMBEDDED
.config:2988: trying to assign nonexistent symbol SQUASHFS_FRAGMENT_CACHE_SIZE
.config:2989: trying to assign nonexistent symbol SQUASHFS_VMALLOC
.config:3035: trying to assign nonexistent symbol LOCK_HARNESS
.config:3036: trying to assign nonexistent symbol GFS_FS
.config:3037: trying to assign nonexistent symbol LOCK_NOLOCK
.config:3038: trying to assign nonexistent symbol LOCK_DLM
.config:3039: trying to assign nonexistent symbol LOCK_GULM
.config:3215: trying to assign nonexistent symbol CLUSTER
.config:3216: trying to assign nonexistent symbol CLUSTER_DLM
.config:3217: trying to assign nonexistent symbol CLUSTER_DLM_PROCLOCKS
.config:3218: trying to assign nonexistent symbol CLUSTER_CMIRROR

```

it seems like the copy procedure doesn't work..

---

