---
title: "problem with pen drive and card reader"
date: 2010-12-19
forum: Hardware
---

### Post by steph7 on 2010-12-19
hi,
this is a very strange problem it happens on an acer aspire one d620:
1) if I insert an usb pen drive and after an usb card reader, the system recognize just this second device
2) if I insert the usb card reader and after the usb pen drive, the system recognize just the second
what I have to do to have all devices working simultaneously?
some info
```
tail -f /var/log/messages
acerone kernel: [   27.304116] ata1: hard resetting link
acerone kernel: [   27.796107] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
acerone kernel: [   27.797028] ata1.00: unexpected _GTF length (4)
acerone kernel: [   27.798258] ata1.00: unexpected _GTF length (4)
acerone kernel: [   27.798527] ata1.00: configured for UDMA/133
acerone kernel: [   27.798542] ata1: EH complete
acerone kernel: [   29.388355] type=1400 audit(1292403566.919:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=823 comm="apparmor_parser"
acerone kernel: [   29.389868] type=1400 audit(1292403566.919:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=823 comm="apparmor_parser"
acerone kernel: [   29.391345] type=1400 audit(1292403566.919:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=823 comm="apparmor_parser"
acerone kernel: [   76.000099] usb 1-5: new high speed USB device using ehci_hcd and address 3
acerone rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="690" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
```

lsusb with all

```
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0718:0622 Imation Corp. 
Bus 001 Device 007: ID 0cf2:6250 ENE Technology, Inc. 
Bus 001 Device 002: ID 0402:9665 ALi Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

