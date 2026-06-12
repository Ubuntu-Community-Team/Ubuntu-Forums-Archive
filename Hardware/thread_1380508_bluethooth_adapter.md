---
title: "bluethooth adapter"
date: 2010-01-13
forum: Hardware
---

### Post by wlraider70 on 2010-01-13
My system is a dell xps
it has a multi-card reader and bluetooth adapter combo unit.

i just installed Ubuntu and it see the card readers but when i open bluetooth from the the system tab it says no adapter.

how can i get it to recognize?

this bluetooth hub is the connection for my mouse and keyboard.
the mouse is working sporadically, but the keyboard seems to cause some problems if used.

---

### Post by studmf on 2010-01-13
bump

---

### Post by wlraider70 on 2010-01-14
Does this help?


```


luke@luke-dell:~$ lspci
00:00.0 Host bridge: Intel Corporation 82X38/X48 Express DRAM Controller
00:01.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Primary PCI Express Bridge
00:06.0 PCI bridge: Intel Corporation 82X38/X48 Express Host-Secondary PCI Express Bridge
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
03:00.0 Multimedia video controller: Conexant Systems, Inc. CX23885 PCI Video and Audio Decoder (rev 02)
04:04.0 Audio device: Creative Labs SB X-Fi
04:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
luke@luke-dell:~$ lsusb
Bus 006 Device 007: ID 046d:c719 Logitech, Inc. 
Bus 006 Device 006: ID 046d:c718 Logitech, Inc. 
Bus 006 Device 005: ID 046d:0b05 Logitech, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0644:0201 TEAC Corp. 
Bus 002 Device 004: ID 413c:5115 Dell Computer Corp. Photo AIO Printer 926
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID beef:0006  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
luke@luke-dell:~$ 



```

---

### Post by wlraider70 on 2010-01-14
i was reading about other people having issues with linux and on board bluetooth. i do not believe that this is actually part of the MB should that effect it?

---

### Post by wlraider70 on 2010-01-18
shameless bump.

i know that Linux is getting I/O from the blue-tooth because my mouse works. but the keyboard won't. It does temporally freeze the mouse for about 5 seconds.

---

