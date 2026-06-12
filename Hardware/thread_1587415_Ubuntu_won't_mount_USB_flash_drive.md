---
title: "Ubuntu won't mount USB flash drive"
date: 2010-10-03
forum: Hardware
---

### Post by MacDaddy1660B on 2010-10-03
Hi all,

Let's begin this yelp with a story. I lent my 16GB OCA Rally 2 flash drive to a friend to use. He plugged it into his brand new ASUS compact notebook to get some files off of it. For some reason, while he was using it, it stopped working. He tried plugging it into a desktop machine we have in the office and then into my computer. The thing doesn't work anymore.

When I run dmesg after plugging it in, I get the following output:
```
[  233.475963] usb 2-1.2: new high speed USB device using ehci_hcd and address 4
[  248.508945] usb 2-1.2: device descriptor read/64, error -110
[  263.655370] usb 2-1.2: device descriptor read/64, error -110
[  263.844889] usb 2-1.2: new high speed USB device using ehci_hcd and address 5
[  278.881620] usb 2-1.2: device descriptor read/64, error -110
[  294.028063] usb 2-1.2: device descriptor read/64, error -110
[  294.217430] usb 2-1.2: new high speed USB device using ehci_hcd and address 6
[  304.607372] usb 2-1.2: device not accepting address 6, error -110
[  304.691145] usb 2-1.2: new high speed USB device using ehci_hcd and address 7
[  315.077260] usb 2-1.2: device not accepting address 7, error -110
[  315.077393] hub 2-1:1.0: unable to enumerate USB device on port 2

```When I run ```
cat /var/log/syslog
```, I get something very similar:
```
Oct  3 09:58:12 system76-pc kernel: [  233.475963] usb 2-1.2: new high speed USB device using ehci_hcd and address 4
Oct  3 09:58:27 system76-pc kernel: [  248.508945] usb 2-1.2: device descriptor read/64, error -110
Oct  3 09:58:42 system76-pc kernel: [  263.655370] usb 2-1.2: device descriptor read/64, error -110
Oct  3 09:58:42 system76-pc kernel: [  263.844889] usb 2-1.2: new high speed USB device using ehci_hcd and address 5
Oct  3 09:58:58 system76-pc kernel: [  278.881620] usb 2-1.2: device descriptor read/64, error -110
Oct  3 09:59:13 system76-pc kernel: [  294.028063] usb 2-1.2: device descriptor read/64, error -110
Oct  3 09:59:13 system76-pc kernel: [  294.217430] usb 2-1.2: new high speed USB device using ehci_hcd and address 6
Oct  3 09:59:23 system76-pc kernel: [  304.607372] usb 2-1.2: device not accepting address 6, error -110
Oct  3 09:59:23 system76-pc kernel: [  304.691145] usb 2-1.2: new high speed USB device using ehci_hcd and address 7
Oct  3 09:59:34 system76-pc kernel: [  315.077260] usb 2-1.2: device not accepting address 7, error -110
Oct  3 09:59:34 system76-pc kernel: [  315.077393] hub 2-1:1.0: unable to enumerate USB device on port 2

```For reference, other USB drives DO work on my laptop (a system 76 Pangolin Performance laptop). This particular drive doesn't work on any other computers that I have plugged it into (Windows, Mac, Linux).

Any help would be appreciated. I have some important data on this drive, so formatting would be an extreme last resort. Thanks.

---

