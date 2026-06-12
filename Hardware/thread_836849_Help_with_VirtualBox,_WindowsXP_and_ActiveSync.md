---
title: "Help with VirtualBox, WindowsXP and ActiveSync"
date: 2008-06-21
forum: Hardware
---

### Post by csete on 2008-06-21
I am running Ubuntu Hardy with a Windows XP guest running on VirtualBox version 1.6 on my Dell Inspiron E1505.  I would like to be able to do some Windows Mobile development using the virtual Windows XP and connect to my Motorola Q9h using ActiveSync for development.  Whenever I try to do that, it seems like I "lose" the USB connection.  This exact same VirtualBox image on my work Macintosh laptop works fine, so I don't think this is an issue with VirtualBox or my Moto Q.  The following information documents what I'm seeing in the logs and such. 

Can anyone offer any insights or thoughts on what I can try to get this to work?

Thanks,
Craig

Before connecting the phone, lsusb shows:

```

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 009: ID 0a5c:4503 Broadcom Corp. 
Bus 004 Device 008: ID 0a5c:4502 Broadcom Corp. 
Bus 004 Device 007: ID 413c:8126 Dell Computer Corp. 
Bus 004 Device 006: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Connecting the device shows:

```

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 009: ID 0a5c:4503 Broadcom Corp. 
Bus 004 Device 008: ID 0a5c:4502 Broadcom Corp. 
Bus 004 Device 007: ID 413c:8126 Dell Computer Corp. 
Bus 004 Device 006: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 22b8:4221 Motorola PCS 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

```

The messages in the log file show:

```

Jun 21 21:19:37 ubuntu-laptop kernel: [ 3121.148019] usb 2-1: new full speed USB device using uhci_hcd and address 2
Jun 21 21:19:37 ubuntu-laptop kernel: [ 3121.316972] usb 2-1: configuration #1 chosen from 1 choice
Jun 21 21:19:38 ubuntu-laptop kernel: [ 3121.460536] usbcore: registered new interface driver cdc_ether
Jun 21 21:19:38 ubuntu-laptop kernel: [ 3121.560927] eth1: register 'rndis_host' at usb-0000:00:1d.1-1, RNDIS device, 80:00:cb:3b:4c:8c
Jun 21 21:19:38 ubuntu-laptop kernel: [ 3121.560950] usbcore: registered new interface driver rndis_host
Jun 21 21:19:38 ubuntu-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason

```

After starting VirtualBox and connecting the USB device to the virtual machine, lsusb shows that the the phone is no longer connected although it is still there.

```

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 009: ID 0a5c:4503 Broadcom Corp. 
Bus 004 Device 008: ID 0a5c:4502 Broadcom Corp. 
Bus 004 Device 007: ID 413c:8126 Dell Computer Corp. 
Bus 004 Device 006: ID 0a5c:4500 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

and the messages in the log:

```

Jun 21 21:23:09 ubuntu-laptop kernel: [ 3333.277199] usb 2-1: USB disconnect, address 3
Jun 21 21:23:09 ubuntu-laptop kernel: [ 3333.278106] eth1: unregister 'rndis_host' usb-0000:00:1d.1-1, RNDIS device
Jun 21 21:23:12 ubuntu-laptop kernel: [ 3336.723140] usb 2-1: new full speed USB device using uhci_hcd and address 4
Jun 21 21:23:12 ubuntu-laptop kernel: [ 3336.893096] usb 2-1: configuration #1 chosen from 1 choice
Jun 21 21:23:12 ubuntu-laptop kernel: [ 3336.997271] eth1: register 'rndis_host' at usb-0000:00:1d.1-1, RNDIS device, 80:00:cb:3b:4c:8c
Jun 21 21:23:15 ubuntu-laptop kernel: [ 3339.127058] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 21 21:23:27 ubuntu-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Jun 21 21:23:27 ubuntu-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Jun 21 21:23:27 ubuntu-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Jun 21 21:23:33 ubuntu-laptop kernel: [ 3357.852515] eth1: unregister 'rndis_host' usb-0000:00:1d.1-1, RNDIS device
Jun 21 21:23:40 ubuntu-laptop kernel: [ 3364.478858] usb 2-1: USB disconnect, address 4

```

---

### Post by TivoTyro on 2008-11-19
Did you ever get anywhere with this?  I am having the same problem with Intrepid.

---

### Post by Coreigh on 2008-11-19
I don't know if this will help but there is some USB "magic" disabled in Hardy and Intrepid. See this link:
[http://www.virtualbox.org/wiki/User_FAQ]("http://www.virtualbox.org/wiki/User_FAQ")
Scroll down to Linux Hosts, there are some lines that need to be added to /etc/init.d/mountdevsubfs.sh

Specifically this is for enabling external USB drives, but it helped me enable other USB peripheral devices.

---

### Post by csete on 2008-11-19
I never got this to work and moved on to other things.  I've since done a complete scratch installation of Ibex, but haven't stopped to see if this works now.  I would love to hear if you work it out.

---

