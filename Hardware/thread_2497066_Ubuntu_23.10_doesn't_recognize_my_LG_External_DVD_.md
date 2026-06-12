---
title: "Ubuntu 23.10 doesn't recognize my LG External DVD Writer (GP65 series)"
date: 2024-04-21
forum: Hardware
---

### Post by eddeemn on 2024-04-21
I cannot get Ubuntu to recognize my external DVD drive (an LG GP65NB60). It was manufactured last year, has the latest available firmware from LG and works fine in Windows. I am on kernel 6.5.0-27-generic. I am at a total loss and don't know how to proceed. LG technical support said to "make sure I have the correct OS drivers" and that was as helpful as nothing really.


Here is the output of [B]sudo lshw -short
[/B]

 ```
H/W path         Device          Class          Description
===========================================================
                                 system         HP Pavilion Laptop 15t-eg200 (4U8D4AV)
/0                               bus            89F6
/0/0                             memory         64KiB BIOS
/0/10                            memory         16GiB System Memory
/0/10/0                          memory         8GiB SODIMM DDR4 Synchronous 3200 MHz (0.3 ns)
/0/10/1                          memory         8GiB SODIMM DDR4 Synchronous 3200 MHz (0.3 ns)
/0/1c                            memory         96KiB L1 cache
/0/1d                            memory         64KiB L1 cache
/0/1e                            memory         2560KiB L2 cache
/0/1f                            memory         12MiB L3 cache
/0/20                            memory         256KiB L1 cache
/0/21                            memory         512KiB L1 cache
/0/22                            memory         4MiB L2 cache
/0/23                            memory         12MiB L3 cache
/0/24                            processor      12th Gen Intel(R) Core(TM) i7-1255U
/0/100                           bridge         Intel Corporation
/0/100/2         /dev/fb0        display        Alder Lake-UP3 GT2 [Iris Xe Graphics]
/0/100/4                         generic        Alder Lake Innovation Platform Framework Processor Participant
/0/100/8                         generic        12th Gen Core Processor Gaussian & Neural Accelerator
/0/100/d                         bus            Alder Lake-P Thunderbolt 4 USB Controller
/0/100/d/0       usb1            bus            xHCI Host Controller
/0/100/d/1       usb2            bus            xHCI Host Controller
/0/100/14                        bus            Alder Lake PCH USB 3.2 xHCI Host Controller
/0/100/14/0      usb3            bus            xHCI Host Controller
/0/100/14/0/1    input20         input          PixArt HP USB Optical Mouse
/0/100/14/0/3                    multimedia     HP Wide Vision HD Camera
/0/100/14/0/7                    generic        ELAN:ARM-M4
/0/100/14/0/a                    communication  Wireless_Device
/0/100/14/1      usb4            bus            xHCI Host Controller
/0/100/14.2                      memory         RAM memory
/0/100/15                        bus            Alder Lake PCH Serial IO I2C Controller #0
/0/100/15.1                      bus            Alder Lake PCH Serial IO I2C Controller #1
/0/100/16                        communication  Alder Lake PCH HECI Controller
/0/100/1c                        bridge         Alder Lake PCH-P PCI Express Root Port #9
/0/100/1c/0      wlp1s0          network        MT7921 802.11ax PCI Express Wireless Network Adapter
/0/100/1d                        bridge         Intel Corporation
/0/100/1d/0      /dev/nvme0      storage        Samsung SSD 980 PRO 2TB
/0/100/1d/0/0    hwmon3          disk           NVMe disk
/0/100/1d/0/2    /dev/ng0n1      disk           NVMe disk
/0/100/1d/0/1    /dev/nvme0n1    disk           2TB NVMe disk
/0/100/1d/0/1/1  /dev/nvme0n1p1  volume         259MiB Windows FAT volume
/0/100/1d/0/1/2  /dev/nvme0n1p2  volume         15MiB reserved partition
/0/100/1d/0/1/3  /dev/nvme0n1p3  volume         639GiB Windows NTFS volume
/0/100/1d/0/1/4  /dev/nvme0n1p4  volume         877MiB Windows NTFS volume
/0/100/1d/0/1/5  /dev/nvme0n1p5  volume         1222GiB EXT4 volume
/0/100/1f                        bridge         Alder Lake PCH eSPI Controller
/0/100/1f/0                      system         PnP device PNP0c02
/0/100/1f/1                      system         PnP device PNP0c02
/0/100/1f/2                      generic        PnP device HPQ8001
/0/100/1f/3                      system         PnP device PNP0c02
/0/100/1f/4                      system         PnP device PNP0c02
/0/100/1f/5                      system         PnP device PNP0c02
/0/100/1f.3      card0           multimedia     Alder Lake PCH-P High Definition Audio Controller
/0/100/1f.4                      bus            Alder Lake PCH-P SMBus Host Controller
/0/100/1f.5                      bus            Alder Lake-P PCH SPI Controller
/1                               power          HW03041XL
/2               input0          input          Lid Switch
/3               input1          input          Power Button
/4               input10         input          SYNA32CE:00 06CB:CE17 Mouse
/5               input11         input          SYNA32CE:00 06CB:CE17 Touchpad
/6               input14         input          Video Bus
/7               input15         input          sof-hda-dsp Mic
/8               input16         input          sof-hda-dsp Headphone
/9               input17         input          sof-hda-dsp HDMI/DP,pcm=3
/a               input18         input          sof-hda-dsp HDMI/DP,pcm=4
/b               input19         input          sof-hda-dsp HDMI/DP,pcm=5
/c               input2          input          Power Button
/d               input3          input          AT Translated Set 2 keyboard
/e               input7          input          Intel HID events
/f               input8          input          Intel HID 5 button array
/10              input9          input          HP WMI hotkeys

```

