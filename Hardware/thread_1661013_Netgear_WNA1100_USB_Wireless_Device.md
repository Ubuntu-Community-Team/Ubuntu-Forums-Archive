---
title: "Netgear WNA1100 USB Wireless Device"
date: 2011-01-06
forum: Hardware
---

### Post by WhiteDwarf on 2011-01-06
Lucid Lynx 10.04

Laptop Compaq Evo N620C.

lsusb output:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9030 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Lines added to etc/modprobe.d/blacklist.conf:

blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist ath_pci
blacklist ath_hal

Using drivers from a 32bit Windows 7 installation, as Netgear now wrap up their drivers in a setup program. 

athur.sys 2.0.0.36
netathur.inf  

ndiswrapper -l output:

netathur : driver installed
    device (0846:9030) present

BUT

/var/log/messages:

Jan  6 08:19:25 gil-laptop kernel: [  222.945077] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Jan  6 08:19:25 gil-laptop kernel: [  223.124082] usb 1-1: reset high speed USB device using ehci_hcd and address 2
Jan  6 08:19:25 gil-laptop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver netathur
Jan  6 08:19:25 gil-laptop kernel: [  223.373278] usbcore: registered new interface driver ndiswrapper

I tried to set up a wireless connection in System -> Preferences -> Network Connections but
iwconfig outputs:
lo        no wireless extensions.

eth0      no wireless extensions.

- which leads me to believe am wasting my time until I solve 'couldn't load driver netathur'.

Is it because the drivers came from Windows 7 ?  Does anybody have XP drivers they could send me ?

I know others have got this device working, and I have searched all known threads, tried everything but recompiling ndiswrapper and I'm out of options.  Can anybody help ?

---

### Post by koanhead on 2011-02-22
Have you seen this thread?

[http://ubuntuforums.org/showthread.php?t=1663232](http://ubuntuforums.org/showthread.php?t=1663232)

---

### Post by WhiteDwarf on 2011-02-24
Yes, thanks Koanhead.  The USB device works fine now.

---

