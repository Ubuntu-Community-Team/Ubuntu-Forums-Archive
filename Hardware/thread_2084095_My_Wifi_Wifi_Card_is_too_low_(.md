---
title: "My Wifi Wifi Card is too low :("
date: 2012-11-14
forum: Hardware
---

### Post by sohaieb on 2012-11-14
Hello every body , My wifi card is very low in ubuntu , I try to connect with the same wifi card in win7 , it worked correctly , but in ubuntu it's very low , here is my lspci output:

lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Whistler XT [AMD Radeon HD 6700M Series]
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
0d:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
13:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
19:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)


Help Me please and thank you .

---

### Post by dannyboy79 on 2012-11-14
not sure what you mean by "too low". Are you saying it's running very slow? IF so, it may be related to this filed bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/951709](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/951709)

---

### Post by sohaieb on 2012-11-14
Hello sir , thanks for this fast reply , and I mean that the internet is very slow , and i think , that wifi configuration causes this problem because I tried woking with it in the same PC but with windows 7 , it worked correctly , but in ubuntu it worked very slow :( any help so?

---

### Post by dannyboy79 on 2012-11-14
read the link I posted, there is a solution to the slow wifi internet.

---

### Post by sohaieb on 2012-11-16
> **dannyboy79 said:**
> read the link I posted, there is a solution to the slow wifi internet.

Hello sir , I followed all instruction in the link , but nothing is done :( and I have did this command :

```
lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Kernel driver in use: r8169
	Kernel modules: r8169
0d:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Kernel driver in use: ath9k
	Kernel modules: ath9k
```
can any one give me another solution please?

---

### Post by dannyboy79 on 2012-11-16
so you did all this as well?

```
sudo modprobe -rfv ath9k
```
```
sudo modprobe -v ath9k nohwcrypt=1
```

it's explained a little better here:
[http://ubuntuforums.org/showthread.php?mode=hybrid&t=1942326&highlight=atheros+acer+722](http://ubuntuforums.org/showthread.php?mode=hybrid&t=1942326&highlight=atheros+acer+722)

---

