---
title: "How to restore amdgpu drivers to working order on 20.04(.2)?"
date: 2021-02-25
forum: Hardware
---

### Post by sjpt2 on 2021-02-25
20.04.1 was working swimmingly with my Ryzen 4700u / RX Vega 8. Then along came 20.04.2 with a kernel upgrade to 5.8 and my system started booting to the black screen of graphic driver problems.

Booting in recovery mode, it was at least working much like with nomodeset, i.e. limited to a resolution of 1024x768. Somewhat foolishly, perhaps, I figured I'd try to install the latest drivers (20.45) directly from AMD, but there was an error compiling dkms, so I removed the faulty installation with `amdgpu-uninstall`. Now the default boot works with the limited resolution, and `inxi -F` says

```

Graphics:
  Device-1: AMD Renoir driver: N/A 
  Display: x11 server: X.Org 1.20.9 
  driver: ati,fbdev 
  unloaded: modesetting,radeon,vesa 
  resolution: 1024x768~76Hz 
  OpenGL: renderer: llvmpipe (LLVM 
  11.0.0 256 bits) 
  v: 4.5 Mesa 20.2.6

```

While limited resolution is a step forward from a blank screen I suppose, I would of course like to get the drivers working again, but where do I go from here? That the radeon module is unloaded is obviously a problem, but fixing only that would only get me back to the blank screen, I image. Can I somehow roll back to the previous kernel (5.4, I seem to remember)? If so, how can I tell when it is safe to upgrade again?

---

