---
title: "Nvidia driver takes 63 seconds to restore during resume from hibernate!"
date: 2011-06-04
forum: Hardware
---

### Post by gen0 on 2011-06-04
I've just installed Ubuntu Lucid on an old Thinkpad T61 running an Nvidia Quadro NVS 140M.

Hibernate/Resume works fine with the stock open-source driver, however as soon as I install the proprietary Nvidia driver, resume from hibernate takes ages.  (Resume from suspend is fine and fast though).

As you can see from the log snippet below - *63 seconds* in this case - and during this time I just see a black screen with no hard-drive activity, and I hear the system-beep twice:

```
kernel: [  281.014030] ata3.00: configured for UDMA/133
kernel: [  281.034897] ata3.00: configured for UDMA/133
kernel: [  281.034899] ata3: EH complete
[B]kernel: [  344.570540] PM: restore of drv:nvidia dev:0000:01:00.0 complete after 63882.918 msecs
[/B]kernel: [  344.708116] PM: restore of drv:yenta_cardbus dev:0000:15:00.0 complete after 137.132 msecs
kernel: [  344.766119] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[f8101000-f81017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]

```

I'm running NVidia driver 195.36.24, but I've also tried the older 173 driver in the repo as well as the newer 270.41.19. driver from ppa:ubuntu-x-swat/x-updates.

I've blacklisted intel_agp and set NvAGP to 1 as recommended here:
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

I've set nomodeset as a grub option as recommended by some other thread I've found.

Nothing has made a difference.

Does anyone out there know a fix?

---

### Post by gen0 on 2011-06-06
I've since found this thread:

[http://www.nvnews.net/vbulletin/showthread.php?t=123003&page=5](http://www.nvnews.net/vbulletin/showthread.php?t=123003&page=5)

on NvNews that seems to accurately describe my problem.  This issue was apparently fixed in the NVidia 180 series drivers but returned in the 185 series and seems to have been around ever since.

I've struggled to find packages for the 180 series drivers on Lucid.  I've managed to download the driver direct from NVidia but I get compile errors trying to install it.

Is there a way to install the 180 series drivers on Lucid?

---

