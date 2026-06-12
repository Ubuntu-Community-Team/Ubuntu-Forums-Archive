---
title: "wifi problem"
date: 2005-12-05
forum: General Help
---

### Post by JamesA on 2005-12-05
Hey guys, this is my very first post and i am a total idiot when it comes to ubuntu.:D 

Now i've never used wifi with linux ever before so i hope my questions don't seem too trivial. My wifi card is detected by ubuntu and is active on eth1, the driver it uses is ipw2100, however i do not know how to use it.

I installed wifi-radar but no wireless connections seem to come up, the same is for gtkwifi. However if i scan on windows i find networks to connect to, so its not that there isn't actually no networks.

I connect to the internet using my ethernet modem on eth0, is there anyfiles i should be editing to get my card to actually scan for networks.

My laptop that is running ubuntu is a dell inspiron 8600.

Thanks.

---

### Post by odin on 2005-12-05
If your card is detected and working try by opening a terminal and type this:

sudo iwconfig eth1 scan

then you'll see a list of networks.After this type:

sudo iwconfig eth1 essid "your_network name"

and after that you have to options:
  
for dhcp:

dhclient eth1

and for static ip:

ifconfig eth1 ip_you_want netmask your_netmask
route add default gw your_gateway

hope this helps :smile:

---

### Post by JamesA on 2005-12-05
Thanks man, will try that when i get home ;).

---

### Post by hedone on 2005-12-05
and if there is no lan card recognised use ndiswrapper to install it... and i still think that NetworkManager is best solution to use WiFi in Gnome!

---

### Post by hw-tph on 2005-12-05
[QUOTE=hedone]and if there is no lan card recognised use ndiswrapper to install it...[/QUOTE]

Who would install the [evil](http://acx100.sourceforge.net/ndis_cludge.html) ndiswrapper crap when there are actually [real device drivers available](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=N&ProductID=944&DwnldID=6649&strOSs=39&OSFullName=Linux*&lang=eng) for it?

The command to scan for available networks would be **iwlist**, not **iwconfig**l.

H&#229;kan

---

### Post by JamesA on 2005-12-05
James@tux:~$ sudo iwconfig eth1 scan
Password:
Error : unrecognised wireless request "scan"



hmmm, ideas?:???:

---

### Post by hw-tph on 2005-12-06
Like I wrote in my post above, the command is iwlist, not iwscan:
**sudo iwlist eth1 scan**


Håkan

---

### Post by JamesA on 2005-12-06
> **hw-tph]Like I wrote in my post above, the command is iwlist, not iwscan:
**sudo iwlist eth1 scan**


H&#229 said:**
> 

ah ok, sorry about that. The results of that command are
:eth1      No scan results

Perhaps i should i post more information because i really need my wifi working.

My wifi card is a PRO/Wireless LAN 2100 3B Mini PCI Adapter. I'm assuing its detected because ubuntus network settings shows this:

[IMG]http://www.minds.may.ie/~jahova/images/network-settings.jpg[/IMG]

 **iwconfig** gives the following.
> 
o        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

**ifconfig** returns this
[quote]
eth0      Link encap:Ethernet  HWaddr 00:0D:56:AD:B9:86
          inet addr:10.0.0.14  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fead:b986/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11205 errors:18 dropped:9 overruns:0 frame:4
          TX packets:10501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11351173 (10.8 MiB)  TX bytes:1685436 (1.6 MiB)
          Interrupt:11

eth1      Link encap:Ethernet  HWaddr 00:04:23:98:8E:8B
          inet6 addr: fe80::204:23ff:fe98:8e8b/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x6000 Memory:faffc000-faffcfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:306119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:306119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:26135191 (24.9 MiB)  TX bytes:26135191 (24.9 MiB)


and **lspci -v** returns this
> 
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
        Subsystem: Dell: Unknown device 016a
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: d0000000-dfffffff

0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 016a
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf80 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 016a
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf40 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell: Unknown device 016a
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf20 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell: Unknown device 016a
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at f4fffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000d000-0000efff
        Memory behind bridge: f6000000-fbffffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell: Unknown device 016a
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at bfa0 [size=16]
        Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell: Unknown device 016a
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at b800 [size=256]
        I/O ports at bc40 [size=64]
        Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
        Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
        Subsystem: Broadcom Corporation: Unknown device 4d64
        Flags: medium devsel, IRQ 5
        I/O ports at b400 [size=256]
        I/O ports at b080 [size=128]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go 5200] (rev a1) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 019c
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Expansion ROM at 80000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
        Subsystem: Dell: Unknown device 8127
        Flags: bus master, fast devsel, latency 32, IRQ 11
        Memory at faffe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <available only to root>

0000:02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
        Subsystem: Dell: Unknown device 016a
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 20001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 20400000-207ff000 (prefetchable)
        Memory window 1: 20800000-20bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller (prog-if 10 [OHCI])
        Subsystem: Dell: Unknown device 016a
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at faffd800 (32-bit, non-prefetchable) [size=2K]
        Memory at faff8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:02:03.0 Network controller: Intel Corp. PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corp.: Unknown device 2561
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at faffc000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>


I hope this information is usefull, i just seen other people having simular problems showing this information on the forum, i am absolutley clueless. Also it should be said im using a ethernet router+modem on eth0 to connect to the internet at this moment, would that have negetive effects on the wireless card?

Thanks in advance :)
James.

---

