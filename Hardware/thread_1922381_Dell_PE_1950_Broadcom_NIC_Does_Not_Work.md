---
title: "Dell PE 1950 Broadcom NIC Does Not Work"
date: 2012-02-08
forum: Hardware
---

### Post by paysonwelch on 2012-02-08
I installed Ubuntu on two Dell Poweredge 1950 servers today, both have a Broadcom NetXtreme II BCM5708 network adapter.  The Ubuntu website says that these adapters are fully supported however DHCP and autoconfiguration do not work.  Also when I use manual configuration it does not work. 

I tested both NICs by loading Windows and CentOS on each server, DHCP and manual configuration works on both.

Is there an open bug for the BCM5708?  I can see the adapter when I run ifconfig, the lights are on, it works no problem on other OSs.  Any ideas?

---

### Post by joshuamichaelsanders on 2012-06-26
Did you ever get this problem resolved. I have a PowerEdge 1950 with the Broadcom NICs and 11.10 isn't picking them up out of the box?
-J

---

### Post by josephmills on 2012-06-26
please open yu terminal (ctrl+alt+t)
and enter in 
```
lspci -nn
```
and 
```
lsmod
```
and 
```
lsusb
```
then 
```
rfkill list all 
```
then paste that all here 
Thanks

---

### Post by joshuamichaelsanders on 2012-06-26
> **josephmills said:**
> please open yu terminal (ctrl+alt+t)
and enter in 
```
lspci -nn
```and 
```
lsmod
```and 
```
lsusb
```then 
```
rfkill list all 
```then paste that all here 
Thanks


Here they are. I couldn't run rfkill. It appears to be not installed on the machine. If I run apt-get install, since I have no network connection it fails.

