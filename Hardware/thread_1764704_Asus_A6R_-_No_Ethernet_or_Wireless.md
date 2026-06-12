---
title: "Asus A6R - No Ethernet or Wireless"
date: 2011-05-22
forum: Hardware
---

### Post by lordsloth on 2011-05-22
Hi,

I've just installed 10.10 on to an Asus A6R notebook and all seems to run just fine except I have no ethernet or wireless at all. All the other hardware seems to work just fine.  I tried 11.04 and had the same issue. They worked just fine when I had windows 7 on the machine so I know they work.

Any Help would be much appreciated, I've no idea where to start!

Thanks.

---

### Post by sanderj on 2011-05-22
> **lordsloth said:**
> Hi,

I've just installed 10.10 on to an Asus A6R notebook and all seems to run just fine except I have no ethernet or wireless at all. All the other hardware seems to work just fine.  I tried 11.04 and had the same issue. They worked just fine when I had windows 7 on the machine so I know they work.

Any Help would be much appreciated, I've no idea where to start!

Thanks.

Your *wired* ethernet not working? Interesting. Your ethernet cable is correctly connected on both sides?

If so, post the output of

```

ifconfig
lspci
lsusb

```

here in this forum. A picture of the output is also OK if you can't get the output in text format.

---

### Post by lordsloth on 2011-05-22
Hi Sanderj,

Yeah the Wired Ethernet isn't working. The cable is correctly connected and I've unplugged my other notebook from the ethernet (works 100%) and connected it to the Asus and still no joy.

Here are the outputs:

sasha@sashaPC:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:d4:c1:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)




sasha@sashaPC:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)



sasha@sashaPC:~$ lsusb
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 067b:2517 Prolific Technology, Inc. Flash Disk Mass Storage Device
Bus 001 Device 004: ID 067b:2515 Prolific Technology, Inc. Flash Disk Embedded Hub
Bus 001 Device 003: ID 174f:a311 Syntek 1.3MPixel Web Cam - Asus A3A, A6J, A6K, A6M, A6R, A6T, A6V, A7T, A7sv, A7U
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sasha@sashaPC:~$

---

### Post by sanderj on 2011-05-22
AFAIK, that's very normal ethernet card:


```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

Next test: the output of "dmesg | grep -i eth". Hopefully it will tell the kernel driver and whether it sees a link up on the ethernet interface.


EDIT:

Oh, PS: you did leave Ubuntu IP address default settings on (thus DHCP), and you have a DHCP-server (like a modem/router) on your LAN?

---

### Post by lordsloth on 2011-05-22
I've tried setting a static IP and entering the mask and gateway manually. When that didn't work i set it back to DHCP. I have my router set up as a DHCP server on my LAN and it serves the 3 other PCs and a few iphones nicely.

Here's the Output:

sasha@sashaPC:~$ dmesg | grep -i eth
[    0.848717] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    0.930977] 8139too: 8139too Fast Ethernet driver 0.9.28
[    0.949508] 8139too 0000:02:00.0: eth0: RealTek RTL8139 at 0xb800, 00:1a:92:d4:c1:70, IRQ 20
[   14.396015] eth0: link down
[   14.396400] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by sanderj on 2011-05-22
> **lordsloth said:**
> I've tried setting a static IP and entering the mask and gateway manually. When that didn't work i set it back to DHCP. I have my router set up as a DHCP server on my LAN and it serves the 3 other PCs and a few iphones nicely.

Here's the Output:

sasha@sashaPC:~$ dmesg | grep -i eth
[    0.848717] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    0.930977] 8139too: 8139too Fast Ethernet driver 0.9.28
[    0.949508] 8139too 0000:02:00.0: eth0: RealTek RTL8139 at 0xb800, 00:1a:92:d4:c1:70, IRQ 20
[   14.396015] eth0: link down
[   14.396400] ADDRCONF(NETDEV_UP): eth0: link is not ready

Well, "[ 14.396015] eth0: link down" is bad; it means there is no ethernet link. So once again check the ethernet cable. Check the LED(s) in your laptop and in your modem/router are on, and turn off when you remove the ethernet cable. And try another cable and another modem/router port.


EDIT:

And please leave your settings on DHCP. Chaning those settings is asking for problems...

---

### Post by lordsloth on 2011-05-22
Swapped out Ethernet cable for a known good cable, swapped to the ethernet port that was working fine on my other laptop. No LEDs on the laptop but nothing happens on the router when the cable is connected or removed. This laptop was working fine yesterday before i removed Win 7 so i can only assume the Ethernet port is working.

Anything else I can try? What does it mean when it says the link is not ready?

Thanks for your help.

---

### Post by lordsloth on 2011-05-22
I found the solution!

So the output that said "Link is not ready" gave me an idea: Google it :)
Here's the link to the thread that solved the problem: 

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

The solution was to unplug and remove the battery from the notebook, wait for all the power to drain and then make sure the Ethernet cable is connected when the machine boots.

Thanks for all your help sanderj!!

---

### Post by sanderj on 2011-05-22
Fascinating!


Now your wireless: If needed, Ubuntu will offer proprietary drivers with a green, pci-card like icon in the upper right corner. I don't know if a (wired) Internet is needed for that.

You should now be able to browse the available WLANs.

---

