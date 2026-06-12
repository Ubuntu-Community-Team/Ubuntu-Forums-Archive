---
title: "USB device detection (or lack thereof)"
date: 2006-05-18
forum: Hardware &amp; Laptops
---

### Post by ktulu1115 on 2006-05-18
Having a recent problem ever since I did the last package update.  USB worked fine, no problem - but now when I plug in a USB device (other than my mouse), it is not fully detected or configured.

After plugging in a USB flash drive, card reader, external drive, etc...  I get the following in /var/log/messages:

May 18 22:35:47 localhost kernel: [  524.206681] usb 1-2.4: new high speed USB device using ehci_hcd and address 5
May 18 22:35:53 localhost kernel: [  527.375858] usb 1-2.4: new high speed USB device using ehci_hcd and address 6
May 18 22:36:00 localhost kernel: [  530.545532] usb 1-2.4: new high speed USB device using ehci_hcd and address 7
May 18 22:36:05 localhost kernel: [  533.089463] usb 1-2.4: new high speed USB device using ehci_hcd and address 8

...and that's it.  Device never configured or accessable.  Same thing happens if I'm plugged into a USB hub, or directly into back of the PC.  usbview shows the hub, but that's it - nothing plugged into it.   Ideas?

---

### Post by joshrobinson on 2006-05-18
when you plug it in does it show up in the disks menu

system administration disks

---

### Post by ktulu1115 on 2006-05-18
absolutely nothing - other than the internal hard drives in the box.  Oh, and the activity light doesn't light up like it normally does when plugged into a USB port.  Just verified it works fine on my XP laptop.

Also - cat /proc/bus/usb/devices:

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh=10
B:  Alloc= 14/900 us ( 2%), #Int=  1, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-23-amd64-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c50e Rev=25.00
S:  Manufacturer=Logitech
S:  Product=USB Receiver
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr= 70mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=10
B:  Alloc=  0/800 us ( 0%), #Int=  1, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-23-amd64-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:02.1
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=02 MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=a700 Rev= 0.00
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr= 98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=01 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms
I:  If#= 0 Alt= 1 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=02 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   1 Ivl=256ms

It also seems that /var/log/messages only reports a plugin once, after removing the device then plugging in again, I see no additional messages.

---

### Post by ktulu1115 on 2006-05-18
One other odd thing I noticed - after it stopped working, I tried plugging in the USB flash drive a few times into the back of the MB directly - most of the time it was the same result (nothing), although one time it stopped my mouse from working while it was plugged in.  I have a Logitech MX laser connected via USB.

---

### Post by kzutter on 2006-05-18
I do not know if it the same with dapper, but breezy (maybe hoary, too) has a pretty well documented error with hal that has the same symptoms.

The problem stopped happening to me when I switched to kubuntu, so I do not remember the fix - I am sure if you search for it you will find stuff on it.

