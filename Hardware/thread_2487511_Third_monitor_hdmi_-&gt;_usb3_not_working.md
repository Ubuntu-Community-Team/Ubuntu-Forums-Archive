---
title: "Third monitor hdmi -&gt; usb3 not working"
date: 2023-06-07
forum: Hardware
---

### Post by robbolo on 2023-06-07
[h=2]Hi you all,[/h][COLOR=#000000][INDENT]I just received my new third Samsung external monitor to attach to my laptop.
It works great but having "only" one hdmi on my laptop I bought a super cheap
hdmi -> usb3 adapter.
It worked fine with windows, because once connected it has an internal usb storage
with the win drivers, but when I rebooted with Ubuntu everything changed.
the kernel recognizes it

rob@rob-At-IE:~$ dmesg
[ 1412.526436] usb 3-4: new high-speed USB device number 10 using xhci_hcd
[ 1412.679400] usb 3-4: New USB device found, idVendor=534d, idProduct=6021, bcdDevice= 1.10
[ 1412.679404] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1412.679405] usb 3-4: Product: usb extscreen
[ 1412.679406] usb 3-4: Manufacturer: USB Display
[ 1412.679407] usb 3-4: SerialNumber: 2019BA7160B0
[ 1412.681293] hid-generic 0003:534D:6021.000B: hiddev0,hidraw1: USB HID v1.10 Device [USB Display usb extscreen] on usb-0000:00:14.0-4/input0
[ 1417.802825] usb 3-4: USB disconnect, device number 10
[ 1418.122396] usb 3-4: new high-speed USB device number 11 using xhci_hcd
[ 1418.271424] usb 3-4: New USB device found, idVendor=534d, idProduct=6021, bcdDevice= 1.10
[ 1418.271427] usb 3-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1418.271428] usb 3-4: Product: usb extscreen
[ 1418.271428] usb 3-4: Manufacturer: USB Display
[ 1418.271429] usb 3-4: SerialNumber: 2019BA7160B0
[ 1418.273912] hid-generic 0003:534D:6021.000C: hiddev0,hidraw1: USB HID v1.10 Device [USB Display usb extscreen] on usb-0000:00:14.0-4/input0
[ 1418.276480] usb-storage 3-4:1.4: USB Mass Storage device detected
[ 1418.276653] scsi host1: usb-storage 3-4:1.4
[ 1419.291060] scsi 1:0:0:0: Direct-Access Hjwdz MS2160 1.01 PQ: 0 ANSI: 2
[ 1419.291239] sd 1:0:0:0: Attached scsi generic sg0 type 0
[ 1419.291908] sd 1:0:0:0: [sda] 16368 512-byte logical blocks: (8.38 MB/7.99 MiB)
[ 1419.292211] sd 1:0:0:0: [sda] Write Protect is off
[ 1419.292213] sd 1:0:0:0: [sda] Mode Sense: 0c 05 00 08
[ 1419.292513] sd 1:0:0:0: [sda] No Caching mode page found
[ 1419.292515] sd 1:0:0:0: [sda] Assuming drive cache: write through
[ 1419.297595] sda:
[ 1419.297881] sd 1:0:0:0: [sda] Attached SCSI removable disk

rob@rob-At-IE:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0c45:6738 Microdia Integrated_Webcam_HD
Bus 003 Device 004: ID 27c6:639c Shenzhen Goodix Technology Co.,Ltd. Goodix USB2.0 MISC
Bus 003 Device 003: ID 145f:02c9 Trust Trust Keyboard
Bus 003 Device 006: ID 8087:0026 Intel Corp. AX201 Bluetooth
Bus 003 Device 002: ID 534d:6021 MacroSilicon VGA Display Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I tried to follow this thread, but the bug seemed to be solved

[https://bbs.archlinux.org/viewtopic....19811#p1919811]("https://bbs.archlinux.org/viewtopic.php?pid=1919811#p1919811")


Do you have any suggestion?

buy another adapter is always an option :smile:

thanks in advance[/INDENT]
[/COLOR]

---

