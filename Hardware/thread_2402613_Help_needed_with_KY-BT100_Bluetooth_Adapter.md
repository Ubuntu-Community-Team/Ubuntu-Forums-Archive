---
title: "Help needed with KY-BT100 Bluetooth Adapter"
date: 2018-10-02
forum: Hardware
---

### Post by tomdkat on 2018-10-02
Hi!  I have a KY-BT100 Bluetooth Adapter I would like to get working with Ubuntu 18.04.1 (64-bit).  It used to work fine on Ubuntu 15.04 on my old computer.  I did some searches and found this thread:

[https://ubuntuforums.org/showthread.php?t=2369183&highlight=KY-BT100](https://ubuntuforums.org/showthread.php?t=2369183&highlight=KY-BT100)

of course, that didn't give me much hope.  :)    However, when I run the commands mentioned in that thread:

```
uname -a; lspci -nnk | grep -iA2 net; lsusb; dmesg | grep -i bluetooth; dmesg | grep -i firmware; lsmod | grep bluetooth
```

I get this output:

```

Linux deathstar 4.15.0-34-generic #37-Ubuntu SMP Mon Aug 27 15:21:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
02:00.0 Ethernet controller [0200]: Broadcom Limited NetLink BCM57788 Gigabit Ethernet PCIe [14e4:1691] (rev 01)
	Subsystem: Dell NetLink BCM57788 Gigabit Ethernet PCIe [1028:043b]
	Kernel driver in use: tg3
	Kernel modules: tg3
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 004 Device 002: ID 03f0:0401 Hewlett-Packard ScanJet 5200c
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 04f2:0841 Chicony Electronics Co., Ltd HP Multimedia Keyboard
Bus 003 Device 002: ID 25a7:fa23  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[  171.604665] Bluetooth: Core ver 2.22
[  171.604712] Bluetooth: HCI device and connection manager initialized
[  171.604716] Bluetooth: HCI socket layer initialized
[  171.604718] Bluetooth: L2CAP socket layer initialized
[  171.604723] Bluetooth: SCO socket layer initialized
[  171.903373] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  171.903377] Bluetooth: BNEP filters: protocol multicast
[  171.903385] Bluetooth: BNEP socket layer initialized
[  402.080458] audit: type=1400 audit(1538485692.912:30): apparmor="STATUS" operation="profile_load" profile="unconfined" name="snap.bluez.bluetoothctl" pid=3541 comm="apparmor_parser"
[  411.640124] audit: type=1400 audit(1538485702.472:49): apparmor="STATUS" operation="profile_replace" info="same as current profile, skipping" profile="unconfined" name="snap.bluez.bluetoothctl" pid=3653 comm="apparmor_parser"
[  418.858496] audit: type=1400 audit(1538485709.692:77): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=3863 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[  418.900450] audit: type=1400 audit(1538485709.732:78): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=3863 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[  419.210767] audit: type=1400 audit(1538485710.044:79): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=3902 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[  419.212607] audit: type=1400 audit(1538485710.044:80): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=3902 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
[  419.463252] audit: type=1400 audit(1538485710.296:83): apparmor="DENIED" operation="create" profile="snap.bluez.bluez" pid=3927 comm="bluetoothd" family="bluetooth" sock_type="raw" protocol=1 requested_mask="create" denied_mask="create"
[  419.463257] audit: type=1400 audit(1538485710.296:84): apparmor="DENIED" operation="connect" profile="snap.bluez.bluez" name="/run/dbus/system_bus_socket" pid=3927 comm="bluetoothd" requested_mask="wr" denied_mask="wr" fsuid=0 ouid=0
bluetooth             548864  12 btrtl,btintel,bnep,btbcm,btusb
ecdh_generic           24576  1 bluetooth

```

What I find interesting are the "DENIED" apparmor lines.   Is apparmor possibly blocking access to the Bluetooth adapter?

Any ideas on how to troubleshoot this?

Thanks in advance!

Peace...

---

### Post by tomdkat on 2018-10-07
I ended up getting the adapter working.  I had to plug it into a **powered** USB port.  Once I did that, I was able to see my phone from my computer.   :)

Peace...

---

### Post by mikegsus on 2019-09-17
I had the same problem, I found something that works to me, it's in Spanish, but I can help you with translation. I'm using Ubuntu 18.04.2
[https://maslinux.es/como-configurar-bluetooth-en-gnulinux/ ]("https://maslinux.es/como-configurar-bluetooth-en-gnulinux/")

---

