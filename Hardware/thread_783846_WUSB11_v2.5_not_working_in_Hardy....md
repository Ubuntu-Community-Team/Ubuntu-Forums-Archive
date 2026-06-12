---
title: "WUSB11 v2.5 not working in Hardy..."
date: 2008-05-06
forum: Hardware
---

### Post by encompass on 2008-05-06
I have a friend using xubuntu installed with a USB based wireless card.
Bus 001 Device 002: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter
And according to here...
[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)
It should be working in hardy out of the box.
I have tried modprobe prism2_usb and many many other things.
I have even gone the route of using ndiswrapper but that tends to be an issue because the driver is built into windows XP and neither of us have it.  And even the linksys website tells me that it's included in windows XP.
I normally would giveup and say it just doesn't have the support.  BUT it does!  And apperently my friend is the only guy with the issue.
Any ideas on the issue and how to resolve it?
He has not wired connection to the net available he has to manually download it on his windows 98 side and copy it over to his linux side.  A real pain.. but we can do it.
I have even tried unplugging all USB devices.  And even installing the now uneeded linux-wlan-ng package.
Any ideas?

---

### Post by adisor19 on 2008-05-08
> **encompass said:**
> I have a friend using xubuntu installed with a USB based wireless card.
Bus 001 Device 002: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter
And according to here...
[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)
It should be working in hardy out of the box.
I have tried modprobe prism2_usb and many many other things.
I have even gone the route of using ndiswrapper but that tends to be an issue because the driver is built into windows XP and neither of us have it.  And even the linksys website tells me that it's included in windows XP.
I normally would giveup and say it just doesn't have the support.  BUT it does!  And apperently my friend is the only guy with the issue.
Any ideas on the issue and how to resolve it?
He has not wired connection to the net available he has to manually download it on his windows 98 side and copy it over to his linux side.  A real pain.. but we can do it.
I have even tried unplugging all USB devices.  And even installing the now uneeded linux-wlan-ng package.
Any ideas?

I'm in the same boat. This devices is based on the Prism2 chipset and it doesn't work at all.

HALP :'(

Adi

---

