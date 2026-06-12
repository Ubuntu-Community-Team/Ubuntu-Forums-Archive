---
title: "k400 logitech keyboard not working"
date: 2013-03-07
forum: Hardware
---

### Post by saadsyed on 2013-03-07
hey there
i have ubuntu 12.04 the keyboard worked fine at first then after reboot stop working. check other forum and installed 12.10 version of ubuntu and still no joy. can anyone advice me on the matter. the keyboard works fine on windows 7 which is also on the same computer. 
i also have a wireless mouse mircosoft which works fine on both OS.

---

### Post by ssiivanov on 2013-03-19
Hey,

Had the same problem, but I literally plugged the receiver into every port of the laptop while running ubuntu until it detected it! Runs nicely now

---

### Post by saadsyed on 2013-04-30
thanks for your help. it works now but the only annoying problem is everytime i restart the system i have to re-plug the keyboard. i can live with that.

---

### Post by netgooroo on 2013-05-01
Hey guys, having same issue with a K800. I posted a thread here..  [http://ubuntuforums.org/showthread.php?t=2139049](http://ubuntuforums.org/showthread.php?t=2139049)

---

### Post by Processorhog on 2014-01-10
I have the same problem with a K800 and a Performance Mouse MX. My old Microsoft keyboard and logitech mouse used to work fine but my new Logitech devices don't.

I have 12.10 (Quetzal). I don't want to upgrade to 13.10 because I have a lot of things set up and need specific versions of my dev tools and don't want to break everything by version upgrades :-)

After a reboot, both the keyboard and mouse stop working. I have to plug the unifying receiver (the little USB thing) between three ports in the front. Sometimes it does not work even if I try all three, so I keep trying until it works.

Here's the dmesg output (I've masked something that looked like my device ID):

