---
title: "Bluetooth can't find new devices"
date: 2014-11-04
forum: Hardware
---

### Post by brilliantcontract on 2014-11-04
[IMG]http://i62.tinypic.com/j0wsc1.png[/IMG]

When I click on "Set Up New Device ..." in popup window "Bluetooth New Device Setup" I get message "Searching for new devices..." and it's all, I can't select next menu item "Device Setup" - this menu item disabled while "Searching for new devices".

How to fix this promlem?

Try this:
```

dima@lol:~$ sudo /etc/init.d/bluetooth restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service bluetooth restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop bluetooth ; start bluetooth. The restart(8) utility is also available.
bluetooth stop/waiting
bluetooth start/running, process 10032

```
But no results.

Setup this packages: sudo apt-get install bluetooth blueman bluez-hcidump bluewho python-bluez bluez-tools
But no results.

Some info:

I use laptop Asus X401A1.

```
dima@lol:~$ cat /sys/class/dmi/id/product_name
X401A1
```

```
dima@lol:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
```

```
dima@lol:~$ uname -a
Linux lol 3.11.0-26-generic #45-Ubuntu SMP Tue Jul 15 04:02:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

```
dima@lol:~$ bluez-test-adapter address
DC:85:DE:A5:AB:7A
```

```
dima@lol:~$ bluez-test-adapter name
ubuntu-0
```

```
dima@lol:~$ bluez-test-adapter pairable
1
```

```
dima@lol:~$ bluez-test-adapter pairabletimeout
0
```

```
dima@lol:~$ bluez-test-adapter discoverable
1
```

```
dima@lol:~$ bluez-test-adapter discovering
1
```

```
dima@lol:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

```
dima@lol:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 7 Series Chipset Family LPC Controller [8086:1e5e] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5289] (rev 01)
03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
```

---

### Post by brilliantcontract on 2014-11-04
Ok, it's was problem with my phone, Ubuntu work just fine! I connected to Ubuntu but when I try send file to phone I get error:

[IMG]http://i57.tinypic.com/14lpq44.png[/IMG]

---

