---
title: "Networking: Broadcom 4401 and k/ubuntu"
date: 2006-04-27
forum: Hardware &amp; Laptops
---

### Post by toxi-city on 2006-04-27
dear all
i'm running a kubuntu [2.6] on my notebook, acer travelmate 4022 with Broadcom
440x 10/100 NIC. i tried to configure my ethernet card, but it jams the
network!!

lspci and ifconfig read:

[FONT="Courier New"][SIZE="2"]mo@wildkat:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corp. Mobile Graphics
Controller (rev 03)
0000:00:02.1 Display controller: Intel Corp. Mobile Graphics Controller
(rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family)
PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family)
PCI Express Port 2 (rev 04)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family)
PCI Express Port 3 (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6
Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6
Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6
Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6
Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6
Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corp.
82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97
Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge
(rev 04)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6
Family) IDE Controller (rev 04)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus
Controller (rev 04)
0000:06:01.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:06:03.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T
(rev 02)[/SIZE][/FONT]

# ifconfig shows:

[FONT="Courier New"][SIZE="2"]eth1 Link encap:Ethernet HWaddr 00:C0:9F:C4:59:5F
inet addr:192.168.10.238 Bcast:192.168.10.255 Mask:255.255.255.0
inet6 addr: fe80::2c0:9fff:fec4:595f/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:190 errors:0 dropped:0 overruns:0 frame:0
TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:12996 (12.6 KiB) TX bytes:1526 (1.4 KiB)
Interrupt:10
[/SIZE][/FONT]


although, it worked perfectly on knoppix and suse live cd 9.1. can any one help? You can have [more information from this thread]("http://www.debianhelp.org/module-pnForum-viewtopic-topic-11242-start-0.html")
 
thanks
mo

---

