---
title: "ata5: hard resetting link - UBUNTU 9.10 Karmic Cola - 2TB Drives, Sata-USB"
date: 2010-04-05
forum: Hardware
---

### Post by supernal on 2010-04-05
[COLOR=#000000][FONT=Times New Roman][COLOR=#000000][FONT=Verdana]**[SIZE=2]Issue. Every 30 mins my system has a SMART interrupt error, and has to "Hard reseting links" [/SIZE]**


So every 30 mins, my other hard drives in my linux box restart, making a squelch sound. (This sound can be reproduced by using hdparm and telling the hard drive to start itself up, even though it is still actively running) This also contributes to currupted data on these drives. Oddly enough this does not effect my primary drive, only additional drives added to the system. (USB or SATA)
This condition is true for two drives connected via SATA, AND my one external drive connected via USB


I have seen bug reports filed with the Kernel guys, and people blaming the hard drive /  motherboard / controller drivers.The truth lies somewhere in between.
I need either a kernel fix from the linux community, or Intel Matrix Storage Controller updates specifically for linux. 
(I can find neither of these)

Where do i turn first?

It should also be mentioned that i loaded up a copy of WInXP with the intel matrix storage manager drivers slipstreamed into the installation.I ran it for several hours, listening for the squeltch sound that indicated that the "hard resetting links" condition has happened, and looking everywhere i know in windows to see if there were any errors.
The external hard drive (USB) never had to remount itself, and the hard drives attached to the Marvell / Ich9r controller never had a single issue.

So this is a Linux only issue, and is in fact NOT my hardware.


Is it possible to use intel's windows drivers within linux?
Are there other possibilities?

Where is a more proper place to file this issue so a developer can actually work on it?
I've read in a lot of places that this issue is at the kernal level, and effects all distrabutions such as Fedora, CentOS, Mint, ubuntu.... etc.

I should be able to use more then one SATA drive in my box, it does after all have 6 ports for sata....

HELP!!!! I don't want to run windows!! If i can fix this issue though i have little other choice  =(





Hardware:
Motherboard: ASUS P5E3 PRO LGA 775 Intel X48 ATX Intel Motherboard
Processor: Intel Core 2 Quad Q8400 Yorkfield 2.66GHz 4MB L2 Cache LGA 775 95W Quad-Core Processor
Video: SAPPHIRE 100253HDMI Radeon HD 4650 512MB 128-bit GDDR2 PCI Express 2.0 x16 HDCP Ready CrossFireX Support Low Profile Ready Video Card
Memory: Kingston ValueRAM 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10600) Dual Channel Kit Desktop Memory Model KVR1333D3K2/4G
Hard Drive (Primary): SAMSUNG Spinpoint F1 HD103UJ 1TB 7200 RPM 32MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare DriveOther hard Drives (x2): SAMSUNG Spinpoint F3EG HD203WI 2TB 5400 RPM 32MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive
```

00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller (rev 01)
00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge (rev 01)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV730 PRO [Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)

```

Software:Ubuntu 9.10 Karmic Cola AMD 64 (Gnome Desktop)
Kernel:  2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux



Error logs as follows:

```

Apr  3 05:38:09 mediaserver kernel: [28837.950029] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 05:38:09 mediaserver kernel: [28837.950038] ata6.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
Apr  3 05:38:09 mediaserver kernel: [28837.950039]          res 40/00:00:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Apr  3 05:38:09 mediaserver kernel: [28837.950042] ata6.00: status: { DRDY }
Apr  3 05:38:09 mediaserver kernel: [28837.950046] ata6: hard resetting link
Apr  3 05:38:09 mediaserver kernel: [28837.982516] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 05:38:09 mediaserver kernel: [28837.982523] ata5.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
Apr  3 05:38:09 mediaserver kernel: [28837.982524]          res 40/00:00:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
Apr  3 05:38:09 mediaserver kernel: [28837.982527] ata5.00: status: { DRDY }
Apr  3 05:38:09 mediaserver kernel: [28837.982531] ata5: hard resetting link
Apr  3 05:38:12 mediaserver kernel: [28841.332500] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  3 05:38:12 mediaserver kernel: [28841.344250] ata5.00: configured for UDMA/133
Apr  3 05:38:12 mediaserver kernel: [28841.344269] ata5: EH complete
Apr  3 05:38:13 mediaserver kernel: [28841.663744] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  3 05:38:13 mediaserver kernel: [28841.675643] ata6.00: configured for UDMA/133
Apr  3 05:38:13 mediaserver kernel: [28841.675664] ata6: EH complete

...
...

Apr  3 06:08:09 mediaserver kernel: [30637.950024] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 06:08:09 mediaserver kernel: [30637.950033] ata6.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
Apr  3 06:08:09 mediaserver kernel: [30637.950035]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  3 06:08:09 mediaserver kernel: [30637.950037] ata6.00: status: { DRDY }
Apr  3 06:08:09 mediaserver kernel: [30637.950042] ata6: hard resetting link
Apr  3 06:08:09 mediaserver kernel: [30638.011274] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 06:08:09 mediaserver kernel: [30638.011283] ata5.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
Apr  3 06:08:09 mediaserver kernel: [30638.011284]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  3 06:08:09 mediaserver kernel: [30638.011287] ata5.00: status: { DRDY }
Apr  3 06:08:09 mediaserver kernel: [30638.011291] ata5: hard resetting link
Apr  3 06:08:12 mediaserver kernel: [30641.430018] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  3 06:08:12 mediaserver kernel: [30641.441765] ata5.00: configured for UDMA/133
Apr  3 06:08:12 mediaserver kernel: [30641.441780] ata5: EH complete
Apr  3 06:08:13 mediaserver kernel: [30641.661266] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  3 06:08:13 mediaserver kernel: [30641.673148] ata6.00: configured for UDMA/133
Apr  3 06:08:13 mediaserver kernel: [30641.673161] ata6: EH complete

...
...

Apr  3 06:38:09 mediaserver kernel: [32437.982531] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 06:38:09 mediaserver kernel: [32437.982540] ata5.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
Apr  3 06:38:09 mediaserver kernel: [32437.982541]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  3 06:38:09 mediaserver kernel: [32437.982544] ata5.00: status: { DRDY }
Apr  3 06:38:09 mediaserver kernel: [32437.982548] ata5: hard resetting link
Apr  3 06:38:09 mediaserver kernel: [32438.040020] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 06:38:09 mediaserver kernel: [32438.040028] ata6.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
Apr  3 06:38:09 mediaserver kernel: [32438.040029]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  3 06:38:09 mediaserver kernel: [32438.040032] ata6.00: status: { DRDY }
Apr  3 06:38:09 mediaserver kernel: [32438.040036] ata6: hard resetting link
Apr  3 06:38:12 mediaserver kernel: [32441.452502] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  3 06:38:12 mediaserver kernel: [32441.464253] ata5.00: configured for UDMA/133
Apr  3 06:38:12 mediaserver kernel: [32441.464270] ata5: EH complete
Apr  3 06:38:13 mediaserver kernel: [32441.930023] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  3 06:38:13 mediaserver kernel: [32441.941909] ata6.00: configured for UDMA/133
Apr  3 06:38:13 mediaserver kernel: [32441.941928] ata6: EH complete

...
...


Apr  3 07:08:09 mediaserver kernel: [34238.040031] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 07:08:09 mediaserver kernel: [34238.040036] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 07:08:09 mediaserver kernel: [34238.040044] ata6.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
Apr  3 07:08:09 mediaserver kernel: [34238.040046]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  3 07:08:09 mediaserver kernel: [34238.040049] ata6.00: status: { DRDY }
Apr  3 07:08:09 mediaserver kernel: [34238.040055] ata5.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
Apr  3 07:08:09 mediaserver kernel: [34238.040057]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  3 07:08:09 mediaserver kernel: [34238.040060] ata6: hard resetting link
Apr  3 07:08:09 mediaserver kernel: [34238.040063] ata5.00: status: { DRDY }
Apr  3 07:08:09 mediaserver kernel: [34238.040066] ata5: hard resetting link
Apr  3 07:08:12 mediaserver kernel: [34241.450022] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  3 07:08:12 mediaserver kernel: [34241.461767] ata5.00: configured for UDMA/133
Apr  3 07:08:12 mediaserver kernel: [34241.461786] ata5: EH complete
Apr  3 07:08:13 mediaserver kernel: [34241.750260] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  3 07:08:13 mediaserver kernel: [34241.762141] ata6.00: configured for UDMA/133
Apr  3 07:08:13 mediaserver kernel: [34241.762162] ata6: EH complete

...
...


Apr  3 07:38:09 mediaserver kernel: [36037.980033] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 07:38:09 mediaserver kernel: [36037.980042] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 07:38:09 mediaserver kernel: [36037.980053] ata6.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
Apr  3 07:38:09 mediaserver kernel: [36037.980057]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  3 07:38:09 mediaserver kernel: [36037.980063] ata6.00: status: { DRDY }
Apr  3 07:38:09 mediaserver kernel: [36037.980072] ata5.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
Apr  3 07:38:09 mediaserver kernel: [36037.980076]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  3 07:38:09 mediaserver kernel: [36037.980081] ata6: hard resetting link
Apr  3 07:38:09 mediaserver kernel: [36037.980086] ata5.00: status: { DRDY }
Apr  3 07:38:09 mediaserver kernel: [36037.980090] ata5: hard resetting link
Apr  3 07:38:12 mediaserver kernel: [36041.392511] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  3 07:38:12 mediaserver kernel: [36041.404253] ata5.00: configured for UDMA/133
Apr  3 07:38:12 mediaserver kernel: [36041.404273] ata5: EH complete
Apr  3 07:38:13 mediaserver kernel: [36041.811268] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  3 07:38:13 mediaserver kernel: [36041.823151] ata6.00: configured for UDMA/133
Apr  3 07:38:13 mediaserver kernel: [36041.823171] ata6: EH complete

...
...


Apr  3 08:08:09 mediaserver kernel: [37837.982526] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 08:08:09 mediaserver kernel: [37837.982535] ata5.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
Apr  3 08:08:09 mediaserver kernel: [37837.982536]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  3 08:08:09 mediaserver kernel: [37837.982539] ata5.00: status: { DRDY }
Apr  3 08:08:09 mediaserver kernel: [37837.982543] ata5: hard resetting link
Apr  3 08:08:09 mediaserver kernel: [37838.049998] ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Apr  3 08:08:09 mediaserver kernel: [37838.050013] ata6.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
Apr  3 08:08:09 mediaserver kernel: [37838.050015]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
Apr  3 08:08:09 mediaserver kernel: [37838.050018] ata6.00: status: { DRDY }
Apr  3 08:08:09 mediaserver kernel: [37838.050023] ata6: hard resetting link
Apr  3 08:08:12 mediaserver kernel: [37841.391269] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  3 08:08:12 mediaserver kernel: [37841.403017] ata5.00: configured for UDMA/133
Apr  3 08:08:12 mediaserver kernel: [37841.403037] ata5: EH complete
Apr  3 08:08:13 mediaserver kernel: [37841.830020] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  3 08:08:13 mediaserver kernel: [37841.841909] ata6.00: configured for UDMA/133
Apr  3 08:08:13 mediaserver kernel: [37841.841926] ata6: EH complete

. . .
. . .





```

[/FONT][/COLOR]
[/FONT][/COLOR]

---

### Post by supernal on 2010-04-05
Wow, took me a month to get fed up enough to ask for help.
and someone releases a patch to correct for what will be a bug fix

FOr anyone else with this issue, here is the answer

[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/445852)

---

