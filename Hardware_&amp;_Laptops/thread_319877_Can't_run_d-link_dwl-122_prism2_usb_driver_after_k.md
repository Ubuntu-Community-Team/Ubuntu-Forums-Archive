---
title: "Can't run d-link dwl-122 prism2_usb driver after kernel update 2.6.17"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by mhoffman on 2006-12-16
Hi,
 
  my usb wireless stick doesn't work anymore. I am pretty sure  du to the kernel upgrade

```
2006-12-14 00:10:17 status installed linux-image-2.6.17-10-386 2.6.17.1-10.34
```
from /var/log/dpkg.log


my usb wlan stick d-link dwl-122 stopped working.

previously it ran very nicely w/ udev and linux-wlan-ng drivers. My /etc/network/interfaces

```

iface wlan0 inet static
pre-up /usr/local/sbin/prism-up wlan0
    wireless_mode managed
    wireless_enc on
    wlan_ng_key 39343735383336303039323932
    wlan_ng_authtype opensystem

    wireless_keymode open
    netmask 255.255.255.0
    address 192.168.178.13
    gateway 192.168.178.1
    wireless-essid hubertus1
    wireless-key open
auto wlan0


```

where the line 
```
pre-up /usr/local/sbin/prism-up wlan0
```

refers to a file w/

```

wlanctl-ng $1 lnxreq_ifstate ifstate=enable
wlanctl-ng $1 lnxreq_autojoin ssid=xxx authtype=opensystem
wlanctl-ng $1 dot11req_mibset mibattribute=dot11WEPDefaultKey0=xxx

```


this went as said above nicely until 3 days ago.

if I run 
```
ifup wlan0
```

I get

```

wlanctl-ng: No such device
wlanctl-ng: No such device
wlanctl-ng: No such device
Failed to bring up wlan0.


```

and when I run /etc/init.d/wlan restart which is run by ifup and when the stick is entered

```

wlan0: FEHLER beim Auslesen der Schnittstellenmerker: No such device

Starting WLAN Devices: Error: Device wlan0 does not seem to be present.
Make sure you've inserted the appropriate
modules or that your modules.conf file contains
the appropriate aliase(s).


```

even though my  /etc/modprobe.d/aliases contain the following line

```

alias wlan0 prism2_usb

```


is this workaround no longer supported? Is there a better way now? What can I do to get my wireless card working again?

Take care,
Max.

---

### Post by mhoffman on 2006-12-25
Merry Christmas!

No idea anyone? Now I made a  fresh install of  edgy on a  different  partition. I installed linux-wlang-ng. But it didn't help.

When I   run dmesg I find a couple of lines like 

```

[17179579.476000] PCI: cache line size of 64 is not supported by device 0000:00:03.2
[17179579.476000] ehci_hcd 0000:00:03.2: irq 185, io mem 0xcffff000
[17179579.476000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.476000] usb usb3: configuration #1 chosen from 1 choice
[17179579.476000] hub 3-0:1.0: USB hub found
[17179579.476000] hub 3-0:1.0: 6 ports detected
[17179579.664000] Attempting manual resume
[17179579.692000] kjournald starting.  Commit interval 5 seconds
[17179579.692000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.160000] ohci_hcd 0000:00:03.0: wakeup
[17179580.624000] usb 1-3: new full speed USB device using ohci_hcd and address 3
[17179580.804000] usb 1-3: device descriptor read/64, error -110
[17179581.088000] usb 1-3: device descriptor read/64, error -110
[17179581.368000] usb 1-3: new full speed USB device using ohci_hcd and address 4
[17179581.548000] usb 1-3: device descriptor read/64, error -110
[17179581.832000] usb 1-3: device descriptor read/64, error -110
[17179582.112000] usb 1-3: new full speed USB device using ohci_hcd and address 5
[17179582.520000] usb 1-3: device not accepting address 5, error -110
[17179582.696000] usb 1-3: new full speed USB device using ohci_hcd and address 6
[17179583.104000] usb 1-3: device not accepting address 6, error -110
[17179583.408000] usb 2-3: new full speed USB device using ohci_hcd and address 2
[17179583.624000] usb 2-3: configuration #1 chosen from 1 choice


```
What does this tell me?

Is this maybe a bug in  the kernel module?

Take care,
Max.

---

