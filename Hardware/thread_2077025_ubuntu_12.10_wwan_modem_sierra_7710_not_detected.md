---
title: "ubuntu 12.10 wwan modem sierra 7710 not detected"
date: 2012-10-27
forum: Hardware
---

### Post by lere on 2012-10-27
Hallo All,

could you please help me? I am trying to get the sierra LTE Module in an Fujitsu U776 running. 

with ubuntu 12.04, the modemmanager showed the device. but it was not possible to connect to the network. 

with ubuntu 12.10, the device doesn't even appear in the modemmanger indicator.

lsubs says this:
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0bda:58b1 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0489:e052 Foxconn / Hon Hai 
Bus 001 Device 004: ID 1199:68a2 Sierra Wireless, Inc. 
Bus 002 Device 003: ID 08ff:2683 AuthenTec, Inc. 

what can i do? Any ideas?

thanks

---

### Post by bmork on 2012-11-10
> **lere said:**
> Hallo All,

could you please help me? I am trying to get the sierra LTE Module in an Fujitsu U776 running. 

with ubuntu 12.04, the modemmanager showed the device. but it was not possible to connect to the network. 

with ubuntu 12.10, the device doesn't even appear in the modemmanger indicator.

lsubs says this:
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 0bda:58b1 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0489:e052 Foxconn / Hon Hai 
Bus 001 Device 004: ID 1199:68a2 Sierra Wireless, Inc. 
Bus 002 Device 003: ID 08ff:2683 AuthenTec, Inc. 

what can i do? Any ideas?

thanks

Did you see the thread
[http://ubuntuforums.org/showthread.php?t=2040205&referrerid=1724590](http://ubuntuforums.org/showthread.php?t=2040205&referrerid=1724590)
?

A lot of the hints provided there are relavant for you as well.  You need to verify that the modem is online in full power mode (i.e. that rfkill isn't blocking it) and that the necessary drivers are loaded.  Then you need to run modem-manager with debugging to see why it doesn't pick it up.

Start with
usb-devices
/var/log/dmesg
rfkill list
minicom /dev/ttyUSB2 and a few AT commands:
AT!GSTATUS?
AT!PCINFO?

---

### Post by lere on 2012-11-11
> **bmork said:**
> Did you see the thread
[http://ubuntuforums.org/showthread.php?t=2040205&referrerid=1724590](http://ubuntuforums.org/showthread.php?t=2040205&referrerid=1724590)

i saw this, but am not familiar with qmi. I don't know which packet i have to install.


Start with
usb-devices
/var/log/dmesg
rfkill list
minicom /dev/ttyUSB2 and a few AT commands:
AT!GSTATUS?
AT!PCINFO?

network tools (GUI) shows "unknown interface (wwan0).

usb-devices:
T:  Bus=01 Lev=02 Prnt=02 Port=04 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1199 ProdID=68a2 Rev=00.06
S:  Manufacturer=Sierra Wireless, Incorporated
S:  Product=MC7710
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
/usr/bin/usb-devices: Zeile 79: printf: 08: Ungültige Oktalzahl.
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=qmi_wwan

ungültige Oktalzahl translates as invalid octal number

/var/log/dmesg (i think this is the relevant part)
  2.008169] usb 1-1.5: New USB device found, idVendor=1199, idProduct=68a2
[    2.008172] usb 1-1.5: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[    2.008174] usb 1-1.5: Product: MC7710
[    2.008176] usb 1-1.5: Manufacturer: Sierra Wireless, Incorporated
[    2.015853] udevd[357]: starting version 175
[    2.068487] lp: driver loaded but no devices found
[    2.076128] mei 0000:00:16.0: setting latency timer to 64
[    2.076180] mei 0000:00:16.0: irq 43 for MSI/MSI-X
[    2.080403] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \_SB_.PCI0.LPCB.PMIO 1 (20120320/utaddress-251)
[    2.080410] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.080412] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[    2.080416] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \_SB_.PCI0.LPCB.PMIO 1 (20120320/utaddress-251)
[    2.080421] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.080488] ACPI Warning: 0x00000500-0x0000053f SystemIO conflicts with Region \_SB_.PCI0.LPCB.OGIO 1 (20120320/utaddress-251)
[    2.080493] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.080495] lpc_ich: Resource conflict(s) found affecting gpio_ich

