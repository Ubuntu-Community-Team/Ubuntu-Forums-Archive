---
title: "ASUS Transformer Book T101HA-GR029T - Webcam not working"
date: 2020-04-13
forum: Hardware
---

### Post by pgfeller on 2020-04-13
Hi all,

I've installed Ubuntu Mate Release 19.10 (64-bit, Kernel Linux 5.3.0-46-generic x86_64) on my ASUS Transformer Book (T101HA-GR029T). Almost everything works out of the box. The only thing not working is the webcam. It would be very nice if that would work as well. I try to post the relevant information about my system below (let me know if something else is required):

> lspci
```
00:00.0 Host bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series SoC Transaction Register (rev 36)
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller (rev 36)
00:03.0 Multimedia controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Imaging Unit (rev 36)
00:0a.0 Non-VGA unclassified device: Intel Corporation Device 22d8 (rev 36)
00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 36)
00:14.0 USB controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series USB xHCI Controller (rev 36)
00:1a.0 Encryption controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Trusted Execution Engine (rev 36)
00:1c.0 PCI bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Express Port #1 (rev 36)
00:1f.0 ISA bridge: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCU (rev 36)
01:00.0 Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter (rev 31)

```

> lsusb
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0b05:183d ASUSTek Computer, Inc. ASUS HID Device 
Bus 001 Device 003: ID 13d3:3501 IMC Networks 
Bus 001 Device 002: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

hw-probe output available @ [https://linux-hardware.org/?probe=9b6660e48d](https://linux-hardware.org/?probe=9b6660e48d)

It might be that the device is not PCI nor USB ... I suspect I2C - but I do not know.

Any help what I might do to make this working would be highly appreciated (I would even try to build a patched kernel).

thanks and kind regards,
Patrik

---

### Post by CelticWarrior on 2020-04-13
Sorry, bad news.

Like what happens with many others crappy "bay trail"/"cherry tail" based hardware, some devices, namely the webcam, are not supported. Whether they will be or not in the future only time will tell.

---

### Post by oldfred on 2020-04-13
This kernel will not be in 20.04 unless you manually install it. Perhaps in 20.10?

Linux Kernel 5.7 finally fixes some Bay Trail & Cherry Trail issues
[https://www.phoronix.com/scan.php?page=news_item&px=Bay-Trail-Cherry-Trail-Touch-57](https://www.phoronix.com/scan.php?page=news_item&px=Bay-Trail-Cherry-Trail-Touch-57)
Bay Trail issues, boot parameter required
[http://ubuntuforums.org/showthread.php?t=2314964](http://ubuntuforums.org/showthread.php?t=2314964)

---

### Post by pgfeller on 2020-04-13
Thank you both for your reply ... bad luck indeed - but there seems to be hope according to oldfred - I'm quite new to those things - but I like the OS already; why not to try to compile my own kernel - will at least give it a try :D.

---

### Post by oldfred on 2020-04-13
You do not have to compile it, but use a ppa to download it for Ubuntu.
You still may have issues as part of creating a distribution is making sure every application works and or has to be recompiled to work with newer kernel.

Never tried to change kernel.
[https://kernel.ubuntu.com/~kernel-ppa/mainline/](https://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by pgfeller on 2020-04-13
I was able to upgrade the kernel to 5.7.0-RC1 and the device still boots - the touchscreen is a bit messed up - but nothing I could not fix with xinput & randr; unfortunately the camera still does not work. I will go back to the supported kernel to be on the safe side. So I assume I have to live with the broken camera.

Many thanks for your help - much appreciated!

---

### Post by mörgæs on 2020-04-15
Which applications have you used for testing the camera?

---

### Post by pgfeller on 2020-04-15
Hi mörgæs, 

I've used "Cheese" to check if the camera was recognized. Is there another application that I should try?

kind regards,
Patrik

---

### Post by mörgæs on 2020-04-15
Yes, guvcview.

---

### Post by pgfeller on 2020-04-15
I tried guvcview on kernel 5.3.0-46 & 5.7.0-RC1; unfortunately with both kernels the application does not start. It displays a message box "Gucview error - no video device found". Does not sound promising :(.

---

### Post by mörgæs on 2020-04-15
Sorry, now I see from the lsusb output that there are no signs of a camera.

---

### Post by pgfeller on 2020-04-17
A small update (I do not give up easily :)) ... it looks as if there was a driver present in the past for "INTEL ATOM IMAGE SIGNAL PROCESSING (ISP)", called atomisp. Not sure if it is still maintained and part of the current kernels - will have to investigate this ....

Update:
There was a driver present in kernel staging (atomisp), but it has been removed as it was deemed unmaintainable ([https://git.kernel.org/pub/scm/linux/kernel/git/mchehab/linux-media.git/commit/?id=51b8dc5163d2ff2bf04019f8bf7e3bd0e75bb654](https://git.kernel.org/pub/scm/linux/kernel/git/mchehab/linux-media.git/commit/?id=51b8dc5163d2ff2bf04019f8bf7e3bd0e75bb654)). It was replaced by a dummy driver (atomisp2) which only makes sure that the device can enter D3 power save :(). I'll try to check if there are plans to implement functionality for the actual device into the new driver. I assume that the HW specs are known, as there was a (unstable/unmaintainable) driver available. But I have to find out whom to ask ...

---

