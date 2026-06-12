---
title: "bluetooth mouse setup using console in 12.04"
date: 2012-03-13
forum: Hardware
---

### Post by motiejus on 2012-03-13
Hi,

I decided to learn to set-up my bluetooth mouse using console only. Before that I set it up using bluetooth-wizard (worked until reboot), now I would like to re-do it. I followed [1].

root@pierce ~ # hcitool dev
Devices:
        hci0    74:F0:6D:F0:84:83
root@pierce ~ # hcitool scan
Scanning ...
        00:07:61:FB:73:F3       Logitech Bluetooth Mouse M555b
root@pierce ~ # bluez-simple-agent hci0 00:07:61:FB:73:F3
Creating device failed: org.bluez.Error.AlreadyExists: Already Exists
root@pierce ~ # bluez-test-device trusted 00:07:61:FB:73:F3 yes
root@pierce ~ # service bluetooth restart
bluetooth stop/waiting
bluetooth start/running, process 2817
root@pierce ~ # dmesg | tail
[   46.957926] wlan0: RX AssocResp from b0:48:7a:db:5c:10 (capab=0x411
status=0 aid=1)
[   46.957941] wlan0: associated
[   46.958999] ieee80211 phy0: brcms_ops_bss_info_changed: qos
enabled: true (implement)
[   46.959176] ieee80211 phy0: brcmsmac: brcms_ops_bss_info_changed: associated
[   46.959318] ieee80211 phy0: changing basic rates failed: -22
[   46.959433] ieee80211 phy0: brcms_ops_bss_info_changed: arp
filtering: enabled true, count 0 (implement)
[   46.961378] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   47.359537] ieee80211 phy0: brcms_ops_bss_info_changed: arp
filtering: enabled true, count 1 (implement)
[   54.692324] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   57.792290] wlan0: no IPv6 routers present

Of course, mouse isn't working. "Already exists" probably because it was already configured using GUI.

I would like to learn to set it up without gnome-bluetooth (and kde-), and, of course, update wiki when it's working.

root@pierce ~ # lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu precise (development branch)
Release:        12.04
Codename:       precise
root@pierce ~ # uname -a
Linux pierce 3.2.0-18-generic #29-Ubuntu SMP Fri Mar 9 21:36:08 UTC
2012 x86_64 x86_64 x86_64 GNU/Linux
root@pierce ~ # lsusb | grep Bluetooth
Bus 003 Device 003: ID 13d3:3315 IMC Networks Bluetooth module
root@pierce ~ # rfkill list
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: asus-wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: asus-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
3: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

Computer model: asus eee pc 1215b.

[1]: [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

Thanks

---

