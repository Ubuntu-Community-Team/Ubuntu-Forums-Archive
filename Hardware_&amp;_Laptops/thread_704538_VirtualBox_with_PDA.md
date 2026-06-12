---
title: "VirtualBox with PDA"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by ziphyre on 2008-02-22
Hi,

I tried to synchronize my PDA (HTC TynTN II running windows mobile 6) using a guest Windows XP installation on VirtualBox (1.5.6) on Gutsy. I read about USB problems, and make the necessary modifications in order to use USB with VirtualBox, and it works quite well. I can use any USB flashdisk in XP. But it doesn't detect my pda. The problem is, I cannot see any evidence of the connection with PDA and the host (Gutsy). Here is what I did while the PDA is connected (at least it's charging):

```
ziphyre@neptune:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

```

I looked at /var/log/messages

```
ziphyre@neptune:~$ tail  /var/log/messages
Feb 22 20:21:23 neptune dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Feb 22 20:21:25 neptune kernel: [   51.530809] NET: Registered protocol family 17
Feb 22 20:21:29 neptune dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Feb 22 20:21:29 neptune dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Feb 22 20:21:29 neptune dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Feb 22 20:21:29 neptune dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Feb 22 20:21:30 neptune kernel: [   56.228594] NET: Registered protocol family 10
Feb 22 20:21:30 neptune kernel: [   56.228774] lo: Disabled Privacy Extensions
Feb 22 20:38:17 neptune kernel: [ 1062.585758] sr0: CDROM not ready.  Make sure there is a disc in the drive.
Feb 22 20:38:49 neptune kernel: [ 1094.464297] sr0: CDROM not ready.  Make sure there is a disc in the drive.

```

nothing about a usb drive inserted?
I tried the VirtualBox's usbhost

```
ziphyre@neptune:~$ VBoxManage list usbhost
VirtualBox Command Line Management Interface Version 1.5.6
(C) 2005-2008 innotek GmbH
All rights reserved.

Host USB Devices:

<none>
```

So nothing happens at all, or I'm missing something?
Thanks...

---

### Post by ziphyre on 2008-02-22
Well,

I found something, if I reboot my PDA, the connection establishes with Gutsy, so VBoxManage gives me.

```

ziphyre@neptune:~$ VBoxManage list usbhost
VirtualBox Command Line Management Interface Version 1.5.6
(C) 2005-2008 innotek GmbH
All rights reserved.

Host USB Devices:

UUID:               2ee1ca3b-e22e-4450-0287-dec34a9f2819
VendorId:           0x0bb4 (0BB4)
ProductId:          0x0b0b (0B0B)
Revision:           0.0 (0000)
Manufacturer:       HTC
Product:            Generic RNDIS
SerialNumber:       3fbf5000-7351-0801-3557-570102477950
Address:            /proc/bus/usb/003/002
Current State:      Available
```

But this is for one time. If I unplug then replug the pda, nothing happens, as usual...

---