rfkill list
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

finally, i see there are some problems but i don't really understand what the problems are and how to solve it.

thank you very much.

---

### Post by bmork on 2012-11-12
> **lere said:**
> network tools (GUI) shows "unknown interface (wwan0).

usb-devices:
T: Bus=01 Lev=02 Prnt=02 Port=04 Cnt=02 Dev#= 4 Spd=480 MxCh= 0
D: Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=1199 ProdID=68a2 Rev=00.06
S: Manufacturer=Sierra Wireless, Incorporated
S: Product=MC7710
C: #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I: If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I: If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I: If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
/usr/bin/usb-devices: Zeile 79: printf: 08: Ungültige Oktalzahl.
I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=qmi_wwan

ungültige Oktalzahl translates as invalid octal number


This looks fine.  I get the same error message, but that is only cosmetical.  Someone needs to fix that script...

> 
/var/log/dmesg (i think this is the relevant part)
2.008169] usb 1-1.5: New USB device found, idVendor=1199, idProduct=68a2
[ 2.008172] usb 1-1.5: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[ 2.008174] usb 1-1.5: Product: MC7710
[ 2.008176] usb 1-1.5: Manufacturer: Sierra Wireless, Incorporated
[ 2.015853] udevd[357]: starting version 175
[ 2.068487] lp: driver loaded but no devices found
[ 2.076128] mei 0000:00:16.0: setting latency timer to 64
[ 2.076180] mei 0000:00:16.0: irq 43 for MSI/MSI-X
[ 2.080403] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \_SB_.PCI0.LPCB.PMIO 1 (20120320/utaddress-251)
[ 2.080410] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[ 2.080412] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[ 2.080416] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \_SB_.PCI0.LPCB.PMIO 1 (20120320/utaddress-251)
[ 2.080421] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[ 2.080488] ACPI Warning: 0x00000500-0x0000053f SystemIO conflicts with Region \_SB_.PCI0.LPCB.OGIO 1 (20120320/utaddress-251)
[ 2.080493] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[ 2.080495] lpc_ich: Resource conflict(s) found affecting gpio_ich
I could be wrong, but I do not think those ACPI warnings are related to any of this at all.


> 

rfkill list
0: hci0: Bluetooth
Soft blocked: yes
Hard blocked: no
1: phy0: Wireless LAN
Soft blocked: yes
Hard blocked: no
OK, so there is no laptop specific platform driver involved here at all.  I guess wwan should work if wlan and bluetooth works.


> 
finally, i see there are some problems but i don't really understand what the problems are and how to solve it.

