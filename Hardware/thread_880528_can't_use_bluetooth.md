---
title: "can't use bluetooth"
date: 2008-08-05
forum: Hardware
---

### Post by fauzi46 on 2008-08-05
hai..
i have some problem..
i using lenovo y410..
i can't using bluetooth..
can anyone tell me how to enable bluetooth..
thakz..

---

### Post by brujoand on 2008-08-05
well, it depends.. 
Is bluetooth enabled? There is usually a button on the computer for enabling this. Because if it is enabled, gnome should recognise this. If it is enabled and not recoginced by gnome, try doing a lspci in terminal and printing it here..
(applications --> accessories --> terminal)

---

### Post by eletha on 2008-08-05
I'm new to this forum but I've read a lot of pages on trying to get bluetooth working on linux. I implemented many of the different suggestions, but I still get this message:

Aug  5 10:13:15 ubuntu1 hcid[24603]: Bluetooth HCI daemon
Aug  5 10:13:15 ubuntu1 hcid[24603]: Could not become the primary owner of org.bluez
Aug  5 10:13:15 ubuntu1 hcid[24603]: Unable to get on D-Bus

 Does you know any commands that can help me debug why the bluetooth hci daemon can't become the primary owner of org.bluez?

Here is my result from lspci command:

```

:/etc$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

Thanks for your time!

---

### Post by fauzi46 on 2008-08-07
tq for advise..
now i can use my bluetooth..
tq

---

