---
title: "Configure Netgear WG111 USB adaptor"
date: 2006-09-11
forum: Hardware &amp; Laptops
---

### Post by Mike@castthestorm.com on 2006-09-11
Hey people,

I've seen one or two threads on this topic, but nothing that seems to help my situation. I'm trying to configure the Netgear WG111 USB adaptor to work with the ubuntu server package, so only command line. I've figured out using iwconfig a bit - but whenever I try to  set power on or the bitrate, it gives me 
{{{
SET failed on device eth1 ; Unknown error 524.
}}}
I haven't done anything other than set ESSID and a few other settings with iwconfig. I'm very new to ubuntu - do I need to "enable" the device before I can set anything on it or something?

Thanks for anyone who can help!
- Mike

---

### Post by olur on 2006-11-06
I've got the same problem, have tried both the bcm43xx and ndiswrapper drivers - in both cases the light on the device never goes on and I can't connect. It works well on XP but it's a pain to have to switch (dual boot laptop) anywhere I can't hook up by wire. I can't find anything at the Netgear site regarding this error either. In case someone can help, here's the output of a few commands:
lsmod|grep ndis
ndiswrapper           177364  0
usbcore               130820  5 ndiswrapper,islsm_usb,ehci_hcd,ohci_hcd

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"alphaville"
          Mode:Auto  Channel=1  Access Point: Invalid
          Sensitivity=0/200
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

 ndiswrapper -l
Installed ndis drivers:
netwg111                driver present, hardware present

 lsusb
Bus 003 Device 002: ID 0846:4240 NetGear, Inc. WG111 WiFi (v2)
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

Nov  5 12:40:42 localhost kernel: [17179676.600000] NET: Registered protocol family 10
Nov  5 12:40:42 localhost kernel: [17179676.604000] lo: Disabled Privacy Extensions
Nov  5 12:40:42 localhost kernel: [17179676.604000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Nov  5 12:40:42 localhost kernel: [17179676.604000] IPv6 over IPv4 tunneling driver
Nov  5 12:40:43 localhost kernel: [17179677.160000] Bluetooth: Core ver 2.8
Nov  5 12:40:43 localhost kernel: [17179677.160000] NET: Registered protocol family 31
Nov  5 12:40:43 localhost kernel: [17179677.160000] Bluetooth: HCI device and connection manager initialized
Nov  5 12:40:43 localhost kernel: [17179677.160000] Bluetooth: HCI socket layer initialized
Nov  5 12:40:43 localhost kernel: [17179677.196000] Bluetooth: L2CAP ver 2.8
Nov  5 12:40:43 localhost kernel: [17179677.196000] Bluetooth: L2CAP socket layer initialized
Nov  5 12:40:43 localhost kernel: [17179677.220000] Bluetooth: RFCOMM socket layer initialized
Nov  5 12:40:43 localhost kernel: [17179677.220000] Bluetooth: RFCOMM TTY layer initialized
Nov  5 12:40:43 localhost kernel: [17179677.220000] Bluetooth: RFCOMM ver 1.7
Nov  5 12:45:19 localhost gconfd (neptune-7137): starting (version 2.14.0), pid 7137 user 'neptune'
Nov  5 12:45:20 localhost gconfd (neptune-7137): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov  5 12:45:20 localhost gconfd (neptune-7137): Resolved address "xml:readwrite:/home/neptune/.gconf" to a writable configuration source at position 1
Nov  5 12:45:20 localhost gconfd (neptune-7137): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Nov  5 12:45:20 localhost gconfd (neptune-7137): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Nov  5 12:45:20 localhost gconfd (neptune-7137): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Nov  5 12:47:01 localhost kernel: [17180055.828000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
Nov  5 12:47:01 localhost kernel: [17180055.844000] usbcore: registered new driver ndiswrapper
Nov  5 13:00:11 localhost -- MARK --


dmesg|grep usb
[17179574.092000] USB0 USB1 USB2 PS2K PS2M MAC0
[17179579.388000] usbcore: registered new driver usbfs
[17179579.388000] usbcore: registered new driver hub
[17179579.388000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179579.592000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179579.676000] hub 1-0:1.0: USB hub found
[17179579.784000] [<e0918730>] (usb_hcd_irq+0x0/0x60 [usbcore])
[17179579.992000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179580.048000] hub 2-0:1.0: USB hub found
[17179580.152000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[17179580.152000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179580.152000] hub 3-0:1.0: USB hub found
[17179580.496000] usb 3-1: new high speed USB device using ehci_hcd and address 2
[17179600.108000] islusb: No suitable configuration found, trying 3887 support
[17179600.108000] usbcore: registered new driver islusb
[17180055.844000] usbcore: registered new driver ndiswrapper

[17180055.828000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)


Thanks for any help -

---

### Post by olur on 2006-11-09
replying to my own post - shortly after posting I tried - as recommended on the Wireless docs - finding the islsm modules through 'lsmod|grep islsm' and then unloading them 'remmod islsm...' for each one loaded. The wireless then immediately worked as soon as I did a 'modprobe ndiswrapper'. Since then I've found that I've had to play with the file at /etc/network/interfaces to get it o work where I am at the time. Hope this helps someone, I should have read the docs more carefully. btw this is a wg111 v.1.

---

