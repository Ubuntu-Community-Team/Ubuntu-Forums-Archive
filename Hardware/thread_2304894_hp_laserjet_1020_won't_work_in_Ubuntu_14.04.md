---
title: "hp laserjet 1020 won't work in Ubuntu 14.04"
date: 2015-12-01
forum: Hardware
---

### Post by raffi_1970 on 2015-12-01
after having no luck with hplip, i tried

[COLOR=#333333][FONT=Ubuntu]to follow the procedure here
[http://foo2zjs.rkkda.com/INSTALL](http://foo2zjs.rkkda.com/INSTALL)
and I still couldn't get the printer to work--
this is what I got when I ran
tail /var/log/syslog
Nov 30 21:45:15 raffi-X550EA kernel: [ 4367.252677] usb 5-1: Manufacturer: Hewlett-Packard
Nov 30 21:45:15 raffi-X550EA kernel: [ 4367.252685] usb 5-1: SerialNumber: JL2A6BF
Nov 30 21:45:15 raffi-X550EA kernel: [ 4367.256966] usblp 5-1:1.0: usblp0: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x03F0 pid 0x2B17
Nov 30 21:45:15 raffi-X550EA mtp-probe: checking bus 5, device 8: "/sys/devices/pci0000:00/0000:00:10.0/usb5/5-1"
Nov 30 21:45:15 raffi-X550EA mtp-probe: bus: 5, device: 8 was not an MTP device
Nov 30 21:45:18 raffi-X550EA /etc/hotplug/usb/hplj1020: foo2zjs: loading HP LaserJet 1020 firmware /usr/share/foo2zjs/firmware/sihp1020.dl to /dev/usb/lp0 ...
Nov 30 21:45:18 raffi-X550EA /etc/hotplug/usb/hplj1020: foo2zjs: ... download successful.
Nov 30 21:45:18 raffi-X550EA kernel: [ 4371.100804] usblp0: removed
Nov 30 21:46:03 raffi-X550EA wpa_supplicant[892]: message repeated 2 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Nov 30 21:46:04 raffi-X550EA wpa_supplicant[892]: nl80211: send_and_recv->nl_recvmsgs failed: -33
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]any suggestions???[/FONT][/COLOR]

---

### Post by Bucky Ball on 2015-12-01
Apparently, installing hplip-gui will take the headache out of this. There is no need to go anywhere other than the hp site and hplip. Installing 'fixes' randomly may only cause more confusion. If hplip didn't help, better to work out why.

---

