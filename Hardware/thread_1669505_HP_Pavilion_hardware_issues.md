---
title: "HP Pavilion hardware issues"
date: 2011-01-17
forum: Hardware
---

### Post by Knofbath on 2011-01-17
I've got this HP Pavilion A1006N I'm working on for a friend.  

Socket 478 with a Celeron D processor, Intel 845GV and ICH4 Chipset.  

First issue is it won't boot Windows XP, which came preinstalled on it. And it won't complete a fresh XP install either, blue screen with a white cursor.  

Enter Linux. Installed Kubuntu 10.10, it works. Hurrah Linux. But, it has no networking.   

ifconfig shows the eth0 connection as running, but connecting an ethernet cable gets no results. 

Nothing showing on the router, nothing showing on the computer.  
Only clue is a boot message about Disabling IRQ 23. irq 23: nobody cared (try booting with the "irqpoll" option)   

ifconfig shows eth0 as Interrupt 23 as well.  

Right now I am passing irqpoll, noapic, and nolapic as boot options. This switches the message to Disabling IRQ 11 instead of 23. I have also disabled "Wake on LAN" for now.

So the question is, what else can I do? Or do I have to write off networking as a hardware issue and give up there. Also the BIOS is pretty locked down, I can't disable ACPI, or set any IRQ options. 

dmesg is attached, simple text renamed to a doc file because of size limits.

---

### Post by Yellow Pasque on 2011-01-17
I tried reading your dmesg, but way too much scrolling is involved. Plain text please.

---

### Post by Knofbath on 2011-01-17
I don't know what the important part is.

Lets start with here:
[    0.145648] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.145687] ehci_hcd 0000:00:1d.7: found PCI INT D -> IRQ 11
[    0.145716] ehci_hcd 0000:00:1d.7: sharing IRQ 11 with 0000:01:0c.0
[    0.145721] ehci_hcd 0000:00:1d.7: sharing IRQ 11 with 0000:01:0d.0
[    0.145754] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.145760] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.145838] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.149767] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    1.380820] irq 11: nobody cared (try booting with the "irqpoll" option)
[    1.380826] Pid: 1, comm: swapper Not tainted 2.6.35-22-generic #33-Ubuntu 



And here:

[    2.472837] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.472871] 8139cp 0000:01:0c.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.502701] firewire_ohci 0000:01:0d.0: found PCI INT A -> IRQ 11
[    2.502721] firewire_ohci 0000:01:0d.0: sharing IRQ 11 with 0000:00:1d.7
[    2.505017] 8139too: 8139too Fast Ethernet driver 0.9.28
[    2.522276] firewire_ohci 0000:01:0d.0: sharing IRQ 11 with 0000:01:0c.0
[    4.475783] irq 11: nobody cared (try booting with the "irqpoll" option)
[    4.475791] Pid: 148, comm: modprobe Not tainted 2.6.35-22-generic #33-Ubuntu 


And here:

[   16.937385] type=1400 audit(1295290168.297:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=572 comm="apparmor_parser"
[   16.958460] type=1400 audit(1295290168.321:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=572 comm="apparmor_parser"
[   16.958895] type=1400 audit(1295290168.321:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=572 comm="apparmor_parser"
[   17.008766] type=1400 audit(1295290168.369:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=582 comm="apparmor_parser"
[   17.009742] type=1400 audit(1295290168.369:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=582 comm="apparmor_parser"
[   19.047325] irq 11: nobody cared (try booting with the "irqpoll" option)
[   19.047377] Pid: 542, comm: NetworkManager Not tainted 2.6.35-22-generic #33-Ubuntu

---

### Post by Knofbath on 2011-01-19
bump

---

### Post by Yellow Pasque on 2011-01-19
Are you using the latest BIOS? Also, if you're not using firewire, see if you can turn it off in the BIOS.
I was also wondering if you;re using a direct internet connection, or you're using a router of some kind.

---

### Post by Knofbath on 2011-01-19
Using the latest BIOS from the HP website, 3.26. It's from about 2007.

Disabling Firewire in the BIOS does remove the set of Firewire error messages from dmesg, but doesn't fix the network issue.

I am plugging it into my router, a Linksys WRT-54G V8. I don't have any reason to suspect its my router, since all I did was unplug an existing device to test this computer. It doesn't light up the LAN connection light on the router, and it doesn't pull a dhcp address from the router either.

---

### Post by Yellow Pasque on 2011-01-19
Can you post output of following?
```
sudo lshw -C network
ifconfig -a
cat /etc/network/interfaces
```
I am not too familiar with KDE's Network Manager, so you may need to configure something in there.

---

### Post by Knofbath on 2011-01-20
Sorry, time ran out on me, I had to return the computer to my friend.

I think Network Manager pretty much auto-configures itself, as far as ethernet goes though.

From the old dmesg:
[   20.199119] eth0: link down
[   20.199413] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

