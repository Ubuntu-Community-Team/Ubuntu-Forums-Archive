---
title: "Usb wlan dongle keeps disconnecting"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by kris_kelvin on 2006-06-09
Hello,

This problem has probably more to do with linux in general than with Ubuntu itself, but hopefully someone in here can suggest a solution to this problem.

I've tried two different usb wlan dongles (DWL G122 C3 and A-link WL54USB) with Debian and Ubuntu kernels and got both of them working. However, I'm having the same problem with both of these sticks. After some time - it may be ten minutes or ten hours - the dongle disconnects itself and the following line appears in system log: "usb 4-1: USB disconnect, address 2". Usb support seems to freeze completely, because "modprobe -r rt73" or "lsusb" both freeze. Only way to continue is to reboot - and actually it doesn't even reboot without physical reset.

This may have something to do with Linux usb support in general, or it may have something to do with my motherboard. I have Shuttle SK41G, which has VIA KM266-based motherboard ([http://global.shuttle.com/Product/barebone/brb_OverView.asp?B_id=10)](http://global.shuttle.com/Product/barebone/brb_OverView.asp?B_id=10)).

Does anyone have any idea how to get rid of these disconnects and solve this problem?

---

### Post by lmp on 2006-07-15
Hi,
i have a linksys WUSB54GV4 USB antenna. It works fine with my desktop, but also disconnects on my laptop. So it seems related to the kind of computer or powermanagement or usb management. If you have found a solution, please let me know. I both tried xubuntu and ubuntu. Both have the problem on the laptop. (i have an old laptop toshiba sattelite 2180 cdt)

---

