---
title: "RT5572 Wireless Adapter Using rt2x00usb kernel module"
date: 2014-11-26
forum: Hardware
---

### Post by a_poenaru on 2014-11-26
Hello.

I've recently bought a TP-Link TL-WDN3200 N600 Wireless Adapter. It uses an RT5572 chip, as shown by lsusb:
```
andrei@Y510p:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 8087:07da Intel Corp. 
Bus 003 Device 005: ID 148f:5572 Ralink Technology, Corp. RT5572 Wireless Adapter
Bus 003 Device 003: ID 062a:4102 Creative Labs 
Bus 003 Device 002: ID 174f:1474 Syntek 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I've done some research before buying it and there is a driver you can download and compile for this network hard. However, as soon as I plugged it into my computer running Ubuntu 14.10, it was automatically recognised without me compiling and installing the modules. It works just fine and I'm posting this message using it. However, it appears to be using some different driver:
```
andrei@Y510p:~$ lsmod | grep rt
rt2800usb              27139  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              93180  1 rt2800usb
rt2x00lib              55170  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              12707  1 rt2800lib
mac80211              660592  4 rt2x00lib,rt2x00usb,rt2800lib,iwldvm
cfg80211              510218  4 iwlwifi,mac80211,rt2x00lib,iwldvm
```

Is this a case for concern? Could bad things happen if I leave it like this? :D  I could compile the driver, but that needs some work to be done first, and it seems there's no reason to do it right now. Has anyone else had this kind of experience?

Thanks!

---

### Post by carmine3 on 2014-12-23
Same risult for me with auto device recognize:

```

root@mail:/home/admini# lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:5572 Ralink Technology, Corp. RT5572 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

root@mail:/home/admini# lsmod | grep rt
xfrm4_mode_transport    12631  0
xfrm6_mode_transport    12631  0
virtio_rng             13027  0
rt2800usb              27380  0
rt2x00usb              20886  1 rt2800usb
rt2800lib              95492  1 rt2800usb
rt2x00lib              56170  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              687021  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              521225  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib
parport                42481  1 lp

```

Device is stable but is very slow. I reached the same performace of [Mediacom driver ]("http://bernaerts.dyndns.org/linux/74-ubuntu/229-ubuntu-precise-dlink-dwa160-revb2")up to 3.9 Mb/s on AP configuration:
/etc/hostapd/hostapd.conf
```

interface=wlan0
driver=nl80211
hw_mode=g
channel=11
country_code=IT
ieee80211n=1
wmm_enabled=1


ssid=MySSID
auth_algs=1
wpa=2
wpa_key_mgmt=WPA-PSK
rsn_pairwise=CCMP
wpa_passphrase=secretpass

```


Ubuntu server
```

root@mail:/home/admini# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty

```

with last kernel
```

root@mail:/home/admini# uname -r
3.16.0-031600-generic

```

Can somebody able to run a better RX/TX rate?

---

