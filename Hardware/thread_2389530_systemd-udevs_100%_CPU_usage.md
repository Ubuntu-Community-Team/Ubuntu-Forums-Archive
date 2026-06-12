---
title: "systemd-udevs 100% CPU usage"
date: 2018-04-18
forum: Hardware
---

### Post by corsairetc on 2018-04-18
Hello I am running Ubuntu 18.04 x64. Everytime I turn on wifi CPU usage is 100% by process:
```
/lib/systemd/systemd-udevd
```
If I turn wifi card off system resources is normal. Lan network is not affected this problem only wifi is. 
My wifi card model is:
```
description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:0c:00.0
       logical name: wlp12s0
       version: 00
       serial: 00:XXXXXX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-15-generic firmware=8.83.5.1 build 33692 ip=192.168.3.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:26 memory:f69fe000-f69fffff
```

What could be wrong ? 
Thank you for help.

---

### Post by kerry_s on 2018-04-18
are you using a external mouse?
if so then try disabling the touchpad in settings-> devices-> mouse

just remembered sometimes it's bluetooth, you can try disabling that.

a reboot might be required.

---

### Post by corsairetc on 2018-04-18
Thank you lot. It was bluetooth I disable the blootooth and now it is ok.

---

### Post by kerry_s on 2018-04-18
welcome to testing, glad it's okay now. hope the fix by release.

---

### Post by hhemken on 2018-04-27
Wasn't fixed by release day, but turning off bluetooth is a viable workaround. Unless you need bluetooth.

---

### Post by aarcos on 2018-05-17
thanks, turnoff bluetooth and now it is ok.

---

### Post by ysg2 on 2018-09-13
Instead of turning off bluetooth, try stopping and starting soon after booting by running the following commands-

sudo systemctl stop systemd-udevd systemd-udevd-kernel.socket systemd-udevd-control.socket

sudo systemctl start systemd-udevd systemd-udevd-kernel.socket systemd-udevd-control.socket

It has worked in my laptop and all the problems are gone.

---