[  272.700671] usb 3-5: USB disconnect, device number 6                                         ------------------------------->>>>>>>>>>>>>   Manually disconnected by removing the USB nano unifying receiver
[  274.146254] usb 3-6: new full-speed USB device number 7 using xhci_hcd
[  274.164728] usb 3-6: New USB device found, idVendor=046d, idProduct=c52b
[  274.164735] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  274.164740] usb 3-6: Product: USB Receiver
[  274.164744] usb 3-6: Manufacturer: Logitech
[  274.170423] logitech-djreceiver xxxx:xxxx:xxxx.000B: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-6/input2
[  274.170695] logitech-djreceiver xxxx:xxxx:xxxx.000B: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
[  274.171007] logitech-djreceiver: probe of xxxx:xxxx:xxxx.000B failed with error -32                                                   ------------------------------------------------->>>>>>>>>>>>    ERROR!!!!
[  278.117211] usb 3-6: USB disconnect, device number 7
[  279.265801] usb 3-5: new full-speed USB device number 8 using xhci_hcd
[  279.284245] usb 3-5: New USB device found, idVendor=046d, idProduct=c52b
[  279.284252] usb 3-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  279.284257] usb 3-5: Product: USB Receiver
[  279.284260] usb 3-5: Manufacturer: Logitech
[  279.289815] logitech-djreceiver xxxx:xxxx:xxxx.000E: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-5/input2
[  279.290105] logitech-djreceiver xxxx:xxxx:xxxx.000E: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
[  279.290798] logitech-djreceiver: probe of xxxx:xxxx:xxxx.000E failed with error -32
[  294.805837] usb 3-5: USB disconnect, device number 8
[  301.787482] usb 3-6: new full-speed USB device number 9 using xhci_hcd
[  301.805863] usb 3-6: New USB device found, idVendor=046d, idProduct=c52b
[  301.805871] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  301.805875] usb 3-6: Product: USB Receiver
[  301.805879] usb 3-6: Manufacturer: Logitech
[  301.811493] logitech-djreceiver xxxx:xxxx:xxxx.0011: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-6/input2
[  301.811769] logitech-djreceiver xxxx:xxxx:xxxx.0011: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
[  301.811976] logitech-djreceiver: probe of xxxx:xxxx:xxxx.0011 failed with error -32
[  321.233628] usb 3-6: USB disconnect, device number 9
[  322.312942] usb 3-5: new full-speed USB device number 10 using xhci_hcd
[  322.331439] usb 3-5: New USB device found, idVendor=046d, idProduct=c52b
[  322.331447] usb 3-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  322.331451] usb 3-5: Product: USB Receiver
[  322.331455] usb 3-5: Manufacturer: Logitech
[  322.337411] logitech-djreceiver xxxx:xxxx:xxxx.0014: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-5/input2
[  322.344684] input: Logitech Unifying Device. Wireless PID:2010 as /devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5:1.2/xxxx:xxxx:xxxx.0014/input/input19     ---------------------------------------->>>>>>>>>>>  Working Now!
[  322.346372] logitech-djdevice xxxx:xxxx:xxxx.0015: input,hidraw1: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:2010] on usb-0000:00:14.0-5:1
[  322.346712] input: Logitech Unifying Device. Wireless PID:101a as /devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5:1.2/xxxx:xxxx:xxxx.0014/input/input20
[  322.347585] logitech-djdevice xxxx:xxxx:xxxx.0016: input,hidraw2: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101a] on usb-0000:00:14.0-5:2
[  935.897051] usb 3-5: USB disconnect, device number 10
[  938.521380] usb 3-5: new full-speed USB device number 11 using xhci_hcd
[  938.539799] usb 3-5: New USB device found, idVendor=046d, idProduct=c52b
[  938.539806] usb 3-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  938.539811] usb 3-5: Product: USB Receiver
[  938.539814] usb 3-5: Manufacturer: Logitech
[  938.545441] logitech-djreceiver xxxx:xxxx:xxxx.0019: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-5/input2
[  938.545730] logitech-djreceiver xxxx:xxxx:xxxx.0019: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
[  938.545974] logitech-djreceiver: probe of xxxx:xxxx:xxxx.0019 failed with error -32
[  948.319432] usb 3-5: USB disconnect, device number 11
[  949.864876] usb 3-6: new full-speed USB device number 12 using xhci_hcd
[  949.883276] usb 3-6: New USB device found, idVendor=046d, idProduct=c52b
[  949.883283] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  949.883288] usb 3-6: Product: USB Receiver
[  949.883291] usb 3-6: Manufacturer: Logitech
[  949.888891] logitech-djreceiver xxxx:xxxx:xxxx.001C: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-6/input2
[  949.889178] logitech-djreceiver xxxx:xxxx:xxxx.001C: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
[  949.889533] logitech-djreceiver: probe of xxxx:xxxx:xxxx.001C failed with error -32
[  961.598445] usb 3-6: USB disconnect, device number 12
[  963.938280] usb 3-8: new full-speed USB device number 13 using xhci_hcd
[  963.956698] usb 3-8: New USB device found, idVendor=046d, idProduct=c52b
[  963.956705] usb 3-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  963.956709] usb 3-8: Product: USB Receiver
[  963.956713] usb 3-8: Manufacturer: Logitech
[  963.962391] logitech-djreceiver xxxx:xxxx:xxxx.001F: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-8/input2
[  963.962659] logitech-djreceiver xxxx:xxxx:xxxx.001F: logi_dj_probe:logi_dj_recv_query_paired_devices error:-32
[  963.962956] logitech-djreceiver: probe of xxxx:xxxx:xxxx.001F failed with error -32
[  981.469373] usb 3-8: USB disconnect, device number 13
[  982.732049] usb 3-6: new full-speed USB device number 14 using xhci_hcd
[  982.750608] usb 3-6: New USB device found, idVendor=046d, idProduct=c52b
[  982.750615] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  982.750620] usb 3-6: Product: USB Receiver
[  982.750624] usb 3-6: Manufacturer: Logitech
[  982.756222] logitech-djreceiver xxxx:xxxx:xxxx.0022: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-6/input2
[  982.759268] input: Logitech Unifying Device. Wireless PID:2010 as /devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.2/xxxx:xxxx:xxxx.0022/input/input21
[  982.759432] logitech-djdevice xxxx:xxxx:xxxx.0023: input,hidraw1: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:2010] on usb-0000:00:14.0-6:1
[  982.761072] input: Logitech Unifying Device. Wireless PID:101a as /devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.2/xxxx:xxxx:xxxx.0022/input/input22
[  982.761287] logitech-djdevice xxxx:xxxx:xxxx.0024: input,hidraw2: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:101a] on usb-0000:00:14.0-6:2




As you can see, it works occasionally. But for some reason, the "djreceiver probe" fails most of the time. 

I don't know enough to determine whether this is Logitech's fault for not implementing something right, but I'm leaning towards something in Ubuntu. This keyboard/mouse combo works just fine EVERY time without fail in Windows 7, Windows 8 and Ubuntu 13.10 LiveUSB.

Just thought I'd paste it here in case anyone still has this problem.

---

