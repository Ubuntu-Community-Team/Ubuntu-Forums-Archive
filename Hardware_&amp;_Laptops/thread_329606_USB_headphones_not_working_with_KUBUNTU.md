---
title: "USB headphones not working with KUBUNTU"
date: 2007-01-01
forum: Hardware &amp; Laptops
---

### Post by baja munda on 2007-01-01
Hi Board,

I have a pair of USB headphones. These headphones just work fine on my laptop, which has ubuntu installed on it. On my desktop, which has kubuntu installed, the headphones are simply not detected. 

Just to make sure that the ports work fine, I rebooted into windows, and the speakers were functioning as usual. 

Any pointers, help will be appreciated.

TIA

Baja Munda

---

### Post by DoctorMO on 2007-01-16
go into a terminal and type in `lsusb` you should see your usb headphones in the list.

You can also look at dmesg which will list when you plug in and unplug any usb device. this will tell you also which module is being used for your device if the primitive is being detected.

I suspect it's probably settings.

---

