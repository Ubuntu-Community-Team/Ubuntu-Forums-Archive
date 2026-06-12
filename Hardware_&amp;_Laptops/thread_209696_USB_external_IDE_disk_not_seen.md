---
title: "USB external IDE disk not seen?"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by ggravier on 2006-07-05
Hi!

I have a PATA/IDE 250 GB disk in an external case... I can see the disk on a Windows machine... but if I plug it into my Ubuntu (6.06 with ALL latest updates), I get the following message in the /var/log/messages :

[FONT="Fixedsys"][COLOR="Red"]Jul  5 20:30:29 localhost kernel: [17180492.432000] usb 4-1: new high speed USB device using ehci_hcd and address 6
Jul  5 20:30:40 localhost kernel: [17180504.092000] usb 4-1: new high speed USB device using ehci_hcd and address 7
Jul  5 20:30:52 localhost kernel: [17180515.752000] usb 4-1: new high speed USB device using ehci_hcd and address 8
Jul  5 20:31:03 localhost kernel: [17180526.292000] usb 4-1: new high speed USB device using ehci_hcd and address 9[/COLOR][/FONT]

and in /var/log/kern.log and /var/log/syslog :

[FONT="Fixedsys"][COLOR="Red"]Jul  5 20:30:29 localhost kernel: [17180492.432000] usb 4-1: new high speed USB device using ehci_hcd and address 6
Jul  5 20:30:40 localhost kernel: [17180503.976000] usb 4-1: device not accepting address 6, error -110
Jul  5 20:30:40 localhost kernel: [17180504.092000] usb 4-1: new high speed USB device using ehci_hcd and address 7
Jul  5 20:30:52 localhost kernel: [17180515.636000] usb 4-1: device not accepting address 7, error -110
Jul  5 20:30:52 localhost kernel: [17180515.752000] usb 4-1: new high speed USB device using ehci_hcd and address 8
Jul  5 20:31:02 localhost kernel: [17180526.176000] usb 4-1: device not accepting address 8, error -110
Jul  5 20:31:03 localhost kernel: [17180526.292000] usb 4-1: new high speed USB device using ehci_hcd and address 9
Jul  5 20:31:13 localhost kernel: [17180536.716000] usb 4-1: device not accepting address 9, error -110[/COLOR][/FONT]

Any idea what could be going wrong?

Thanks in advance,
Gilles.

---

