---
title: "Bluetooth activation issue with RTL8822BE on 18.04"
date: 2019-06-18
forum: Hardware
---

### Post by castor_fou on 2019-06-18
Hello

I have a ROG motherboard: Asus ROG Strix B450-I, coming with RTL8822BE 802.11a/b/g/n/ac WiFi adapter.
This is a combo for both wifi and bluetooth.

I have troubles with Bluetooth; it looks like not detected on my system.

Here are some information.

uname -a
```
guillaume@newhtpc:~$ uname -a
Linux newhtpc 4.18.0-21-generic #22~18.04.1-Ubuntu SMP Thu May 16 15:07:19 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

bootctl
```
guillaume@newhtpc:~$ bootctl
Couldn't find EFI system partition. It is recommended to mount it to /boot or /efi.
Alternatively, use --path= to specify path to mount point.
System:
    Not booted with EFI
```

lsusb
```
guillaume@newhtpc:~$ lsusb
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0681:0756 Siemens Information and Communication Products 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0b05:1872 ASUSTek Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lspci -nnk | grep 0280 -A3
```
guillaume@newhtpc:~$ lspci -nnk | grep 0280 -A3
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter [10ec:b822]
	Subsystem: ASUSTeK Computer Inc. Device [1043:8746]
	Kernel driver in use: r8822be
	Kernel modules: r8822be
```

dmesg | egrep -i 'blue|firm'
```
guillaume@newhtpc:~$ dmesg | egrep -i 'blue|firm'
[    0.090378] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    0.107512] acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    5.268314] r8822be: Using firmware rtlwifi/rtl8822befw.bin
[    5.404248] [drm] Found VCN firmware Version: 1.73 Family ID: 18
[    5.404253] [drm] PSP loading VCN firmware
```

dmesg | egrep -i 'r8822be'
```

guillaume@newhtpc:~$ dmesg | egrep -i 'r8822be'
[    5.248477] r8822be: module is from the staging directory, the quality is unknown, you have been warned.
[    5.268314] r8822be: Using firmware rtlwifi/rtl8822befw.bin
[    5.297348] r8822be: rtlwifi: wireless switch is on
[    5.334286] r8822be 0000:04:00.0 wlp4s0: renamed from wlan0
```

rfkill
```
guillaume@newhtpc:~$ rfkill 
ID TYPE DEVICE      SOFT      HARD
 0 wlan phy0   unblocked unblocked
```

systemctl status bluetooth
```
guillaume@newhtpc:~$ systemctl status bluetooth
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: inactive (dead)
     Docs: man:bluetoothd(8)
```

bt-adapter -i
```
guillaume@newhtpc:/var/log$ bt-adapter -i
**
ERROR:lib/helpers.c:318:intf_supported: assertion failed: (introspection_proxy != NULL)
Abandon (core dumped)
```

in apport.log
```
ERROR: apport (pid 17311) Tue Jun 18 08:20:51 2019: wrote report /var/crash/_usr_bin_bt-adapter.1000.crash
ERROR: apport (pid 17677) Tue Jun 18 08:22:44 2019: called for pid 17671, signal 6, core limit 0, dump mode 1
ERROR: apport (pid 17677) Tue Jun 18 08:22:44 2019: executable: /usr/bin/bt-adapter (command line "bt-adapter -i")
```

and syslog
```

Jun 18 08:22:19 newhtpc dbus-daemon[757]: [system] Activating via systemd: service name='org.bluez' unit='dbus-org.bluez.service' requested by ':1.189' (uid=1000 pid=17671 comm="bt-adapter -i " label="unconfined")
Jun 18 08:22:44 newhtpc systemd[1]: Starting Process error reports when automatic reporting is enabled...
Jun 18 08:22:47 newhtpc whoopsie-upload-all[17682]: ERROR: processing /var/crash/_usr_bin_bt-adapter.1000.crash: Compressed file ended before the end-of-stream marker was reached
Jun 18 08:22:47 newhtpc whoopsie-upload-all[17682]: /var/crash/_usr_bin_variety.1000.crash already marked for upload, skipping
Jun 18 08:22:47 newhtpc whoopsie-upload-all[17682]: Collecting info for /var/crash/_usr_bin_bt-adapter.1000.crash...
Jun 18 08:22:47 newhtpc whoopsie-upload-all[17682]: All reports processed
Jun 18 08:22:47 newhtpc systemd[1]: Started Process error reports when automatic reporting is enabled.
```

Then
```

guillaume@newhtpc:/var/log$ sudo modprobe -r r8822be
guillaume@newhtpc:/var/log$ sudo modprobe r8822be
```

in kern.log
```
Jun 18 10:56:30 newhtpc kernel: [48659.212297] cfg80211: Loading compiled-in X.509 certificates for regulatory database
Jun 18 10:56:30 newhtpc kernel: [48659.212548] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
Jun 18 10:56:30 newhtpc kernel: [48659.230126] r8822be: module is from the staging directory, the quality is unknown, you have been warned.
Jun 18 10:56:31 newhtpc kernel: [48659.251020] r8822be: Using firmware rtlwifi/rtl8822befw.bin
Jun 18 10:56:31 newhtpc kernel: [48659.252080] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
Jun 18 10:56:31 newhtpc kernel: [48659.252291] r8822be: rtlwifi: wireless switch is on
Jun 18 10:56:31 newhtpc kernel: [48659.256307] r8822be 0000:04:00.0 wlp4s0: renamed from wlan0
```

I tried loading an updated module from jeremy31
```
sudo apt install git build-essential dkms
git clone https://github.com/jeremyb31/newbtfix-4.15.git
sudo dkms add ./newbtfix-4.15
sudo dkms install btusb/4.0
```
and reboot without any more success

Seems similar to [https://ubuntuforums.org/showthread.php?t=2394125&page=4&highlight=bluetooth+rtl8822b](https://ubuntuforums.org/showthread.php?t=2394125&page=4&highlight=bluetooth+rtl8822b)
But I am not sure.

Any help would be greatly appreciated ;)

---

