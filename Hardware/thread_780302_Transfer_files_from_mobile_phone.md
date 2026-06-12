---
title: "Transfer files from mobile phone"
date: 2008-05-03
forum: Hardware
---

### Post by bossa on 2008-05-03
Hi All

How do I get to transfer files ie pics/video/mp3 to and from my mobile phone. I have a Samsung SGH-E740 and I downloaded and installed the software "Samsung PC studio" with Wine but it says the phone is not connected (By USB), is there a Linux program that does the same thing?
Really dont want to have to use windows again :(
Any advice will be much appreciated.

---

### Post by starcannon on 2008-05-03
Bitpim works great if it has support for your phone.
Check it out, and side note, I've occasionally found phones that aren't listed but will work with other phone profiles, so its worth a go either way.[http://www.bitpim.org/]("http://www.bitpim.org/")

---

### Post by bossa on 2008-05-03
starcannon

Thanks for that ,will try it out and report back
Cheers

---

### Post by bossa on 2008-05-05
Bitpim does not detect my phone and also detects my phone :confused:
at first I am prompted to use the wizard as it does not detect my phone.
When going through the wizard I chose other CDMA phone and it shows PORT Summary USB::001::009::0 Samsung product 665B (interface 00) and then fails detection.
Any ideas?

```
steve@steve-desktop:~$ dmesg | grep usb
[   45.083896] usbcore: registered new interface driver usbfs
[   45.083913] usbcore: registered new interface driver hub
[   45.095476] usbcore: registered new device driver usb
[   45.175803] usb usb1: configuration #1 chosen from 1 choice
[   45.289714] usb usb2: configuration #1 chosen from 1 choice
[   46.021150] usb 1-10: new full speed USB device using ohci_hcd and address 2
[   46.224090] usb 1-10: configuration #1 chosen from 1 choice
[   46.561809] usb 1-10.1: new low speed USB device using ohci_hcd and address 3
[   46.674786] usb 1-10.1: configuration #1 chosen from 1 choice
[   46.889595] usb 1-10.3: new low speed USB device using ohci_hcd and address 4
[   47.003583] usb 1-10.3: configuration #1 chosen from 1 choice
[   47.010524] usbcore: registered new interface driver hiddev
[   47.015643] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-10/1-10.1/1-10.1:1.0/input/input1
[   47.024525] input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:02.0-10.1
[   47.034722] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:02.0/usb1/1-10/1-10.1/1-10.1:1.1/input/input2
[   47.056502] input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:02.0-10.1
[   47.062607] input: Technology Switch as /devices/pci0000:00/0000:00:02.0/usb1/1-10/1-10.3/1-10.3:1.0/input/input3
[   47.076471] input,hidraw2: USB HID v1.10 Keyboard [Technology Switch] on usb-0000:00:02.0-10.3
[   47.082566] input: Technology Switch as /devices/pci0000:00/0000:00:02.0/usb1/1-10/1-10.3/1-10.3:1.1/input/input4
[   47.096449] input,hidraw3: USB HID v1.10 Mouse [Technology Switch] on usb-0000:00:02.0-10.3
[   47.096460] usbcore: registered new interface driver usbhid
[   47.096463] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  425.629115] usb 1-5: new full speed USB device using ohci_hcd and address 5
[  425.856738] usb 1-5: configuration #2 chosen from 1 choice
[  426.066621] usbcore: registered new interface driver cdc_acm
[  426.067111] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[  449.537743] usb 1-5: USB disconnect, address 5
[  451.228112] usb 1-5: new full speed USB device using ohci_hcd and address 6
[  451.455701] usb 1-5: configuration #1 chosen from 1 choice
[ 1638.001525] usb 1-5: USB disconnect, address 6
[ 3255.662119] usb 1-5: new full speed USB device using ohci_hcd and address 7
[ 3255.886509] usb 1-5: configuration #2 chosen from 1 choice
[ 3279.550836] usb 1-5: USB disconnect, address 7
[ 3281.241132] usb 1-5: new full speed USB device using ohci_hcd and address 8
[ 3281.466489] usb 1-5: configuration #1 chosen from 1 choice
[ 3387.215705] usb 1-5: USB disconnect, address 8
[ 6944.313042] usb 1-5: new full speed USB device using ohci_hcd and address 9
[ 6944.539654] usb 1-5: configuration #1 chosen from 1 choice

```

---

### Post by bossa on 2008-05-05
I tried setting the phone to "mass storage" but ubuntu does not see it. Tried setting the phone to "pictbridge" Ubuntu recognizes as a camera and asks if I would like to download images ,unfortunately there are no images in the box that opens :confused:. I have tried with PCLinuxOS in "mass storage" and the phone is recognized and I can download photos and video that I have transfered to the micro card in the phone. There must be a way to get Ubuntu to do this.....please 8-[

---

### Post by bossa on 2008-05-05
bump

---

### Post by bossa on 2008-05-06
if I can get Ubuntu to access the photos with the phone in pictbridge or as a mass storage drive it would be great (Via USB). I can do this in PCLinuxOS and Mandriva no problem, also I transfer files (Mp3 /photos/Mp4)to the micro card. 
Anyone know how I can do this ? Any advice will be much apreciated.

---

### Post by bossa on 2008-05-06
bump

---

### Post by bossa on 2008-05-07
bump

---

### Post by Thelasko on 2008-05-13
I have the same issue.  It lists the phone as not available.  When I try to connect to it manually it crashes.

Edit:
I'm using a Motorola V3 "RAZR" on Gusty Gibbon.

---

### Post by Thelasko on 2008-05-13
Sounds like the problem is the phone gets installed with root access by default.  Therefore, you can see the phone is available but you can't do anything with it as a normal user.

You can either run BitPim as root, i.e. typing:```
sudo bitpim
```which I don't recommend for security and reliability reasons, or you can try following the instructions [posted here.]("http://www.bitpim.org/help/howto-linuxusb.htm")

---

### Post by Greenskycity on 2008-07-20
I've got a Razr and I set it to connect via USB.  On the phone I go to menu/settings/connections/USB settings/ and for default connection I use Memory card.  when I plug it into my new Hardy install it shows up as a 125.9meg media player on my desktop and launches Rythmbox.  I just drag and drop files though, I don't use it other than to charge my phone.  I also did nothing else to the OS, it just did it magically, unlike windows that had to be hacked to work.
Green
I should mention that mine is a V3T through T-mobile.

---

### Post by Thelasko on 2008-07-21
Yeah, I posted that before I upgraded to Hardy.  I must say Hardy is a massive leap forward.  For the Razr, I found Moto4lin to work much better than bitpim.  I since switched to a Sony Ericsson W580i.  I don't need any special software, if I use bluetooth.

---

