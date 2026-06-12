---
title: "2in1 card read in Acer M3-481T"
date: 2013-02-24
forum: Hardware
---

### Post by casposa on 2013-02-24
Hello community!
I have an Acer Aspire M3-481T running Kubuntu 12.10. I can't seem to be able to make de card reader to work. I Know I need to identify the card to be able to download the driver but neither lspci nor lsusb seem to list the card. Am I missing something?

lspci returns:
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.7 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 8 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
09:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)

```

and lsusb:
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:2c32 Sunplus Innovation Technology Inc. 
Bus 001 Device 004: ID 0489:e04e Foxconn / Hon Hai
```

---

### Post by casposa on 2013-02-26
anyone?
I have the feeling I am missing something really stupid! ](*,)

---

### Post by gordintoronto on 2013-02-26
I'm sorry, I don't understand what this means: "I Know I need to identify the card to be able to download the driver..."

Actually, I guess I do know what you are saying, but in my experience it is not true.

Did you have a memory card plugged in when you ran lsusb? Whether I have a card plugged in or not, I see these lines:
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer

(It's an external hub/card reader.)

---

### Post by casposa on 2013-02-27
Hey, thanks for the answer. I made some progress. It turns out that if I boot with a card inserted, lspci does "see" the card.

lspci:
> 03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)

Now that I finally found out which model I had, I downloaded the driver (this is what my first post was about) from [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false#2](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false#2)

The installation went smoothly but now, when I try to acces the sdcard folder (from dolphin) I get the following error:

> An error occurred while accessing '3.7 GiB Removable Media', the system responded: The kernel driver for this filesystem type is not available.: Error mounting: mount: /dev/mmcblk0p1: can't read superblock

What am I doing wrong? 

Thanks

---

### Post by gordintoronto on 2013-02-27
Wow, first time I have seen a PCI card reader. How is the card formatted? If it's not formatted, I suggest installing and running Gparted. (From terminal: sudo gparted) You must be very cautious, since Gparted can wipe out anything on your hard drive. There's a drop-down in the top-right to select the drive you want to work with.

---

