---
title: "USB ports not working (Ryzen, Ubuntu, kernel 5.11.)"
date: 2021-06-09
forum: Hardware
---

### Post by WimiBuntu on 2021-06-09
Hi everyone,

I have a problem, because on my Lenovo T14s the USB ports (I guess 3.0) stopped working. When I connect an optical drive via cable or my smartphone nothing happens. The smartphone is also not loading the battery. And also I cannot access any USB flash drives.

Previously I downgraded to the 5.8.0-50-generic kernel (but this was just an attempt, as I am not really knowing what I am doing there). For a short while it seemed to work, but then again I do not always plug in USB devices and now I saw that it stopped working again. I have no idea what to check to narrow down the problem. On other computers all of these USB devices work and it is same disfunctionality for both USB ports of my laptop.

I guess, you might ask for the output of certain commands. I will try to deliver those directly here.

```

lsusb
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 003: ID 8087:0029 Intel Corp. 
Bus 006 Device 002: ID 06cb:00bd Synaptics, Inc. 
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 004 Device 002: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 04f2:b6cb Chicony Electronics Co., Ltd Integrated Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I have also attached the output of lsusb -v. While redirecting it to the file, there were also error messages displayed:

```

lsusb -v > lsusbvoutput
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
can't get device qualifier: Resource temporarily unavailable
can't get debug descriptor: Resource temporarily unavailable
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing

```

What else could I provide? 

Thanks for every help in advance!

PS:

```

sudo uhubctl
Current status for hub 3 [1d6b:0003 Linux 5.8.0-50-generic xhci-hcd xHCI Host Controller 0000:05:00.0, USB 3.00, 2 ports]
  Port 1: 02a0 power 5gbps Rx.Detect
  Port 2: 02a0 power 5gbps Rx.Detect
Current status for hub 2 [1d6b:0002 Linux 5.8.0-50-generic xhci-hcd xHCI Host Controller 0000:05:00.0]
  Port 1: 0100 power
  Port 2: 0507 power highspeed suspend enable connect [04f2:b6cb Chicony Electronics Co.,Ltd. Integrated Camera 0001]

```

---

### Post by WimiBuntu on 2021-06-09
Here comes another update, but I am not sure if it is helping. I have rebooted several times today. And that did not help. Now, however suddenly both USB ports worked again. Fine, but how long will this work?

I have compared the previous lsusb -v output and this is the diff:
```

496c496
< Bus 004 Device 002: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
---
> Bus 004 Device 003: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
592a593,650
>         bInterval               0
> 
> Bus 004 Device 002: ID 0e8d:1887 MediaTek Inc. Portable Super Multi Drive
> Device Descriptor:
>   bLength                18
>   bDescriptorType         1
>   bcdUSB               2.00
>   bDeviceClass            0 
>   bDeviceSubClass         0 
>   bDeviceProtocol         0 
>   bMaxPacketSize0        64
>   idVendor           0x0e8d MediaTek Inc.
>   idProduct          0x1887 
>   bcdDevice            0.00
>   iManufacturer           1 
>   iProduct                2 
>   iSerial                 3 
>   bNumConfigurations      1
>   Configuration Descriptor:
>     bLength                 9
>     bDescriptorType         2
>     wTotalLength       0x0020
>     bNumInterfaces          1
>     bConfigurationValue     1
>     iConfiguration          4 
>     bmAttributes         0xa0
>       (Bus Powered)
>       Remote Wakeup
>     MaxPower              500mA
>     Interface Descriptor:
>       bLength                 9
>       bDescriptorType         4
>       bInterfaceNumber        0
>       bAlternateSetting       0
>       bNumEndpoints           2
>       bInterfaceClass         8 Mass Storage
>       bInterfaceSubClass      2 SFF-8020i, MMC-2 (ATAPI)
>       bInterfaceProtocol     80 
>       iInterface              5 
>       Endpoint Descriptor:
>         bLength                 7
>         bDescriptorType         5
>         bEndpointAddress     0x81  EP 1 IN
>         bmAttributes            2
>           Transfer Type            Bulk
>           Synch Type               None
>           Usage Type               Data
>         wMaxPacketSize     0x0200  1x 512 bytes
>         bInterval               0
>       Endpoint Descriptor:
>         bLength                 7
>         bDescriptorType         5
>         bEndpointAddress     0x02  EP 2 OUT
>         bmAttributes            2
>           Transfer Type            Bulk
>           Synch Type               None
>           Usage Type               Data
>         wMaxPacketSize     0x0200  1x 512 bytes

