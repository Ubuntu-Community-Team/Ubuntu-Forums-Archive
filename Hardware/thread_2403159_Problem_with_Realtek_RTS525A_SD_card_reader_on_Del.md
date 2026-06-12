---
title: "Problem with Realtek RTS525A SD card reader on Dell Latitude 7480 under 18.04"
date: 2018-10-08
forum: Hardware
---

### Post by murp2 on 2018-10-08
Hi,

I've been struggling with getting my (micro)SD card reader working on my laptop under 18.04; I
have not used it before, so I'm not sure if this issue is specific to 18.04 or whether it also manifested
in previous releases.

There have been multiple reported problems getting RTS525A working on different linux variants.

[https://askubuntu.com/questions/1026216/sd-card-reader-rts525a-unassigned-class-ff00](https://askubuntu.com/questions/1026216/sd-card-reader-rts525a-unassigned-class-ff00)
[https://forums.linuxmint.com/viewtopic.php?t=221583](https://forums.linuxmint.com/viewtopic.php?t=221583)
[https://forum.manjaro.org/t/laptop-not-recognizing-realtek-rts525a-pci-express-card-reader/54800](https://forum.manjaro.org/t/laptop-not-recognizing-realtek-rts525a-pci-express-card-reader/54800)
[https://bbs.archlinux.org/viewtopic.php?id=215337](https://bbs.archlinux.org/viewtopic.php?id=215337)

It seems that the rtsx_pci driver should have support for this chipset. However, this seems to have
dependencies on rtsx_pci_ms and rtsx_pci_sdmmc. When I rmmod the latter two, I don't get any
errors, but things do not work. When I include the two drivers, I get this error in my kernel logs 
whenever I insert an SD card:

Oct  8 10:52:35 sean-Latitude-7480 kernel: [  178.884807] mmc0: error -110 whilst initialising SD card
Oct  8 10:52:37 sean-Latitude-7480 kernel: [  180.248986] mmc0: error -110 whilst initialising SD card
Oct  8 10:52:38 sean-Latitude-7480 kernel: [  181.616937] mmc0: error -110 whilst initialising SD card

Also, the device does not appear in lsblk - it does appear in lspci but in a slightly unusual manner:

01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)

I've seen some content relating to drivers for other RTS chipsets - recompiling them etc, but I'm not
so sure it will address this issue.

I'm on the following kernel:

Linux sean-Latitude-7480 4.15.0-36-generic #39-Ubuntu SMP Mon Sep 24 16:19:09 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Any thoughts/pointers/help appreciated.

Best,
Seán.

---

### Post by takeawaydave on 2019-01-04
Hey Seán - Did you ever move forward with this? Looking at getting the same working on 18.04 (Dell Precision 7510)

---

### Post by sven0 on 2019-01-08
Hi,

I have a Dell XPS 13 9350 with a RTS525A SD card reader and it works out of the box with both Ubuntu 16.04 and Ubuntu 18.04 LTS.

Here is the output of  "lsmod|grep rtsx":

[FONT=courier new]rtsx_pci_ms            20480  0
memstick               16384  1 rtsx_pci_ms
rtsx_pci_sdmmc         24576  0
rtsx_pci               65536  2 rtsx_pci_sdmmc,rtsx_pci_ms


[/FONT]and here is the output of "lspci -v":

[FONT=courier new]3b:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS525A PCI Express Card Reader (rev 01)
    Subsystem: Dell RTS525A PCI Express Card Reader
    Flags: bus master, fast devsel, latency 0, IRQ 123
    Memory at dc600000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci

[/FONT]And here is the relevant section from "lshw":

[FONT=courier new]           *-generic
                description: Unassigned class
                product: RTS525A PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:3b:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:123 memory:dc600000-dc600fff
[/FONT]
When booting with an SD card present, I get stuff in "dmesg" that looks like this:

[    3.965139] mmc0: cannot verify signal voltage switch

[    4.084947] mmc0: new ultra high speed SDR104 SDXC card at address 59b4

[    4.418782] mmcblk0: mmc0:59b4 EFAQK 477 GiB 
[    4.420450] mmcblk0: response CRC error sending r/w cmd command, card status 0x900
[    4.429503]  mmcblk0: p1


The card works but I get only around 40-48mbyte/s write speed (tested with f3write) using Linux 4.15.0-43 whereas I get 60-70MByte/s write speed with the same card and cardreader when using Windows 10 tested with h2testw

---

