---
title: "Belkin Components Bluetooth Device with trace filter"
date: 2012-07-20
forum: Hardware
---

### Post by robvnl on 2012-07-20
Hello, maybe somebody can help me with a USB bluetooth device to connect my Nokia 6021 trough bluetooth. In the end I would like to use Xgnokii on it.

I have Bluez bluetooth installed on Ubuntu 10.04 (LTS). The bluetooth device is a 
Belkin Components Bluetooth Device sticked into a USB port.

From the GUI I can search and find the mobile phone. It does connect, I have to enter a pin code, it connects. However, the connection is lost immediately. From the phone I cannot find the computer. At the PC in the GUI the name of the phone is listed, it pretends it is connected but it is not.

lsusb
...
Bus 004 Device 002: ID 050d:0131 Belkin Components Bluetooth Device with trace filter
...

service bluetooth status
 * bluetooth is running

hcitool scan
Scanning ...
    00:17:B0:63:F5:63    Pinguins <-- my GSM

Thank you very much in advance for any hints and tips.

---

### Post by robvnl on 2012-07-21
I found in daemon.log:
Jul 22 01:47:41 earth bluetoothd[7776]: link_key_request        (sba=00:0A:3A:7E:2B:F7, dba=00:17:B0:63:F5:63)
Jul 22 01:47:41 earth bluetoothd[7776]: pin_code_request (sba=00:0A:3A:7E:2B:F7, dba=00:17:B0:63:F5:63)
Jul 22 01:47:51 earth bluetoothd[7776]: link_key_notify (sba=00:0A:3A:7E:2B:F7, dba=00:17:B0:63:F5:63, type=0)
[B]Jul 22 01:47:51 earth bluetoothd[7776]: probe failed with driver input-headset for device /org/bluez/7775/hci0/dev_00_17_B0_63_F5_63
[/B]Jul 22 01:47:51 earth bluetoothd[7776]: Stopping discovery

as soon as I entered the pincode to connect it fails on driver input-headset.
When  I select in the properties (with bluetooth-properties) dialogue explicitly "phone" it does not make a difference.

In /etc/bluetooth/input.conf there is only this:
# Configuration file for the input service

# This section contains options which are not specific to any
# particular interface
[General]

# Set idle timeout (in minutes) before the connection will
# be disconnect (defaults to 0 for no timeout)
#IdleTimeout=30

Is there any documentation on Bluez ?

I installed Blueman from the repos and I managed to browse the phone. So there is probably a bug in bluetooth-properties.
How Xgnokii can be used is still unclear, it stays in connecting and it crashes after a while.

Thank you in advance.

---

