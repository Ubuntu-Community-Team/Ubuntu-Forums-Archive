---
title: "Sony Vaio VGN-FE41Z &amp; Feisty (7.04)"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by IntuitiveNipple on 2007-05-18
This Widescreen, Intel Core 2 Duo laptop is almost completely supported by Feisty at first install. I thought I'd record here what I've found as I deal with the last few issues.

**Features**
Intel Core 2 Duo 2GHz Processor T7200, Supports Enhanced SpeedStep Technology, L2 Cache 4096KB, Frontside Bus 667MHz, 2GB DDR2 SDRAM, GEForce Go 7600, 200GB SATA disk, DVD-RAM, 1280x800 DFP 385mm display, built-in Motion-Eye video camera and microphone.

**Ubuntu 7.04 Feisty 64-bit Desktop** Live CD installation.


**Intel Core 2 Duo T7200 VMX (has Virtualisation support)**

Allows full hardware virtualisation support for Kernel KVM, Xen, VMWare and other hypervisors.

This is the only model in the FE range that uses a VMX capable CPU. Vaio BIOS versions R0190J3 and R0200J3 (21 Feb 2007) do not enable the VMX function, and they lock the CPU MSR 0x3A Feature Control register (bit-0 is set). Once 0x3A is locked the CPU(s) require a power-cycle to reset.

Therefore the BIOS needs to be modified. Until Sony release a VMX-enabled BIOS, I shall be looking to hack the existing BIOS and Flash my own version that enables VMX. Currently 0x01 is written to MSR 0x3A; the hack will write 0x03. Please contact Sony Support and request a VMX-enabled BIOS.

**Motion Eye built-in Webcam**

Supported by V4L2 as a UVC camera, using the Ricoh R5U870 drivers and Linux UVC. There is an excellent article [Ricoh R5U870 Webcam Driver for Linux](http://lsb.blogdns.net/ry5u870/) that describes how to download and install the driver, either from source or as Debian/Ubuntu packages.

I use **luvcview** to test it. The quality is good. Download the source package from [Michel Xhaard's excellent Linux webcam driver](http://mxhaard.free.fr/download.html) site. You'll find the luvcview link almost at the end of the page.

```
$ mkdir ~/build
$ cd build
$ tar xzvf ../luvcview-20070512.tar.gz
$ cd luvcview-20070512
$ make
$ ./luvcview -d /dev/video0 -f yuv
```
**Nvidia GEForce Go 7600**

I Installed the [NVidia 100.14.03 64-bit accelerated drivers](http://www.nvidia.com/object/linux_display_amd64_100.14.03.html").

A test with glxgears -info reports rates of over 5,000 fps.

**Suspend/Resume & Hibernate**

Currently these don't work at all. Suspend to RAM has more problems than hibernate. When resuming the video doesn't work, and/or the WiFi network requires a shutdown-restart to get it going again.

**Fn+Function keys**

Hot-keys using the blue **Fn** key don't currently work. This is due to a problem with the sony_acpi module not yet handling the hardware, although there are good signs that support is due soon in newer kernel version.

The non-working keys are: Fn+F5 and Fn+F6 (brightness up/down), Fn+F7 (LCD/external switch), Fn+F12 (Hibernate), Fn+NumLk (Scroll Lock), Fn+Insert (Pause), Fn+Delete (Break).

The dedicated Mute, Volume +/- buttons do work, including On-Screen-Display.

**Multimedia Card Slots**

Both the built-in MemoryStick Duo/Pro slot, and the ExpressCard/34 5-in-1 adapter (MemoryStick Pro & Duo, SD, MC, xD) are detected.

**Wireless**

Both the 802.11a/b/g and Bluetooth radios are detected and drivers installed. 802.11a/b/g supports open, WEP, WPA and WPA2.

**Connectors**

There are 3 USB 2.0 sockets, a 4-pin IEEE1394 (iLink/Firewire) socket, PC-Card CardBus. All are supported.

**External Video**

There are external VGA and S-Video sockets. I haven't had the opportunity to test them yet.

**Modem**

There is an RJ11 connector for a V92 modem but I believe it requires a software (aka WinModem) modem. So far I've not been able to identify the modem in the hardware information.

I'll add updates as things progress. If you have news or tips, especially for getting Suspend/Resume and hotkey working, please post details here.

---

### Post by AndrewGene on 2007-08-16
I have my webcam working but what about the microphone?? Do you have that working also?

---

### Post by willfleury on 2008-04-18
this link worked for me in fixing hibernate and suspend on my FE41Z. Only thing i dont have 
working are the function keys still..

[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

### Post by IntuitiveNipple on 2008-04-18
On Gutsy and Hardy I discovered the solution is to unload the MotionEye driver. It is a known issue that uvcvideo and/or r5u870 will causes issues:

Edit **/etc/default/acpi-support** so it has at least these:
```

MODULES="uvcvideo r5u870"

```

---

### Post by Weisswurst on 2008-04-19
AAAH YES!!!
Adding uvc and r5 to the acpi-support didn't helped at all.
But blacklisting them in etc/modprobe.d/blacklist did it!

Now my Vaio is hibernating just fine.

---

