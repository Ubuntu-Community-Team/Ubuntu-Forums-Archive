---
title: "ubuntu 5.04 on Toshiba Satellite A80"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by mitropank on 2005-05-23
Hi everyone, i've problems installing Ubuntu 5.04 on my new Toshiba Satellite A80 laptop.

It's a centrino 730 sonoma, here some specifics:

Sound: Realtek ALC250
VGA: Nvidia 6200go
Modem: Softmodem (Lucent SCORPIO)
IrDA: Super IO SMSC LPC47N217
PCMCIA: Texas Instruments PCI 7421
Bluetooth: TAIYO-YUDEN (CSR)
Firewire: Texas Instruments PCI 7421
Mouse: PS2
ACPI: V1.0b
Network: Marvell 88E8036
Wireless: Intel PRO/Wireless 2200BG

I've booted using acpi=off and pcmcia=off parameters as suggested by some users searching on google,
because it freezes when search to recognise the pcmcia. the installation find only the wireless card (not the marvell wired card) but i'm not able to connect because support only wep encryption (i use wpa).
when installation is finished, and it go to the login screen of gnome the system freezes, i hear audio in loop for 2 seconds and also the cursor, moves for 2 seconds and then is blocked, then i can do nothing... :-(

Any advice?

---

### Post by luca_linux on 2005-05-23
For ipw2200 and wpa just follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by mitropank on 2005-05-23
[QUOTE=luca_linux]For ipw2200 and wpa just follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)[/QUOTE]

tnx, i've just seen this guide, but my problem is the freeze of system....    ](*,)

---

### Post by luca_linux on 2005-05-23
Try to pass the parameter "nolapic" at boot.

---

### Post by mitropank on 2005-05-23
[QUOTE=luca_linux]Try to pass the parameter "nolapic" at boot.[/QUOTE]

va lo stesso in freeze..  ](*,)   ma c'e' qualche log che posso guardare per vedere cosa succede?

---

### Post by luca_linux on 2005-05-23
Try: > sudo cat /var/log/acpid

---

### Post by luca_linux on 2005-05-23
Also try:
> dmesg | grep acpi
and
> dmesg

---

### Post by luca_linux on 2005-05-23
And make sure you have the modules "toshiba.ko" and "toshiba_acpi.ko" loaded:
> lsmod | grep toshiba
If not, load them:
> modprobe toshiba.ko > modprobe toshiba_acpi.ko

---

### Post by mitropank on 2005-05-23
there is no /var/log/acpid on the system

dmesg | grep acpi :

```

Kernel command line: root=/dev/sda7 ro acpi=off pcmcia=off lapic=off single
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001


``` 

dmesg is too long, i attached on the message  :) 

if i do lsmod | grep toshiba  there is nothing and there aren't toshiba.ko and toshiba_acpi.ko

I think is interesting the log of gdm:

```


X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 root@terranova.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux cosmos 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686
Build Date: 05 April 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 23 21:04:11 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Synaptics Touchpad no synaptics event device found (checked 5 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0


```

---

### Post by luca_linux on 2005-05-24
Remove "acpi=off" and see /var/log/acpid and if those modules are loaded. If not, try to load them manually and let me know what happens.
Why are you booting in single mode? And why are you using ramdisk?

---