Here is one fix: [http://www.ubuntuforums.org/showthread.php?t=173300](http://www.ubuntuforums.org/showthread.php?t=173300)

good luck - and thanx for your testing work

---

### Post by ktulu1115 on 2006-05-19
Thanks for the info - tried that, but unfortunately, no luck.

I've searched the forums, havn't found this problem anywhere else really.  Anyone else have any suggestions?

---

### Post by ktulu1115 on 2006-05-19
Also noticed that usb-storage module was not being loaded - tried manually loading, then plugging in device - still nothing.  Now it seems I'm not even getting any entries in /var/log/messages anymore.  This almost sounds like a udev issue to me, but I have no clue where to start tackling it.  Anyone else experience a similar problem?

---

### Post by ktulu1115 on 2006-05-21
*bump*

---

### Post by brandon moore on 2006-05-22
i am having a very similar problem.  when i plug in my usb flash stick, i get this from dmesg:

> [4358035.312000] usb 2-2: new full speed USB device using uhci_hcd and address 2[4358035.425000] usb 2-2: device descriptor read/64, error -71
[4358035.639000] usb 2-2: device descriptor read/64, error -71
[4358035.842000] usb 2-2: new full speed USB device using uhci_hcd and address 3[4358035.955000] usb 2-2: device descriptor read/64, error -71
[4358036.169000] usb 2-2: device descriptor read/64, error -71
[4358036.372000] usb 2-2: new full speed USB device using uhci_hcd and address 4[4358036.780000] usb 2-2: device not accepting address 4, error -71
[4358036.882000] usb 2-2: new full speed USB device using uhci_hcd and address 5[4358037.290000] usb 2-2: device not accepting address 5, error -71


---

### Post by ktulu1115 on 2006-05-22
I don't get those errors in dmesg, but in /var/log/kern.log and syslog I get the following:

May 22 12:26:35 localhost kernel: [136710.722817] usb 2-1: new high speed USB device using ehci_hcd and address 5
May 22 12:26:41 localhost kernel: [136713.780109] usb 2-1: device descriptor read/all, error -110
May 22 12:26:41 localhost kernel: [136713.832021] usb 2-1: new high speed USB device using ehci_hcd and address 6
May 22 12:26:47 localhost kernel: [136716.888792] usb 2-1: device descriptor read/all, error -110
May 22 12:26:47 localhost kernel: [136716.939726] usb 2-1: new high speed USB device using ehci_hcd and address 7
May 22 12:26:57 localhost kernel: [136722.043586] usb 2-1: device descriptor read/all, error -110
May 22 12:26:58 localhost kernel: [136722.101548] usb 2-1: new high speed USB device using ehci_hcd and address 8
May 22 12:27:03 localhost kernel: [136724.615528] usb 2-1: device descriptor read/8, error -110
May 22 12:27:08 localhost kernel: [136727.170476] usb 2-1: device descriptor read/8, error -110

This only seems to occur when I plug the memory stick into a new USB port - onced plugged into a port and removed, further connections do not provide a message on that port.

---

### Post by gsanse on 2006-05-31
Having a similar problem here. My mobo does not support USB2 so I added a VIA PCI USB card. The card works perfeclty in Breezy, but since I upgraded to Dapper the ports on the card stopped working. If I try to connect a device to a port on the PCI USB card, here are the messages I get in dmesg:

[4295456.807000] usb 5-2: new high speed USB device using ehci_hcd and address 15
[4295459.911000] usb 5-2: device descriptor read/64, error -110
[4295475.116000] usb 5-2: device descriptor read/64, error -110
[4295475.320000] usb 5-2: new high speed USB device using ehci_hcd and address 16
[4295478.423000] usb 5-2: device descriptor read/64, error -110
[4295493.627000] usb 5-2: device descriptor read/64, error -110
[4295493.830000] usb 5-2: new high speed USB device using ehci_hcd and address 17
[4295504.232000] usb 5-2: device not accepting address 17, error -110
[4295504.335000] usb 5-2: new high speed USB device using ehci_hcd and address 18
[4295514.738000] usb 5-2: device not accepting address 18, error -110

If I connect the same device to a mobo usb port it works perfectly. 

The PCI card is correcty detected by the system, here is the output for lspci:

0000:00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
0000:00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
0000:00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
0000:00:00.3 RAM memory: nVidia Corporation nForce 420 Memory Controller (DDR) (rev b2)
0000:00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
0000:00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
0000:00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
0000:00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce Audio (rev c2)
0000:00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
0000:00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
0000:01:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:01:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:01:07.0 Multimedia video controller: Brooktree Corporation Bt848 Video Capture (rev 11)
0000:01:08.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
0000:01:08.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
0000:01:08.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
0000:01:09.0 Multimedia controller: Sigma Designs, Inc. REALmagic Hollywood Plus DVD Decoder (rev 02)
0000:02:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)

Anyone has any ideas?

---

### Post by Jeff Johnston on 2006-06-03
This is the first post that describes my problem completely. At least I know I am not alone :(.

My error message is:
[4299242.171000] usb 4-6: can't read configurations, error -71
[4299242.490000] usb 4-6: new high speed USB device using ehci_hcd and address 80

I am trying to plug in an iAudio player USB device. It works perfectly on my old computer, but not my newer one. It is probably just bad luck with the device. Other USB devices work perfectly.

---

