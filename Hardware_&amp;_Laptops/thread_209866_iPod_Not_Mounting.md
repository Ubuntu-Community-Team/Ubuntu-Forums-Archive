---
title: "iPod Not Mounting"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by natsmith9 on 2006-07-05
When I first plugged in my iPod 4G b/w click-wheel to my computer while Ubuntu (Dapper Drake) was running, it recognized my iPod and worked just fine.  Now everytime I start up Ubuntu it no longer mounts my iPod.  I have even followed the instructions from Ubuntux.org ([http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu)](http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu)).

Any thoughts?

---

### Post by Kethinov on 2006-07-05
Unplug it, plug it back in, open the terminal, type **dmesg**, show us the last few lines it shows you.

---

### Post by natsmith9 on 2006-07-08
This is what it gave me...I obviously cut a lot of it out.

```
[17179606.120000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17179606.120000] ide: failed opcode was: unknown
[17179606.120000] end_request: I/O error, dev hdc, sector 0
[17179606.120000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17179606.120000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17179606.120000] ide: failed opcode was: unknown
[17179606.120000] end_request: I/O error, dev hdc, sector 4
[17179606.120000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17179606.120000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17179606.120000] ide: failed opcode was: unknown
[17179606.120000] end_request: I/O error, dev hdc, sector 0
[17179606.124000] hdc: command error: status=0x51 { DriveReady SeekComplete Erro r }
[17179606.124000] hdc: command error: error=0x54 { AbortedCommand LastFailedSens e=0x05 }
[17179606.124000] ide: failed opcode was: unknown
[17179606.124000] end_request: I/O error, dev hdc, sector 4
[17179606.392000] Bluetooth: Core ver 2.8
[17179606.392000] NET: Registered protocol family 31
[17179606.392000] Bluetooth: HCI device and connection manager initialized
[17179606.392000] Bluetooth: HCI socket layer initialized
[17179606.408000] Bluetooth: L2CAP ver 2.8
[17179606.408000] Bluetooth: L2CAP socket layer initialized
[17179606.408000] Bluetooth: RFCOMM socket layer initialized
[17179606.408000] Bluetooth: RFCOMM TTY layer initialized
[17179606.408000] Bluetooth: RFCOMM ver 1.7

```

---

