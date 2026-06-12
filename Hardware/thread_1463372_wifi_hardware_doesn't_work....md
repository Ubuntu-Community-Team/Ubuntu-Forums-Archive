---
title: "wifi hardware doesn't work..."
date: 2010-04-26
forum: Hardware
---

### Post by bzapple8888 on 2010-04-26
Hello, I am very new to ubuntu and looking for some help. I just installed ubuntu 9.10 karmic koala on my laptop and the wireless won't work. I've explored some forums for this problem but they are for older ubuntu releases (6.10 and further). I have a HP pavilion dv5000. Any help would much appreciated. thanks!

also when the lid closes, or the computer goes to sleep the screen will not wake back up when in linux. anyone who knows anything about that would be my savior. thanks. 

BB

---

### Post by Leanderk on 2010-04-26
Limited support for Linux  software  and use more trouble, especially in the 64-bit systems  support. Linux desktop like window  98, the user demanding. this may lead to your wifi incompatible.:guitar:

---

### Post by steveneddy on 2010-04-26
I don't know what poster #2 means.....

But, please in terminal perform these two processes and post in this thread

```
lsusb
```

and

```
lspci
```

remember that if you highlight the text and hit the **#** key at the top of the chat box it will put it in the code tags for you.

This will help us determine without a doubt the brand and model of your wireless chip.

---

### Post by bzapple8888 on 2010-04-27
Here is the code out put from the commands.
```
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```
PS. I was confused as to what #2 was saying as well. thanks for the help!

---

### Post by gordintoronto on 2010-04-27
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/how-to-for-the-bcm4318-airforce-one-card-473194/)

It's quite old, there might be a simpler solution.

---

### Post by coffeecat on 2010-04-27
This is your wireless chipset:

> **bzapple8888 said:**
> ```
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

The problem with Broadcom wireless chips is that licensing issues prevent the firmware from being included in a default install. Have a look at:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Your BCM4318 is not listed as being supported by the STA hybrid driver but that doesn't necessarily mean that it isn't. Try the STA driver and/or b43-fwcutter if you can connect to the internet with your ethernet interface. If you can't connect to the internet, you can install the STA driver from the CD by enabling the CD as a repository. The instructions are in that link. There's also something on using ndiswrapper and the Windows driver, but that's a last resort.

Good Luck!

By the way....

> **bzapple8888 said:**
> I was confused as to what #2 was saying as well.

Possibly a spammer posting non-specific stuff to establish a posting record before the real spam links appear. The weird syntax makes me suspicious. I'll report this to the mods so that they can keep an eye on this one.

---

### Post by drbobb on 2010-05-03
Dealing with the same problem as the OP. Same chip, too - BCM4318 [14e4:4318]. The solution involving the b43 driver and b43-fwcutter worked great in karmic, but no longer works in lucid. The chip is recognized and a connection is established, but is dropped within a minute or so. I'll be trying other router settings, but if Wifi can be made to work only by fine-tuning the AP, that's a non-solution. 

The Broadcom proprietary driver positively does not support this chip.

---

### Post by bzapple8888 on 2010-05-03
Thanks to all that helped. I managed (with the help of a Ubuntu savvy friend) to get the wifi working! thanks so much!!

---

