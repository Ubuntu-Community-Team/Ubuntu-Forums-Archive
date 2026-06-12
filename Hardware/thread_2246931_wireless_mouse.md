---
title: "wireless mouse"
date: 2014-10-04
forum: Hardware
---

### Post by david298 on 2014-10-04
Dear All,
I am strugling with my new Wireless Mouse (vivanco) , it doesn't work in ubuntu 14. would you please advice me, if you need more information please let me know.below you see two different commands and their resutls.


[HTML]
ThinkPad-Edge-E531:/etc$ dmesg | tail -20
[   25.048993] r8169 0000:05:00.0 eth1: link down
[   25.049017] r8169 0000:05:00.0 eth1: link down
[   25.049040] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.049570] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.945073] init: samba-ad-dc main process (1152) terminated with status 1
[   26.752715] r8169 0000:05:00.0 eth1: link up
[   26.752723] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   53.012522] audit_printk_skb: 132 callbacks suppressed
[   53.012525] type=1400 audit(1412429533.947:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2161 comm="apparmor_parser"
[   53.012530] type=1400 audit(1412429533.947:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2161 comm="apparmor_parser"
[   53.012850] type=1400 audit(1412429533.947:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2161 comm="apparmor_parser"
[  517.297082] usb 1-1.2: USB disconnect, device number 3
[  569.261171] usb 1-1.2: new low-speed USB device number 6 using ehci-pci
[  569.357928] usb 1-1.2: New USB device found, idVendor=04f3, idProduct=02f4
[  569.357936] usb 1-1.2: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[  569.357939] usb 1-1.2: Product: 2.4G Wireless Mouse
[  569.361898] input: 2.4G Wireless Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input15
[  569.362317] hid-generic 0003:04F3:02F4.0002: input,hiddev0,hidraw0: USB HID v1.11 Mouse [2.4G Wireless Mouse] on usb-0000:00:1a.0-1.2/input0
[  601.242970] systemd-hostnamed[3036]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 1000.878960] systemd-hostnamed[3378]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!



ThinkPad-Edge-E531:/etc$ grep -i mouse /var/log/dmesg
[    2.508027] mousedev: PS/2 mouse device common for all mice
[    3.325691] usb 1-1.2: Product: 2.4G Wireless Mouse
[    3.334573] input: 2.4G Wireless Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input6
[    3.334693] hid-generic 0003:04F3:02F4.0001: input,hiddev0,hidraw0: USB HID v1.11 Mouse [2.4G Wireless Mouse] on usb-0000:00:1a.0-1.2/input0
[    3.566311] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd001a3/0x940300/0x127c00, board id: 2722, fw id: 1484859
[    3.566317] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[    8.041839] psmouse serio2: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[    9.902779] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3


[/HTML]

---

### Post by Vladlenin5000 on 2014-10-04
Hi, welcome.

It's a common RF wireless mouse. For all intended purposes and from the OS point of view it's a USB mouse like any other. The USB receiver should be identified as a mouse and it is according to the results you posted therefore if it isn't working the problem is somewhere between the mouse and its receiver.

---

### Post by david298 on 2014-10-04
Thank you so much Galiza, what should I do now?

---

### Post by Vladlenin5000 on 2014-10-04
I really don't know, it depends mostly on the mouse. The receiver is working as far as I can tell. Whatever is happening or not has to do with the (wireless) connection between the mouse itself and its receiver. 
Some wireless mice have a small button underneath to establish connection; others do this with a left or right click or both or the wheel... Check your manual (and the batteries just in case).

---

### Post by david298 on 2014-10-04
Thank you so much, I will try it on a windows pc.

---

