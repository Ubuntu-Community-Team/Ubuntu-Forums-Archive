---
title: "Bluetooth dongle"
date: 2014-06-29
forum: Hardware
---

### Post by kuckunniwi on 2014-06-29
Hi all!

Am trying to get my "Cambridge Silicon Radio, Ltd Bluetooth Dongle" working under Kubuntu 14.04 amd64, but there's no way. 

Kubuntu actually detects the device, but from there to it actually working....
```

$ lsusb
Bus 001 Device 004: ID 8086:0189 Intel Corp. 
Bus 001 Device 003: ID 174f:143f Syntek 
Bus 001 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```

$ hciconfig
hci1:   Type: BR/EDR  Bus: USB
        BD Address: 00:1A:7D:DA:71:08  ACL MTU: 310:10  SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:606 acl:0 sco:0 events:36 errors:0
        TX bytes:939 acl:0 sco:0 commands:36 errors:0

hci0:   Type: BR/EDR  Bus: USB
        BD Address: 88:53:2E:84:02:A0  ACL MTU: 310:10  SCO MTU: 64:8
        DOWN 
        RX bytes:507 acl:0 sco:0 events:23 errors:0
        TX bytes:329 acl:0 sco:0 commands:22 errors:0
```

I'm attempting to use *this* as opposed to my laptop's integrated bluetooth, because for streaming music to a bluetooth receiver, the integrated BT is worthless, being a shared wifi/BT card (choppy, constant dropouts, etc.)

When configuring bluetooth, the system actually lists both BT adapters. I power off the integrated one and leave USB adapter on, but using USB dongle, it can't even manage to find my bluetooth receiver (which is in discoverable mode, of course). There are actually a couple of bug reports ([1]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1221995"), [2]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1314621")) for this particular dongle in 14.04, but there don't appear to be any "quick fixes" as of yet. 

Does anyone know of a quick workaround?

Thanks!!!

---

### Post by jeremy31 on 2014-06-29
> **kuckunniwi said:**
> Hi all!

Am trying to get my "Cambridge Silicon Radio, Ltd Bluetooth Dongle" working under Kubuntu 14.04 amd64, but there's no way. 

Kubuntu actually detects the device, but from there to it actually working....
```

$ lsusb
Bus 001 Device 004: ID 8086:0189 Intel Corp. 
Bus 001 Device 003: ID 174f:143f Syntek 
Bus 001 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```

$ hciconfig
hci1:   Type: BR/EDR  Bus: USB
        BD Address: 00:1A:7D:DA:71:08  ACL MTU: 310:10  SCO MTU: 64:8
        UP RUNNING PSCAN ISCAN 
        RX bytes:606 acl:0 sco:0 events:36 errors:0
        TX bytes:939 acl:0 sco:0 commands:36 errors:0

hci0:   Type: BR/EDR  Bus: USB
        BD Address: 88:53:2E:84:02:A0  ACL MTU: 310:10  SCO MTU: 64:8
        DOWN 
        RX bytes:507 acl:0 sco:0 events:23 errors:0
        TX bytes:329 acl:0 sco:0 commands:22 errors:0
```

I'm attempting to use *this* as opposed to my laptop's integrated bluetooth, because for streaming music to a bluetooth receiver, the integrated BT is worthless, being a shared wifi/BT card (choppy, constant dropouts, etc.)

When configuring bluetooth, the system actually lists both BT adapters. I power off the integrated one and leave USB adapter on, but using USB dongle, it can't even manage to find my bluetooth receiver (which is in discoverable mode, of course). There are actually a couple of bug reports ([1]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1221995"), [2]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1314621")) for this particular dongle in 14.04, but there don't appear to be any "quick fixes" as of yet. 

Does anyone know of a quick workaround?

Thanks!!!

It says it is fixed upstream, so a newer kernel should work

```
[COLOR=#2E8B57][FONT=Monaco]wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15.2-utopic/linux-headers-3.15.2-031502-generic_3.15.2-031502.201406261639_amd64.deb[/FONT][/COLOR]
```
```
[COLOR=#2E8B57][FONT=Monaco]wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15.2-utopic/linux-headers-3.15.2-031502_3.15.2-031502.201406261639_all.deb[/FONT][/COLOR]
```
```
[COLOR=#2E8B57][FONT=Monaco]wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15.2-utopic/linux-image-3.15.2-031502-generic_3.15.2-031502.201406261639_amd64.deb[/FONT][/COLOR]
```
```
[COLOR=#2E8B57][FONT=Monaco]sudo dpkg -i linux-*-3.15.2*.deb[/FONT][/COLOR]
```

and reboot

---

### Post by kuckunniwi on 2014-06-29
Thanks a ton! I'll try that right away!

---

### Post by kuckunniwi on 2014-06-30
Thanks for your reply, but I've decided to postpone it for now. The last time I started playing around with upstream kernels I ending up having to do a fresh install (I don't expect 24/7 tech support to help me get my laptop up & running if this upstream solves *this* particular issues but doesn't get along with other, more vital system components). This is my work laptop, and I can't afford to have it down for even 1/2 a day...I guess I'll just stick to minijack cable for the time being.

All the same, thanks for taking the time to reply :)

---

### Post by jeremy31 on 2014-06-30
I had kernel updates that wouldn't boot and if wasn't for the grub option of advanced ubuntu options or previous linux versions, I would have been down for a while

---

### Post by kuckunniwi on 2014-06-30
Yeah, I just can't afford to play around with anything that might compromise overall system stability. Self-employed translator...if my computer's down, it's a ROYAL pain in the ass. Not going to risk it, for the time being, just to free myself on one extra cable :P

On the other hand...it's a pity that bluetooth is so unreliable, in general, in Kubuntu (and has been for several releases). I managed to sync audio in 13.10, but it involved installing blueman, padevchooser and a bunch of extra pulseaudio modules that later had to be messed around with before anything worked at all. I pray for the day BT audio will be out-of-the box, like everything else!

---

