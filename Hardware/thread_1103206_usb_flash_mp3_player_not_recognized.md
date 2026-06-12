---
title: "usb flash mp3 player not recognized"
date: 2009-03-22
forum: Hardware
---

### Post by m4lte on 2009-03-22
Hi guys,
I have an old fashioned usb flash mp3 player (Creative Nomad Muvo 128MB), which used to show up in my file browser like any usb-drive when I connected it. Recently I formatted the drive and now it's not being recognized anymore. Neither on Ubuntu nor Windows. When I plug it into the usb, nothing happens.


I'm not sure what happened. I suspect there's something wrong with the formatting of the drive or the player's firmware. **Is there a way how I can force ubuntu to detect it?** Maybe formatting it again would help.


thanks for your help. I hope I don't have to throw away my good old mp3 player just because of a software problem. :(

---

### Post by prshah on 2009-03-22
> **m4lte said:**
> When I plug it into the usb, nothing happens.


Plug it in, open a terminal (Applications-Accessories-Terminal) and give the command```
sleep 10 && dmesg | tail
lsusb
``` Post back the output; it may contain diagnostic information we can use to resolve this.

---

### Post by m4lte on 2009-03-22
Hi prshah. I did as you suggested. Here is the output:

```
malte@malte-laptop:~$ sleep 10 && dmesg | tail
[   97.784285] Monitor-Mwait will be used to enter C-3 state
[   98.036092] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   98.189403] usb 1-1: configuration #1 chosen from 1 choice
[  122.365218] NET: Registered protocol family 10
[  122.367722] lo: Disabled Privacy Extensions
[  122.370260] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  133.276523] wlan0: no IPv6 routers present
[  375.144245] usb 1-1: USB disconnect, address 2
[ 5847.697513] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 7061.325433] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

malte@malte-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 08ff:2810 AuthenTec, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root
```

Afterwards I entered the same commands without the usb-player plugged in, and with the player plugged into another usb port. The output was exactly the same. I had no other external usb devices connected while running the commands.


Then I tried holding the player's play-button while plugging it in. (This used to be necessary when recovering the player on Windows after it had crashed.) Now I get got the following output:

```
malte@malte-laptop:~$ sleep 10 && dmesg | tail
[   98.189403] usb 1-1: configuration #1 chosen from 1 choice
[  122.365218] NET: Registered protocol family 10
[  122.367722] lo: Disabled Privacy Extensions
[  122.370260] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  133.276523] wlan0: no IPv6 routers present
[  375.144245] usb 1-1: USB disconnect, address 2
[ 5847.697513] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 7061.325433] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 7729.868663] usb 5-2: new full speed USB device using uhci_hcd and address 2
[ 7730.023399] usb 5-2: configuration #1 chosen from 1 choice
malte@malte-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 066f:3410 SigmaTel, Inc. STMP3410 D-Major MP3 Player
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 08ff:2810 AuthenTec, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by m4lte on 2009-04-17
push

---

