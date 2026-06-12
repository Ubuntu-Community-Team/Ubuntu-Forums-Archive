---
title: "wlan not working due block by rfkill"
date: 2011-01-28
forum: Hardware
---

### Post by _winnetou_ on 2011-01-28
Hey,
my wireless lan is turned cannot be turned on. It is caused by rfkill. It always soft blocks my device on startup...
I only can manage to enable networking by 'sudo rfkill unblock wifi' on startup then, unchecking the enable networking button in the network manager of kde, enabling it again, then enabling wireless networking...
my question here is, how could i make rfkill stopp blocking my device on startup. There could be some workaround by running 'rfkill unblock wifi' before the network manager starts, but i just do not know how.
Thanks for any help! :)

---

### Post by IcarusR on 2011-01-28
Do you have a physical wifi on / off switch ?
If so try turning it to the off position, shut down, restart & switch it on after system is up.

Could also try unplugging any ethernet cable & see if it then works.

---

### Post by _winnetou_ on 2011-01-29
I tryed it.. still my wifi is soft blocked...
here is the output of rfkill list:
```
0: acer-wireless: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: sony-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
2: sony-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
4: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
```
there are two devices listed somehow.. one is always being softblocked.. here the output of sudo rfkill unblock all && rfkill list
```
0: acer-wireless: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: sony-wifi: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
2: sony-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
4: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
```
could it be that somehow that one dead device listed causes rfkill to block sony-wifi??

---

### Post by IcarusR on 2011-01-29
Lets go back a step. What is make & model of your laptop ?
Can you post output of these two commands please..

```
lspci
```

```
lsusb
```

> I only can manage to enable networking by 'sudo rfkill unblock wifi' on startup then, unchecking the enable networking button in the network manager of kde, enabling it again, then enabling wireless networking...

Does wifi then work ??

---

### Post by _winnetou_ on 2011-01-29
output lspci:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```

and here the output of lsusb:
```
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0489:e00f Foxconn / Hon Hai 
Bus 001 Device 003: ID 04f2:b1dc Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

edit: notebook model is sony vaio vpcy21-s1-e

---

### Post by IcarusR on 2011-01-29
I don't understand why 'rfkill list' lists three different wireless, with one being called acer-wireless.

I have read in some other threads on this subject about blacklisting 'acer-wmi' module.

Others have resolved this by installing 'linux-backports-modules-wireless-maverick-generic'

Another fix that has worked for some is to install 'wicd' & use it to manager network instead of 'network-manager'

---

### Post by _winnetou_ on 2011-01-29
thanks alot, blacklisting the device made my wifi work :)

---

### Post by kopalka on 2011-04-29
> **_winnetou_ said:**
> thanks alot, blacklisting the device made my wifi work :)
I have the same problem. What device do you blacklist?

---

### Post by drastys on 2011-04-29
I tried it on Lenovo V460 with Ubuntu 11.04 and now wifi is working OK , it seems so :-)

---

### Post by simomo on 2011-04-29
I have the same problem.I have solved this by adding
```
blacklist acer-wmi
```

in the file:
```
root@ubuntu:/# find / -name blacklist.conf
/etc/modprobe.d/blacklist.conf

```

---