thank you very much.Nothing of the above indicates any problem AFAICS.  Maybe you are  hitting a modemmanager bug which was recently fixed in the stable MM branches? See
[https://bugzilla.redhat.com/show_bug.cgi?id=835153](https://bugzilla.redhat.com/show_bug.cgi?id=835153)

(I have no idea where the Ubuntu packages are related to this, but I would expect this fix to be included in the latest stable releases).

NetworkManager and/or ModemManager logs should show if this is the case.

---

### Post by lere on 2012-11-18
In the meantime, i went back to 12.04 due to lots of other problems. Finally, the device shows up in the network-manager applet. When trying to connect, that is what 

grep -i networkmanager /var/log/syslog

reports:


Nov 18 18:14:03 smallbird NetworkManager[945]: <info> (eth0): deactivating device (reason 'user-requested') [39]
Nov 18 18:14:04 smallbird NetworkManager[945]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1252
Nov 18 18:14:04 smallbird NetworkManager[945]: <info> DNS: starting dnsmasq...
Nov 18 18:14:04 smallbird NetworkManager[945]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) starting connection 'O2 Pay-by-MB'
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> (ttyUSB2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) scheduled...
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) starting...
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> (ttyUSB2): device state change: prepare -> config (reason 'none') [40 50 0]
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) successful.
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) scheduled.
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 2 of 5 (Device Configure) complete.
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) started...
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> (ttyUSB2): device state change: config -> ip-config (reason 'none') [50 70 0]
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> starting PPP connection
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> pppd started with pid 27462
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 3 of 5 (IP Configure Start) complete.
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv6 Configure Timeout) started...
Nov 18 18:14:06 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Nov 18 18:14:06 smallbird NetworkManager[945]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 18 18:14:06 smallbird NetworkManager[945]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Nov 18 18:14:23 smallbird NetworkManager[945]: <info> (ttyUSB2): disconnecting for new activation request.
Nov 18 18:14:23 smallbird NetworkManager[945]: <info> (ttyUSB2): device state change: ip-config -> disconnected (reason 'none') [70 30 0]
Nov 18 18:14:23 smallbird NetworkManager[945]: <info> (ttyUSB2): deactivating device (reason 'none') [0]
Nov 18 18:14:23 smallbird NetworkManager[945]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Nov 18 18:14:23 smallbird NetworkManager[945]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Nov 18 18:14:23 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) starting connection 'O2 Pay-by-MB'
Nov 18 18:14:23 smallbird NetworkManager[945]: <info> (ttyUSB2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 18 18:14:23 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Nov 18 18:14:23 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Nov 18 18:14:23 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Nov 18 18:14:23 smallbird NetworkManager[945]: <warn> GSM connection failed: (32) Sending command failed: device is connected
Nov 18 18:14:23 smallbird NetworkManager[945]: <info> (ttyUSB2): device state change: prepare -> failed (reason 'unknown') [40 120 1]
Nov 18 18:14:23 smallbird NetworkManager[945]: <warn> Activation (ttyUSB2) failed.
Nov 18 18:14:23 smallbird NetworkManager[945]: <info> (ttyUSB2): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 18 18:14:23 smallbird NetworkManager[945]: <info> (ttyUSB2): deactivating device (reason 'none') [0]
Nov 18 18:14:23 smallbird NetworkManager[945]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Nov 18 18:14:23 smallbird NetworkManager[945]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Nov 18 18:14:23 smallbird NetworkManager[945]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov 18 18:14:23 smallbird NetworkManager[945]: <info> disconnect failed: (32) The device is already being disconnected.
Nov 18 18:14:27 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) starting connection 'O2 Pay-by-MB'
Nov 18 18:14:27 smallbird NetworkManager[945]: <info> (ttyUSB2): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Nov 18 18:14:27 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) scheduled...
Nov 18 18:14:27 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) started...
Nov 18 18:14:27 smallbird NetworkManager[945]: <info> Activation (ttyUSB2) Stage 1 of 5 (Device Prepare) complete.
Nov 18 18:14:57 smallbird NetworkManager[945]: <warn> GSM connection failed: (32) Serial command timed out
Nov 18 18:14:57 smallbird NetworkManager[945]: <info> (ttyUSB2): device state change: prepare -> failed (reason 'unknown') [40 120 1]
Nov 18 18:14:57 smallbird NetworkManager[945]: <warn> Activation (ttyUSB2) failed.
Nov 18 18:14:57 smallbird NetworkManager[945]: <info> (ttyUSB2): device state change: failed -> disconnected (reason 'none') [120 30 0]
Nov 18 18:14:57 smallbird NetworkManager[945]: <info> (ttyUSB2): deactivating device (reason 'none') [0]
Nov 18 18:14:57 smallbird NetworkManager[945]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Nov 18 18:14:57 smallbird NetworkManager[945]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Nov 18 18:15:03 smallbird NetworkManager[945]: <info> Activation (eth0) starting connection 'Kabelnetzwerkverbindung 1'
Nov 18 18:15:03 smallbird NetworkManager[945]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]


Unfortunately, i don't know how to interpret this.

---

### Post by TeMgaic24 on 2013-03-01
Should be fixed with Ubbuntu 13.04. Alternatively update kernel to version 3.6.1 or newer as it has implemented qmi and lte fix, supposedly making the mc7710 work.

---

### Post by Cobuntu on 2013-03-09
Edit: Thanks to the great help of bmork I got mine working without any problems in 13.04: [http://ubuntuforums.org/showthread.php?t=2121838?](http://ubuntuforums.org/showthread.php?t=2121838?)

---