```

As rookie I only see that one of the problematic ports is bus 004 device 002. But more I do not get from that. Can you make more out of it?

---

### Post by WimiBuntu on 2021-11-16
Sadly, now the USB do not work again. I have recently installed an update. And now I am running 5.11.0-40-generic #44~20.04.2-Ubuntu SMP Tue Oct 26 18:07:44 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux.

Do you have any idea how to solve this?

---

### Post by tea for one on 2021-11-16
Did the recent update include a new kernel?

Have you tried to boot into an earlier kernel via Grub Menu - Advanced Options for Ubuntu?

---

### Post by WimiBuntu on 2021-11-16
Yes, it included linux-headers and so on. I also tried earlier kernels via Grub menu, but this did not help either. But maybe an older version that worked got thrown out? I don't know. How could I narrow down this problem?

---

### Post by tea for one on 2021-11-16
Between June 09 2021 and November 16 2021, your USB ports were OK?

It would be beneficial to know which kernel was being used?

Can you open a terminal and post the output from
```
ls /boot | grep vmlinuz-

```

---

### Post by WimiBuntu on 2021-11-17
Hi

Yes, between these dates it worked, but unfortunately I do not know which kernel I used then. I also guess that I upgrade a few times in between, but I am not sure.

Here is the output you asked for for:

```

ls /boot | grep vmlinuz-
vmlinuz-5.11.0-38-generic
vmlinuz-5.11.0-40-generic
vmlinuz-5.8.0-63-generic

```

---

### Post by tea for one on 2021-11-17
I assume that you have tried all the installed kernels without any success?

Anyway, it seems to be a matter of tracking down the kernel used between June 09 and November 16.

Did the USB ports work when you installed Ubuntu?
Perhaps you still have the ISO?

---

### Post by WimiBuntu on 2021-11-17
Yes, I tried all of the installed kernels. But I don't know how to narrow down the problem. I guess it is not a good idea to use very old kernels. But I don't know how to get a more current kernel to work.

I had some USB problems right from the start when I got this laptop. I guess it has something to do with AMD Ryzen. This is just because I read snippets about some incompatabilities.

---

### Post by tea for one on 2021-11-17
There is nothing wrong with using older kernels which support your hardware.
Having established that you had reasonable performance earlier this year, you are in the best position to try and identify the kernel which provided best results.

A couple of suggestions:-

Have you explored all the USB options in your UEFI firmware?
Download and try a live session of Ubuntu 21.10 with the 5.13 kernel?

---

### Post by WimiBuntu on 2021-11-17
Dear "tea for one"

Thanks. In the meantime I got it to work, but in a different way. First, I did not reboot as I did several times before, but I really shut down the entire PC. Then I started the new 5.11.0-40-generich kernel, but in recovery mode. There USB worked again. Then I just did the same, but with the normal start routine without the recovery mode. And for whatever reason now it works again. Hopefully it stays that way.

Best regards

---

### Post by tea for one on 2021-11-18
> **WimiBuntu said:**
> Dear "tea for one"

Thanks. In the meantime I got it to work, but in a different way. First, I did not reboot as I did several times before, but I really shut down the entire PC. Then I started the new 5.11.0-40-generich kernel, but in recovery mode. There USB worked again. Then I just did the same, but with the normal start routine without the recovery mode. And for whatever reason now it works again. Hopefully it stays that way.

Best regards

That's an improvement.
Please post back after a few days to report if it is a permanent fix.

The advice to [COLOR="#0000FF"]Turn it off completely, leave it 15 minutes and turn it on again[/COLOR] can often be misconstrued as a touch condescending.
However, sometimes, it can be just the right suggestion. 

Tricky coves personal computers ;)

---

