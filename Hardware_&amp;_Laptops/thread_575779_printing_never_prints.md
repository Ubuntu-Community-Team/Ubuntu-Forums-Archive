---
title: "printing never prints"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by sromagazine on 2007-10-14
I have a hp laserjet 1000 printer connected via usb and the system finds it.  I installed it but it does not print.  the print jobs just sits in the que forever.

so then I installed cups and removed all the printers and then reinstalled and the same thing.

Description: HP LaserJet 1000
Location: Local Printer
Make and Model: HP LaserJet 1000 Foomatic/foo2zjs (recommended)
Printer State: idle, accepting jobs, published.
Device URI: hp:/usb/hp_LaserJet_1000?serial=?

ID  	Name  	User  	Size  	Pages  	State  	Control 
HP_LaserJet_1000_USB_-13  	Test Page  	ryans  	19k  	Unknown  	processing since
Sun 14 Oct 2007 10:41:09 AM PDT 


this sucks because i need to make this system my printer server for my wife.  she prints a lot remotely and I don't want to have to switch back to XP.

---

### Post by sromagazine on 2007-10-14
[   61.830842] usbcore: registered new device driver usb
[   61.927358] usb usb1: configuration #1 chosen from 1 choice
[   62.095633] usb usb2: configuration #1 chosen from 1 choice
[   62.202154] usb usb3: configuration #1 chosen from 1 choice
[   63.280179] usb 3-1: new high speed USB device using ehci_hcd and address 2
[   63.436755] usb 3-1: configuration #1 chosen from 1 choice
[   63.679743] usb 3-2: new high speed USB device using ehci_hcd and address 3
[   63.820542] usb 3-2: configuration #1 chosen from 1 choice
[   64.434916] usb 3-5: new high speed USB device using ehci_hcd and address 6
[   64.598200] usb 3-5: configuration #1 chosen from 1 choice
[   64.873377] usb 3-6: new high speed USB device using ehci_hcd and address 7
[   65.007213] usb 3-6: configuration #1 chosen from 1 choice
[   65.007555] usbcore: registered new interface driver libusual
[   65.313964] usb 2-1: new full speed USB device using ohci_hcd and address 2
[   65.526623] usb 2-1: configuration #1 chosen from 1 choice
[   65.833390] usb 2-2: new low speed USB device using ohci_hcd and address 3
[   66.134882] usb 2-2: configuration #1 chosen from 1 choice
[   66.137963] usb-storage: device found at 2
[   66.137965] usb-storage: waiting for device to settle before scanning
[   66.138047] usb-storage: device found at 3
[   66.138049] usb-storage: waiting for device to settle before scanning
[   66.138120] usb-storage: device found at 6
[   66.138122] usb-storage: waiting for device to settle before scanning
[   66.138197] usb-storage: device found at 7
[   66.138199] usb-storage: waiting for device to settle before scanning
[   66.138214] usbcore: registered new interface driver usb-storage
[   71.115832] usb-storage: device scan complete
[   71.115861] usb-storage: device scan complete
[   71.115945] usb-storage: device scan complete
[   71.116181] usb-storage: device scan complete
[   76.244635] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x1C02
[   76.550929] drivers/usb/class/usblp.c: usblp1: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
[   76.550949] usbcore: registered new interface driver hiddev
[   76.613071] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:02.1-2
[   76.613090] usbcore: registered new interface driver usbhid
[   76.613094] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   76.613505] usbcore: registered new interface driver usblp
[   76.613508] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[  106.576757] usb 3-2: reset high speed USB device using ehci_hcd and address 3
[  430.881154] drivers/usb/class/usblp.c: usblp1: removed

---

### Post by sromagazine on 2007-10-14
bump.

---

### Post by tdmoore on 2007-11-03
I have the same issue and cannot get it to work either.

Another post had unplug power and USB, then connect.  One person had success with this.  I tried and did not.

Anyone?

---

### Post by stchman on 2007-11-13
> **sromagazine said:**
> I have a hp laserjet 1000 printer connected via usb and the system finds it.  I installed it but it does not print.  the print jobs just sits in the que forever.

so then I installed cups and removed all the printers and then reinstalled and the same thing.

Description: HP LaserJet 1000
Location: Local Printer
Make and Model: HP LaserJet 1000 Foomatic/foo2zjs (recommended)
Printer State: idle, accepting jobs, published.
Device URI: hp:/usb/hp_LaserJet_1000?serial=?

ID  	Name  	User  	Size  	Pages  	State  	Control 
HP_LaserJet_1000_USB_-13  	Test Page  	ryans  	19k  	Unknown  	processing since
Sun 14 Oct 2007 10:41:09 AM PDT 


this sucks because i need to make this system my printer server for my wife.  she prints a lot remotely and I don't want to have to switch back to XP.

The foo2zjs driver will not work in Ubuntu.  I believe that the problem is fixed in Gutsy.  I have a LaserJet 1000 hooked up and working on my system.

Read my tutorial here:

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

---

### Post by scorp001 on 2007-11-16
Well yes gutsy and all earlier foo drivers all work but there are a couple of issues

1. The original install may not point to the right location for the printer

2. The firmware needs to be uploaded to the printer each time you start the pc. even if you restart the cupsys service you will need to repower the printer and then use lpr command to send the firmware to the pc.

check ur printer is installed using standard printer installation procedure - gutsy does it automatically - tho you may need to make the printer default by going to menus System>Administration>Printing - now select ur printer on the left pane and click on make default.

Now basis that ur HP 1000 is installed as the Ubuntu

1st problem solution
For the first problem look in the /dev folder for usb subfolder in which you will see lp0 so you do need to give the correct location if you are having a problem uploading the firmware.  The print command is waiting for ever or u get the info that printer not connected.

type this command :
sudo gedit /etc/cups/printers.conf

look for DeviceURI - u might see the line showing something like for eg DeviceURI usb://HP/hp%20LaserJet%201000 - in which case you will need to give the correct location :
DeviceURI file:///dev/usb/lp0

2nd problem solution
restart the cupsys by typing in the terminal window :
sudo /etc/init.d/cupsys restart

now repower the printer - put the power switch off and on after say 15 20 seconds.

send the firmware to your printer using lpr command on the terminal window
lpr /home/user name/your file location/sihp1000.img

This file is attached with this post sihp1000.img and is zipped - just download and unzip.
and use the lpr command. I have made a small script of it and added to my session so that each time my pc starts it also uploads the firmware to the printer.

I hope this helps out all those in agony.

cheers

---

