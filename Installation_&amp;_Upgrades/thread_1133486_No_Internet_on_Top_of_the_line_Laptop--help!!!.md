---
title: "No Internet on Top of the line Laptop--help!!!"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by rreyes1316 on 2009-04-23
While my frien was ill about 2 years ago. We would joke about his assets and how much I wanted his laptop. It was our way of trying to shed some humor on his renal failure and dire need of a kidney. Well . . .he decided to send it to me and there really is not much that can be done with it. He had XP Pro on it--which was very straining on it--and I decided to put Xubuntu on it. We both decided this would be the year we would boot windows and move over to Ubuntu. I am about 90% converted but have a few issues to iron out on my pc. 

Anyhow, as a learning tool and for the experience, I have been toying with his laptop he gave me. This is what we have to work with:

Powerful Intel Celeron Performance, 700 MHZ of blazing fast PIII performance, 24 X CDRom, Dual Scan 13" screen, 64 megs(upgraded to 128) of on board memory (upgraded to 192 megs), a hefty 10 gig hard drive for plenty of storage, built in floppy drive, on board 56K V90 modem, 4 megs on board video, 100 MHZ front size bus, 128 bit PC 100 front side bus, stereo speakers, Wi-Fi compatible, serial port, parallel port, RJ45 jack, 2 PCMCIA slots, 2 USB.

Aside from the futuristic specs, it actually works with Xubuntu as a web browser--if I could get it connected to the Net, however. So I hope you can help.

Thank

---

### Post by tommcd on 2009-04-23
How are you trying to connect to the internet? From ethernet? wireless? Are you using cable, DSL, or something else? Do you use dhcp or static ip address?
Open up a terminal and run:
```
lspci -v
```
Your ethernet and wireless devices will be near the end of that output. Post those parts of lspci here.
Also run 
```

ifconfig

```
and
```
ifconfig -a
```
and post the output of those as well. 
Getting connected via wired ethernet should not be difficult.

---

### Post by rreyes1316 on 2009-04-23
Um, DUH!!! My bad . . .I forgot to mention that detail:eek:

I am trying to connect with the RJ45 dsl cable. I am connecting through a lynksys router--I have comcast. I was trying to use the ViewSonic PCMCIA Wireless 802.11g PC Card my buddy gave me, byt that did nor work either :(

---

### Post by rreyes1316 on 2009-04-23
DAMN that took a while--sorry.

Hope I have all the info correct. Here it is:


lspci -v

Communication Controller : Agere System LT WinModem
Subsystem:Askey Computer Corp. Device 4005
Flags: medium devsel, IRQ 10
Memory at fc011000 (32-bit, non-prefetchable) [disabled] [size=256]
I/O ports at 1080 [disabled] [size=8]
I/O ports at 1400 [disabled] [size=256]
Capabilities: <access denied>

Network controller: Broadcom Corporation BCM4306 802.11b/g wireless LAN Controller (rev 03)
Subsystem: Device 0543:1a10
Flags: bus master, fast devsel, latency 64, IRQ 10
Memory at 1c000000 (32-bit, non-prefetchable) [size=8k]
kernal driver in use: b43-pci-bridge
kernel modules: ssb

ipconfig

bash: ipconfig: command not found

ipconfig -a

bash: ipconfig: command not found

---

### Post by tommcd on 2009-04-23
[QUOTE=rreyes1316;7123563
I am trying to connect with the RJ45 dsl cable. I am connecting through a lynksys router--I have comcast. I was trying to use the ViewSonic PCMCIA Wireless 802.11g PC Card my buddy gave me, byt that did nor work either :([/QUOTE]
So you have cable internet and connect via dhcp? Is that correct?

---

### Post by rreyes1316 on 2009-04-23
yes

I appreciate your help, thanks in advance.

---

### Post by tommcd on 2009-04-23
> **rreyes1316 said:**
> 
lspci -v
Communication Controller : Agere System LT WinModem
Subsystem:Askey Computer Corp. Device 4005

Network controller: Broadcom Corporation BCM4306 802.11b/g wireless LAN Controller (rev 03)

ipconfig

It is **ifconfig** and **ifconfig -a**, not iPconfig. 
It looks like you have a dial-up modem, and a wireless card. And you have no ethernet jack on the laptop. Is that correct?

For your Broadcom wireless, see these guides:
[http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/](http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
First, disable all encryption on the router, then try to connect via the wireless. If you can connect, then post what kind of encryption you are using (if any) and we can go from there.

---

### Post by rreyes1316 on 2009-04-23
here it is again. I thought it was "IP" not "IF":


laptop@laptop-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
	Flags: bus master, medium devsel, latency 64
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
	Flags: bus master, 66MHz, medium devsel, latency 128
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: fc100000-fdffffff
	Prefetchable memory behind bridge: 20000000-200fffff
	Kernel modules: shpchp

00:04.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at 20100000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 10000000-13fff000 (prefetchable)
	Memory window 1: 14000000-17fff000
	I/O window 0: 00001800-000018ff
	I/O window 1: 00001c00-00001cff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

00:04.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 168, IRQ 10
	Memory at 20101000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
	Memory window 0: 18000000-1bfff000 (prefetchable)
	Memory window 1: 1c000000-1ffff000
	I/O window 0: 00003000-000030ff
	I/O window 1: 00003400-000034ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
	Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
	Flags: bus master, medium devsel, latency 64
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 1050 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
	Flags: bus master, medium devsel, latency 64, IRQ 10
	I/O ports at 1060 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
	Flags: medium devsel, IRQ 9
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:08.0 Multimedia audio controller: Cirrus Logic Crystal CS4281 PCI Audio (rev 01)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at fc010000 (32-bit, non-prefetchable) [size=4K]
	Memory at fc000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: CS4281
	Kernel modules: snd-cs4281

00:10.0 Communication controller: Agere Systems LT WinModem
	Subsystem: Askey Computer Corp. Device 4005
	Flags: medium devsel, IRQ 10
	Memory at fc011000 (32-bit, non-prefetchable) [disabled] [size=256]
	I/O ports at 1080 [disabled] [size=8]
	I/O ports at 1400 [disabled] [size=256]
	Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility P/M AGP 2x (rev 64)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, stepping, medium devsel, latency 66, IRQ 10
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	I/O ports at 2000 [size=256]
	Memory at fc100000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 20000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: atyfb

06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
	Subsystem: Device 0543:1a10
	Flags: bus master, fast devsel, latency 64, IRQ 10
	Memory at 1c000000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

laptop@laptop-laptop:~$ ipconfig
bash: ipconfig: command not found
laptop@laptop-laptop:~$ ipconfig -a
bash: ipconfig: command not found
laptop@laptop-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:644 (644.0 B)  TX bytes:644 (644.0 B)

laptop@laptop-laptop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:644 (644.0 B)  TX bytes:644 (644.0 B)

pan0      Link encap:Ethernet  HWaddr 02:46:10:4f:56:4f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:bd:1e:99  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-BD-1E-99-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Also, there is a eternet jack.

---

### Post by tommcd on 2009-04-23
So how are you trying to connect to the internet? Are you trying to connect via ethernet and dhcp via comcast cable? Do you have an ethernet cable plugged in?
Or are you trying to connect via wireless??

Once again,
Are you trying to connect via ethernet???
Or wireless???

---

### Post by rreyes1316 on 2009-04-23
Sorry about that. It was late and have to work.

Right now, I am trying to connect via ethernet.

Once I get that up and running I will try wireless.

---

### Post by tommcd on 2009-04-23
Your output of lspci indicates you have:
Agere Systems LT WinModem 
Broadcom BCM4306
A "winmodem" usually means a dial-up modem and not an ethernet device. I would not know how to connect with that.
You may have better luck with the Broadcom wireless. First, disable any encryption on the router for wireless, then follow the 2 guides I linked to in post #7 of this thread.
This of course  assumes that your router has wireless capability.

---

### Post by SnaveDogg on 2009-04-24
> **tommcd said:**
> How are you trying to connect to the internet? From ethernet? wireless? Are you using cable, DSL, or something else? Do you use dhcp or static ip address?
Open up a terminal and run:
```
lspci -v
```Your ethernet and wireless devices will be near the end of that output. Post those parts of lspci here.
Also run 
```

ifconfig

```and
```
ifconfig -a
```and post the output of those as well. 
Getting connected via wired ethernet should not be difficult.

[br]

I too am having trouble connecting to the internet. Question: How will I determine if I use Static IP or DHCP? I do not know enough about that stuff to make an informed choice. I'm in the dark...

---

### Post by tommcd on 2009-04-24
> **SnaveDogg said:**
> [br]
I too am having trouble connecting to the internet. Question: How will I determine if I use Static IP or DHCP? I do not know enough about that stuff to make an informed choice. I'm in the dark...
How are you connecting now? ethernet? wireless? Unless your ISP issued you a static IP address, or you set up static IP addresses on a home network, then you are likely using dhcp.
Post the ouput of:
```

lspci
ifconfig
ifconfig -a

```

---

