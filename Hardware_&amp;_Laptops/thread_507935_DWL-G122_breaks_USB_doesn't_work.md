---
title: "DWL-G122 breaks USB doesn't work"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by arthur_kalm on 2007-07-23
Hi everyone,

I've recently done a fresh install of Feisty on a computer that was previously running Dapper. Upon upgrading the wifi stopped working. It's a D-Link DWL-G122 USB wireless adapter. It worked flawlessly in Dapper. Here is what happens:

[LIST=1]
[*]Computer boots up
[*]USB works fine, can mount and read external hard drives, etc
[*]Plugin D-Link adapter
[*]Message shows up saying that USB external hard drives were ejected unsafely
[*]USB stops working
[*]Wifi doesn't work
[/LIST]

The following error appears in /var/log/messages:

> 
host system error, PCI problems?
host controller halted, very bad!
HC died; cleaning up
p54usb: reset failed!


Any help would be greatly appreciated.

---

### Post by geraldm on 2007-07-23
Prior to the "HC died; cleaning up" message, was the usb device assigned to a port AND
was there a message about disconnect on that same assigned usb port?
The HC died may mean that the usb hub died.  The probable cause might be 
interrupts that go unanswered, and then the hub is killed.

Which hardware does your usb controller have: uhci, ohci, both ? (ehci does not count here)
If you have only one type(say uhci), was the other module (ohci_hcd) loaded, as shown  
in  "lsmod" ?

Gerald

---

### Post by arthur_kalm on 2007-07-25
OK I've solved the problem. I asked around on IRC and someone pointed me to a Ubuntu wiki page (here: ) which said that the DWL-G122 rev A2 works with Feisty but prism54usb needs to be blacklisted (add "blacklist prism54usb" to */etc/modprobe.d/blacklist*). After blacklisting prism, the adapter stopped dropping USB devices.

After blacklisting the driver, I installed ndiswrapper, rebooted and viola, the adapter worked.

---

