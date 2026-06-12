---
title: "Kodak ESP 1.2 Printer &amp; Ubuntu"
date: 2013-02-27
forum: Hardware
---

### Post by roly33 on 2013-02-27
I'm currently running Windows 8 Pro on my Laptop & I'm considering switching to Ubuntu, but I've got a Kodak ESP1.2 AIO Printer, and wondered  if the Printer will work with Ubuntu? 

Roland

---

### Post by CharlesA on 2013-02-27
I don't know what they are talking about, but have a read:
[http://askubuntu.com/questions/195304/kodak-esp-1-2-printer-not-printing-on-ubuntu-12-04](http://askubuntu.com/questions/195304/kodak-esp-1-2-printer-not-printing-on-ubuntu-12-04)

---

### Post by paulnewall on 2013-02-27
The link in the reply above suggests that you can tell the printer setup tool to use the (ppd file for the) Hero 9.1 printer. And the Kodak ESP 1.2 (and presumably also the ESP 3.2) will print.
Since the ESP 1.2 and 3.2 do not have some of the features of the Hero 9.1 (like the photo paper tray and duplex) It might be better to tell the setup tool they are a Hero 3.1

To scan, you would need SANE. I might need to add these printers to the sane backend before they will work. Can anyone tell me the USB ID for them?
Running lsusb in a terminal might find the USB ID.

---

### Post by roly33 on 2013-03-22
I've tried using the Hero 9.1 ppd file but when I print a test page I get a printer already in use error.  I might give the Hero 3.2 ppd file a go though.

Roland

---

### Post by roly33 on 2013-03-22
> **paulnewall said:**
> The link in the reply above suggests that you can tell the printer setup tool to use the (ppd file for the) Hero 9.1 printer. And the Kodak ESP 1.2 (and presumably also the ESP 3.2) will print.
Since the ESP 1.2 and 3.2 do not have some of the features of the Hero 9.1 (like the photo paper tray and duplex) It might be better to tell the setup tool they are a Hero 3.1

To scan, you would need SANE. I might need to add these printers to the sane backend before they will work. Can anyone tell me the USB ID for them?
Running lsusb in a terminal might find the USB ID.

There was no Hero 3.1 ppd file in the Printer settings of 13.04 so I used the Hero 3.1 one and my esp 1.2 Printed the Test Page via Wifi , so one happy bunny, as I don't scan much I'm in no rush to setup the scanning as I only really use Printing & Copying.

Roland

---

