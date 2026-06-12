---
title: "HP 1018 firmware loading failure"
date: 2010-01-23
forum: Hardware
---

### Post by Gorizon on 2010-01-23
I am a "happy" owner of a very popular albeit not very supported HP LaserJet 1018 printer
Since my first acquaintence with Linux i would struggle with him from time to time to kick it work

For now, nevertheless, the picture is like this:
[LIST=1][*]```
crystal@Crystal:~$ lsusb
Bus 002 Device 002: ID 0c10:0000  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 03f0:4117 Hewlett-Packard Printing Support
Bus 001 Device 006: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 003: ID 0951:1603 Kingston Technology Data Traveler 1GB/2GB Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 051d:0002 American Power Conversion uninterruptible Power Supply
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0458:0049 KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
[*]foo2zjs drivers are installed and CUPS see them[*]firmware lie in /usr/share/foo2zjs/firmware and hotplug script is in /etc/hotplug

[/LIST]
After all, that is how the problem is observed: after switching on the printer no firmware is loaded into it and it doesn't print anything, despite CUPS reports all is OK. When I try manually 
```
cat /usr/share/foo2zjs/firmware/sihp1018.img > /dev/lp0
```
it blocks and nothing happens
Please anyone, suggest something to load firmware to him!

---

