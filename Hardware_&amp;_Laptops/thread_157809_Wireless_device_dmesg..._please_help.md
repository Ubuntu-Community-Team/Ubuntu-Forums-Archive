---
title: "Wireless device dmesg... please help"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by mrios on 2006-04-09
Could someone please help me troubleshoot for this wireless card I have? I am using an iBook dual USB running 5.10; I am trying to use a D-link DWL-g122 USB wireless card on my computer. I have followed the directions from this howto: [HOWTO: RALink 2570 usb wireless driver]("http://ubuntuforums.org/showthread.php?t=106846"). 

It is not working and I am not receiving useful advice. Here are some salient facts that might help someone discover what I am missing.


This is the dmesg of my system  when I plug in the USB device:

[INDENT]rtusb: probe of 2-1:1.0 failed with error -12
[ 4590.856611] usbcore: registered new driver rtusb
[ 5405.759475] usb 2-1: USB disconnect, address 3
[ 5409.134325] usb 1-1: new full speed USB device using ohci_hcd and address 2
[ 5409.401584] Device Descriptor not matching
[ 5409.401612] rtusb: probe of 1-1:1.0 failed with error -12[/INDENT]

The rt2570.ko driver is located in these directories:
[INDENT]/lib/modules/2.6.12/extra/rt2570.ko
/lib/modules/2.6.12-10-powerpc/kernel/drivers/net/wireless/rt2570.ko
/lib/modules/2.6.12-10-powerpc/drivers/rt2570.ko[/INDENT]

These are the configuration files that have been modified to make this driver run:
/etc/modutils/rt2570 exists and contains the single line "alias rausb0 rt2570".
/etc/modprobe.d/rt2570 exists and contains the single line "alias rausb0 rt2570".
/etc/modules contains the line "rt2570", insuring that the module is loaded on boot.

This is my wireless configuration file:

[INDENT]auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth0

iface eth0 inet dhcp

iface rausb0 inet dhcp
wireless-essid "something"
wireless-mode Managed
auto rausb0

auto eth0
[/INDENT]

When I try to load the rausb0 device, this is my error message:

[INDENT]sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
rausb0: ERROR while getting interface flags: No such device
rausb0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up rausb0.
[/INDENT]

These are all of the important facts that may have some bearing on the source of this problem.

Please help! I am lost here. Any help is appreciated.

---

### Post by mrios on 2006-04-11
I tried to install the linux port of the BSD driver set for this card. I have tried the dwl-g122 on OpenBSD and it worked fine. 

The port is still in alpha. It did not work for me; whereas the driver compiled correctly, it had conflicts with some settings in my kernel. This was part of the error output in the dmesg:

[INDENT][ 4256.201440] ural: disagrees about version of symbol ieee80211_chan2ieee
[ 4256.201447] ural: Unknown symbol ieee80211_chan2ieee
[ 4256.201646] ural: disagrees about version of symbol ieee80211_ioctl_siwretry
[ 4256.201654] ural: Unknown symbol ieee80211_ioctl_siwretry
[ 4256.201752] ural: disagrees about version of symbol ieee80211_ioctl_siwnickn
[ 4256.201760] ural: Unknown symbol ieee80211_ioctl_siwnickn
[ 4256.201867] ural: disagrees about version of symbol ieee80211_ioctl_siwscan
[ 4256.201875] ural: Unknown symbol ieee80211_ioctl_siwscan
[ 4256.201972] ural: disagrees about version of symbol ieee80211_ioctl_siwmode
[ 4256.201989] ural: Unknown symbol ieee80211_ioctl_siwmode
[ 4256.202085] ural: disagrees about version of symbol ieee80211_ioctl_getoptie
[ 4256.202092] ural: Unknown symbol ieee80211_ioctl_getoptie
[ 4256.202190] ural: disagrees about version of symbol ieee80211_ioctl_giwessid
[ 4256.202198] ural: Unknown symbol ieee80211_ioctl_giwessid
[ 4256.202293] ural: disagrees about version of symbol ieee80211_ioctl_giwscan
[ 4256.202300] ural: Unknown symbol ieee80211_ioctl_giwscan
[ 4256.202397] ural: disagrees about version of symbol ieee80211_crypto_encap
[ 4256.202405] ural: Unknown symbol ieee80211_crypto_encap
[ 4256.202560] ural: disagrees about version of symbol ieee80211_ioctl_siwessid
[ 4256.202568] ural: Unknown symbol ieee80211_ioctl_siwessid
[ 4256.202817] ural: disagrees about version of symbol ieee80211_ioctl_giwtxpow
[ 4256.202825] ural: Unknown symbol ieee80211_ioctl_giwtxpow [/INDENT]

Does anyone know a way that these errors can be worked around?

---

### Post by mrios on 2006-04-11
This is the link to the ural software: [http://etudiants.insia.org/~jbobbio/ural-linux/]("http://etudiants.insia.org/~jbobbio/ural-linux/")

---

