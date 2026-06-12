---
title: "HP DeskJet d2663 &amp; Ubuntu 8.10: how to make them work together?"
date: 2010-05-02
forum: Hardware
---

### Post by cforest on 2010-05-02
Hi all!

I have HP DeskJet d2663 printer connected to Lenovo notebook with Ubuntu 8.10 installed. Interface: USB 2.0. The printer itself is good(I tried it with other PC). 

On [http://hplipopensource.com/]("http://hplipopensource.com/"), I selected my Ubuntu and DeskJet versions and downloaded a corresponding hplip file (ver 3.10.2). I ran this sh script, and all this stuff has been installed without any problem. But the printer does nothing. I can see printing jobs appear and disappear in printer queue and that's all. HPLIP Status Server says all jobs complete successfully. Far from it - nothing has been printed.

System info:

f4@lambda:~$ uname -a
Linux lambda 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

f4@lambda:~$ lsusb 
Bus 007 Device 003: ID 045e:00cb Microsoft Corp. 
Bus 007 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 03f0:8011 Hewlett-Packard 
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

f4@lambda:~$ dmesg|tail
[  135.810013] type=1503 audit(1272716437.911:16): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6641 profile="/usr/sbin/cupsd"
[  261.933366] usb 3-1: USB disconnect, address 3
[  264.640327] usb 3-1: new high speed USB device using ehci_hcd and address 4
[  264.775073] usb 3-1: configuration #1 chosen from 1 choice
[  264.778299] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x8011

/var/log/messages:
May  1 16:22:44 lambda kernel: [  261.933366] usb 3-1: USB disconnect, address 3
May  1 16:22:46 lambda kernel: [  264.640327] usb 3-1: new high speed USB device using ehci_hcd and address 4
May  1 16:22:46 lambda kernel: [  264.775073] usb 3-1: configuration #1 chosen from 1 choice
May  1 16:22:46 lambda kernel: [  264.778299] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x8011
May  1 16:24:02 lambda kernel: [  340.033766] __ratelimit: 6 callbacks suppressed
May  1 16:24:02 lambda kernel: [  340.033779] type=1503 audit(1272716642.136:19): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=6844 profile="/usr/sbin/cupsd"
May  1 16:24:02 lambda kernel: [  340.321558] usblp0: removed
May  1 16:24:19 lambda kernel: [  356.906147] type=1503 audit(1272716659.007:20): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=7 name="/dev/tty" pid=6879 profile="/usr/sbin/cupsd"
May  1 16:28:46 lambda kernel: [  623.968318] CE: hpet increasing min_delta_ns to 15000 nsec

hp-check -t:  No errors or warnings.

I don't want to move to newer Ubuntu version but dream to make my printer work. Any idea?

Thanks,

---

### Post by cforest on 2010-05-06
Hi! Any idea?

Thanks,

---

