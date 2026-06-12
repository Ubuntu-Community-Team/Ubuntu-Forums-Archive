---
title: "Installing a gig nic"
date: 2006-07-21
forum: Hardware &amp; Laptops
---

### Post by mallen on 2006-07-21
Ive got a intel pro 1000t ( Intel® 82544 Gigabit Ethernet Controllers ) and I cant get this card installed on my ubuntu machine,. I have looked and looked online for hours now and I cant find any damn help about it. Mind you I have only been working with linux for 2 weeks so Im a total retard with this. Ill need step by step instructions on doing this so any help is GREATLY appreciated.

---

### Post by Ocxic on 2006-07-22
have you tried simply installing the card and plugin the eathernet cable? it all I've ever had to do?

---

### Post by mallen on 2006-07-22
Why do you think I asked this question? Its obviously plugged into the pci slot and I cant get it installed on the os......and yes it does work because I had fedora on this before.

---

### Post by costoa on 2006-07-22
Could you post the dump from "dmesg | grep eth" svp?

---

### Post by mallen on 2006-07-24
what???

---

### Post by damien.yep on 2006-07-24
can you post the result of:
$dmesg | grep eth

It will help us to understand your problem, thx.

Damien.

---

### Post by mallen on 2006-07-24
the terminal isnt picking up that command at all....unless im dumb and doing it wrong. Im new to ubuntu..:\

---

### Post by damien.yep on 2006-07-25
What do you mean "the terminal isnt picking up that command at all", do you have an error, or is it that nothing is displayed when you execute the command?

Damien.

---

### Post by mallen on 2006-07-25
...it does nothing. I put that command in and all it does is act like nothing  was ever entered.

---

### Post by damien.yep on 2006-07-25
This means you don't have "eth" on your dmesg log.

can you give us more info about your card? you can type:
$lspci
an post the output of this command.

---

### Post by mallen on 2006-07-25
with command dmesg | grep eth
[42949391.890000] e100: eth0: e100_probe: addr 0xf8440000, irq 209, MAC addr 00:0B:CD:21:2B:82
[42949392.590000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection[42949429.430000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[42949683.520000] e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
[42949683.530000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[42949694.170000] eth1: no IPv6 routers present

[COLOR="Blue"]with command lspci
0000:00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
0000:00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)
0000:05:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VM (LOM) Ethernet Controller (rev 81)
0000:05:09.0 Ethernet controller: Intel Corporation 82544GC Gigabit Ethernet Controller (Copper) (rev 02)[/COLOR]

---

### Post by damien.yep on 2006-07-25
from the log, it seams your lan card is up:
"eth1: e100_watchdog: link up, 100Mbps, full-duplex"

your Gigabit card is eth1 (eth0 is the other lan card). Can't you configure it via:
$sudo ifconfig eth1 192.168.0.1

check if eth1 is correctly configured via:
$ifconfig

(you should have information displayed about eth1 configuration like:
```

eth1      Lien encap:Ethernet  HWaddr 00:0B:6A:BB:2D:1F
          inet adr:192.168.0.3  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::20b:6aff:febb:2d1f/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:980484 erreurs:0 :0 overruns:0 frame:0
          TX packets:1162863 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:643183565 (613.3 MiB) Octets transmis:666204051 (635.3 MiB)
          Interruption:217 Adresse de base:0xbc00
```
)

and if eth1 is correctly configured, ping it via:
$ping 192.168.0.1

Maybe you should put a different address, I don't know your network configuration (is there a DHCP server, what is the address of other computer you whant to access...)

---