### Post by Yellow Pasque on 2021-02-25
You can stay on the 5.4.x kernel series if you'd like:
```
sudo apt-get install linux-generic     #this may already be installed
```
Reboot into the 5.4.x kernel from the GRUB menu: [https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time](https://askubuntu.com/questions/16042/how-to-get-to-the-grub-menu-at-boot-time)

If you are happy with 5.4 kernel and want to remove 5.8.x kernels:
```
sudo apt-get purge linux-generic-hwe-20.04 linux-headers-generic-hwe-20.04 linux-image-generic-hwe-20.04 linux-headers-5.8* linux-image-5.8*
```

---

### Post by Yellow Pasque on 2021-02-25
Also, you may want to try booting a LiveUSB of Ubuntu 20.04.2 to see if it has the same black screen issue: [https://releases.ubuntu.com/20.04/ubuntu-20.04.2.0-desktop-amd64.iso.torrent](https://releases.ubuntu.com/20.04/ubuntu-20.04.2.0-desktop-amd64.iso.torrent)

---

### Post by sjpt2 on 2021-02-26
Well, now it gets rather confusing. Looks like it was in fact 20.04.2 that was running OK, with the 5.8.0-43-generic kernel. As far as I can tell, this was the apt update that caused the problems:

```

Log started: 2021-02-22  08:11:16
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 181082 files and directories currently installed.)
Preparing to unpack .../00-whoopsie_0.2.69ubuntu0.3_amd64.deb ...
Unpacking whoopsie (0.2.69ubuntu0.3) over (0.2.69ubuntu0.2) ...
Preparing to unpack .../01-libwhoopsie0_0.2.69ubuntu0.3_amd64.deb ...
Unpacking libwhoopsie0:amd64 (0.2.69ubuntu0.3) over (0.2.69ubuntu0.2) ...
Preparing to unpack .../02-gpg-wks-client_2.2.19-3ubuntu2.1_amd64.deb ...
Unpacking gpg-wks-client (2.2.19-3ubuntu2.1) over (2.2.19-3ubuntu2) ...
Preparing to unpack .../03-dirmngr_2.2.19-3ubuntu2.1_amd64.deb ...
Unpacking dirmngr (2.2.19-3ubuntu2.1) over (2.2.19-3ubuntu2) ...
Preparing to unpack .../04-gnupg-utils_2.2.19-3ubuntu2.1_amd64.deb ...
Unpacking gnupg-utils (2.2.19-3ubuntu2.1) over (2.2.19-3ubuntu2) ...
Preparing to unpack .../05-gpg-wks-server_2.2.19-3ubuntu2.1_amd64.deb ...
Unpacking gpg-wks-server (2.2.19-3ubuntu2.1) over (2.2.19-3ubuntu2) ...
Preparing to unpack .../06-gpg-agent_2.2.19-3ubuntu2.1_amd64.deb ...
Unpacking gpg-agent (2.2.19-3ubuntu2.1) over (2.2.19-3ubuntu2) ...
Preparing to unpack .../07-gpg_2.2.19-3ubuntu2.1_amd64.deb ...
Unpacking gpg (2.2.19-3ubuntu2.1) over (2.2.19-3ubuntu2) ...
Preparing to unpack .../08-gpgconf_2.2.19-3ubuntu2.1_amd64.deb ...
Unpacking gpgconf (2.2.19-3ubuntu2.1) over (2.2.19-3ubuntu2) ...
Preparing to unpack .../09-gnupg-l10n_2.2.19-3ubuntu2.1_all.deb ...
Unpacking gnupg-l10n (2.2.19-3ubuntu2.1) over (2.2.19-3ubuntu2) ...
Preparing to unpack .../10-gnupg_2.2.19-3ubuntu2.1_all.deb ...
Unpacking gnupg (2.2.19-3ubuntu2.1) over (2.2.19-3ubuntu2) ...
Preparing to unpack .../11-gpgsm_2.2.19-3ubuntu2.1_amd64.deb ...
Unpacking gpgsm (2.2.19-3ubuntu2.1) over (2.2.19-3ubuntu2) ...
Preparing to unpack .../12-gpgv_2.2.19-3ubuntu2.1_amd64.deb ...
Unpacking gpgv (2.2.19-3ubuntu2.1) over (2.2.19-3ubuntu2) ...
Setting up gpgv (2.2.19-3ubuntu2.1) ...
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 181082 files and directories currently installed.)
Preparing to unpack .../00-libssl1.1_1.1.1f-1ubuntu2.2_amd64.deb ...
Unpacking libssl1.1:amd64 (1.1.1f-1ubuntu2.2) over (1.1.1f-1ubuntu2.1) ...
Preparing to unpack .../01-openssl_1.1.1f-1ubuntu2.2_amd64.deb ...
Unpacking openssl (1.1.1f-1ubuntu2.2) over (1.1.1f-1ubuntu2.1) ...
Preparing to unpack .../02-bind9-dnsutils_1%3a9.16.1-0ubuntu2.6_amd64.deb ...
Unpacking bind9-dnsutils (1:9.16.1-0ubuntu2.6) over (1:9.16.1-0ubuntu2.4) ...
Preparing to unpack .../03-bind9-libs_1%3a9.16.1-0ubuntu2.6_amd64.deb ...
Unpacking bind9-libs:amd64 (1:9.16.1-0ubuntu2.6) over (1:9.16.1-0ubuntu2.4) ...
Preparing to unpack .../04-bind9-host_1%3a9.16.1-0ubuntu2.6_amd64.deb ...
Unpacking bind9-host (1:9.16.1-0ubuntu2.6) over (1:9.16.1-0ubuntu2.4) ...
Preparing to unpack .../05-friendly-recovery_0.2.41ubuntu0.20.04.1_all.deb ...
Unpacking friendly-recovery (0.2.41ubuntu0.20.04.1) over (0.2.41) ...
Preparing to unpack .../06-libctf0_2.34-6ubuntu1.1_amd64.deb ...
Unpacking libctf0:amd64 (2.34-6ubuntu1.1) over (2.34-6ubuntu1) ...
Preparing to unpack .../07-binutils-x86-64-linux-gnu_2.34-6ubuntu1.1_amd64.deb ...
Unpacking binutils-x86-64-linux-gnu (2.34-6ubuntu1.1) over (2.34-6ubuntu1) ...
Preparing to unpack .../08-libbinutils_2.34-6ubuntu1.1_amd64.deb ...
Unpacking libbinutils:amd64 (2.34-6ubuntu1.1) over (2.34-6ubuntu1) ...
Preparing to unpack .../09-binutils_2.34-6ubuntu1.1_amd64.deb ...
Unpacking binutils (2.34-6ubuntu1.1) over (2.34-6ubuntu1) ...
Preparing to unpack .../10-binutils-common_2.34-6ubuntu1.1_amd64.deb ...
Unpacking binutils-common:amd64 (2.34-6ubuntu1.1) over (2.34-6ubuntu1) ...
Preparing to unpack .../11-libctf-nobfd0_2.34-6ubuntu1.1_amd64.deb ...
Unpacking libctf-nobfd0:amd64 (2.34-6ubuntu1.1) over (2.34-6ubuntu1) ...
Preparing to unpack .../12-libwebkit2gtk-4.0-37_2.30.5-0ubuntu0.20.04.1_amd64.deb ...
Unpacking libwebkit2gtk-4.0-37:amd64 (2.30.5-0ubuntu0.20.04.1) over (2.30.3-0ubuntu0.20.04.1) ...
Preparing to unpack .../13-libjavascriptcoregtk-4.0-18_2.30.5-0ubuntu0.20.04.1_amd64.deb ...
Unpacking libjavascriptcoregtk-4.0-18:amd64 (2.30.5-0ubuntu0.20.04.1) over (2.30.3-0ubuntu0.20.04.1) ...
Preparing to unpack .../14-gir1.2-webkit2-4.0_2.30.5-0ubuntu0.20.04.1_amd64.deb ...
Unpacking gir1.2-webkit2-4.0:amd64 (2.30.5-0ubuntu0.20.04.1) over (2.30.3-0ubuntu0.20.04.1) ...
Preparing to unpack .../15-gir1.2-javascriptcoregtk-4.0_2.30.5-0ubuntu0.20.04.1_amd64.deb ...
Unpacking gir1.2-javascriptcoregtk-4.0:amd64 (2.30.5-0ubuntu0.20.04.1) over (2.30.3-0ubuntu0.20.04.1) ...
Preparing to unpack .../16-software-properties-common_0.98.9.4_all.deb ...
Unpacking software-properties-common (0.98.9.4) over (0.98.9.3) ...
Preparing to unpack .../17-software-properties-gtk_0.98.9.4_all.deb ...
Unpacking software-properties-gtk (0.98.9.4) over (0.98.9.3) ...
Preparing to unpack .../18-python3-software-properties_0.98.9.4_all.deb ...
Unpacking python3-software-properties (0.98.9.4) over (0.98.9.3) ...
Setting up libssl1.1:amd64 (1.1.1f-1ubuntu2.2) ...
Setting up binutils-common:amd64 (2.34-6ubuntu1.1) ...
Setting up libjavascriptcoregtk-4.0-18:amd64 (2.30.5-0ubuntu0.20.04.1) ...
Setting up libctf-nobfd0:amd64 (2.34-6ubuntu1.1) ...
Setting up libwhoopsie0:amd64 (0.2.69ubuntu0.3) ...
Setting up gir1.2-javascriptcoregtk-4.0:amd64 (2.30.5-0ubuntu0.20.04.1) ...
Setting up gnupg-l10n (2.2.19-3ubuntu2.1) ...
Setting up friendly-recovery (0.2.41ubuntu0.20.04.1) ...
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.8.0-43-generic
Found initrd image: /boot/initrd.img-5.8.0-43-generic
Adding boot menu entry for UEFI Firmware Settings
done
Setting up libwebkit2gtk-4.0-37:amd64 (2.30.5-0ubuntu0.20.04.1) ...
Setting up gpgconf (2.2.19-3ubuntu2.1) ...
Setting up libbinutils:amd64 (2.34-6ubuntu1.1) ...
Setting up openssl (1.1.1f-1ubuntu2.2) ...
Setting up gpg (2.2.19-3ubuntu2.1) ...
Setting up gnupg-utils (2.2.19-3ubuntu2.1) ...
Setting up libctf0:amd64 (2.34-6ubuntu1.1) ...
Setting up gir1.2-webkit2-4.0:amd64 (2.30.5-0ubuntu0.20.04.1) ...
Setting up gpg-agent (2.2.19-3ubuntu2.1) ...
Setting up bind9-libs:amd64 (1:9.16.1-0ubuntu2.6) ...
Setting up whoopsie (0.2.69ubuntu0.3) ...
Setting up gpgsm (2.2.19-3ubuntu2.1) ...
Setting up dirmngr (2.2.19-3ubuntu2.1) ...
Setting up python3-software-properties (0.98.9.4) ...
Setting up gpg-wks-server (2.2.19-3ubuntu2.1) ...
Setting up bind9-host (1:9.16.1-0ubuntu2.6) ...
Setting up binutils-x86-64-linux-gnu (2.34-6ubuntu1.1) ...
Setting up gpg-wks-client (2.2.19-3ubuntu2.1) ...
Setting up binutils (2.34-6ubuntu1.1) ...
Setting up software-properties-common (0.98.9.4) ...
Setting up gnupg (2.2.19-3ubuntu2.1) ...
Setting up bind9-dnsutils (1:9.16.1-0ubuntu2.6) ...
Setting up software-properties-gtk (0.98.9.4) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for dbus (1.12.16-2ubuntu2.1) ...
Processing triggers for shared-mime-info (1.15-1) ...
Processing triggers for install-info (6.7.0.dfsg.2-5) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu3) ...
Processing triggers for mime-support (3.64ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.64.6-1~ubuntu20.04.1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.2) ...
Processing triggers for systemd (245.4-4ubuntu3.4) ...
Log ended: 2021-02-22  08:11:36

```

And now, for the really confusing stuff. Booting a LiveUSB worked. Once. But when I decided that the most painless course of action would probably be to do a reinstall, it no longer works. The time it was working, `inxi -F` said the graphics driver was `amdgpu`, but on subsequent attempts it has been `radeon` I believe, and `amdgpu` not even listed as unloaded (and on the installed, not properly working system, it says `ati,fbdev` as previously mentioned).

---

### Post by Yellow Pasque on 2021-02-28
Have you tried installing and booting into the 5.4.x kernel?

> **sjpt2 said:**
> As far as I can tell, this was the apt update that caused the problems

Nothing there jumps out at me as something that would cause the video kernel module not to load.

> The time it was working, `inxi -F` said the graphics driver was `amdgpu`, but on subsequent attempts it has been `radeon` I believe and on the installed, not properly working system, it says `ati,fbdev` as previously mentioned).

The radeon X driver is too old for your GPU. Same with ati. But I guess Xserver stil  tries them when it sees an ATI/AMD card.
It's best to look at /var/log/Xorg.0.log to see what's really going on. inxi is a nice overview when things work, but it's not a great troubleshooting tool.

---

### Post by sjpt2 on 2021-02-28
Yeah, it's the same story with 5.4 kernel.

This is the Xorg.0.log. The only thing that stands out to me is the distinct lack of anything amdgpu, but I don't really know what to look for.

```

[     3.701] 
X.Org X Server 1.20.9
X Protocol Version 11, Revision 0
[     3.701] Build Operating System: Linux 4.15.0-130-generic x86_64 Ubuntu
[     3.701] Current Operating System: Linux sarek 5.8.0-44-generic #50~20.04.1-Ubuntu SMP Wed Feb 10 21:07:30 UTC 2021 x86_64
[     3.701] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.8.0-44-generic root=UUID=68a55d9a-d8b0-4880-a07d-a68884c897dd ro quiet splash vt.handoff=7
[     3.701] Build Date: 17 January 2021  09:13:31AM
[     3.701] xorg-server 2:1.20.9-2ubuntu1.2~20.04.1 (For technical support please see http://www.ubuntu.com/support) 
[     3.701] Current version of pixman: 0.38.4
[     3.701]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     3.701] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.701] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb 28 10:56:05 2021
[     3.702] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     3.702] (==) No Layout section.  Using the first Screen section.
[     3.702] (==) No screen section available. Using defaults.
[     3.702] (**) |-->Screen "Default Screen Section" (0)
[     3.702] (**) |   |-->Monitor "<default monitor>"
[     3.703] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     3.703] (==) Automatically adding devices
[     3.703] (==) Automatically enabling devices
[     3.703] (==) Automatically adding GPU devices
[     3.703] (==) Automatically binding GPU devices
[     3.703] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     3.704] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.704]     Entry deleted from font path.
[     3.704] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.704]     Entry deleted from font path.
[     3.704] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.704]     Entry deleted from font path.
[     3.704] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.704]     Entry deleted from font path.
[     3.704] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.704]     Entry deleted from font path.
[     3.704] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     3.704] (==) ModulePath set to "/usr/lib/xorg/modules"
[     3.704] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     3.705] (II) Loader magic: 0x560e0d82d020
[     3.705] (II) Module ABI versions:
[     3.705]     X.Org ANSI C Emulation: 0.4
[     3.705]     X.Org Video Driver: 24.1
[     3.705]     X.Org XInput driver : 24.1
[     3.705]     X.Org Server Extension : 10.0
[     3.705] (++) using VT number 7

[     3.705] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     3.709] (--) PCI:*(5@0:0:0) 1002:1636:103c:8730 rev 194, Mem @ 0xd0000000/268435456, 0xe0000000/2097152, 0xe0600000/524288, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[     3.709] (II) LoadModule: "glx"
[     3.709] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     3.714] (II) Module glx: vendor="X.Org Foundation"
[     3.714]     compiled for 1.20.9, module version = 1.0.0
[     3.714]     ABI class: X.Org Server Extension, version 10.0
[     3.714] (==) Matched ati as autoconfigured driver 0
[     3.714] (==) Matched modesetting as autoconfigured driver 1
[     3.714] (==) Matched fbdev as autoconfigured driver 2
[     3.714] (==) Matched vesa as autoconfigured driver 3
[     3.714] (==) Assigned the driver to the xf86ConfigLayout
[     3.714] (II) LoadModule: "ati"
[     3.714] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[     3.714] (II) Module ati: vendor="X.Org Foundation"
[     3.714]     compiled for 1.20.5, module version = 19.1.0
[     3.714]     Module class: X.Org Video Driver
[     3.714]     ABI class: X.Org Video Driver, version 24.0
[     3.776] (II) LoadModule: "radeon"
[     3.777] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[     3.779] (II) Module radeon: vendor="X.Org Foundation"
[     3.779]     compiled for 1.20.5, module version = 19.1.0
[     3.779]     Module class: X.Org Video Driver
[     3.779]     ABI class: X.Org Video Driver, version 24.0
[     3.779] (II) LoadModule: "modesetting"
[     3.779] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     3.780] (II) Module modesetting: vendor="X.Org Foundation"
[     3.780]     compiled for 1.20.9, module version = 1.20.9
[     3.780]     Module class: X.Org Video Driver
[     3.780]     ABI class: X.Org Video Driver, version 24.1
[     3.780] (II) LoadModule: "fbdev"
[     3.780] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     3.780] (II) Module fbdev: vendor="X.Org Foundation"
[     3.780]     compiled for 1.20.1, module version = 0.5.0
[     3.780]     Module class: X.Org Video Driver
[     3.780]     ABI class: X.Org Video Driver, version 24.0
[     3.781] (II) LoadModule: "vesa"
[     3.781] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     3.781] (II) Module vesa: vendor="X.Org Foundation"
[     3.781]     compiled for 1.20.4, module version = 2.4.0
[     3.781]     Module class: X.Org Video Driver
[     3.781]     ABI class: X.Org Video Driver, version 24.0
[     3.781] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
    ATI Radeon Mobility X600 (M24), ATI FireMV 2400,
    ATI Radeon Mobility X300 (M24), ATI FireGL M24 GL,
    ATI Radeon X600 (RV380), ATI FireGL V3200 (RV380),
    ATI Radeon IGP320 (A3), ATI Radeon IGP330/340/350 (A4),
    ATI Radeon 9500, ATI Radeon 9600TX, ATI FireGL Z1, ATI Radeon 9800SE,
    ATI Radeon 9800, ATI FireGL X2, ATI Radeon 9600, ATI Radeon 9600SE,
    ATI Radeon 9600XT, ATI FireGL T2, ATI Radeon 9650, ATI FireGL RV360,
    ATI Radeon 7000 IGP (A4+), ATI Radeon 8500 AIW,
    ATI Radeon IGP320M (U1), ATI Radeon IGP330M/340M/350M (U2),
    ATI Radeon Mobility 7000 IGP, ATI Radeon 9000/PRO, ATI Radeon 9000,
    ATI Radeon X800 (R420), ATI Radeon X800PRO (R420),
    ATI Radeon X800SE (R420), ATI FireGL X3 (R420),
    ATI Radeon Mobility 9800 (M18), ATI Radeon X800 SE (R420),
    ATI Radeon X800XT (R420), ATI Radeon X800 VE (R420),
    ATI Radeon X850 (R480), ATI Radeon X850 XT (R480),
    ATI Radeon X850 SE (R480), ATI Radeon X850 PRO (R480),
    ATI Radeon X850 XT PE (R480), ATI Radeon Mobility M7,
    ATI Mobility FireGL 7800 M7, ATI Radeon Mobility M6,
    ATI FireGL Mobility 9000 (M9), ATI Radeon Mobility 9000 (M9),
    ATI Radeon 9700 Pro, ATI Radeon 9700/9500Pro, ATI FireGL X1,
    ATI Radeon 9800PRO, ATI Radeon 9800XT,
    ATI Radeon Mobility 9600/9700 (M10/M11),
    ATI Radeon Mobility 9600 (M10), ATI Radeon Mobility 9600 (M11),
    ATI FireGL Mobility T2 (M10), ATI FireGL Mobility T2e (M11),
    ATI Radeon, ATI FireGL 8700/8800, ATI Radeon 8500, ATI Radeon 9100,
    ATI Radeon 7500, ATI Radeon VE/7000, ATI ES1000,
    ATI Radeon Mobility X300 (M22), ATI Radeon Mobility X600 SE (M24C),
    ATI FireGL M22 GL, ATI Radeon X800 (R423), ATI Radeon X800PRO (R423),
    ATI Radeon X800LE (R423), ATI Radeon X800SE (R423),
    ATI Radeon X800 XTP (R430), ATI Radeon X800 XL (R430),
    ATI Radeon X800 SE (R430), ATI Radeon X800 (R430),
    ATI FireGL V7100 (R423), ATI FireGL V5100 (R423),
    ATI FireGL unknown (R423), ATI Mobility FireGL V5000 (M26),
    ATI Mobility Radeon X700 XL (M26), ATI Mobility Radeon X700 (M26),
    ATI Radeon X550XTX, ATI Radeon 9100 IGP (A5),
    ATI Radeon Mobility 9100 IGP (U3), ATI Radeon XPRESS 200,
    ATI Radeon XPRESS 200M, ATI Radeon 9250, ATI Radeon 9200,
    ATI Radeon 9200SE, ATI FireMV 2200, ATI Radeon X300 (RV370),
    ATI Radeon X600 (RV370), ATI Radeon X550 (RV370),
    ATI FireGL V3100 (RV370), ATI FireMV 2200 PCIE (RV370),
    ATI Radeon Mobility 9200 (M9+), ATI Mobility Radeon X800 XT (M28),
    ATI Mobility FireGL V5100 (M28), ATI Mobility Radeon X800 (M28),
    ATI Radeon X850, ATI unknown Radeon / FireGL (R480),
    ATI Radeon X800XT (R423), ATI FireGL V5000 (RV410),
    ATI Radeon X700 XT (RV410), ATI Radeon X700 PRO (RV410),
    ATI Radeon X700 SE (RV410), ATI Radeon X700 (RV410),
    ATI Radeon X1800, ATI Mobility Radeon X1800 XT,
    ATI Mobility Radeon X1800, ATI Mobility FireGL V7200,
    ATI FireGL V7200, ATI FireGL V5300, ATI Mobility FireGL V7100,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1550 64-bit,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI FireGL V3300,
    ATI FireGL V3350, ATI Mobility Radeon X1450,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1650, ATI Mobility FireGL V5200,
    ATI Mobility Radeon X1600, ATI Radeon X1300 XT/X1600 Pro,
    ATI FireGL V3400, ATI Mobility FireGL V5250,
    ATI Mobility Radeon X1700, ATI Mobility Radeon X1700 XT,
    ATI FireGL V5200, ATI Radeon X2300HD, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI AMD Stream Processor,
    ATI RV560, ATI Mobility Radeon X1900, ATI Radeon X1950 GT, ATI RV570,
    ATI FireGL V7400, ATI Radeon 9100 PRO IGP,
    ATI Radeon Mobility 9200 IGP, ATI Radeon X1200, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro,
    ATI Radeon HD 2900 GT, ATI FireGL V8650, ATI FireGL V8600,
    ATI FireGL V7600, ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon HD 4850 x2, ATI FirePro V8750 (FireGL),
    ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
    ATI Mobility RADEON HD 4850 X2, ATI FirePro RV770,
    AMD FireStream 9270, AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI FirePro M7750, ATI M98, ATI Mobility Radeon HD 4650,
    ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
    ATI FirePro M5750, ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI RV610,
    ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
    ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI Radeon HD 2350,
    ATI Mobility Radeon HD 2400 XT, ATI Mobility Radeon HD 2400,
    ATI RADEON E2400, ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI Mobility Radeon HD 3870,
    ATI Mobility Radeon HD 3870 X2, ATI Radeon HD3870 X2,
    ATI FireGL V7700, ATI Radeon HD3690, AMD Firestream 9170,
    ATI Radeon HD 4550, ATI Radeon RV710, ATI Radeon HD 4350,
    ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3430, ATI FirePro V3700,
    ATI FireMV 2450, ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
    ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon 3000 Graphics, SUMO, SUMO2,
    ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI Radeon HD 5670, ATI Radeon HD 5570, ATI Radeon HD 5500 Series,
    REDWOOD, ATI Mobility Radeon Graphics, CEDAR, ATI FirePro 2270,
    ATI Radeon HD 5450, CAYMAN, AMD Radeon HD 6900 Series,
    AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6700 Series, TURKS, CAICOS,
    ARUBA, TAHITI, PITCAIRN, VERDE, OLAND, HAINAN, BONAIRE, KABINI,
    MULLINS, KAVERI, HAWAII
[     3.784] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     3.784] (II) FBDEV: driver for framebuffer: fbdev
[     3.784] (II) VESA: driver for VESA chipsets: vesa
[     3.784] (EE) open /dev/dri/card0: No such file or directory
[     3.784] (WW) Falling back to old probe method for modesetting
[     3.784] (EE) open /dev/dri/card0: No such file or directory
[     3.784] (II) Loading sub module "fbdevhw"
[     3.784] (II) LoadModule: "fbdevhw"
[     3.784] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     3.784] (II) Module fbdevhw: vendor="X.Org Foundation"
[     3.784]     compiled for 1.20.9, module version = 0.0.2
[     3.784]     ABI class: X.Org Video Driver, version 24.1
[     3.784] (**) FBDEV(1): claimed PCI slot 5@0:0:0
[     3.784] (II) FBDEV(1): using default device
[     3.784] (EE) Screen 0 deleted because of no matching config section.
[     3.784] (II) UnloadModule: "modesetting"
[     3.785] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     3.785] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[     3.785] (==) FBDEV(0): RGB weight 888
[     3.785] (==) FBDEV(0): Default visual is TrueColor
[     3.785] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[     3.785] (II) FBDEV(0): hardware: EFI VGA (video memory: 3072kB)
[     3.785] (II) FBDEV(0): checking modes against framebuffer device...
[     3.785] (II) FBDEV(0): checking modes against monitor...
[     3.785] (II) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[     3.785] (**) FBDEV(0):  Built-in mode "current": 78.7 MHz, 59.9 kHz, 75.7 Hz
[     3.785] (II) FBDEV(0): Modeline "current"x0.0   78.65  1024 1056 1184 1312  768 772 776 792 -hsync -vsync -csync (59.9 kHz b)
[     3.785] (==) FBDEV(0): DPI set to (96, 96)
[     3.785] (II) Loading sub module "fb"
[     3.785] (II) LoadModule: "fb"
[     3.785] (II) Loading /usr/lib/xorg/modules/libfb.so
[     3.785] (II) Module fb: vendor="X.Org Foundation"
[     3.785]     compiled for 1.20.9, module version = 1.0.0
[     3.785]     ABI class: X.Org ANSI C Emulation, version 0.4
[     3.785] (**) FBDEV(0): using shadow framebuffer
[     3.785] (II) Loading sub module "shadow"
[     3.785] (II) LoadModule: "shadow"
[     3.785] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     3.786] (II) Module shadow: vendor="X.Org Foundation"
[     3.786]     compiled for 1.20.9, module version = 1.1.0
[     3.786]     ABI class: X.Org ANSI C Emulation, version 0.4
[     3.786] (II) UnloadModule: "radeon"
[     3.786] (II) Unloading radeon
[     3.786] (II) UnloadModule: "vesa"
[     3.786] (II) Unloading vesa
[     3.786] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[     3.787] (==) FBDEV(0): Backing store enabled
[     3.787] (==) FBDEV(0): DPMS enabled
[     3.787] (II) Initializing extension Generic Event Extension
[     3.787] (II) Initializing extension SHAPE
[     3.788] (II) Initializing extension MIT-SHM
[     3.788] (II) Initializing extension XInputExtension
[     3.788] (II) Initializing extension XTEST
[     3.788] (II) Initializing extension BIG-REQUESTS
[     3.788] (II) Initializing extension SYNC
[     3.789] (II) Initializing extension XKEYBOARD
[     3.789] (II) Initializing extension XC-MISC
[     3.789] (II) Initializing extension SECURITY
[     3.789] (II) Initializing extension XFIXES
[     3.789] (II) Initializing extension RENDER
[     3.789] (II) Initializing extension RANDR
[     3.789] (II) Initializing extension COMPOSITE
[     3.790] (II) Initializing extension DAMAGE
[     3.790] (II) Initializing extension MIT-SCREEN-SAVER
[     3.790] (II) Initializing extension DOUBLE-BUFFER
[     3.790] (II) Initializing extension RECORD
[     3.790] (II) Initializing extension DPMS
[     3.790] (II) Initializing extension Present
[     3.790] (II) Initializing extension DRI3
[     3.790] (II) Initializing extension X-Resource
[     3.791] (II) Initializing extension XVideo
[     3.791] (II) Initializing extension XVideo-MotionCompensation
[     3.791] (II) Initializing extension SELinux
[     3.791] (II) SELinux: Disabled on system
[     3.791] (II) Initializing extension GLX
[     3.791] (II) AIGLX: Screen 0 is not DRI2 capable
[     3.858] (II) IGLX: Loaded and initialized swrast
[     3.858] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[     3.858] (II) Initializing extension XFree86-VidModeExtension
[     3.859] (II) Initializing extension XFree86-DGA
[     3.859] (II) Initializing extension XFree86-DRI
[     3.859] (II) Initializing extension DRI2
[     3.904] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[     3.904] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[     3.904] (II) LoadModule: "libinput"
[     3.904] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[     3.906] (II) Module libinput: vendor="X.Org Foundation"
[     3.906]     compiled for 1.20.4, module version = 0.29.0
[     3.906]     Module class: X.Org XInput Driver
[     3.906]     ABI class: X.Org XInput driver, version 24.1
[     3.906] (II) Using input driver 'libinput' for 'Power Button'
[     3.906] (**) Power Button: always reports core events
[     3.906] (**) Option "Device" "/dev/input/event3"
[     3.906] (**) Option "_source" "server/udev"
[     3.908] (II) event3  - Power Button: is tagged by udev as: Keyboard
[     3.908] (II) event3  - Power Button: device is a keyboard
[     3.908] (II) event3  - Power Button: device removed
[     3.936] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[     3.936] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     3.936] (**) Option "xkb_model" "pc105"
[     3.936] (**) Option "xkb_layout" "se"
[     3.958] (II) event3  - Power Button: is tagged by udev as: Keyboard
[     3.958] (II) event3  - Power Button: device is a keyboard
[     3.959] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[     3.959] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[     3.959] (II) Using input driver 'libinput' for 'Video Bus'
[     3.959] (**) Video Bus: always reports core events
[     3.959] (**) Option "Device" "/dev/input/event5"
[     3.959] (**) Option "_source" "server/udev"
[     3.960] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[     3.960] (II) event5  - Video Bus: device is a keyboard
[     3.960] (II) event5  - Video Bus: device removed
[     3.992] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0d/LNXVIDEO:00/input/input5/event5"
[     3.992] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     3.992] (**) Option "xkb_model" "pc105"
[     3.992] (**) Option "xkb_layout" "se"
[     3.994] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[     3.994] (II) event5  - Video Bus: device is a keyboard
[     3.995] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     3.995] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[     3.995] (II) Using input driver 'libinput' for 'Power Button'
[     3.995] (**) Power Button: always reports core events
[     3.995] (**) Option "Device" "/dev/input/event0"
[     3.995] (**) Option "_source" "server/udev"
[     3.996] (II) event0  - Power Button: is tagged by udev as: Keyboard
[     3.996] (II) event0  - Power Button: device is a keyboard
[     3.996] (II) event0  - Power Button: device removed
[     4.016] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     4.016] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     4.016] (**) Option "xkb_model" "pc105"
[     4.016] (**) Option "xkb_layout" "se"
[     4.018] (II) event0  - Power Button: is tagged by udev as: Keyboard
[     4.018] (II) event0  - Power Button: device is a keyboard
[     4.018] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[     4.019] (II) No input driver specified, ignoring this device.
[     4.019] (II) This device may have been added with another device file.
[     4.019] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[     4.019] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[     4.019] (II) Using input driver 'libinput' for 'Sleep Button'
[     4.019] (**) Sleep Button: always reports core events
[     4.019] (**) Option "Device" "/dev/input/event1"
[     4.019] (**) Option "_source" "server/udev"
[     4.020] (II) event1  - Sleep Button: is tagged by udev as: Keyboard
[     4.020] (II) event1  - Sleep Button: device is a keyboard
[     4.020] (II) event1  - Sleep Button: device removed
[     4.036] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[     4.036] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[     4.036] (**) Option "xkb_model" "pc105"
[     4.036] (**) Option "xkb_layout" "se"
[     4.037] (II) event1  - Sleep Button: is tagged by udev as: Keyboard
[     4.038] (II) event1  - Sleep Button: device is a keyboard
[     4.038] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event11)
[     4.038] (II) No input driver specified, ignoring this device.
[     4.038] (II) This device may have been added with another device file.
[     4.039] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=7 (/dev/input/event12)
[     4.039] (II) No input driver specified, ignoring this device.
[     4.039] (II) This device may have been added with another device file.
[     4.039] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=8 (/dev/input/event13)
[     4.039] (II) No input driver specified, ignoring this device.
[     4.039] (II) This device may have been added with another device file.
[     4.040] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=9 (/dev/input/event14)
[     4.040] (II) No input driver specified, ignoring this device.
[     4.040] (II) This device may have been added with another device file.
[     4.040] (II) config/udev: Adding input device HP HD Camera: HP HD Camera (/dev/input/event15)
[     4.040] (**) HP HD Camera: HP HD Camera: Applying InputClass "libinput keyboard catchall"
[     4.040] (II) Using input driver 'libinput' for 'HP HD Camera: HP HD Camera'
[     4.041] (**) HP HD Camera: HP HD Camera: always reports core events
[     4.041] (**) Option "Device" "/dev/input/event15"
[     4.041] (**) Option "_source" "server/udev"
[     4.042] (II) event15 - HP HD Camera: HP HD Camera: is tagged by udev as: Keyboard
[     4.042] (II) event15 - HP HD Camera: HP HD Camera: device is a keyboard
[     4.042] (II) event15 - HP HD Camera: HP HD Camera: device removed
[     4.080] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:08.1/0000:05:00.4/usb3/3-4/3-4:1.0/input/input19/event15"
[     4.080] (II) XINPUT: Adding extended input device "HP HD Camera: HP HD Camera" (type: KEYBOARD, id 10)
[     4.080] (**) Option "xkb_model" "pc105"
[     4.080] (**) Option "xkb_layout" "se"
[     4.082] (II) event15 - HP HD Camera: HP HD Camera: is tagged by udev as: Keyboard
[     4.082] (II) event15 - HP HD Camera: HP HD Camera: device is a keyboard
[     4.083] (II) config/udev: Adding input device HP HD Camera: HP IR Camera (/dev/input/event16)
[     4.084] (**) HP HD Camera: HP IR Camera: Applying InputClass "libinput keyboard catchall"
[     4.084] (II) Using input driver 'libinput' for 'HP HD Camera: HP IR Camera'
[     4.084] (**) HP HD Camera: HP IR Camera: always reports core events
[     4.084] (**) Option "Device" "/dev/input/event16"
[     4.084] (**) Option "_source" "server/udev"
[     4.085] (II) event16 - HP HD Camera: HP IR Camera: is tagged by udev as: Keyboard
[     4.085] (II) event16 - HP HD Camera: HP IR Camera: device is a keyboard
[     4.085] (II) event16 - HP HD Camera: HP IR Camera: device removed
[     4.120] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:08.1/0000:05:00.4/usb3/3-4/3-4:1.2/input/input20/event16"
[     4.120] (II) XINPUT: Adding extended input device "HP HD Camera: HP IR Camera" (type: KEYBOARD, id 11)
[     4.120] (**) Option "xkb_model" "pc105"
[     4.120] (**) Option "xkb_layout" "se"
[     4.122] (II) event16 - HP HD Camera: HP IR Camera: is tagged by udev as: Keyboard
[     4.122] (II) event16 - HP HD Camera: HP IR Camera: device is a keyboard
[     4.123] (II) config/udev: Adding input device HD-Audio Generic Mic (/dev/input/event17)
[     4.123] (II) No input driver specified, ignoring this device.
[     4.123] (II) This device may have been added with another device file.
[     4.124] (II) config/udev: Adding input device HD-Audio Generic Headphone (/dev/input/event18)
[     4.124] (II) No input driver specified, ignoring this device.
[     4.124] (II) This device may have been added with another device file.
[     4.124] (II) config/udev: Adding input device SYNA30AD:00 06CB:CDEC Mouse (/dev/input/event7)
[     4.124] (**) SYNA30AD:00 06CB:CDEC Mouse: Applying InputClass "libinput pointer catchall"
[     4.124] (II) Using input driver 'libinput' for 'SYNA30AD:00 06CB:CDEC Mouse'
[     4.124] (**) SYNA30AD:00 06CB:CDEC Mouse: always reports core events
[     4.124] (**) Option "Device" "/dev/input/event7"
[     4.124] (**) Option "_source" "server/udev"
[     4.126] (II) event7  - SYNA30AD:00 06CB:CDEC Mouse: is tagged by udev as: Mouse Pointingstick
[     4.126] (II) event7  - SYNA30AD:00 06CB:CDEC Mouse: device is a pointer
[     4.127] (II) event7  - SYNA30AD:00 06CB:CDEC Mouse: device removed
[     4.160] (**) Option "config_info" "udev:/sys/devices/platform/AMDI0010:00/i2c-0/i2c-SYNA30AD:00/0018:06CB:CDEC.0001/input/input12/event7"
[     4.160] (II) XINPUT: Adding extended input device "SYNA30AD:00 06CB:CDEC Mouse" (type: MOUSE, id 12)
[     4.160] (**) Option "AccelerationScheme" "none"
[     4.160] (**) SYNA30AD:00 06CB:CDEC Mouse: (accel) selected scheme none/0
[     4.160] (**) SYNA30AD:00 06CB:CDEC Mouse: (accel) acceleration factor: 2.000
[     4.160] (**) SYNA30AD:00 06CB:CDEC Mouse: (accel) acceleration threshold: 4
[     4.162] (II) event7  - SYNA30AD:00 06CB:CDEC Mouse: is tagged by udev as: Mouse Pointingstick
[     4.162] (II) event7  - SYNA30AD:00 06CB:CDEC Mouse: device is a pointer
[     4.164] (II) config/udev: Adding input device SYNA30AD:00 06CB:CDEC Mouse (/dev/input/mouse0)
[     4.164] (II) No input driver specified, ignoring this device.
[     4.164] (II) This device may have been added with another device file.
[     4.164] (II) config/udev: Adding input device SYNA30AD:00 06CB:CDEC Touchpad (/dev/input/event10)
[     4.164] (**) SYNA30AD:00 06CB:CDEC Touchpad: Applying InputClass "libinput touchpad catchall"
[     4.164] (**) SYNA30AD:00 06CB:CDEC Touchpad: Applying InputClass "touchpad catchall"
[     4.164] (**) SYNA30AD:00 06CB:CDEC Touchpad: Applying InputClass "Default clickpad buttons"
[     4.164] (II) LoadModule: "synaptics"
[     4.165] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     4.167] (II) Module synaptics: vendor="X.Org Foundation"
[     4.167]     compiled for 1.20.8, module version = 1.9.1
[     4.167]     Module class: X.Org XInput Driver
[     4.168]     ABI class: X.Org XInput driver, version 24.1
[     4.168] (II) Using input driver 'synaptics' for 'SYNA30AD:00 06CB:CDEC Touchpad'
[     4.168] (**) SYNA30AD:00 06CB:CDEC Touchpad: always reports core events
[     4.168] (**) Option "Device" "/dev/input/event10"
[     4.200] (II) synaptics: SYNA30AD:00 06CB:CDEC Touchpad: found clickpad property
[     4.200] (--) synaptics: SYNA30AD:00 06CB:CDEC Touchpad: x-axis range 0 - 1332 (res 12)
[     4.200] (--) synaptics: SYNA30AD:00 06CB:CDEC Touchpad: y-axis range 0 - 828 (res 12)
[     4.200] (II) synaptics: SYNA30AD:00 06CB:CDEC Touchpad: device does not report pressure, will use touch data.
[     4.200] (II) synaptics: SYNA30AD:00 06CB:CDEC Touchpad: device does not report finger width.
[     4.200] (--) synaptics: SYNA30AD:00 06CB:CDEC Touchpad: buttons: left double triple
[     4.200] (--) synaptics: SYNA30AD:00 06CB:CDEC Touchpad: Vendor 0x6cb Product 0xcdec
[     4.200] (--) synaptics: SYNA30AD:00 06CB:CDEC Touchpad: invalid pressure range.  defaulting to 0 - 255
[     4.200] (--) synaptics: SYNA30AD:00 06CB:CDEC Touchpad: invalid finger width range.  defaulting to 0 - 15
[     4.200] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[     4.200] (--) synaptics: SYNA30AD:00 06CB:CDEC Touchpad: touchpad found
[     4.200] (**) SYNA30AD:00 06CB:CDEC Touchpad: always reports core events
[     4.256] (**) Option "config_info" "udev:/sys/devices/platform/AMDI0010:00/i2c-0/i2c-SYNA30AD:00/0018:06CB:CDEC.0001/input/input13/event10"
[     4.256] (II) XINPUT: Adding extended input device "SYNA30AD:00 06CB:CDEC Touchpad" (type: TOUCHPAD, id 13)
[     4.256] (**) synaptics: SYNA30AD:00 06CB:CDEC Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[     4.256] (**) synaptics: SYNA30AD:00 06CB:CDEC Touchpad: (accel) MaxSpeed is now 1.75
[     4.256] (**) synaptics: SYNA30AD:00 06CB:CDEC Touchpad: (accel) AccelFactor is now 0.128
[     4.257] (**) SYNA30AD:00 06CB:CDEC Touchpad: (accel) keeping acceleration scheme 1
[     4.257] (**) SYNA30AD:00 06CB:CDEC Touchpad: (accel) acceleration profile 1
[     4.257] (**) SYNA30AD:00 06CB:CDEC Touchpad: (accel) acceleration factor: 2.000
[     4.257] (**) SYNA30AD:00 06CB:CDEC Touchpad: (accel) acceleration threshold: 4
[     4.257] (--) synaptics: SYNA30AD:00 06CB:CDEC Touchpad: touchpad found
[     4.257] (II) config/udev: Adding input device SYNA30AD:00 06CB:CDEC Touchpad (/dev/input/mouse1)
[     4.257] (**) SYNA30AD:00 06CB:CDEC Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[     4.258] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[     4.258] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[     4.258] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[     4.258] (**) AT Translated Set 2 keyboard: always reports core events
[     4.258] (**) Option "Device" "/dev/input/event4"
[     4.258] (**) Option "_source" "server/udev"
[     4.259] (II) event4  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[     4.260] (II) event4  - AT Translated Set 2 keyboard: device is a keyboard
[     4.260] (II) event4  - AT Translated Set 2 keyboard: device removed
[     4.292] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[     4.292] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[     4.292] (**) Option "xkb_model" "pc105"
[     4.292] (**) Option "xkb_layout" "se"
[     4.294] (II) event4  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[     4.294] (II) event4  - AT Translated Set 2 keyboard: device is a keyboard
[     4.295] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event9)
[     4.295] (II) No input driver specified, ignoring this device.
[     4.295] (II) This device may have been added with another device file.
[     4.296] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[     4.296] (II) No input driver specified, ignoring this device.
[     4.296] (II) This device may have been added with another device file.
[     4.298] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event6)
[     4.298] (**) HP WMI hotkeys: Applying InputClass "libinput keyboard catchall"
[     4.298] (II) Using input driver 'libinput' for 'HP WMI hotkeys'
[     4.298] (**) HP WMI hotkeys: always reports core events
[     4.298] (**) Option "Device" "/dev/input/event6"
[     4.298] (**) Option "_source" "server/udev"
[     4.299] (II) event6  - HP WMI hotkeys: is tagged by udev as: Keyboard Switch
[     4.299] (II) event6  - HP WMI hotkeys: device is a keyboard
[     4.299] (II) event6  - HP WMI hotkeys: device removed
[     4.320] (**) Option "config_info" "udev:/sys/devices/virtual/input/input11/event6"
[     4.320] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 15)
[     4.320] (**) Option "xkb_model" "pc105"
[     4.320] (**) Option "xkb_layout" "se"
[     4.321] (II) event6  - HP WMI hotkeys: is tagged by udev as: Keyboard Switch
[     4.321] (II) event6  - HP WMI hotkeys: device is a keyboard
[     4.322] (II) config/udev: Adding input device HP Wireless hotkeys (/dev/input/event8)
[     4.322] (**) HP Wireless hotkeys: Applying InputClass "libinput keyboard catchall"
[     4.322] (II) Using input driver 'libinput' for 'HP Wireless hotkeys'
[     4.322] (**) HP Wireless hotkeys: always reports core events
[     4.322] (**) Option "Device" "/dev/input/event8"
[     4.322] (**) Option "_source" "server/udev"
[     4.323] (II) event8  - HP Wireless hotkeys: is tagged by udev as: Keyboard
[     4.323] (II) event8  - HP Wireless hotkeys: device is a keyboard
[     4.323] (II) event8  - HP Wireless hotkeys: device removed
[     4.356] (**) Option "config_info" "udev:/sys/devices/virtual/input/input9/event8"
[     4.356] (II) XINPUT: Adding extended input device "HP Wireless hotkeys" (type: KEYBOARD, id 16)
[     4.356] (**) Option "xkb_model" "pc105"
[     4.356] (**) Option "xkb_layout" "se"
[     4.357] (II) event8  - HP Wireless hotkeys: is tagged by udev as: Keyboard
[     4.357] (II) event8  - HP Wireless hotkeys: device is a keyboard

```

---

### Post by mastablasta on 2021-03-01
is this on a fresh install? 

you are loading Radeon drivers. i am not sure why system would recognise the chip as Radeon.

also - what?
> [COLOR=#000000][FONT=&quot]Build Operating System: Linux 4.15.0-130-generic x86_64 Ubuntu[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2021-03-01
```
(EE) open /dev/dri/card0: No such file or directory
```

Kernel module is probably not loading. It's time to dig into dmesg and try and figure out why:
```
dmesg
dmesg | grep -i amd
```

> **mastablasta said:**
> you are loading Radeon drivers. i am not sure why system would recognize the chip as Radeon.

That is the Xserver's autodetection of possible drivers (based on PCI ID I'm guessing). But if you look further down the log, you'll see the fbdev driver is the one X ultimately chooses because of the aforementioned error.

> also - what?

It is nothing specific to the user or to worry about. It is just the kernel used when Canonical built the image. (In other words, they used 18.04 to build 20.04.)

---

### Post by sjpt2 on 2021-03-02
> is this on a fresh install?

Relatively fresh, but  no. I tried to fix the problem on my own by installing the drivers  straight from AMD, but the build failed so I subsequently ran the  uninstall script that was bundled with it. I have since reinstalled  `xserver-xorg-video-amdgpu` for good measure.

Here is the output of dmesg:

[https://paste.ubuntu.com/p/gHWG2YJHPT/](https://paste.ubuntu.com/p/gHWG2YJHPT/)

And here are just the amd parts:

```

[     0.000000] Linux version 5.8.0-44-generic (buildd@lgw01-amd64-054) (gcc  (Ubuntu 9.3.0-17ubuntu1~20.04) 9.3.0, GNU ld (GNU Binutils for Ubuntu)  2.34) #50~20.04.1-Ubuntu SMP Wed Feb 10 21:07:30 UTC 2021 (Ubuntu  5.8.0-44.50~20.04.1-generic 5.8.18)
[    0.000000]   AMD AuthenticAMD
[    0.004894] RAMDISK: [mem 0x3a2dd000-0x3d484fff]
[    0.004926] ACPI: SSDT 0x00000000B8461000 007216 (v02 AMD    AmdTable 00000002 MSFT 04000000)
[    0.004928] ACPI: IVRS 0x00000000B8460000 0001A4 (v02 AMD    AmdTable 00000001 AMD  00000000)
[    0.004930] ACPI: SSDT 0x00000000B845F000 000257 (v01 AMD    STD3     00000001 INTL 20160527)
[    0.004955] ACPI: SSDT 0x00000000B8439000 001BF4 (v01 AMD    AmdTable 00000001 AMD  00000001)
[    0.004956] ACPI: CRAT 0x00000000B846B000 000F28 (v01 AMD    AmdTable 00000001 AMD  00000001)
[    0.004958] ACPI: CDIT 0x00000000B8438000 000029 (v01 AMD    AmdTable 00000001 AMD  00000001)
[    0.004968] ACPI: SSDT 0x00000000B842F000 0032BA (v01 AMD    AmdTable 00000001 INTL 20160527)
[    0.004971] ACPI: SSDT 0x00000000B842D000 00008D (v01 AMD    AmdTable 00000001 INTL 20160527)
[    0.004972] ACPI: SSDT 0x00000000B842C000 00089D (v01 AMD    AmdTable 00000001 INTL 20160527)
[    0.077162] AMD-Vi: ivrs, add hid:AMDI0020, uid:\_SB.FUR0, rdevid:160
[    0.077163] AMD-Vi: ivrs, add hid:AMDI0020, uid:\_SB.FUR1, rdevid:160
[    0.077163] AMD-Vi: ivrs, add hid:AMDI0020, uid:\_SB.FUR2, rdevid:160
[    0.077164] AMD-Vi: ivrs, add hid:AMDI0020, uid:\_SB.FUR3, rdevid:160
[    0.194989] Spectre V2 : Mitigation: Full AMD retpoline
[    0.307744] smpboot: CPU0: AMD Ryzen 7 4700U with Radeon Graphics (family: 0x17, model: 0x60, stepping: 0x1)
[    0.307881] Performance Events: Fam17h+ core perfctr, AMD PMU driver.
[    0.523948] pci 0000:00:00.2: AMD-Vi: Unable to read/write to IOMMU perf counter.
[    0.526531] pci 0000:00:00.2: AMD-Vi: Found IOMMU cap 0x40
[    0.526533] pci 0000:00:00.2: AMD-Vi: Extended features (0x206d73ef22254ade):
[    0.526537] AMD-Vi: Interrupt remapping enabled
[    0.526537] AMD-Vi: Virtual APIC enabled
[    0.526537] AMD-Vi: X2APIC enabled
[    0.526737] AMD-Vi: Lazy IO/TLB flushing enabled
[    0.528153] amd_uncore: AMD NB counters detected
[    0.528157] amd_uncore: AMD LLC counters detected
[    0.528996] perf: AMD IBS detected (0x000003ff)
[     1.462094] input: SYNA30AD:00 06CB:CDEC Mouse as  /devices/platform/AMDI0010:00/i2c-0/i2c-SYNA30AD:00/0018:06CB:CDEC.0001/input/input6
[     1.462425] input: SYNA30AD:00 06CB:CDEC Touchpad as  /devices/platform/AMDI0010:00/i2c-0/i2c-SYNA30AD:00/0018:06CB:CDEC.0001/input/input7
[     2.880947] input: SYNA30AD:00 06CB:CDEC Mouse as  /devices/platform/AMDI0010:00/i2c-0/i2c-SYNA30AD:00/0018:06CB:CDEC.0001/input/input12
[     2.881069] input: SYNA30AD:00 06CB:CDEC Touchpad as  /devices/platform/AMDI0010:00/i2c-0/i2c-SYNA30AD:00/0018:06CB:CDEC.0001/input/input13
[    2.890553] EDAC amd64: F17h_M60h detected (node 0).
[    2.890599] EDAC amd64: Node 0: DRAM ECC disabled.
[    2.930050] EDAC amd64: F17h_M60h detected (node 0).
[    2.930101] EDAC amd64: Node 0: DRAM ECC disabled.
[    3.137711] EDAC amd64: F17h_M60h detected (node 0).
[    3.137755] EDAC amd64: Node 0: DRAM ECC disabled.
[    3.238452] EDAC amd64: F17h_M60h detected (node 0).
[    3.238504] EDAC amd64: Node 0: DRAM ECC disabled.
[    3.321739] EDAC amd64: F17h_M60h detected (node 0).
[    3.321802] EDAC amd64: Node 0: DRAM ECC disabled.
[    3.398085] EDAC amd64: F17h_M60h detected (node 0).
[    3.398129] EDAC amd64: Node 0: DRAM ECC disabled.
[    3.485361] EDAC amd64: F17h_M60h detected (node 0).
[    3.485402] EDAC amd64: Node 0: DRAM ECC disabled.
[    3.558677] EDAC amd64: F17h_M60h detected (node 0).
[    3.558736] EDAC amd64: Node 0: DRAM ECC disabled.

```

UPDATE: Today the live USB was OK again, so here is a good dmesg output for reference:

[https://paste.ubuntu.com/p/QjDw6Wjxxc/](https://paste.ubuntu.com/p/QjDw6Wjxxc/)

And here are the amd parts of that:

```

[    0.000000] Linux version 5.8.0-43-generic (buildd@lcy01-amd64-018) (gcc (Ubuntu 9.3.0-17ubuntu1~20.04) 9.3.0, GNU ld (GNU Binutils for Ubuntu) 2.34) #49~20.04.1-Ubuntu SMP Fri Feb 5 09:57:56 UTC 2021 (Ubuntu 5.8.0-43.49~20.04.1-generic 5.8.18)
[    0.000000]   AMD AuthenticAMD
[    0.004676] RAMDISK: [mem 0x379cc000-0x3d485fff]
[    0.004708] ACPI: SSDT 0x00000000B8461000 007216 (v02 AMD    AmdTable 00000002 MSFT 04000000)
[    0.004710] ACPI: IVRS 0x00000000B8460000 0001A4 (v02 AMD    AmdTable 00000001 AMD  00000000)
[    0.004711] ACPI: SSDT 0x00000000B845F000 000257 (v01 AMD    STD3     00000001 INTL 20160527)
[    0.004735] ACPI: SSDT 0x00000000B8439000 001BF4 (v01 AMD    AmdTable 00000001 AMD  00000001)
[    0.004737] ACPI: CRAT 0x00000000B846B000 000F28 (v01 AMD    AmdTable 00000001 AMD  00000001)
[    0.004739] ACPI: CDIT 0x00000000B8438000 000029 (v01 AMD    AmdTable 00000001 AMD  00000001)
[    0.004748] ACPI: SSDT 0x00000000B842F000 0032BA (v01 AMD    AmdTable 00000001 INTL 20160527)
[    0.004751] ACPI: SSDT 0x00000000B842D000 00008D (v01 AMD    AmdTable 00000001 INTL 20160527)
[    0.004753] ACPI: SSDT 0x00000000B842C000 00089D (v01 AMD    AmdTable 00000001 INTL 20160527)
[    0.077113] AMD-Vi: ivrs, add hid:AMDI0020, uid:\_SB.FUR0, rdevid:160
[    0.077114] AMD-Vi: ivrs, add hid:AMDI0020, uid:\_SB.FUR1, rdevid:160
[    0.077115] AMD-Vi: ivrs, add hid:AMDI0020, uid:\_SB.FUR2, rdevid:160
[    0.077116] AMD-Vi: ivrs, add hid:AMDI0020, uid:\_SB.FUR3, rdevid:160
[    0.195155] Spectre V2 : Mitigation: Full AMD retpoline
[    0.308013] smpboot: CPU0: AMD Ryzen 7 4700U with Radeon Graphics (family: 0x17, model: 0x60, stepping: 0x1)
[    0.308149] Performance Events: Fam17h+ core perfctr, AMD PMU driver.
[    0.606502] pci 0000:00:00.2: AMD-Vi: Unable to read/write to IOMMU perf counter.
[    0.609404] pci 0000:00:00.2: AMD-Vi: Found IOMMU cap 0x40
[    0.609406] pci 0000:00:00.2: AMD-Vi: Extended features (0x206d73ef22254ade):
[    0.609409] AMD-Vi: Interrupt remapping enabled
[    0.609409] AMD-Vi: Virtual APIC enabled
[    0.609409] AMD-Vi: X2APIC enabled
[    0.609568] AMD-Vi: Lazy IO/TLB flushing enabled
[    0.610266] amd_uncore: AMD NB counters detected
[    0.610269] amd_uncore: AMD LLC counters detected
[    0.610966] perf: AMD IBS detected (0x000003ff)
[    0.905959] AMD-Vi: AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>
[    0.975447] [drm] amdgpu kernel modesetting enabled.
[    0.975552] amdgpu: Topology: Add CPU node
[    0.975625] fb0: switching to amdgpudrmfb from EFI VGA
[    0.975715] amdgpu 0000:05:00.0: vgaarb: deactivate vga console
[    0.975849] amdgpu 0000:05:00.0: amdgpu: Trusted Memory Zone (TMZ) feature disabled as experimental (default)
[    0.979573] amdgpu: ATOM BIOS: SWBRT58350.001
[    0.979618] amdgpu 0000:05:00.0: amdgpu: VRAM: 512M 0x000000F400000000 - 0x000000F41FFFFFFF (512M used)
[    0.979618] amdgpu 0000:05:00.0: amdgpu: GART: 1024M 0x0000000000000000 - 0x000000003FFFFFFF
[    0.979619] amdgpu 0000:05:00.0: amdgpu: AGP: 267419648M 0x000000F800000000 - 0x0000FFFFFFFFFFFF
[    0.979708] [drm] amdgpu: 512M of VRAM memory ready
[    0.979710] [drm] amdgpu: 3072M of GTT memory ready.
[    1.608626] input: SYNA30AD:00 06CB:CDEC Mouse as /devices/platform/AMDI0010:00/i2c-0/i2c-SYNA30AD:00/0018:06CB:CDEC.0001/input/input6
[    1.608863] input: SYNA30AD:00 06CB:CDEC Touchpad as /devices/platform/AMDI0010:00/i2c-0/i2c-SYNA30AD:00/0018:06CB:CDEC.0001/input/input7
[    1.803316] amdgpu: SMU is initialized successfully!
[    1.855512] [drm:dm_helpers_dp_write_dpcd [amdgpu]] *ERROR* Failed to find connector for link!
[    1.856146] [drm:dm_helpers_dp_write_dpcd [amdgpu]] *ERROR* Failed to find connector for link!
[    1.856348] [drm:dm_helpers_dp_write_dpcd [amdgpu]] *ERROR* Failed to find connector for link!
[    1.946821] amdgpu: Topology: Add dGPU node [0x1636:0x1002]
[    1.946832] amdgpu 0000:05:00.0: amdgpu: SE 1, SH per SE 1, CU per SH 8, active_cu_number 7
[    1.948110] fbcon: amdgpudrmfb (fb0) is primary device
[    2.649530] amdgpu 0000:05:00.0: fb0: amdgpudrmfb frame buffer device
[    2.680820] amdgpu 0000:05:00.0: amdgpu: ring gfx uses VM inv eng 0 on hub 0
[    2.680824] amdgpu 0000:05:00.0: amdgpu: ring comp_1.0.0 uses VM inv eng 1 on hub 0
[    2.680826] amdgpu 0000:05:00.0: amdgpu: ring comp_1.1.0 uses VM inv eng 4 on hub 0
[    2.680828] amdgpu 0000:05:00.0: amdgpu: ring comp_1.2.0 uses VM inv eng 5 on hub 0
[    2.680830] amdgpu 0000:05:00.0: amdgpu: ring comp_1.3.0 uses VM inv eng 6 on hub 0
[    2.680831] amdgpu 0000:05:00.0: amdgpu: ring comp_1.0.1 uses VM inv eng 7 on hub 0
[    2.680833] amdgpu 0000:05:00.0: amdgpu: ring comp_1.1.1 uses VM inv eng 8 on hub 0
[    2.680835] amdgpu 0000:05:00.0: amdgpu: ring comp_1.2.1 uses VM inv eng 9 on hub 0
[    2.680837] amdgpu 0000:05:00.0: amdgpu: ring comp_1.3.1 uses VM inv eng 10 on hub 0
[    2.680839] amdgpu 0000:05:00.0: amdgpu: ring kiq_2.1.0 uses VM inv eng 11 on hub 0
[    2.680841] amdgpu 0000:05:00.0: amdgpu: ring sdma0 uses VM inv eng 0 on hub 1
[    2.680843] amdgpu 0000:05:00.0: amdgpu: ring vcn_dec uses VM inv eng 1 on hub 1
[    2.680844] amdgpu 0000:05:00.0: amdgpu: ring vcn_enc0 uses VM inv eng 4 on hub 1
[    2.680846] amdgpu 0000:05:00.0: amdgpu: ring vcn_enc1 uses VM inv eng 5 on hub 1
[    2.680848] amdgpu 0000:05:00.0: amdgpu: ring jpeg_dec uses VM inv eng 6 on hub 1
[    2.687810] [drm] Initialized amdgpu 3.38.0 20150101 for 0000:05:00.0 on minor 0
[   21.856546] input: SYNA30AD:00 06CB:CDEC Mouse as /devices/platform/AMDI0010:00/i2c-0/i2c-SYNA30AD:00/0018:06CB:CDEC.0001/input/input12
[   21.856700] input: SYNA30AD:00 06CB:CDEC Touchpad as /devices/platform/AMDI0010:00/i2c-0/i2c-SYNA30AD:00/0018:06CB:CDEC.0001/input/input13
[   22.158349] snd_hda_intel 0000:05:00.1: bound 0000:05:00.0 (ops amdgpu_dm_audio_component_bind_ops [amdgpu])
[   22.625722] EDAC amd64: F17h_M60h detected (node 0).
[   22.625766] EDAC amd64: Node 0: DRAM ECC disabled.
[   22.693339] EDAC amd64: F17h_M60h detected (node 0).
[   22.693412] EDAC amd64: Node 0: DRAM ECC disabled.
[   22.745697] EDAC amd64: F17h_M60h detected (node 0).
[   22.745753] EDAC amd64: Node 0: DRAM ECC disabled.
[   22.793348] EDAC amd64: F17h_M60h detected (node 0).
[   22.793412] EDAC amd64: Node 0: DRAM ECC disabled.
[   22.837399] EDAC amd64: F17h_M60h detected (node 0).
[   22.837459] EDAC amd64: Node 0: DRAM ECC disabled.
[   22.901411] EDAC amd64: F17h_M60h detected (node 0).
[   22.901471] EDAC amd64: Node 0: DRAM ECC disabled.
[   22.957364] EDAC amd64: F17h_M60h detected (node 0).
[   22.957425] EDAC amd64: Node 0: DRAM ECC disabled.
[   23.005153] EDAC amd64: F17h_M60h detected (node 0).
[   23.005206] EDAC amd64: Node 0: DRAM ECC disabled.

```

---

### Post by mastablasta on 2021-03-02
at this point they go sideways.

```
[COLOR=#000000][FONT=&quot][    0.610966] perf: AMD IBS detected (0x000003ff)
[/FONT][/COLOR][COLOR=#000000][FONT=&quot][    0.905959] AMD-Vi: AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>[/FONT][/COLOR]
```

i wonder... the old kernel had an error on vega 8 which should have been corrected by now. the old issue was that the drivers didn't load properly as they weren't assigned the correct amount of memory or moved to correct memory slot. something like that. as this chip uses onboard RAM, not it's own vram.

the sollution was to add iommu=soft code to the boot option. however the symptoms this manifest are different from yours. in other words you do get desktop loaded, but it looks and acts kind of strange. and this happens sometimes (not always) when you run on battery power only on laptop. but these lines where it starts behaving strange are suspicious and you could add this option as test to kernel.  

again i find this strange IOMMU issue to still be present in kernel when it was supposedly already fixed in 5.6, 5.5 or something like that. but since you were making some changes to defaults, you might have got it "working"?

---

### Post by sjpt2 on 2021-03-03
> **mastablasta said:**
> but these lines where it starts behaving strange are suspicious and you could add this option as test to kernel.

Yeah, that did not make a difference, unfortunately (or, perhaps, fortunately)

---

### Post by sjpt2 on 2021-03-05
Well, it looks like I could find the solution in BIOS. I had secure boot options set to "Legacy mode enabled and secure boot disabled", and changing it to "Legacy mode disabled and secure boot disabled" seems to have done the trick. At least for now. Unless I've been sleepwalking, I haven't changed those settings since before installation, so it's still confusing to me why it worked before, and why live USB worked sometimes (since my last report of it working, it stopped working again). But as long as it works I'm happy and I'm not going to look a gift horse in the mouth.

---

### Post by mastablasta on 2021-03-05
would it be possible that a firmware update caused this setting to change?

legacy off & secure boot off is correct/better option (unless you need secure boot).

---

### Post by sjpt2 on 2021-03-05
> **mastablasta said:**
> would it be possible that a firmware update caused this setting to change?

legacy off & secure boot off is correct/better option (unless you need secure boot).

I'm 99% certain it never changed since now a bunch of other live USB's that I tried before Xubuntu started working as well.

---

