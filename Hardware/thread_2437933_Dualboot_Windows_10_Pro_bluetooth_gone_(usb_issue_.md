---
title: "Dualboot Windows 10 Pro bluetooth gone (usb issue - device descriptor read/8, error)"
date: 2020-03-03
forum: Hardware
---

### Post by panalien on 2020-03-03
Moin,

I dual-boot Kubuntu 19.10 with Windows 10 pro on an Acer Spin-1. When logging out of Kubuntu this morning, I noticed that the Bluetooth hci0 was timing out and the Bluetooth service had stopped with the error:

```
usb 1-7: device descriptor read/64, error -71
```

When booting into Windows, I noticed my bluetooth there was missing. This didn't worry me, because usually uninstalling the driver fixes things (Windows then automatically re-installs the driver). However, upon rebooting into Kubuntu later, I noticed that there, too, the bluetooth adaptor was completely missing. I checked my logs, and sure enough there was a message from the kernel: "usb issue - device descriptor read/8, error".

I had been having problems with bluetooth connectivity even before installing Windows, and after installing Windows they got worse. At this point, the bluetooth adapter was completely 'missing' in Kubuntu, and in the Windows devices menu kept detecting changes and refreshing (I suspect) because Windows wasn't properly detecting the devices.

SOLUTION:
Long story short, a forum post somewhere tipped me off that this was a boot issue. I went into the BIOS and disabled secure boot (I should have done this anyway before, but I forgot). Now my bluetooth works in both systems, and I see no more errors in my Kubuntu system log. I suspect that, for other people, disabling fast boot or turbo boot in the BIOS will do the same trick (that is what tipped me off, but the Acer Spin 1 has none of these options). This may as well work for people who don't dual-boot. I hope this helps people avoid a lot of frustration. I will report back here if the problem pops up again, or if the bluetooth connectivity and other issues aren't solved after all.

Cheers,
Lawrence

PS. I am not sure what disabling secure boot does for other computers, so I suggest checking that before messing around with the BIOS settings.
PPS. 'Moin' is Northern German for 'hello', and in some places 'goodbye'. Moin!

---

