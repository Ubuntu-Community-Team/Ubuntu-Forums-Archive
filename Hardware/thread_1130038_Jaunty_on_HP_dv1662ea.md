---
title: "Jaunty on HP dv1662ea"
date: 2009-04-19
forum: Hardware
---

### Post by bulusglo on 2009-04-19
Jaunty on HP dv1662ea

Works fine, here is a summary & a few settings I did 

**> uname -a**
Linux 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

**> lspci**
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

**> lsusb**
Bus 001 Device 003: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05fe:0007 Chic Technology Corp. Twinhead Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


**Function keys** (hp quick play, volume control, play/next/previous, suspend, hybernate)  : OK


**On jaunty, poor video 3D performance with INTEL 945GM** , glxgears (is not a benchmark) at about 200, compiz cube slow when transparency activated. Use to work better on previous versions or ubuntu / xorg desktop, for INTEL 945GM/GMS VGA Card, I did : 
create a file "/etc/X11/xorg.conf" to put : 

```

Section "Device"
    Identifier "Configured Video Device"
        # ...
        # Option to restore compiz performance on INTEL 945GM/GMS VGA Card
    Option "AccelMethod" "uxa"
    Option "FramebufferCompression" "true"
    Option "Legacy3D" "true"
EndSection

```

> glxinfo
```
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.4
```

**HP dv1000 webcam Ricoh R5C832, device id is 05ca:1870**
get [http://avilella.googlepages.com/r5u870_patched.tar.bz2](http://avilella.googlepages.com/r5u870_patched.tar.bz2)
> sudo make
> sudo make install
> sudo chmod a+rw /dev/video0
=> OK with v4l and skype 

**Eliminate CPU noise (high frequency irritating noise that occurs when CPU is idle) : I added the option "idle=halt", in my /etc/boot/grub/menu.lst : **
```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        3db4b594-ef37-44d2-8bd0-5e36ad514c0d
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3db4b594-ef37-44d2-8bd0-5e36ad514c0d ro **idle=halt** quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

```

**For IBM lotus notes on Jaunty, problem with small fonts, in addition to IBM's package :**
sudo apt-get install xfonts-scalable ttf-xfree86-nonfree

**Firefox : set the backspace key to act as "previous page" button**
Type &#8220;about:config&#8221; in the address bar of Firefox and press Enter.
`Filter` for &#8216;browser.backspace_action&#8217; and change its value to 0 (zero).

**Setting terminal character encoding permanently**
To avoid setting character encoding in gnome terminal (I am launching "tn5250" to work on as400 iSeries i5 , using the run command in the profile settings of gnome-terminal)
> env LANG=fr_FR.ISO-8859-1 gnome-terminal --profile=myProfile

**I hope that can help :**
- other people solve similar problems, 
- some solutions being taken into acount for next releases,
...

GNU/Linux Ubuntu is really a nice system.

---

### Post by novatillasku on 2009-05-27
Muchas gracias por toda la información,conseguí configurar mi Webcam de mi Hp Pavilion Dv 1000.Lo pongo aqui por si alguien con ese modelo necesita configurarla que sepa que sirve exactamente igual.Gracias!

---

### Post by pallabbasu1234 on 2009-09-03
Many thanks especially for the webcam.

---

### Post by sergiom99 on 2009-09-03
> **bulusglo said:**
> Jaunty on HP dv1662ea
(...)
**Firefox : set the backspace key to act as "previous page" button**
Type “about:config” in the address bar of Firefox and press Enter.
`Filter` for ‘browser.backspace_action’ and change its value to 0 (zero).
(...)
GNU/Linux Ubuntu is really a nice system.

Nice Tip!!

---

