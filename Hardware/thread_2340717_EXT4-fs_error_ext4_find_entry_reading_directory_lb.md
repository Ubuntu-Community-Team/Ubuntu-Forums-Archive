---
title: "EXT4-fs error ext4_find_entry reading directory lblock 0"
date: 2016-10-21
forum: Hardware
---

### Post by Kornelia on 2016-10-21
Hello

I installed Ubuntu 16.04 system on a USB flash drive (brand new Samsung USB 3.0 64GB) so that I can easily switch between OS (and not have to carry big external HDD with me on which the system I'm using is now).
I've been experiencing various problems with that new installation. I re-installed it about 7 times, trying different methods/iso  but with no luck. I've also tried numerous suggestions on forums. Some of them worked but I still have 1 issue that I can't resolve. 

Anyway...

Initially I kept getting Input/Output errors which I solved with:
```

for i in /sys/bus/usb/devices/*/power/autosuspend; do echo 2 > $i; done
for foo in /sys/bus/usb/devices/*/power/level; do echo on > $foo; done

```


Also boot kept dropping to initramfs:
I managed to 'solve' it using 
```

root=/dev/sdb1

```
Although I've only just realised it probably should have been 'root=/dev/sda1'
I got mislead since it was sdb1 partition when I was initially installing the system but from flash drive's perspective it's sda1. I'm looking into how to correct it.

The issue I don't seem to be able to resolve is disappearing launcher, menus etc...
I tried to solve this by installing laptop-mode and adding the ID of the flash drive to ```
/etc/laptop-mode/conf.d/runtime-pm.conf
``` file within ```
AUTOSUSPEND_RUNTIME_DEVID_BLACKLIST=""
``` but it didn't seem to work. 

When the launcher and other elements disappear after I press Ctrl+Alt+F1 and after I type in my username name I get this type of errors
```

EXT4-fs error (device sda1): ext4_find_entry:1450 inode #number: comm systemd-udevd: reading directory lblock 0

```
 Shortly after that the screen goes blank with a single _ blinking.

To get out of that I force shut down my laptop. 

I would appreciate any help with this issue.
[FONT=Verdana]
[/FONT]
[FONT=Verdana]
[/FONT]

---

### Post by jmindreau on 2017-09-23
similar problem here...
using new hp AMD A8-8600 portable with standard 500GB hard disk and SSD M2 SATA 2280 128GB Kingston
dual boot Win10/ubuntu 16.04, boot partition on EFI primary disk (500GB) and ubuntu root and home in 128GB (both fresh and licensed installation)
The problem appears after switching from one screen (main laptop screen) to DisplayPort interface using DisplayPort adapter to HDMI -> cable -> TV or LCD projector...
system hangs...
then, after freeze, and similar EXT4-fs error message, you need to hard power off the computer, and restart one or two times, entering display settings to reset to one-screen display only, reboot and goes-on again...
any information on how to resolve this, will be appreciated.
I suppose the problem was on how this 'new' installation goes, using now the standard 500GB as dual and boot disk and ubuntu root and home installation on M2 SATA.  Months ago this equipment was installed using the root and dualboot installation using a fast SSD main internal disk (sda), where ubuntu was installed, and win10 on sdb (m2sata) and with that configuration, this situation or problem never shows...
and we are using the display port and adapters several times...
Im not an expert, but i feel this is very strange...
any help, or info, welcome!

---

