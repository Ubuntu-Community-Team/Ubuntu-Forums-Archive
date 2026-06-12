---
title: "wireless card not found on toshiba laptop"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by hunteramor on 2005-11-08
I have a Toshiba A25 S207 laptop dual-booting XP and Ubuntu with an integrated wireless card.  It works fine in XP, but I don't think the card is being recognized by linux.

The output from ifconfig -a is:
>  eth0 Link encap:Ethernet HWaddr 00:00:39:EA:F15
inet addr:192.168.1.100 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::200:39ff:feea:f1d5/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:61073 errors:0 dropped:0 overruns:0 frame:0
TX packets:56970 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:60197863 (57.4 MiB) TX bytes:7869908 (7.5 MiB)
Interrupt:11 Base address:0xed00

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:224330 errors:0 dropped:0 overruns:0 frame:0
TX packets:224330 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:73560245 (70.1 MiB) TX bytes:73560245 (70.1 MiB)

sit0 Link encap:IPv6-in-IPv4
NOARP MTU:1480 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

and from lspci: 
> 0000:00:00.0 Host bridge: ALi Corporation: Unknown device 1672
0000:00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
0000:00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0c.0 USB Controller: NEC Corporation USB (rev 43)
0000:00:0c.1 USB Controller: NEC Corporation USB (rev 43)
0000:00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:00:10.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
0000:00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 33)
0000:00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
0000:01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)


i've installed the driver for the card using ndiswrapper, but ndiswrapper -l still shows:> 
Installed ndis drivers:
net5211 driver present

when i think it should have "driver present, hardware present"

does it look like my card is being recognized at all?  why wouldn't it be?

---

### Post by jml on 2005-11-08
It seems that the card is not being recognized.
The actual chipset in the wireless card may not be supported.  Try looking up what chip set your laptop uses.  That information might be listed in your laptop's owner's manual.  If its not there, you might try finding the spec. sheat for your laptop on the Toshiba web site.  Failing that, try 'googling" for the information.  If it is supported, you might want to see if there are different drivers for the card and try those.  Getting wireless working in Linux is a real challenge. Good luck.

Joe

---

