---
title: "USBEE Logic Probe Installation under Ubuntu (Wine)"
date: 2009-09-02
forum: Hardware
---

### Post by jobattle on 2009-09-02
I want to use my USBEE <http://www.usbee.com/> probes under Linux. The installation program works OK  and the application it installs works except it doesn't communicate with the USBEE logic probe.  I am thinking that the answer lies in /etc/udev/rules.d, specifically I need to write one but, alas, I don't know how.  Any suggestions would be greatly appreciated.  This is a very useful little device and I really want to be able to use it under Linux since I no longer have ANY windows machines (I destroyed all copies of that evil os).

---

### Post by merc64 on 2010-01-12
My understanding is that Wine doesn't support *any* usb as-is. See [this thread]("http://www.winehq.org/pipermail/wine-users/2007-October/028096.html") and the [details on USB in the Wine wiki]("http://wiki.jswindle.com/index.php/Drivers#Is_it_possible_to_add_USB_functionality_to_WiNE.3F") for some details.

---

