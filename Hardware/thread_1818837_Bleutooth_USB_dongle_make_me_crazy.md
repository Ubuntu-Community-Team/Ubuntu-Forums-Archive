---
title: "Bleutooth USB dongle make me crazy"
date: 2011-08-05
forum: Hardware
---

### Post by dubis on 2011-08-05
[FONT=Arial][SIZE=2]Hello Guys,

This is my epic story for enable my Bluetooth USB dongle. 
I've an ASUS  eepc T101MT without Bluetooth built in with kubuntu 11.04 installed inside. So I bought a Bluetooth USB dongle. This last one works under Windows 7 and Boodhi Linux (like UBUNTU 10.10 with E17). 

So I downgraded my Kubuntu 11.4 to 10.10 and the bleutooth dongle worked, until I installed the eepc package as described in this documentation :
[https://help.ubuntu.com/community/T101MT](https://help.ubuntu.com/community/T101MT)
I don't know why the bluetooth management disipear, after installing these packages. So I investigated [/SIZE][/FONT][FONT=Arial][SIZE=2]the problem and I found these package don't disturb the bleutooth :[/SIZE][/FONT][FONT=Arial][SIZE=2]
eeepc-brightness-workaround egalax-multitouch-driver-common

And these ones disturb the bluetooth :
eepc-touchpad-twofingers eeepc-acpi-workaround eeepc-powersave

So I purge them and the bluetooth is back. I decided to upgrade my release 10.10 to 11.04, and one more time I lost my bluetooth management[/SIZE][/FONT].

```

user@T101MT:~$ hcitool dev
Devices:
user@T101MT:~$ dmesg | tail
[  535.473583] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  546.030042] wlan0: no IPv6 routers present
[  947.790218] usb 2-1: USB disconnect, address 3
[  952.510127] usb 2-1: new full speed USB device using uhci_hcd and address 4
[  952.662100] usb 2-1: device descriptor read/all, error -71
[  952.780157] usb 2-1: new full speed USB device using uhci_hcd and address 5
[ 1042.040197] usb 2-1: USB disconnect, address 5
[ 1044.870130] usb 2-1: new full speed USB device using uhci_hcd and address 6
[ 1045.022139] usb 2-1: device descriptor read/all, error -71
[ 1045.140107] usb 2-1: new full speed USB device using uhci_hcd and address 7
user@T101MT:~$ 

```Someone knows what's happen ??
Thanks for your help .....[SIZE=3]
[/SIZE]

---

### Post by dubis on 2011-08-08
Hi, 

I found solution here : 
[http://ubuntuforums.org/showthread.php?t=1661879](http://ubuntuforums.org/showthread.php?t=1661879)

Thanks

---

