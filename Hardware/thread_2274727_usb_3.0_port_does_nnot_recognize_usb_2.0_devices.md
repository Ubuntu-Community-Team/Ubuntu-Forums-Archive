---
title: "usb 3.0 port does nnot recognize usb 2.0 devices"
date: 2015-04-21
forum: Hardware
---

### Post by xxangel-of-lightxx on 2015-04-21
[COLOR=#333333][FONT=Ubuntu]ok so here this goes, also i want to thank you in advance with whoever takes the time and effort to help me with this.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]         well here is the scenario, ok so i have an ASUS x200ma notebook. I switched over from windows a few months and, am currently using Ubuntu 14.04. this particular model of laptop has a total of 3 USB ports, two on the right which are USB 2.0 and one on the left which is a 3.0 port. I noticed when i first started running ubuntu on this machine that the 3.0 port would not recognize USB devices. it would not even signal that the device was powered on.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]       Fast foward to today and i am try to connect a razer tarterus keypad in the USB 3.0 port, on the left. however, it wont power on, the led indication doesnt light up. whenever i plug it into the the USB ports on the right it works. on the contrary when i plug my usb 3.0 gigstick in the 3.0 port it works but only after i entered the "devmod" command in the terminal.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]     below is a list of output from some commands,[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]      (lsusb) [with the razer keypad plugged into the USB 3.0 port][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]eerie-noizez@Cy-Gor:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 25a7:2433
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 0bda:5605 Realtek Semiconductor Corp.
Bus 001 Device 002: ID 0457:1029 Silicon Integrated Systems Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
eerie-noizez@Cy-Gor:~$[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]____________________________________________________________________________________[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]ls /dev | grep [s,h]d -with the razer keypad in the usb 3.0 port[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]eerie-noizez@Cy-Gor:~$ ls /dev | grep [s,h]d
sda
sda1
sda2
sda3[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]____________________________________________________________________________________[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]dmesg | grep USB [with the razer keypad plugged into the USB 3.0 port][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]eerie-noizez@Cy-Gor:~$ dmesg | grep USB
[ 0.216078] ACPI: Power Resource [USBC] (on)
[ 0.255282] ACPI: bus type USB registered
[ 1.174539] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 1.174600] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 1.174654] uhci_hcd: USB Universal Host Controller Interface driver
[ 1.174913] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[ 1.175501] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[ 1.175506] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1.175860] hub 1-0:1.0: USB hub found
[ 1.177599] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[ 1.177693] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[ 1.177698] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1.177974] hub 2-0:1.0: USB hub found
[ 1.489000] usb 1-2: new full-speed USB device number 2 using xhci_hcd
[ 1.689934] usb 1-2: New USB device found, idVendor=0457, idProduct=1029
[ 1.689939] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1.689947] usb 1-2: Manufacturer: USBest Technology
[ 1.706302] usbhid: USB HID core driver
[ 1.861272] usb 1-3: new high-speed USB device number 3 using xhci_hcd
[ 2.021801] usb 1-3: New USB device found, idVendor=0bda, idProduct=5605
[ 2.021807] usb 1-3: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[ 2.021812] usb 1-3: Product: USB2.0 HD UVC WebCam
[ 2.189350] usb 1-4: new high-speed USB device number 4 using xhci_hcd
[ 2.319425] usb 1-4: New USB device found, idVendor=05e3, idProduct=0608
[ 2.319431] usb 1-4: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[ 2.319436] usb 1-4: Product: USB2.0 Hub
[ 2.320487] hub 1-4:1.0: USB hub found
[ 28.141895] usb 1-4.2: new full-speed USB device number 5 using xhci_hcd
[ 28.232471] usb 1-4.2: New USB device found, idVendor=25a7, idProduct=2433
[ 28.232477] usb 1-4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 28.242827] hid-generic 0003:25A7:2433.0002: input,hidraw0: USB HID v1.01 Keyboard [2.4G 2.4G Wireless Device] on usb-0000:00:14.0-4.2/input0
[ 28.243650] hid-generic 0003:25A7:2433.0003: input,hiddev0,hidraw1: USB HID v1.01 Mouse [2.4G 2.4G Wireless Device] on usb-0000:00:14.0-4.2/input1
[ 52.275397] input: USBest Technology SiS HID Touch Controller as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/0003:0457:1029.0001/input/input18
[ 52.275876] hid-multitouch 0003:0457:1029.0001: input,hiddev0,hidraw2: USB HID v1.11 Device [USBest Technology SiS HID Touch Controller] on usb-0000:00:14.0-2/input0
[ 52.361018] uvcvideo: Found UVC 1.00 device USB2.0 HD UVC WebCam (0bda:5605)
[ 52.367227] input: USB2.0 HD UVC WebCam as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/input/input20
[ 52.367482] USB Video Class driver (1.1.1)
[ 325.558615] usb 2-1: new SuperSpeed USB device number 2 using xhci_hcd
[ 325.577998] usb 2-1: New USB device found, idVendor=05dc, idProduct=a205
[ 325.578019] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 325.689426] usb-storage 2-1:1.0: USB Mass Storage device detected
[ 380.622213] usb 2-1: USB disconnect, device number 2
[ 3504.654210] usb 1-4.3: new high-speed USB device number 6 using xhci_hcd
[ 3505.256303] usb 1-4.3: New USB device found, idVendor=05dc, idProduct=a815
[ 3505.256310] usb 1-4.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3505.256314] usb 1-4.3: Product: USB Flash Drive
[ 3505.258084] usb-storage 1-4.3:1.0: USB Mass Storage device detected
[ 3506.970891] scsi 3:0:0:0: Direct-Access Lexar USB Flash Drive 1100 PQ: 0 ANSI: 4
[ 4075.271155] usb 1-4.3: USB disconnect, device number 6[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]____________________________________________________________________________________ ------------------------------------------------------------------------------------------------------------------------------
From this point i plugged the razer keypad into USB 2.0 port on the right
------------------------------------------------------------------------------------------------------------------------------____________________________________________________________________________________[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]lsusb [with USB 3.0 gigstick in the 3.0 port[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]eerie-noizez@Cy-Gor:~$ lsusb
Bus 002 Device 003: ID 05dc:a205 Lexar Media, Inc.
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 1532:0201 Razer USA, Ltd
Bus 001 Device 005: ID 25a7:2433
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 0bda:5605 Realtek Semiconductor Corp.
Bus 001 Device 002: ID 0457:1029 Silicon Integrated Systems Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]____________________________________________________________________________________[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]ls /dev |grep [s,h]d --with the USB 3.0 gigstick in the USB 3.0 port[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]eerie-noizez@Cy-Gor:~$ ls /dev | grep [s,h]d
sda
sda1
sda2
sda3
sdb
sdb1[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]____________________________________________________________________________________[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]dmesg | grep USB [ with the USB 3.0 gigstick in the USB 3.0 port][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]eerie-noizez@Cy-Gor:~$ dmesg | grep USB
[ 0.216078] ACPI: Power Resource [USBC] (on)
[ 0.255282] ACPI: bus type USB registered
[ 1.174539] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 1.174600] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 1.174654] uhci_hcd: USB Universal Host Controller Interface driver
[ 1.174913] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[ 1.175501] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[ 1.175506] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1.175860] hub 1-0:1.0: USB hub found
[ 1.177599] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[ 1.177693] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[ 1.177698] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 1.177974] hub 2-0:1.0: USB hub found
[ 1.489000] usb 1-2: new full-speed USB device number 2 using xhci_hcd
[ 1.689934] usb 1-2: New USB device found, idVendor=0457, idProduct=1029
[ 1.689939] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1.689947] usb 1-2: Manufacturer: USBest Technology
[ 1.706302] usbhid: USB HID core driver
[ 1.861272] usb 1-3: new high-speed USB device number 3 using xhci_hcd
[ 2.021801] usb 1-3: New USB device found, idVendor=0bda, idProduct=5605
[ 2.021807] usb 1-3: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[ 2.021812] usb 1-3: Product: USB2.0 HD UVC WebCam
[ 2.189350] usb 1-4: new high-speed USB device number 4 using xhci_hcd
[ 2.319425] usb 1-4: New USB device found, idVendor=05e3, idProduct=0608
[ 2.319431] usb 1-4: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[ 2.319436] usb 1-4: Product: USB2.0 Hub
[ 2.320487] hub 1-4:1.0: USB hub found
[ 28.141895] usb 1-4.2: new full-speed USB device number 5 using xhci_hcd
[ 28.232471] usb 1-4.2: New USB device found, idVendor=25a7, idProduct=2433
[ 28.232477] usb 1-4.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 28.242827] hid-generic 0003:25A7:2433.0002: input,hidraw0: USB HID v1.01 Keyboard [2.4G 2.4G Wireless Device] on usb-0000:00:14.0-4.2/input0
[ 28.243650] hid-generic 0003:25A7:2433.0003: input,hiddev0,hidraw1: USB HID v1.01 Mouse [2.4G 2.4G Wireless Device] on usb-0000:00:14.0-4.2/input1
[ 52.275397] input: USBest Technology SiS HID Touch Controller as /devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/0003:0457:1029.0001/input/input18
[ 52.275876] hid-multitouch 0003:0457:1029.0001: input,hiddev0,hidraw2: USB HID v1.11 Device [USBest Technology SiS HID Touch Controller] on usb-0000:00:14.0-2/input0
[ 52.361018] uvcvideo: Found UVC 1.00 device USB2.0 HD UVC WebCam (0bda:5605)
[ 52.367227] input: USB2.0 HD UVC WebCam as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/input/input20
[ 52.367482] USB Video Class driver (1.1.1)
[ 325.558615] usb 2-1: new SuperSpeed USB device number 2 using xhci_hcd
[ 325.577998] usb 2-1: New USB device found, idVendor=05dc, idProduct=a205
[ 325.578019] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 325.689426] usb-storage 2-1:1.0: USB Mass Storage device detected
[ 380.622213] usb 2-1: USB disconnect, device number 2
[ 3504.654210] usb 1-4.3: new high-speed USB device number 6 using xhci_hcd
[ 3505.256303] usb 1-4.3: New USB device found, idVendor=05dc, idProduct=a815
[ 3505.256310] usb 1-4.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3505.256314] usb 1-4.3: Product: USB Flash Drive
[ 3505.258084] usb-storage 1-4.3:1.0: USB Mass Storage device detected
[ 3506.970891] scsi 3:0:0:0: Direct-Access Lexar USB Flash Drive 1100 PQ: 0 ANSI: 4
[ 4075.271155] usb 1-4.3: USB disconnect, device number 6
[ 7448.599441] usb 1-4.3: new full-speed USB device number 7 using xhci_hcd
[ 7448.688455] usb 1-4.3: New USB device found, idVendor=1532, idProduct=0201
[ 7448.688462] usb 1-4.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 7448.690896] hid-generic 0003:1532:0201.0004: input,hidraw3: USB HID v1.11 Keyboard [Razer Razer Tartarus] on usb-0000:00:14.0-4.3/input0
[ 7448.693471] hid-generic 0003:1532:0201.0005: input,hidraw4: USB HID v1.11 Keyboard [Razer Razer Tartarus] on usb-0000:00:14.0-4.3/input1
[ 7448.695409] hid-generic 0003:1532:0201.0006: input,hidraw5: USB HID v1.11 Mouse [Razer Razer Tartarus] on usb-0000:00:14.0-4.3/input2
[ 7478.242336] usb 2-1: new SuperSpeed USB device number 3 using xhci_hcd
[ 7478.258621] usb 2-1: New USB device found, idVendor=05dc, idProduct=a205
[ 7478.258629] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 7478.259178] usb-storage 2-1:1.0: USB Mass Storage device detected[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]why wont the USB 3.0 port recognize my USB 2.0 razer keypad???[/FONT][/COLOR]

---

### Post by ajgreeny on 2015-04-22
Perhaps the razer keypad needs more power than the single usb 3 port is supplying, as you say it does not even show it powered on.

I have a portable, host powered USB external hard drive which on some machines, but not all, needs the two plugs on the Y cord inserted to get sufficient power for it to work; maybe the razer keypad is the same?

My knowledge of any differences between USB2 and USB3 is zero, apart from the read/write speeds that should be available, so I may be talking total rubbish.

---

### Post by xxangel-of-lightxx on 2015-04-22
[http://www.usr.com/en/education/usb-30-peripherals/](http://www.usr.com/en/education/usb-30-peripherals/)

so if i am reading this right, USB 3.0 uses more power than 2.0. therefore, 3.0 should have sufficient power to run this device.Also i have a windows desktop and the 3.0 ports on that machine recognize the device no problem.

---

### Post by davidvandoren on 2015-04-24
I keep pasting this now to the second thread here in 2 minutes.

Restart your pc and go into your bios.
Enable advanced settings and look for usb settings.
Change the USB 3.0 from XHCI enabled to disabled.
And if available the usb 2 settings EHCI settings from enabled to disabled or vise verse.

Try out both options with the EHCI settings.

---

