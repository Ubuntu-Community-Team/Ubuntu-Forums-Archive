---
title: "printer service fails to start"
date: 2020-03-27
forum: Hardware
---

### Post by roberto-ranzani on 2020-03-27
First  post for me, sorry if unappropriate.

My installation of 19.10 worked OK, until I made probably some error trying to configure CUPS. Now no printer service available.

In configuration>devices>printers I see: 
"Sorry! the system printing printer service doesn't seems to be available"

in LOG I see:```
10:01:26 colord-sane: io/hpmud/musb.c 2101: Invalid usb_open: Permission denied
10:01:20 kernel: sd 3:0:0:0: [sdc] Assuming drive cache: write through
09:49:41 colord-sane: io/hpmud/musb.c 2101: Invalid usb_open: Permission denied
09:49:34 kernel: xhci_hcd 0000:39:00.0: HC died; cleaning up
09:49:01 colord-sane: io/hpmud/musb.c 2101: Invalid usb_open: Permission denied
09:47:48 gdm-session-wor: gkr-pam: unable to locate daemon control file
09:47:46 systemd: Failed to start Configure Plugged-In Printer.
09:47:45 colord-sane: io/hpmud/musb.c 2101: Invalid usb_open: Permission denied
09:47:45 colord-sane: io/hpmud/musb.c 2101: Invalid usb_open: Permission denied
09:47:45 colord-sane: io/hpmud/musb.c 2101: Invalid usb_open: Permission denied
09:47:45 colord-sane: io/hpmud/musb.c 2101: Invalid usb_open: Permission denied
09:47:41 systemd: Failed to start Configure Plugged-In Printer.
09:47:41 systemd: Failed to start Configure Plugged-In Printer.
09:47:36 systemd: Failed to start CUPS Scheduler.
09:47:32 kernel: Initramfs unpacking failed: Decoding failed
```


tried to reinstall CUPS with Synaptic, but no changes

maybe is a side effect of "initramfs unpacking failed"?  where to investigate?

thanks in advance for any contribution
Roberto

---

### Post by Autodave on 2020-03-27
Please give us some info on your equipment, especially the printer.  How is printer connected to the PC: wirelessly, ethernet cable, USB?

---

### Post by slickymaster on 2020-03-27
Thread moved to **Hardware** for a better fit

---

### Post by roberto-ranzani on 2020-03-27
> **Autodave said:**
> Please give us some info on your equipment, especially the printer.  How is printer connected to the PC: wirelessly, ethernet cable, USB?

Thanks for reply

it is HW independent: both Canon and HP printers was working OK before the service failed to start, I did'nt change printer.   I'm not sure it is an HW issue

Roberto

---

### Post by oldfred on 2020-03-27
I am using 20.04 and have similar printer issue with USB HP printer.
I initially unplugged USB and printed using Wi-Fi.

It may be something about printer configured twice once IPv4 & IPv6, but not sure. 
Changed settings to turn off IPv6, and it works, but have to release it twice?

Printer bug
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1826159](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1826159)
[https://launchpad.net/ubuntu/+source/cups/+bugs](https://launchpad.net/ubuntu/+source/cups/+bugs)
[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/1099184](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/1099184)

---