This is the output for **lsusb**

```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 04f3:0c00 Elan Microelectronics Corp. ELAN:ARM-M4
Bus 003 Device 003: ID 30c9:0065 Luxvisions Innotech Limited HP Wide Vision HD Camera
Bus 003 Device 006: ID 13d3:3567 IMC Networks Wireless_Device
Bus 003 Device 007: ID 03f0:094a HP, Inc Optical Mouse [672662-001]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by guiverc on 2024-04-21
Also asked at [https://askubuntu.com/questions/1511156/how-do-i-get-ubuntu-23-10-to-recognize-my-lg-external-dvd-writer-gp65](https://askubuntu.com/questions/1511156/how-do-i-get-ubuntu-23-10-to-recognize-my-lg-external-dvd-writer-gp65)

---

### Post by eddeemn on 2024-04-21
**EDIT**: Apparently it offends some users to post on both forums and I didn't mean to offend anyone, I was just not sure where to post first. I deleted my post on askubuntu.

---

### Post by guiverc on 2024-04-21
> **eddeemn said:**
> **EDIT**: Apparently it offends some users to post on both forums and I didn't mean to offend anyone, I was just not sure where to post first. I deleted my post on askubuntu.

I sure wasn't offended... after all it was me that +1'd (*upvoted*) your askubuntu post.

I don't consider it *bad form*, **I just have a *preference ***for when a question is posted on multiple sites, that the OP (*Original Poster*) reveals that detail, as many of use multiple such sites, and we can come across many questions where we're unsure if multiple people are having the same issue OR its the same post (*names aren't always the same** or similar*).  Mention of the *cross* or *other *post just avoids that decision.

The only rule I'm aware on the matter is *Stack Exchange* which has rules that prevent asking the same question on multiple SE sites.. so that wasn't breached to my knowledge, as whilst AskUbuntu is a SE site, this forum is not.

I'll suggest un-deleting your askubu post.. My 2c/opinion anyway.

---