```
00:00.0 Host bridge [0600]: Intel Corporation 5000X Chipset Memory Controller Hub [8086:25c0] (rev 12)
00:02.0 PCI bridge [0604]: Intel Corporation 5000 Series Chipset PCI Express x4 Port 2 [8086:25e2] (rev 12)
00:03.0 PCI bridge [0604]: Intel Corporation 5000 Series Chipset PCI Express x4 Port 3 [8086:25e3] (rev 12)
00:04.0 PCI bridge [0604]: Intel Corporation 5000 Series Chipset PCI Express x8 Port 4-5 [8086:25f8] (rev 12)
00:05.0 PCI bridge [0604]: Intel Corporation 5000 Series Chipset PCI Express x4 Port 5 [8086:25e5] (rev 12)
00:06.0 PCI bridge [0604]: Intel Corporation 5000 Series Chipset PCI Express x8 Port 6-7 [8086:25f9] (rev 12)
00:07.0 PCI bridge [0604]: Intel Corporation 5000 Series Chipset PCI Express x4 Port 7 [8086:25e7] (rev 12)
00:10.0 Host bridge [0600]: Intel Corporation 5000 Series Chipset FSB Registers [8086:25f0] (rev 12)
00:10.1 Host bridge [0600]: Intel Corporation 5000 Series Chipset FSB Registers [8086:25f0] (rev 12)
00:10.2 Host bridge [0600]: Intel Corporation 5000 Series Chipset FSB Registers [8086:25f0] (rev 12)
00:11.0 Host bridge [0600]: Intel Corporation 5000 Series Chipset Reserved Registers [8086:25f1] (rev 12)
00:13.0 Host bridge [0600]: Intel Corporation 5000 Series Chipset Reserved Registers [8086:25f3] (rev 12)
00:15.0 Host bridge [0600]: Intel Corporation 5000 Series Chipset FBD Registers [8086:25f5] (rev 12)
00:16.0 Host bridge [0600]: Intel Corporation 5000 Series Chipset FBD Registers [8086:25f6] (rev 12)
00:1c.0 PCI bridge [0604]: Intel Corporation 631xESB/632xESB/3100 Chipset PCI Express Root Port 1 [8086:2690] (rev 09)
00:1d.0 USB Controller [0c03]: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #1 [8086:2688] (rev 09)
00:1d.1 USB Controller [0c03]: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #2 [8086:2689] (rev 09)
00:1d.2 USB Controller [0c03]: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #3 [8086:268a] (rev 09)
00:1d.3 USB Controller [0c03]: Intel Corporation 631xESB/632xESB/3100 Chipset UHCI USB Controller #4 [8086:268b] (rev 09)
00:1d.7 USB Controller [0c03]: Intel Corporation 631xESB/632xESB/3100 Chipset EHCI USB2 Controller [8086:268c] (rev 09)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d9)
00:1f.0 ISA bridge [0601]: Intel Corporation 631xESB/632xESB/3100 Chipset LPC Interface Controller [8086:2670] (rev 09)
00:1f.1 IDE interface [0101]: Intel Corporation 631xESB/632xESB IDE Controller [8086:269e] (rev 09)
01:00.0 RAID bus controller [0104]: LSI Logic / Symbios Logic MegaRAID SAS 1078 [1000:0060] (rev 04)
02:00.0 PCI bridge [0604]: Broadcom EPB PCI-Express to PCI-X Bridge [1166:0103] (rev c3)
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet [14e4:164c] (rev 12)
04:00.0 PCI bridge [0604]: Intel Corporation 6311ESB/6321ESB PCI Express Upstream Port [8086:3500] (rev 01)
04:00.3 PCI bridge [0604]: Intel Corporation 6311ESB/6321ESB PCI Express to PCI-X Bridge [8086:350c] (rev 01)
05:00.0 PCI bridge [0604]: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E1 [8086:3510] (rev 01)
05:01.0 PCI bridge [0604]: Intel Corporation 6311ESB/6321ESB PCI Express Downstream Port E2 [8086:3514] (rev 01)
06:00.0 PCI bridge [0604]: Broadcom EPB PCI-Express to PCI-X Bridge [1166:0103] (rev c3)
07:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme II BCM5708 Gigabit Ethernet [14e4:164c] (rev 12)
0e:0d.0 VGA compatible controller [0300]: ATI Technologies Inc ES1000 [1002:515e] (rev 02)
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
radeon                961723  1 
shpchp                 32356  0 
psmouse                63474  0 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
i5000_edac             17435  0 
ghes                   13360  0 
drm                   196322  3 radeon,ttm,drm_kms_helper
edac_core              46858  3 i5000_edac
dcdbas                 14098  0 
hed                    13066  1 ghes
i2c_algo_bit           13199  1 radeon
lp                     17455  0 
serio_raw              12990  0 
i5k_amb                13072  0 
parport                40930  1 lp
ses                    17217  0 
enclosure              14744  1 ses
usb_storage            44173  1 
uas                    17699  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
bnx2                   76868  0 
megaraid_sas           73078  8 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 003 Device 002: ID 09ae:0002 Tripp Lite 
Bus 001 Device 004: ID 090c:1000 Feiya Technology Corp. Flash Drive
```

---

### Post by josephmills on 2012-06-26
I am sorry but I am not that familiar with that card. I wish I could help more. Good luck I am sure that someone will come along :)

---

### Post by DELL JonathanS on 2012-06-27
The PE1950 has two integrated Broadcom 5708 Ethernet ports and both seem to be correctly identified in the lspci output. From the lsmod output you appear to have the correct driver loaded, bnx2, though it shows not in use, so I would not expect the ports to be represented in the output of ifconfig. I understand apt-get isn't able to access the network but Windows and CentOS are able to. From Ubuntu, are you able to access other network resources such as pinging the gateway or any other hosts on the same LAN?
 
Do you get any error or other output when attempting to assign an address i.e.:
```

ifconfig eth0 10.1.2.3 netmask 255.248.0.0

```
 
What does ifconfig -a look like after attempting to manually assign?
 
Also can you please paste the output of this command:
```

ethtool eth0

```
for each interface mentioned in the output of "ifconfig -a"?
 
The PE1950 also supports PCI-e or PCI-X expansion NICs depending on the riser -- out of curiosity do you have any expansion NICs installed as well? It doesn't appear so from the lspci output, just wondering. I hope we can get this sorted out!

---

