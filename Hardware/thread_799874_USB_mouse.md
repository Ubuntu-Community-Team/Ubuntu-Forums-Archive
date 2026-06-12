---
title: "USB mouse"
date: 2008-05-19
forum: Hardware
---

### Post by alex sun on 2008-05-19
Dear inhabitants of the forum,
I kindly ask you to help me with 1 little problem:
In gusty 64 a USB mouse worked on my tx1000, in hardy 64 any USB mouse doesn't.
Flash cards and other USB devices work fine. "dmesg |tail" gives no messages when I connect or disconnect a mouse. How to make a mouse work?
Please, help!

---

### Post by alex sun on 2008-05-20
I've just found out that some mouses do not shine at all, and some shine correctly (more when I move them), but do not make a cursor move.
Any considerations?

---

### Post by alex sun on 2008-05-23
My USB mouse still doesn't work at all - doesn't matter if I reboot or not.

lsusb returns:
```

Bus 001 Device 007: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 006: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 001 Device 005: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 0000:0000

```

I'm running Ubuntu Hardy Heron 64bit and have tried A4-TECH OP-35D mouse and several other ones (Asus, Acer and HP) with same results.
In previous version of Ubuntu (Gusty 64bit) everything worked.

In log by grep there are only 2 mouse-related strings:
```

[ 18.457701] input: A4Tech PS/2+USB Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input2
[ 18.472509] input,hidraw0: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:0b.0-1

```

On connecting\disconnecting mouse during work grep returns nothing.

I heard that Ndiswrapper has a reputation for hijacking USB ports and I use Ndiswrapper for my Wireless. However all other USB devises (like USB flash cards) work fine.
I really need some help with my mouse

---

### Post by GedDarkstorm on 2008-06-05
I have the Exact same problem, but with the 32 bit version of Hardy. Mouse worked fine in the older version. Likewise, with Hardy, the tablet and flash drives seem to have no trouble, but the mouse will NOT light up, and will not work. This is an issue only with Hardy, and I can find nothing, anywhere (not on google and not via searching the forums), about it, just unanswered posts like this one. Won't someone help? This touch pad is starting to rub my fingers raw..

I've already tried all the ehci_hcd/ohci_hcd/uhci_hcd stuff that I've seen talked about with mouse loss after standby mode, but none of that does a lick of anything.

---

